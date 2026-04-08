# AI-From-Zero

🤖 AI knowledge for everyone - concepts, tools & resources explained in simple terms | AI知识科普

---

## 📚 文章列表

快速导航：

- [大模型基础](#大模型基础)
- [Prompt 工程](#prompt-工程)
- [RAG 与知识图谱](#rag-与知识图谱)
- [推荐系统](#推荐系统)
- [Agent 与 OpenClaw](#agent-与-openclaw)

### 大模型基础

- [什么是 LLM 蒸馏技术](./20260209-what-is-LLM-distill/what-is-LLM-distill.md) - 大语言模型知识蒸馏技术解析
- [什么是 Transformer](./20260209-what-is-Transformer/what-is-Transformer.md) - Transformer 架构详解：从原理到优化
- [什么是 LLM Fine-tuning](./20260212-what-is-LLM-Fine-tuning/what-is-LLM-Fine-tuning.md) - 大语言模型微调技术详解
- [什么是 LoRA](./20260213-what-is-LoRA/what-is-LoRA.md) - LoRA 低秩适配技术详解：用 1.6% 的参数微调大模型
- [什么是 MoE 模型](./20260215-what-is-MoE-model/what-is-MoE-model.md) - MoE 混合专家模型详解：用稀疏激活实现高效扩展
- [什么是 AI 幻觉](./20260217-what-is-ai-hallucination/what-is-ai-hallucination.md) - AI 幻觉技术原理详解：从成因到 Text2SQL 实战
- [什么是 Tokenization](./20260222-what-is-tokenization-in-llm/what-is-tokenization-in-llm.md) - 深入理解 LLM 的语言编码：为什么 ChatGPT 要把"人工智能"拆成两个 Token？
- [困惑度（Perplexity）：评估大语言模型的核心指标](./20260226-what-is-perplexity-in-LLM/20260226-what-is-perplexity-in-LLM/what-is-perplexity-in-LLM.md)
- [什么是 n-grams 语言模型](./20260302-what-is-ngrams-language-model/what-is-ngrams-language-model.md) - n-grams 语言模型详解：从统计规律到现代语言模型
- [什么是 RNN 长距离依赖](./20260302-what-is-rnn-long-distance-dependency/what-is-rnn-long-distance-dependency.md) - RNN 长距离依赖问题详解：从梯度消失到 Transformer
- [什么是贪心搜索？为什么它会让生成的文本变得单调重复？](./20260303-what-is-greedy-search/what-is-greedy-search.md)
- [什么是随机采样](./20260303-what-is-random-sampling/what-is-random-sampling.md) - 随机采样技术详解：从贪心搜索到温度控制
- [什么是 top-k 采样](./20260303-what-is-top-k-sampling/what-is-top-k-sampling.md) - top-k 采样技术详解：在合理性与多样性间取得平衡
- [什么是 Temperature](./20260304-what-is-temperature-parameter/what-is-temperature-parameter.md) - 温度参数详解：控制 AI 的创造性和保守性
- [什么是"大数据+大模型"范式](./20260305-what-is-big-data-big-model/what-is-big-data-big-model.md) - "大数据+大模型"范式详解：从规模定律到涌现能力
- [什么是Decoder-only架构？为什么GPT系列专注于预测下一个词？](./20260305-what-is-decoder-only/what-is-decoder-only.md)
- [什么是Encoder-only架构？为什么BERT只需要"读懂"而不需要"生成"？](./20260305-what-is-encoder-only/what-is-encoder-only.md)
- [什么是模型架构的能力扩展？为什么规模扩大后会出现新能力？](./20260306-what-is-emergent-abilities/what-is-emergent-abilities.md)
- [什么是Encoder-Decoder架构？为什么翻译任务需要两个网络配合？](./20260306-what-is-encoder-decoder/what-is-encoder-decoder.md)
- [什么是KV Cache？为什么推理时要缓存之前的计算结果？](./20260306-what-is-kv-cache/what-is-kv-cache.md)
- [什么是模型架构的能力增强？为什么更大的模型能记住更多知识？](./20260306-what-is-model-scaling/what-is-model-scaling.md)
- [什么是混合专家模型（MoE）？为什么让不同专家处理不同任务更高效？](./20260306-what-is-moe/what-is-moe.md)
- [什么是位置编码？为什么Transformer需要知道词的顺序？](./20260306-what-is-positional-encoding/what-is-positional-encoding.md)
- [什么是稀疏激活？为什么不是所有参数都要参与每次计算？](./20260306-what-is-sparse-activation/what-is-sparse-activation.md)
- [什么是模型架构的历史演变？为什么Transformer成为主流选择？](./20260307-what-is-model-architecture-evolution/what-is-model-architecture-evolution.md)
- [什么是多头注意力？为什么从多个角度理解句子更全面？](./20260307-what-is-multi-head-attention/what-is-multi-head-attention.md)

### Prompt 工程

- [什么是思维链（Chain-of-Thought）？为什么让AI"一步步思考"更准确？](./20260311-what-is-chain-of-thought/what-is-chain-of-thought.md)
- [什么是少样本学习？为什么给几个例子就能让AI学会新任务？](./20260311-what-is-few-shot-learning/what-is-few-shot-learning.md)
- [什么是上下文学习？为什么在Prompt中包含示例如此有效？](./20260311-what-is-in-context-learning/what-is-in-context-learning.md)
- [什么是Prompt工程？为什么提示词的质量决定AI输出的好坏？](./20260311-what-is-prompt-engineering/what-is-prompt-engineering.md)
- [什么是Prompt模板？为什么标准化的格式能提高稳定性？](./20260311-what-is-prompt-template/what-is-prompt-template.md)
- [什么是角色扮演Prompt？为什么给AI设定身份能提升表现？](./20260311-what-is-role-playing-prompt/what-is-role-playing-prompt.md)
- [什么是零样本学习？为什么好的Prompt能让AI直接解决问题？](./20260311-what-is-zero-shot-learning/what-is-zero-shot-learning.md)
- [什么是自动Prompt优化？为什么需要算法来寻找最佳提示词？](./20260320-what-is-automatic-prompt-optimization/what-is-automatic-prompt-optimization.md)
- [什么是多轮对话Prompt？为什么上下文管理对聊天机器人至关重要？](./20260320-what-is-multi-turn-dialogue-prompt/what-is-multi-turn-dialogue-prompt.md)
- [什么是Prompt注入攻击？为什么恶意输入能操控AI行为？](./20260320-what-is-prompt-injection-attack/what-is-prompt-injection-attack.md)

### RAG 与知识图谱

- [什么是 RAG](./20260212-what-is-RAG/what-is-RAG.md) - 检索增强生成技术详解：让 AI 告别幻觉
- [什么是向量嵌入](./20260217-what-is-vector-embedding/what-is-vector-embedding.md) - Vector Embedding 详解：从文本到向量的语义转换
- [什么是向量数据库](./20260221-what-is-vector-database/what-is-vector-database.md) - 向量数据库入门：从精确匹配到语义理解
- [模态编码：让计算机统一理解多种形式信息的方法论](./20260222-what-is-multimodal-encoding/20260222-what-is-multimodal-encoding.md)
- [什么是外在评估](./20260304-what-is-extrinsic-evaluation/what-is-extrinsic-evaluation.md) - 外在评估详解：从实际应用效果衡量AI性能
- [RAG向量数据库如何实现增量更新？](./20260320-ragn-vector-database-incremental-update/ragn-vector-database-incremental-update.md)
- [什么是上下文压缩？如何减少Token消耗？](./20260320-what-is-context-compression/what-is-context-compression.md)
- [CRF和BERT做命名实体识别有什么区别？如何选择合适的方法？](./20260320-what-is-crf-vs-bert-ner/what-is-crf-vs-bert-ner.md)
- [什么是GraphRAG？知识图谱如何增强RAG系统？](./20260320-what-is-graph-rag/what-is-graph-rag.md)
- [知识工程和知识图谱有什么区别？如何构建完整的知识体系？](./20260320-what-is-knowledge-engineering-vs-knowledge-graph/what-is-knowledge-engineering-vs-knowledge-graph.md)
- [什么是知识图谱？实体、关系、属性分别是什么？](./20260320-what-is-knowledge-graph/what-is-knowledge-graph.md)
- [什么是知识图谱补全？如何预测缺失的关系？](./20260320-what-is-knowledge-graph-completion/what-is-knowledge-graph-completion.md)
- [RAG系统中如何处理多跳问答（Multi-hop QA）？](./20260320-what-is-multi-hop-qa-in-rag/what-is-multi-hop-qa-in-rag.md)
- [RAG系统如何支持多模态检索？图文检索如何实现？](./20260320-what-is-multimodal-retrieval/what-is-multimodal-retrieval.md)
- [什么是Self-RAG？如何让模型自主判断是否需要检索？](./20260320-what-is-self-rag/what-is-self-rag.md)
- [TransE、DistMult、ComplEx有什么区别？知识图谱嵌入方法如何选择？](./20260330-what-is-comparison-of-knowledge-graph-embedding-methods/what-is-comparison-of-knowledge-graph-embedding-methods.md)
- [什么是远程监督？怎么自动生成训练数据？](./20260330-what-is-distant-supervision/what-is-distant-supervision.md)
- [什么是 GraphRAG？知识图谱如何增强 RAG 系统？](./20260330-what-is-graphrag/what-is-graphrag.md)
- [知识融合(Knowledge Fusion)是什么？多个知识源怎么整合？](./20260330-what-is-knowledge-fusion/what-is-knowledge-fusion.md)
- [什么是RAG文档切分策略？](./20260330-what-is-rag-document-chunking-strategy/what-is-rag-document-chunking-strategy.md)
- [什么是RAG中的幻觉问题？引用溯源如何实现？](./20260330-what-is-rag-hallucination-citation/what-is-rag-hallucination-citation.md)
- [什么是Semantic Chunking？与固定长度切分有什么区别？](./20260330-what-is-semantic-chunking/what-is-semantic-chunking.md)

### 推荐系统

- [怎么用大模型生成推荐的训练数据？Data Augmentation怎么做？](./20260330-how-to-use-llm-generate-recommendation-training-data/how-to-use-llm-generate-recommendation-training-data.md)
- [强化学习在广告算法里怎么用？长期收益怎么建模？](./20260330-reinforcement-learning-in-advertising/reinforcement-learning-in-advertising.md)
- [推荐系统怎么做AB测试？线上指标有哪些？](./20260330-what-is-ab-test-in-recommendation-system/what-is-ab-test-in-recommendation-system.md)
- [什么是协同过滤？User-based和Item-based有什么区别？](./20260330-what-is-collaborative-filtering/what-is-collaborative-filtering.md)
- [内容推荐和协同过滤各有什么优缺点？](./20260330-what-is-content-based-vs-collaborative-filtering/what-is-content-based-vs-collaborative-filtering.md)
- [什么是连续特征离散化？分桶(Bucketing)有什么技巧？](./20260330-what-is-continuous-feature-discretization/what-is-continuous-feature-discretization.md)
- [广告推荐和内容推荐有什么区别？eCPM是怎么计算的？](./20260330-what-is-difference-between-advertising-and-content-recommendation/what-is-difference-between-advertising-and-content-recommendation.md)
- [什么是曝光去偏(Exposure Debiasing)？怎么处理没曝光的物品？](./20260330-what-is-exposure-debiasing/what-is-exposure-debiasing.md)
- [什么是特征交叉？为什么它是推荐系统的秘密武器？](./20260330-what-is-feature-crossing/what-is-feature-crossing.md)
- [什么是漏斗转化？从曝光到点击到转化怎么优化？](./20260330-what-is-funnel-conversion/what-is-funnel-conversion.md)
- [图神经网络(GNN)怎么用在推荐系统里？](./20260330-what-is-gnn-in-recommendation-system/what-is-gnn-in-recommendation-system.md)
- [什么是信息茧房？推荐系统怎么平衡个性化和多样性？](./20260330-what-is-information-bubble/what-is-information-bubble.md)
- [什么是知识图谱增强推荐？实体和关系怎么建模？](./20260330-what-is-knowledge-graph-enhanced-recommendation/what-is-knowledge-graph-enhanced-recommendation.md)
- [什么是LLM冷启动推荐？新用户对话几轮就能精准推荐？](./20260330-what-is-llm-cold-start-recommendation/what-is-llm-cold-start-recommendation.md)
- [推荐系统怎么结合大模型的常识推理能力？](./20260330-what-is-llm-commonsense-reasoning-recsys/what-is-llm-commonsense-reasoning-recsys.md)
- [怎么用大模型生成推荐理由？解释性推荐怎么做？](./20260330-what-is-llm-explainable-recommendation/what-is-llm-explainable-recommendation.md)
- [大模型能直接做推荐吗？和传统推荐模型有什么区别？](./20260330-what-is-llm-recommendation/what-is-llm-recommendation.md)
- [什么是大模型推荐的成本控制与推理加速？](./20260330-what-is-llm-recommendation-cost-control/what-is-llm-recommendation-cost-control.md)
- [什么是LLM做推荐的三种范式？Prompt-based、Embedding-based、Fine-tuning深度解析](./20260330-what-is-llm-recommendation-paradigms/what-is-llm-recommendation-paradigms.md)
- [什么是多行为推荐？点击、收藏、购买如何融合？](./20260330-what-is-multi-behavior-recommendation/what-is-multi-behavior-recommendation.md)
- [什么是大模型多轮对话式推荐？如何维护对话上下文？](./20260330-what-is-multi-turn-conversational-recommendation/what-is-multi-turn-conversational-recommendation.md)
- [推荐模型的Negative Sampling怎么做？随机负采样够吗？](./20260330-what-is-negative-sampling-in-recommendation/what-is-negative-sampling-in-recommendation.md)
- [什么是实时竞价(RTB)？广告竞价的毫秒级博弈](./20260330-what-is-real-time-bidding/what-is-real-time-bidding.md)
- [什么是实时用户兴趣？怎么捕捉用户的即时意图？](./20260330-what-is-real-time-user-interest/what-is-real-time-user-interest.md)
- [推荐系统的多样性(Diversity)怎么衡量？怎么避免推荐结果太单一？](./20260330-what-is-recommender-system-diversity/what-is-recommender-system-diversity.md)
- [什么是社交推荐？社交关系图如何提升推荐效果](./20260330-what-is-social-recommendation/what-is-social-recommendation.md)
- [什么是推荐系统中的负反馈？用户的"踩"和"不感兴趣"怎么用？](./20260330-what-is-user-negative-feedback-in-recommendation/what-is-user-negative-feedback-in-recommendation.md)
- [什么是用户画像？为什么电商平台比你更懂你自己？](./20260330-what-is-user-profile/what-is-user-profile.md)
- [什么是用户短期兴趣和长期兴趣建模？](./20260330-what-is-user-short-term-and-long-term-interest-modeling/what-is-user-short-term-and-long-term-interest-modeling.md)
- [大模型时代，推荐算法工程师还需要什么技能？](./20260331-what-is-llm-era-recsys-engineer-skills/what-is-llm-era-recsys-engineer-skills.md)
- [推荐系统的 Prompt 设计：如何把用户历史行为融入 Prompt？](./20260331-what-is-prompt-design-for-recommendation-system/what-is-prompt-design-for-recommendation-system.md)
- [推荐系统的实时性如何保证？用户点击后下一刷能推相似内容吗？](./20260331-what-is-realtime-recommendation-system/what-is-realtime-recommendation-system.md)
- [推荐系统的召回、粗排、精排、重排分别是干什么的？](./20260331-what-is-recall-ranking-pipeline-in-recommendation/what-is-recall-ranking-pipeline-in-recommendation.md)
- [什么是目标注意力（Target Attention）？DIN 深度解析](./20260331-what-is-target-attention-and-din/what-is-target-attention-and-din.md)

### Agent 与 OpenClaw

- [什么是 AI Agent](./20260214-what-is-AI-Agent/what-is-AI-Agent.md) - AI Agent 智能体详解：从工具到数字员工
- [什么是Skills？为什么说Skill是被"理解"而不是被"执行"的？](./20260308-what-are-skills/what-are-skills.md)
- [OpenClaw 和传统 Chatbot 的本质区别是什么?](./20260308-what-is-difference-between-openclaw-and-chatbot/what-is-difference-between-openclaw-and-chatbot.md)
- [什么是OpenClaw？为什么它是一个能真正"干活"的AI助理？](./20260308-what-is-openclaw/what-is-openclaw.md)
- [什么是向量数据库？为什么OpenClaw需要它来存储记忆？](./20260308-why-does-openclaw-use-vector-database/why-does-openclaw-use-vector-database.md)
- [如果一个Skill执行耗时很长，你会如何处理？](./20260310-handling-long-running-skills/handling-long-running-skills.md)
- [你认为当前LLM哪些能力瓶颈最制约OpenClaw的上限？](./20260310-llm-bottlenecks-limiting-openclaw/llm-bottlenecks-limiting-openclaw.md)
- [OpenClaw的持久化记忆是什么原理？本地存储和向量数据库方案各有什么局限？](./20260310-openclaw-persistent-memory-principles/openclaw-persistent-memory-principles.md)
- [OpenClaw如何防备提示词注入？](./20260310-openclaw-prompt-injection-defense/openclaw-prompt-injection-defense.md)
- [OpenClaw Skill和OpenAI Function Calling有何异同？](./20260310-openclaw-skill-vs-function-calling/openclaw-skill-vs-function-calling.md)
- [聊聊OpenClaw可能在哪里依赖结构化JSON？](./20260310-openclaw-structured-json-dependencies/openclaw-structured-json-dependencies.md)
- [调用OpenClaw和调用普通API有什么区别？](./20260310-openclaw-vs-traditional-api/openclaw-vs-traditional-api.md)
- [一个Skill需要串行调用三个外部API，如何正确处理局部失败？](./20260310-skill-api-error-handling/skill-api-error-handling.md)
- [为什么OpenClaw在实时推送场景下选择拥抱WebSocket？](./20260310-why-openclaw-chooses-websocket/why-openclaw-chooses-websocket.md)
- [为什么提示词注入在OpenClaw场景更危险？](./20260310-why-prompt-injection-more-dangerous-in-openclaw/why-prompt-injection-more-dangerous-in-openclaw.md)
- [DST 怎么处理多轮对话？历史轮次的信息怎么利用？](./20260318-what-is-dst-history-management/what-is-dst-history-management.md)
- [OpenClaw如何控制上下文不超过Context Window？](./20260320-openclaw-context-window-management/openclaw-context-window-management.md)
- [如何对OpenClaw龙虾做最小权限设计？](./20260320-openclaw-least-privilege-design/openclaw-least-privilege-design.md)

---
## 🤝 贡献

由于个人能力有限，难免会有错误，欢迎大家指正！

任何形式的贡献或者讨论都十分欢迎：

- 💬 提交 [Issue](https://github.com/laizhuoc/AI-From-Zero/issues) 反馈问题或建议
- 🔧 直接提交 [PR](https://github.com/laizhuoc/AI-From-Zero/pulls) 贡献内容

---

## ⭐ Star

如果觉得有帮助，欢迎点个 Star ⭐ 支持一下！
