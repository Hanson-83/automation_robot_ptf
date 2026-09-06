# AI Agent 项目框架（AI4S 自动化与机器人系统）

一套**标准、通用、可复用**的 AI Agent 项目文档框架，用于支撑由 AI Agent（Claude Code / Cursor / Codex / OpenCode 等，可多平台多智能体协作）承担的调研、可行性评估、需求梳理、方案设计、规划、开发构建、测试、部署等全流程工作。

## 目录结构

```text
项目根目录/
├── AGENTS.md                    # 稳定入口：角色/领域/行为规范/规则/安全/参考索引（低频更新，可跨项目复用）
├── CLAUDE.md                    # Claude Code 兼容入口（一行引用 AGENTS.md）
├── README.md                    # 本文件：框架索引、引用关系、初始化流程、维护纪律
├── ref/                         # 动态参考文档（随项目推进持续更新）
│   ├── project.md               # 项目总览：背景/粗目标/粗需求/Idea/粗规划/环境概览（低频）
│   ├── requirements.md          # 具体目标、问题定义、功能/非功能需求、验收标准（中频）
│   ├── environments.md          # 开发/测试/部署环境、工具链、访问与权限（中频）
│   ├── plan.md                  # 方案、设计/测试/执行规划（中频，复杂时可拆分）
│   ├── progress.md              # 进度、任务状态、里程碑、风险摘要（高频）
│   ├── issues.md                # 问题清单与解决方案（高频）
│   ├── lessons_learned.md       # 经验教训（中频）
│   ├── operation_log.md         # 高风险操作留痕（按需）
│   ├── RTM.md                   # 需求追踪矩阵（中频）
│   ├── handover.md              # 交接文档，含历史时间线（按需）
│   ├── workflow.md              # 【可选】工作流定义（低频）
│   ├── risks.md                 # 【可选】风险台账（高频，被 progress.md 引用）
│   ├── design_spec.md           # 【可选】设计规范（按需，被 plan.md 引用）
│   ├── test_plan.md             # 【可选】测试规划（按需，被 plan.md 引用）
│   └── execution_plan.md        # 【可选】执行计划（中频，被 plan.md 引用）
└── doc/                         # 技术沉淀
    ├── technical_manual.md      # 技术说明：设计/实现思路/疑难杂症/迁移指导（里程碑更新）
    └── topic_report.md          # 专题报告模板（按需，按专题改名，如 robot_adapter_report.md）
```

## 文档引用关系

```text
AGENTS.md（顶层索引，稳定）
  └─→ ref/project.md（总览入口，粗粒度）
        ├─→ ref/requirements.md（细粒度需求）
        ├─→ ref/environments.md（环境）
        ├─→ ref/workflow.md（可选·工作流）
        └─→ ref/plan.md（规划）
              ├─→ ref/design_spec.md（可选·设计规范）
              ├─→ ref/test_plan.md（可选·测试规划）
              └─→ ref/execution_plan.md（可选·执行计划）
ref/progress.md ──→ ref/risks.md（可选·风险台账）
ref/requirements.md ⇄ ref/RTM.md（需求追踪状态回填）
里程碑完成 ──→ doc/technical_manual.md（技术沉淀）
专项调研 ──→ doc/<topic>_report.md（专题报告）
```

## 文档生命周期分类

| 类别 | 文档 | 更新频率 |
|---|---|---|
| 稳定入口 | AGENTS.md / CLAUDE.md / README.md | 低频（可跨项目复用） |
| 核心参考 | project.md / requirements.md / environments.md / plan.md | 低频~中频 |
| 动态追踪 | progress.md / issues.md / lessons_learned.md / operation_log.md / RTM.md / handover.md | 高频~按需 |
| 可选拆分 | workflow.md / risks.md / design_spec.md / test_plan.md / execution_plan.md | 按需启用 |
| 技术沉淀 | technical_manual.md / topic_report.md | 里程碑/按需 |

## 新项目初始化流程（复用本框架时）

1. 复制本目录（AGENTS.md + ref/ + doc/）到新项目根目录；删除用不到的「可选」文档。
2. 更新 `AGENTS.md` 第 0 节「项目标识」；按需修订「6. 参考文档索引」。
3. 依次初始化 `ref/project.md` → `ref/requirements.md` → `ref/environments.md` → `ref/plan.md`（需要时拆分 `workflow.md` / `design_spec.md` / `test_plan.md` / `execution_plan.md`）。
4. 开工后维护 `ref/progress.md`、`ref/issues.md`、`ref/risks.md`、`ref/RTM.md`；里程碑完成更新 `doc/technical_manual.md`。

## 维护纪律

- **单一事实源**：同一事实只在一个文档维护，其他文档引用而非复制。
- **先读后写**：任何 Agent 行动前先读 `ref/project.md` + 相关文档；修改前先读目标文档。
- **变更留痕**：动态文档每次更新登记「变更记录」；高风险操作记入 `ref/operation_log.md`。
- **引用纪律**：跨文档一律用相对链接；AGENTS.md 只做顶层索引，交叉引用在各文档内部维护。
- **状态权威**：任务状态以 `ref/progress.md` + `ref/RTM.md` 为唯一权威来源。
