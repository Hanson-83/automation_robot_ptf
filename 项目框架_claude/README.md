# 通用项目管理框架（claude 版）

一套**可复制迁移**的项目文档框架，适用于**机器人、自动化、数字化、系统集成、软件应用、AI Agent 应用**等领域，支持**人机协作 + 多智能体 + 跨平台/跨环境**的项目全生命周期管理。

综合自 `项目框架_doubao` 与 `项目框架_qwen` 两套模板，取舍详见 [`FRAMEWORK_NOTES.md`](FRAMEWORK_NOTES.md)。

## 目录结构

```
项目框架_claude/
├── AGENTS.md                 # 主 Agent 权威规范（规则 SSOT）——迁移时主要改 §0/§2
├── CLAUDE.md                 # Claude Code 薄入口（@AGENTS.md）
├── README.md                 # 本文件：框架说明与初始化指南
├── FRAMEWORK_NOTES.md        # 相对 doubao/qwen 的综合取舍与版本记录
├── framework_structure.html  # 结构与引用关系图（浏览器打开）
├── ref/                      # 项目参考与动态状态
│   ├── workflow.md           # 生命周期/阶段门/必停点/委派流程
│   ├── project.md            # 项目宪章/背景/分层目标/文档索引
│   ├── requirements.md       # FR/NFR/约束/变更
│   ├── environments.md       # 环境/Agent 平台矩阵/网络协议/凭据指引
│   ├── plan.md               # 方案/ADR/里程碑/WBS/委派
│   ├── progress.md           # 状态/任务/风险摘要/工作日志（会话必读）
│   ├── issues.md             # 问题清单
│   ├── operation_log.md      # 高风险操作审计
│   ├── lessons_learned.md    # 经验教训
│   ├── handover.md           # 交接
│   ├── risks.md              # ○可选：独立风险登记册
│   ├── RTM.md                # ○可选：需求追踪矩阵
│   ├── design_spec.md        # ○可选：详细设计
│   └── test_plan.md          # ○可选：测试规划
└── doc/                      # 交付沉淀
    ├── technical_manual.md   # 里程碑滚动技术手册
    └── topic_report.md       # 专题/调研报告模板（复制改名用）
```

## 文档引用关系

```
AGENTS.md（规则 SSOT）
  └─ CLAUDE.md（@引用）        workflow.md（流程）
project.md ─→ requirements.md ─→ plan.md ─┬─→ (design_spec.md 可选)
     │              │                     └─→ (test_plan.md 可选)
     └─→ environments.md              plan.md ─→ progress.md ─┐
                                                              ├─ issues.md
   requirements.md ─→ (RTM.md 可选)    progress.md 风险摘要 ─→ (risks.md 可选)
                                       operation_log.md · lessons_learned.md · handover.md
   里程碑交付 ─→ doc/technical_manual.md · doc/topic_report.md
```
> 更直观的分组与引用图见 [`framework_structure.html`](framework_structure.html)。

## 文档生命周期分类（按需最小化加载）

| 分类 | 文档 | 更新频率 | 会话何时读 |
|---|---|---|---|
| 稳定入口 | AGENTS、CLAUDE、workflow | 低频 | 规则不确定时 |
| 核心参考 | project、requirements、environments、plan | 低/中频 | 规划任务 |
| 动态追踪 | progress、issues、operation_log、lessons_learned、handover | 高/按需 | **每次开工必读 progress→issues** |
| 可选 | risks、RTM、design_spec、test_plan | 按需 | 启用后 |
| 交付 | doc/technical_manual、doc/topic_report | 里程碑/按需 | 交付时 |

## 新项目初始化流程（4 步）

1. **复制**：将 `项目框架_claude/` 整个目录复制到新项目根目录（可自行去掉 `_claude` 后缀或改名）。
2. **改标识与领域**：填写 `AGENTS.md` §0（项目标识）与 §2（领域），填写 `ref/project.md`。
3. **删可选**：删除本项目用不到的**可选文档**（risks/RTM/design_spec/test_plan）——用到时再从上游文档拆出。
4. **接平台**：其他 Agent 平台入口文件（`.cursorrules`、`GEMINI.md` 等）各写**一行引用** `AGENTS.md`，不复制规则。

> **占位约定**：所有模板中用 `〔…〕` 方括号包裹的内容均为**占位/示例**（含 `〔示例：…〕` 与 `〔YYYY-MM-DD〕` 等），正式使用前逐一**替换为真实内容或删除**；清理干净后即为可用文档。

## 维护纪律（5 条）

1. **引用而非拷贝**：每个事实只存在于一个文档（SSOT），其余用相对链接引用。
2. **动态文档追加**：progress/handover 等最新在上、追加不覆盖，保留可追溯历史。
3. **模板纪律**：追加条目沿用文档内既有格式，不发明新格式。
4. **变更传播**：上游文档变更时，主 Agent 同步受影响的下游文档。
5. **框架自迭代**：使用中的经验教训写入 `ref/lessons_learned.md`，反哺框架优化。

## 备份命名规则

修改原有文件前按风险备份，备份与原文件同目录（**不进模板树**）：
`原文件名_backup_YYYYMMDD_特别标记_流水号.后缀`，例如 `plan.md_backup_20260908_大改_001.md`。
