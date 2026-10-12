# Issue #1｜总控 Agent、接口与集成

**负责人：吕洪宇**

## 一眼看懂：你不需要查外部数据

你需要做的是准备其他四人可立刻使用的**空壳数据和接口**。今天先创建 1 个示例事件、1 条示例路径、3 家示例公司、3 条示例证据和 3 条示例评分；这些都是 `mock`，字段齐全即可，不宣称为真实事实。

完成顺序：先建立 `contracts/` 字段模型 → 再建立 `data/mock/` 五类 JSON → 最后让前端能读、让总控能串起来。

## 开始前必读

1. [README](../../README.md)
2. [团队分工](../TEAM_WORK.md)
3. [数据收集与交付标准](../DATA_COLLECTION_STANDARD.md)
4. [GitHub 协作工作流](../GITHUB_WORKFLOW.md)

## 先做什么

- 建立 `contracts/`，定义 `event`、`graph_path`、`company`、`financial_score`、`evidence`、`report` 的 JSON Schema 或等效 Pydantic 模型；
- 建立 `data/mock/`，至少提供“动力电池价格下降 15%”的全链路样例；
- 给每次运行分配 `run_id`，记录输入事件、数据版本、输出时间和错误状态。

## 必须接收/输出的数据

| 模块 | 核心字段 |
|---|---|
| 事件 | `event_id,event_name,event_type,event_date,direction,affected_node_ids` |
| 图谱 | `path_id,node_ids,relation_ids,rule_id,impact_direction` |
| 公司 | `stock_code,company_name,chain_role,exposure_score` |
| 财务 | `exposure,sensitivity,financial_materiality,impact_score,formula_version,risk_flags` |
| 证据 | `evidence_id,source_title,published_date,source_url,quote,credibility_level` |

## 交付与验收

- 交付 `contracts/`、`data/mock/`、总控模块和 `docs/ARCHITECTURE.md`；
- 任一模块替换 mock 后仍可运行；
- 每条结论返回至少一个 `evidence_id`，否则展示“待核验”；
- 对空数据、错误代码、缺评分提供可读提示；PR 附启动命令和输出样例。
