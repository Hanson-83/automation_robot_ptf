# README — 项目框架说明

> 本框架是一套面向 **AI Agent 多智能体、多平台、跨环境协作** 的标准化、可复用项目文档框架，适用于 AI4S 自动化 & 机器人系统集成等软硬件一体项目。

## 目录结构

```
项目根目录/
├── AGENTS.md              # 主 Agent 规范入口（角色/规范/规则/约束/安全/文档地图），稳定低频维护，跨项目复用
├── CLAUDE.md              # Claude Code 平台入口，仅引用 AGENTS.md
├── README.md              # 本文件：框架使用说明
├── ref/                   # 项目参考与动态状态文档
│   ├── project.md         # 项目总览（背景/粗粒度目标/规划/环境概述），引用其余 ref/ 文档
│   ├── requirements.md    # 具体需求（FR/NFR/约束/变更记录）
│   ├── environments.md    # 开发/测试/部署环境 + AI Agent 平台矩阵
│   ├── workflow.md        # 标准工作流（阶段流转/多智能体协作流程/文档联动规则）
│   ├── plan.md            # 项目规划（方案选型/里程碑/ADR 索引）
│   ├── design_spec.md     # 设计规范（架构/接口/软硬件规范/详细设计）
│   ├── test_plan.md       # 测试规划（策略/用例/执行记录）
│   ├── execution_plan.md  # 执行计划（任务分解/委派跟踪）
│   ├── progress.md        # 进度（会话必读：状态快照/工作日志）
│   ├── risks.md           # 风险登记册（风险项/可能性/可观察性/影响/应对/状态）
│   ├── issues.md          # 问题清单（描述/状态/解决方案）
│   ├── lessons_learned.md # 经验教训（跨会话集体记忆）
│   ├── operation_log.md   # 风险操作日志（操作前登记→批准→执行→记录）
│   ├── RTM.md             # 需求追踪矩阵（需求→设计→实现→测试→验收）
│   └── handover.md        # 工作交接（按时间线累积交接记录）
└── doc/                   # 交付文档
    ├── technical_manual.md       # 技术说明手册（按里程碑滚动更新）
    └── topic_report_template.md  # 专题报告模版（复制后按专题重命名使用）
```

## 使用方法

1. **新项目初始化**：复制整个目录到新项目根目录；仅需更新 `AGENTS.md` 第 2 节（领域描述）与 `ref/` 下的项目内容；
2. **各平台接入**：Claude Code 读 `CLAUDE.md`；Cursor 在 `.cursor/rules`、Codex/OpenClaw 等读 `AGENTS.md` 或建对应入口文件，均只做一行引用，不复制规范；
3. **会话启动**：任何 Agent 会话开始按 `AGENTS.md` 第 3.1 节流程读取 `ref/project.md` → `ref/progress.md` → `ref/issues.md`；
4. **文档更新**：按 `AGENTS.md` 第 3.3 节的更新时机表执行；文档联动规则见 `ref/workflow.md` 第 3 节。

## 维护原则

- 稳定内容（规范/规则）进 `AGENTS.md`，动态内容进 `ref/`，交付内容进 `doc/`；
- 引用而非复制：文档间用相对路径链接，修改一处、处处生效；
- 所有动态文档"只增不删"（问题闭环移归档、交接按时间线追加），保证全程可追溯。

## 框架自身迭代

对框架模版本身的改进建议，记录在各项目的 `ref/lessons_learned.md` 中（标注"可跨项目复用"），定期汇总回本模版。
