# 📈 Agentic-Trade-Observer (智能投研与自动化分析系统)

> 🚀 **Status:** MVP (Minimum Viable Product) Phase / Architecture Verification
> 💡 **Core:** Multi-Agent Collaboration & Long-chain Reasoning

## 📖 项目简介
本项目是一个基于大语言模型（LLMs）驱动的多 Agent 协同投研分析系统。旨在解决高频变动市场（如 ETH/USDT）中，单一技术指标（如 MACD 策略）容易产生假信号的痛点。通过引入多 Agent 架构，系统能够自动完成“信号捕捉 -> 多维信息交叉验证 -> 历史回溯 -> 研判归档”的全流程自动化。

## ⚙️ 核心架构 (Multi-Agent 协作流)
系统底层根据任务复杂度动态路由，目前设计包含三个核心 Agent：

1. **🔔 Sensor Agent (数据感知)**: 
   - 监听 TradingView 等平台的 Webhook 报警。
   - 同步抓取科技简报、X（Twitter）动态等行业情绪数据。
2. **🧠 Reasoning Agent (长链推理 - 核心)**:
   - 接收到异动信号后，触发长链推理工作流。
   - 执行逻辑：技术面初步验证 ➡️ 基本面/情绪面交叉验证 ➡️ 胜率与盈亏比测算。
   - **痛点解决**：深度过滤无效噪音，阻断高达 70% 的技术面“假突破”信号。
3. **💾 Execution Agent (沉淀与执行)**:
   - 将结构化的深度分析报告通过 API 自动推送到 Notion 看板。
   - 同步沉淀至 Obsidian 知识库，构建个人投研大脑。

## 🛠 技术栈
- **Infrastructure**: Vercel (Serverless Functions)
- **Framework**: Next.js / Node.js
- **LLM Integration**: Claude / Gemini / GPT (Dynamic Routing)
- **Data & APIs**: TradingView Webhooks, Notion API, Obsidian Sync

## 🚀 为什么需要算力支持 (Roadmap)
目前的 MVP 版本在小规模测试中已经验证了逻辑的闭环，但我将大部分时间节省下来的同时，也遇到了瓶颈：
**深度的长链推理（Long-chain Reasoning）和多 Agent 之间的 Context 共享需要极大的 Token 消耗。** 
未来计划接入更高维度的实时流数据并优化 Agent 的反思（Reflection）机制，因此迫切需要引入更强大的底层模型算力支持（如 MiMo）来完成系统的全面进化。
