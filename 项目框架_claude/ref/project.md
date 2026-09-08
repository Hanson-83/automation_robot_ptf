# Project — 项目总览（宪章）

> **定位**：项目背景、粗粒度目标与环境总览（macro 视角）。 · **更新频率**：低频 · **上游**：[`AGENTS.md`](../AGENTS.md) · **下游**：[`requirements.md`](requirements.md)、[`plan.md`](plan.md)

## 1. 项目元信息

| 项 | 内容 |
|---|---|
| 项目名称 | 〔示例：Unitree H2 人形机器人具身智能系统〕 |
| 领域 | 〔示例：机器人 / 具身智能 / 实验室自动化〕 |
| 干系人 | 〔人类负责人、需求方、协作方〕 |
| 起止 | 〔开始日期 ~ 预计交付〕 |

## 2. 背景（Background）

<!-- 为什么做这个项目？业务/研究动因、现状痛点 -->
〔示例：公司采购宇树 H2 人形机器人，目标是以 AI 模型驱动机器人完成任务，主要面向药物发现实验室实验场景，兼顾接待/导览/展示/表演。正式使用时替换。〕

## 3. 粗粒度目标（Goals，按时序分层）

| 层级 | 目标 | 关键交付物 | 时限 |
|---|---|---|---|
| 短期 | 〔示例：打通单条简单 AI 驱动任务，产出 Demo 视频〕 | 〔Demo 系统 + 视频〕 | 〔3–6 个月〕 |
| 中期 | 〔示例：多步骤任务达可发表质量〕 | 〔可复现实验流程〕 | 〔6–12 个月〕 |
| 长期 | 〔示例：生产级多机多品牌多模型平台〕 | 〔客户端/网关 + 数据平台 + 训练/推理平台〕 | 〔12+ 个月〕 |

## 4. 粗粒度需求与设想（Idea）

<!-- 一段话描述要做成什么样，细化见 requirements.md -->
〔示例：构建可组合的三模块 Demo 系统——数据采集与回放、模型训练/评估/推理、机器人上位机客户端；采用开源预训练 VLA 模型完成试管取放任务。〕

## 5. 环境与配置总览

<!-- 概述即可，详情见 environments.md -->
- **硬件**：〔示例：H2 本体（31 关节）+ BrainCo 灵巧手 + PC1 运控主机/PC2 开发机 + RealSense 相机〕
- **开发/部署机**：〔示例：Dell 工作站(RTX 4090)、WSL、GPU87 服务器〕
- **网络**：〔有线/无线局域网，详见 environments.md〕
- 详情 → [`environments.md`](environments.md)

## 6. 关联文档索引

| 类别 | 文档 | 说明 |
|---|---|---|
| 需求 | [`requirements.md`](requirements.md) | FR/NFR/约束 |
| 环境 | [`environments.md`](environments.md) | 环境/平台/网络 |
| 流程 | [`workflow.md`](workflow.md) | 生命周期/协作 |
| 规划 | [`plan.md`](plan.md) | 方案/ADR/里程碑 |
| 进度 | [`progress.md`](progress.md) | 状态/任务/风险 |
| 交付 | [`../doc/technical_manual.md`](../doc/technical_manual.md) | 技术手册 |

## 7. 术语表（Glossary）

| 术语 | 含义 |
|---|---|
| 〔示例：VLA〕 | 〔Vision-Language-Action 模型〕 |
| 〔示例：HIL〕 | 〔Hardware-in-the-Loop 硬件在环测试〕 |

---
*最后更新：〔YYYY-MM-DD〕 | 更新人：〔填写〕*
