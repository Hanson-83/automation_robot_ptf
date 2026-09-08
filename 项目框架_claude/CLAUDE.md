# CLAUDE.md — Claude Code 入口

> **权威规范**：@AGENTS.md
> 本文件为薄入口，Claude Code 会自动加载上面 `@` 引用的 AGENTS.md（规则单一事实源）。请勿在此复制规则内容。

## 会话启动必读（按顺序）

1. [`ref/project.md`](ref/project.md) — 项目背景与目标
2. [`ref/progress.md`](ref/progress.md) — 当前进度与状态（一句话摘要 + 下一步）
3. [`ref/issues.md`](ref/issues.md) — 待解决问题

## 按需查阅（不自动加载，用到再读）

- 需求细节：[`ref/requirements.md`](ref/requirements.md)
- 环境/凭据指引：[`ref/environments.md`](ref/environments.md)
- 规划/方案/ADR/里程碑：[`ref/plan.md`](ref/plan.md)
- 生命周期与协作流程：[`ref/workflow.md`](ref/workflow.md)
- 完整文档地图：见 AGENTS.md §7

## 多平台迁移提示

其他 Agent 平台（Cursor / Codex / Gemini / OpenCode 等）的入口文件（如 `.cursorrules`、`GEMINI.md`）**只写一行引用 AGENTS.md**，不复制规则；跨平台信息传递以本仓库 markdown 文档为共同介质。
