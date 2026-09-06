# workflow.md — 工作流文档

> **文档性质**：描述项目标准工作流，包括阶段流转、多智能体协作流程、文档联动规则。
> **维护策略**：工作流程发生实质变化时更新。
> **上游文档**：[`project.md`](project.md)。

## 1. 项目生命周期总览

```
调研 → 可行性评估 → 需求梳理 → 方案设计 → 规划 → 具体设计 → 开发与构建 → 测试 → 部署 → 运维/交接
```

| 阶段 | 主要输入 | 主要产出 | 关键文档更新 |
|---|---|---|---|
| 调研 | 粗粒度问题 | 调研笔记、专题报告（`../doc/`） | `requirements.md`（草案） |
| 可行性评估 | 调研产出 | 可行性结论（Go/No-Go） | `risks.md`、专题报告 |
| 需求梳理 | 可行性结论 | 确认后的需求 | `requirements.md`、`RTM.md` |
| 方案设计 | 需求 | 候选方案与选型结论 | `plan.md`、`design_spec.md` |
| 规划 | 方案 | 里程碑与任务分解 | `execution_plan.md`、`test_plan.md` |
| 具体设计 | 规划 | 详细设计 | `design_spec.md` |
| 开发与构建 | 详细设计 | 代码、构建产物 | `progress.md`、`issues.md` |
| 测试 | 构建产物 | 测试报告 | `test_plan.md`（执行记录）、`issues.md` |
| 部署 | 测试通过版本 | 上线系统 | `operation_log.md`、`technical_manual.md` |
| 运维/交接 | 运行系统 | 交接文档 | `handover.md` |

## 2. 多智能体协作流程

### 2.1 任务委派标准流程

1. 主 Agent 将任务写入 [`execution_plan.md`](execution_plan.md)（或临时任务记入 [`progress.md`](progress.md)）；
2. 主 Agent 向子 Agent / 其他平台 Agent 发出委派：目标 + 输入 + 期望产出 + 验收标准 + 约束；
3. 执行 Agent 完成任务，产出物落到指定位置，并更新 [`progress.md`](progress.md)、[`issues.md`](issues.md)（如有问题）；
4. 主 Agent 审查产出，审查结论记入 [`progress.md`](progress.md)，审查通过后任务闭环。

### 2.2 平台间协作

- 各平台 Agent 遵循 [`../AGENTS.md`](../AGENTS.md) 统一规范；
- 平台分工见 [`environments.md`](environments.md) 第 3 节"AI Agent 平台矩阵"；
- 跨平台信息同步只通过本仓库文档，不通过会话历史。

### 2.3 人工介入点（必停点）

以下情况必须暂停并请求人类负责人决策：
- 需求变更确认；
- Go/No-Go 可行性决策；
- 高风险操作批准（见 [`../AGENTS.md`](../AGENTS.md) 第 4.1 节）；
- 生产环境变更批准；
- 里程碑验收。

## 3. 文档联动规则

| 触发事件 | 必须同步更新的文档 |
|---|---|
| 需求变更 | `requirements.md` → `RTM.md` → `plan.md`（如影响计划）→ `test_plan.md`（如影响测试） |
| 完成一个任务 | `progress.md` |
| 发现新问题 | `issues.md` → `progress.md` |
| 识别新风险 | `risks.md` → `progress.md` |
| 完成一个里程碑 | `technical_manual.md` → `RTM.md`（验收状态） |
| 执行风险操作 | `operation_log.md`（操作前登记 + 操作后记录结果） |
| 正式交接 | `handover.md` |

## 4. 会话启动检查单（每个 Agent 会话开始时）

1. 读 [`project.md`](project.md) 第 2~4 节（快速定位目标）；
2. 读 [`progress.md`](progress.md) 最新状态（当前任务）；
3. 读 [`issues.md`](issues.md) 未解决问题（避免踩同样的坑）；
4. 视任务需要读取其他文档；
5. 确认当前环境与身份（见 [`environments.md`](environments.md)）。

---

*最后更新：2026-09-06 | 更新人：*
