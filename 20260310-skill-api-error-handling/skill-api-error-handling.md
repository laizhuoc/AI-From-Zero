🚀 本文收录于Github：AI-From-Zero 项目 —— 一个从零开始系统学习 AI 的知识库。如果觉得有帮助，欢迎 ⭐ Star 支持！

# 一个Skill需要串行调用三个外部API，如何正确处理局部失败？

> by @Laizhuocheng

---

## 一、最常见的错误：一刀切的错误处理

串行调用三个API，最容易犯的错是把三个await直接写在一起，然后用一个try/catch包住——这意味着**任何一步失败都会中断后续步骤，也无法区分是哪一步出了问题，更无法决定是否要重试或跳过**。

**说人话就是：** 想象你要做一顿饭，需要买菜、洗菜、炒菜三个步骤。如果你采用"一刀切"的做法，买菜时发现超市关门了，你就直接放弃整顿饭，连家里已有的食材都不用了。但实际上，你可能家里还有存货，或者可以去其他地方买，或者干脆做个简单的面条。

在OpenClaw的Skill上下文里，Skill的结果最终会被Brain读取并决定下一步行动，所以**错误信息本身也是有价值的输出**——不应该只抛异常，而应该把每一步的成功或失败状态都结构化地返回给Brain，让LLM来决定如何处理局部失败。

---

## 二、策略一：强依赖链，任意失败即中止

### 适用场景
步骤之间有严格的数据依赖，中间结果缺失无法继续。

### 典型例子
获取用户信息 → 查询订单 → 获取物流详情（每步都依赖前一步的结果）

```javascript
// Skill: 获取用户信息 → 查询订单 → 获取物流详情
async function getOrderTrackingSkill(userId) {
  let user, orders, tracking;
  
  // 步骤一：获取用户
  try {
    user = await fetchUser(userId);
  } catch (err) {
    return { 
      success: false, 
      failedAt: 'fetchUser', 
      error: err.message 
    };
  }
  
  // 步骤二：查询订单（依赖 user.accountId）
  try {
    orders = await fetchOrders(user.accountId);
  } catch (err) {
    return { 
      success: false, 
      failedAt: 'fetchOrders', 
      error: err.message 
    };
  }
  
  // 步骤三：物流详情（依赖 orders[0].trackingId）
  try {
    tracking = await fetchTracking(orders[0]?.trackingId);
  } catch (err) {
    return { 
      success: false, 
      failedAt: 'fetchTracking', 
      error: err.message 
    };
  }
  
  return { success: true, user, orders, tracking };
}
```

### 关键优势
- **明确标注failedAt**：Brain能知道具体哪步失败
- **精准错误提示**：可以给用户更具体的反馈，而不是模糊的"操作失败"
- **保留部分数据**：即使失败，也可能包含有用的中间结果

---

## 三、策略二：弱依赖，局部失败用降级值填充

### 适用场景
某些步骤失败不影响整体流程，可以用默认值或空值继续。

### 典型例子
生成早报（日历 + 天气 + 邮件摘要，各自独立）

```javascript
// Skill: 生成早报（日历 + 天气 + 邮件摘要，各自独立）
async function morningBriefingSkill() {
  // 三个步骤并发发起，但各自独立捕获错误
  const [calendarResult, weatherResult, emailResult] = await Promise.allSettled([
    fetchCalendarEvents(),
    fetchWeather(),
    fetchEmailSummary(),
  ]);
  
  // 结构化每一步的结果
  const briefing = {
    calendar: calendarResult.status === 'fulfilled' 
      ? calendarResult.value 
      : { error: calendarResult.reason?.message || 'Unknown error', data: [] },
    weather: weatherResult.status === 'fulfilled' 
      ? weatherResult.value 
      : { error: weatherResult.reason?.message || 'Unknown error', data: null },
    email: emailResult.status === 'fulfilled' 
      ? emailResult.value 
      : { error: emailResult.reason?.message || 'Unknown error', data: [] },
  };
  
  // 告诉 Brain 哪些部分有问题
  const partialFailures = Object.entries(briefing)
    .filter(([, v]) => v.error)
    .map(([k, v]) => `${k}: ${v.error}`);
    
  return { 
    success: partialFailures.length === 0, 
    partialFailures, 
    briefing 
  };
}
```

### 关键工具：Promise.allSettled
- **不会短路**：一个Promise reject不会影响其他Promise
- **完整结果**：等待所有Promise完成，每个都标记fulfilled或rejected
- **灵活处理**：可以根据业务需求选择串行或并发执行

> **注意**：虽然示例使用并发，但如果业务要求串行，换回逐步await即可，错误处理结构不变。

