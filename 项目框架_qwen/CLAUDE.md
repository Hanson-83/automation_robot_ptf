# CLAUDE.md

@AGENTS.md

> 本文件是 Claude Code 平台的入口文件。上方通过 @ 引用同目录的 AGENTS.md，将项目主 Agent 规范（角色定义、行为规范、技术约定、规则、约束与安全要求，唯一事实来源）自动加载进每次会话的上下文，无需重复维护。

## 会话启动流程

按 `AGENTS.md` 第 3.1 节执行：阅读 `ref/project.md` → `ref/progress.md` → `ref/issues.md`，快速掌握项目现状后再开始工作。

## 其他项目文档（按需查阅）

以下仅给出路径，不使用 `@` 自动加载——执行任务时由你（智能体）根据任务需要自行决定是否阅读（文档地图详见 `AGENTS.md` 第 7 节）：

- `ref/requirements.md` — 具体需求与问题定义
- `ref/environments.md` — 开发/测试/部署环境与 AI Agent 平台矩阵
- `ref/workflow.md` — 标准工作流与文档联动规则
- `ref/plan.md` — 项目规划（含 `ref/design_spec.md`、`ref/test_plan.md`、`ref/execution_plan.md`）
- `ref/risks.md` — 风险登记册
- `ref/lessons_learned.md` — 经验教训（开始新任务前建议按关键词检索）
- `ref/operation_log.md` — 风险操作日志
- `ref/RTM.md` — 需求追踪矩阵
- `ref/handover.md` — 工作交接
- `doc/technical_manual.md` — 技术说明手册
- `doc/` — 专题报告目录（模版：`doc/topic_report_template.md`）

> **给其他平台的迁移提示**：Cursor（`.cursor/rules`）、Hermes、OpenClaw、Open Code、Codex（原生读取 `AGENTS.md`）等平台同理——保持各平台入口文件只做对 `AGENTS.md` 的引用（支持自动加载语法时可用类似 `@` 的机制），不要复制维护多份规范；其余文档同样只给路径、按需加载。
