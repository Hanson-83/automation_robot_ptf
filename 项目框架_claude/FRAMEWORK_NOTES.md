# Framework Notes — 综合取舍与版本记录

本文件记录 claude 版框架相对 `项目框架_doubao` 与 `项目框架_qwen` 的综合设计决策，便于回溯与后续迭代。**本文件是框架元信息，迁移到实际项目时可不带走。**

## 1. 设计目标

在**保持清晰、完整**的前提下**尽量精简**，产出一套可复制迁移、适用于机器人/自动化/数字化/系统集成/软件/AI Agent 领域的通用文档框架。

- **精简程度**：适度精简——核心 14 文档 + 可选 4 文档，明确「必选/可选」，仅合并少数高度重叠项。
- **示例策略**：每模板内联基于真实机器人项目（宇树 H2 / VLA / 试管取放）的样例，统一用 `〔…〕` 占位约定（`〔示例：…〕`）标注，正式使用前替换或删除。
- **平台约定**：技术栈保持 Ubuntu 优先，跨平台作为兼容性评估项；已有项目二开时遵循原项目约定。

## 2. 两套源模板的取长补短

| 采纳自 doubao | 采纳自 qwen |
|---|---|
| 6 步工作闭环（探查→约束→证据→执行→验证→交付） | 人工必停点（Human Checkpoints） |
| 更新频率分类学（低/中/高/按需） | 委派 5 要素 + 委派跟踪表(D-001) |
| 必选/可选显式标注 | 风险登记的「可观察性/早期信号」维度 |
| 阶段门(Gate)规则 | ISO 10218 / ISO-TS 15066 机器人安全标准 |
| framework_structure.html 结构图 | HIL/SIL + 急停/联锁安全测试 |
| §0 项目标识表 | 每文档头/尾元信息块（本版精简为单行） |

## 3. 相对两版的精简/合并决策

| 决策 | 处理 | 理由 |
|---|---|---|
| `execution_plan.md` | 合并进 `plan.md`（新增 WBS/排期/委派表） | 与 plan 里程碑、progress 高度重叠 |
| `risks.md` | 降为可选；默认由 `progress.md` 风险摘要承载 | 消除 risks↔progress 冗余 |
| `RTM.md` | 保留但降为可选（中大型项目建议启用） | 小项目过重 |
| `design_spec.md` / `test_plan.md` | 保留为可选（默认内联 plan.md，规模大再拆） | 沿用 doubao |
| ADR 记录 | 单一归属于 `plan.md`，design_spec 仅引用 | 消除 ADR 双写 |
| 里程碑/状态 | plan 定义计划、progress 追踪实际，其余只引用 | 单一事实源 |
| 文档头/尾元信息块 | 精简为单行 | 保留可追溯，去冗长 |
| 备份文件 | 不放进模板树，仅在此说明命名规则 | 避免工作树杂乱 |

## 4. 文档清单

- **核心 14（默认全保留）**：AGENTS、CLAUDE、workflow、project、requirements、environments、plan、progress、issues、operation_log、lessons_learned、handover、doc/technical_manual、doc/topic_report。
- **可选 4（不用即删/变大再拆）**：risks、RTM、design_spec、test_plan。
- **框架元 3（迁移可不带）**：README、FRAMEWORK_NOTES、framework_structure.html。

## 5. 已知局限与后续迭代建议

- **无自动校验**：ID 唯一性、交叉链接有效性、RTM 断链、准出门（P0 100%）目前靠纪律约定。后续可增补一个轻量 lint 脚本（检查断链/孤儿 ID）或 CI 钩子。
- **示例需清理**：正式使用前须替换或删除所有 `〔…〕` 占位（含 `〔示例：…〕`）——见 README「占位约定」。
- **跨平台约定**：当前 Ubuntu 优先；若团队主力为 Windows/WSL，可在迁移时调整 AGENTS.md §4。

## 6. 版本记录

| 日期 | 版本 | 摘要 |
|---|---|---|
| 〔YYYY-MM-DD〕 | v1.0 | 初始版：综合 doubao/qwen，精简为 14 核心 + 4 可选 |
