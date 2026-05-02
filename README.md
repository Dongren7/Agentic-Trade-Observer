# 📈 Agentic-Trade-Observer (基于多 Agent 与自我回溯的智能投研系统)

> 🚀 **Status:** MVP (Minimum Viable Product) / Core Architecture Validation
> 🧠 **Core:** Multi-Agent Collaboration | Long-chain Reasoning | RAG-based Self-Reflection

## 📖 项目简介 (Introduction)

本项目是一个由大语言模型（LLMs）驱动、具备“记忆与反思”能力的自动化投研分析系统。
在高度波动的加密资产市场（如 ETH/USDT）中，传统的单一技术指标（如 MACD、RSI 突破）极易产生“假信号”（Fakeouts），导致频繁的无效交易。同时，常规的单次 AI 脚本调用缺乏“记忆力”，无法从过去的误判中吸取教训。

**Agentic-Trade-Observer** 旨在通过构建多 Agent 协作工作流，并深度整合 RAG（检索增强生成）技术，打造一个能够自动进行“信号捕捉 ➡️ 历史回溯 ➡️ 多维交叉验证 ➡️ 自我纠偏与归档”的进化型系统。

## ⚙️ 核心架构与多 Agent 工作流 (Architecture)

系统底层采用动态模型路由（Dynamic Routing），针对不同复杂度的任务调度最合适的底层模型，目前包含三个核心 Agent 和一个记忆中枢：

### 1. 🔔 Sensor Agent (数据感知与聚合引擎)
作为系统的“触觉神经”，主要负责高频实时数据的监控与粗筛。
- **异动监听**：实时接收来自 TradingView 等平台的 Webhook 预警（如关键阻力位突破、均线金叉）。
- **情绪面聚合**：同步抓取指定信息源（如特定的科技/加密简报、X平台重点关注列表）的最新动态，提供宏观环境上下文。

### 2. 🧠 Reasoning & Reflection Agent (长链推理与自我回溯中枢)
系统的“大脑”，负责执行高消耗、深层次的复杂推理。这是解决假信号痛点的核心。
- **RAG 历史检索**：当接收到新的突破信号时，主动访问“经验记忆库”（Obsidian），拉取过去 3 个月内类似形态的历史研判记录及其最终的真实走势结果。
- **历史总结与自我纠偏**：对比当前盘面与历史相似误判点，AI 会进行 Self-Correction（自我纠偏），评估当前信号是真实突破还是诱多/诱空的概率。
- **长链推演**：结合技术面（当前指标）、基本面（抓取的情绪资讯）以及回溯面（历史胜率），输出最终的置信度评分（Confidence Score）和盈亏比预期。

### 3. 💾 Execution Agent (沉淀与执行器)
负责执行最终的动作并持续扩充系统记忆。
- **自动化预警**：仅针对置信度极高（>80%）的信号，格式化深度研判报告，并通过 API 推送至 Notion 个人看板。
- **记忆沉淀**：将完整的分析逻辑、参考指标及预期走势写入 Obsidian 知识库。这一步至关重要，它为下一次的“自我回溯”提供了更庞大的基准数据，形成数据飞轮。

## 🛠 技术栈 (Tech Stack)
- **基础设施**: Vercel Serverless Functions (确保高并发与极速响应)
- **核心框架**: Next.js (TypeScript) / Node.js
- **大模型集成**: 支持一键切换调用不同维度的 LLM (如 MiMo, Claude, Gemini, DeepSeek)
- **外部集成**: TradingView Webhooks, Notion API, Obsidian Sync

## 🚀 演进路线 (Roadmap & Compute Needs)

目前 MVP 版本已在本地及小规模环境中跑通了闭环逻辑，成功利用历史回溯机制过滤了约 75% 的高频无效信号。