---

## 四、策略三：带重试的串行调用

### 适用场景
外部API不稳定，瞬时失败应该重试而不是立刻上报错误。

### 重试工具函数
```javascript
async function withRetry(fn, { maxRetries = 3, baseDelay = 500 } = {}) {
  let lastError;
  for (let attempt = 0; attempt < maxRetries; attempt++) {
    try {
      return await fn();
    } catch (err) {
      lastError = err;
      // 不重试客户端错误（4xx），只重试服务端/网络错误
      if (err.status >= 400 && err.status < 500) throw err;
      if (attempt < maxRetries - 1) {
        const delay = baseDelay * Math.pow(2, attempt); // 指数退避
        await sleep(delay);
      }
    }
  }
  throw lastError;
}

const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));
```

### 在Skill中的应用
```javascript
async function robustSkill(input) {
  const step1 = await withRetry(() => callApiA(input), { maxRetries: 3 });
  const step2 = await withRetry(() => callApiB(step1.id), { maxRetries: 2 });
  const step3 = await withRetry(() => callApiC(step2.data), { maxRetries: 3 });
  return { step1, step2, step3 };
}
```

### 重试策略要点
- **指数退避**：避免频繁重试加重服务器负担
- **区分错误类型**：4xx错误（客户端错误）不重试，5xx错误（服务端错误）重试
- **限制重试次数**：避免无限重试导致任务长时间阻塞

---

## 五、把错误结构化返回给Brain是关键

OpenClaw的Brain是ReAct循环——它读Skill的输出，然后决定下一步Thought和Action。**如果Skill直接throw异常，Brain只能知道"Skill执行失败"；如果Skill把失败信息结构化返回，Brain可以做更细粒度的决策**。

### Skill返回格式的最佳实践
```javascript
// Skill 返回格式的约定（供 Brain 解析）
return {
  success: false,
  failedAt: 'fetchOrders',        // Brain 可以据此决策
  completedSteps: ['fetchUser'],  // 已完成的步骤
  partialData: { user },          // 部分数据仍可用
  error: 'Orders API timeout',    // 人类可读的错误描述
  retryable: true,                // 是否值得重试
  suggestedAction: 'ask_user_for_alternative_account' // 建议的下一步行动
};
```

### 结构化错误的优势
| 信息类型 | 传统异常 | 结构化返回 | Brain能做什么 |
|---------|---------|-----------|--------------|
| **失败位置** | 调用栈 | failedAt字段 | 精准定位问题 |
| **已完成步骤** | 无 | completedSteps | 避免重复执行 |
| **部分数据** | 无 | partialData | 利用已有信息 |
| **重试建议** | 无 | retryable字段 | 自动重试或询问用户 |
| **下一步建议** | 无 | suggestedAction | 智能决策 |

---

## 六、设计哲学：Skill输出要对LLM友好

这个设计哲学和OpenClaw的Skill是Markdown自然语言说明书的理念一致——**Skill不只是执行代码，它的输出要对LLM友好，让Brain能读懂发生了什么，而不是只看到一个二进制的成功/失败**。

### 对比两种设计思路
- **传统API设计**：成功返回数据，失败抛异常
- **Agent-friendly设计**：总是返回结构化结果，包含成功/失败的详细信息

### 实际效果差异
当用户问"我的订单到哪了？"：

**传统设计**：
- Skill失败 → Brain收到异常 → 回复"抱歉，查询失败了"

**结构化设计**：
- Skill返回`{success: false, failedAt: 'fetchOrders', partialData: {user: {...}}, error: 'No orders found'}`
- Brain理解"用户存在但没有订单" → 回复"您还没有下单，需要帮您创建订单吗？"

---

## 七、选择策略的决策树

面对串行API调用，如何选择合适的错误处理策略？

```
三个API调用是否有数据依赖？
├─ 是 → 是否允许部分成功？
│   ├─ 否 → 使用策略一（强依赖链）
│   └─ 是 → 使用策略二（弱依赖+降级）
└─ 否 → API是否稳定？
    ├─ 否 → 使用策略三（带重试）
    └─ 是 → 使用策略二（并发+独立错误处理）
```

### 实用建议
1. **优先考虑业务语义**：技术方案服务于业务需求
2. **总是结构化返回**：无论选择哪种策略，都要返回详细的状态信息
3. **为Brain提供决策依据**：错误信息要包含足够的上下文
4. **测试各种失败场景**：确保Skill在各种异常情况下都能优雅降级

在Agent时代，错误处理不再是简单的try/catch，而是**为智能决策提供高质量输入**的关键环节。