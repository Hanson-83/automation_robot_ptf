# Workflow — 工作流程与多智能体协作

> **定位**：项目生命周期、阶段门、人工必停点、委派流程（稳定，跨项目复用）。 · **更新频率**：低频 · **上游**：[`AGENTS.md`](../AGENTS.md)

## 1. 生命周期（10 阶段）

```
调研 → 可行性 → 需求 → 方案 → 规划 → 详细设计 → 开发构建 → 测试 → 部署 → 运维/交接
```
> 阶段可裁剪：小任务可合并阶段；纯测试任务从「测试」进入。每阶段完成其**退出物**并通过**阶段门**后方可推进。

| 阶段 | 主要输入 | 主要活动 | 退出物（文档） | 主责角色 |
|---|---|---|---|---|
| 调研 | 项目背景、Idea | 领域/方案/开源项目调研 | `doc/topic_report.md`（复制改名） | 主 Agent |
| 可行性 | 调研结论 | 技术/资源/风险可行性评估 → **Go/No-Go** | 可行性报告 + `plan.md` 方案备选 | 主 Agent + 人类 |
| 需求 | project.md、干系人 | 梳理 FR/NFR、验收标准 | [`requirements.md`](requirements.md) + [`RTM.md`](RTM.md)（可选） | 主 Agent（经确认） |
| 方案 | 需求 | 架构与技术选型、ADR | [`plan.md`](plan.md) | 主 Agent |
| 规划 | 方案 | 里程碑、WBS、排期、委派 | [`plan.md`](plan.md) | 主 Agent |
| 详细设计 | 方案 | 模块/接口/硬件/安全设计 | [`plan.md`](plan.md) 内联或 [`design_spec.md`](design_spec.md) | 主 Agent |
| 开发构建 | 设计 | 编码、构建、自测 | 代码 + [`doc/technical_manual.md`](../doc/technical_manual.md) | 主/子 Agent |
| 测试 | 开发产出 | 单元/集成/系统/验收测试 | [`plan.md`](plan.md) 内联或 [`test_plan.md`](test_plan.md) + 测试报告 | 主 Agent + 人类（高风险） |
| 部署 | 通过测试的产物 | 环境部署、上线验证 | [`operation_log.md`](operation_log.md) | 主 Agent + 人类 |
| 运维/交接 | 运行系统 | 监控、迭代、交接 | [`handover.md`](handover.md)、[`technical_manual.md`](../doc/technical_manual.md) | 主 Agent |

## 2. 阶段门（Gate）规则

阶段推进的三个必要条件（任一不满足则不得推进，原因记 [`progress.md`](progress.md)）：
1. 本阶段**退出物完整**；2. **关键验证通过**（对应验收标准）；3. **风险受控**（无未处置的高风险）。

## 3. 人工必停点（Human Checkpoints）

以下节点**必须**上报人类负责人确认后方可继续：

| 必停点 | 触发时机 | 记录位置 |
|---|---|---|
| 需求变更确认 | 需求新增/变更/删除 | [`requirements.md`](requirements.md) 变更记录 |
| Go/No-Go | 可行性评估完成 | [`plan.md`](plan.md) |
| 高风险操作批准 | 涉人身/数据/系统安全的操作前 | [`operation_log.md`](operation_log.md) |
| 生产/现场变更批准 | 部署或现场调试前 | [`operation_log.md`](operation_log.md) |
| 里程碑验收 | 里程碑完成 | [`progress.md`](progress.md) |

## 4. 多智能体委派流程

```
主 Agent 拆分任务 → 委派(含5要素) → 子 Agent 执行并更新 progress/issues
        → 主 Agent 审查(review) → 通过则合并、记结论；不通过则退回重做 → 任务闭环
```

**委派 5 要素**（缺一不可）：① 目标；② 输入材料（文件路径）；③ 期望产出（路径/格式）；④ 验收标准；⑤ 约束与注意事项。

**审查回收门**：子 Agent 产出必须经主 Agent 审查后才能合并进主线文档/代码，审查结论记入 [`progress.md`](progress.md)（委派跟踪见 [`plan.md`](plan.md) 委派表）。

## 5. 会话启动清单（每次开工）

- [ ] 读 [`project.md`](project.md) → [`progress.md`](progress.md) → [`issues.md`](issues.md)
- [ ] 确认当前阶段与下一步任务（progress.md「下一步」）
- [ ] 确认是否触及必停点；若是，先上报
- [ ] 规划先行：不确定处先提问，再动手

---
*最后更新：〔YYYY-MM-DD〕 | 更新人：〔填写〕*
