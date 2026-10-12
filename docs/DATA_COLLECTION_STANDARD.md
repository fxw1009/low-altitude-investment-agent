# 数据收集与交付标准（V1）

> [!IMPORTANT]
> 每条分析结论必须能回溯到 **原始来源链接 + 结构化数据记录 + 生成时间**。不确定的信息可以保留，但必须标记 `pending_verification`，不得写成既定事实。

## 开始前的共同规则

1. 先阅读 [团队分工](TEAM_WORK.md) 和 [GitHub 工作流](GITHUB_WORKFLOW.md)，再开始建立数据或代码。
2. 所有 ID 全局唯一：`NODE_`、`REL_`、`COMP_`、`EVT_`、`EVD_`、`CASE_` 分别对应节点、关系、公司、事件、证据、测试案例。
3. 日期统一为 `YYYY-MM-DD`；证券代码统一为 `000001.SZ` 格式；金额统一为 `CNY_million`（人民币百万元）；比例统一为 `0–100`。
4. 每份数据都要有 `source_url`、`source_title`、`published_date`（没有则留空）和 `verification_status`。
5. 不上传 Wind 原始导出、付费研报全文、账号、Cookie、API Key、个人信息或版权受限全文；只提交字段口径、公开/脱敏样例和处理代码。

## 来源优先级

| 优先级 | 可用来源 | 典型用途 |
|---|---|---|
| A | 政府部门、交易所、证监会指定披露平台、公司公告/年报、民航主管部门 | 政策、公告、财务披露、适航/空域事实 |
| B | 公司官网、投资者关系页面、官方微信公众号/新闻稿 | 产品、订单、试点进展；需记录发布日期 |
| C | 权威媒体、行业协会 | 发现线索和补充背景；关键结论须尽量回溯 A/B |
| D | 自媒体、论坛、聚合站 | 只可作为检索线索，不得单独支撑结论 |

## 武桐宇：产业链与公司映射数据

| 文件 | 最少字段 | 数量/质量要求 |
|---|---|---|
| `data/graph/nodes.csv` | `node_id,node_name,node_type,aliases,description,source_url,verification_status` | 至少 35 个节点；节点类型覆盖材料、零部件、整机、基础设施、应用场景 |
| `data/graph/relations.csv` | `relation_id,from_node_id,relation_type,to_node_id,effect_direction,condition,source_url,verification_status` | 至少 50 条关系；每条关系写明方向与适用条件 |
| `data/graph/company_mapping.csv` | `company_id,stock_code,company_name,product,product_node_id,chain_role,exposure_score,source_url,verification_status` | 20–30 家公司；不得仅凭“概念股”标签映射 |
| `data/graph/event_rules.json` | `rule_id,event_type,trigger_node_id,path,impact_direction,exception,source_url` | 至少 10 条可查询规则 |

优先找：上市公司年报中的主营构成/产品描述、公司公告、官网产品页、政府或民航部门对产业链与应用的正式说明。`exposure_score` 暂用 0–100，并写明是主营收入、产品匹配度还是待核验估计。

## 刘芯妤：政策、公告、新闻与原始证据数据

| 文件 | 最少字段 | 数量/质量要求 |
|---|---|---|
| `data/events.csv` | `event_id,event_name,event_type,event_date,region,direction,affected_node_ids,source_title,source_url,source_level,verification_status` | 至少 30 条；每条至少关联一个产业链节点 |
| `data/evidence.csv` | `evidence_id,event_id,source_title,publisher,published_date,source_url,quote,location,claim_supported,credibility_level` | 每个事件至少 1 条 A/B 级或标注为待核验 |
| `tests/test_cases.json` | `case_id,question,event_id,expected_path,expected_company_types,required_evidence_ids` | 至少 30 题，其中前 10 题须人工核验 |

事件配额：政策/规划不少于 8 条，公司公告/订单合作不少于 8 条，适航/空域/试点不少于 4 条，原材料或关键零部件价格变化不少于 4 条，运营场景落地不少于 6 条。`quote` 只保存支撑结论的必要短摘录；`location` 写明网页段落标题、公告页码或表格位置。

## 范笑薇：Wind 财务与市场数据

| 数据组 | 必须字段 | 时间范围/口径 |
|---|---|---|
| 公司基础 | `stock_code,company_name,as_of_date,industry,chain_role` | 使用武桐宇的公司清单；差异单独记录 |
| 年度财务 | `report_period,revenue,revenue_yoy,net_profit,gross_margin,operating_cash_flow,rd_expense,inventory,accounts_receivable,capex,asset_liability_ratio` | 近 3 个完整年度；金额均为 `CNY_million` |
| 季度财务 | `report_period,revenue,net_profit,gross_margin,operating_cash_flow` | 最近 8 个季度；无数据标为 `null` 并解释 |
| 市场估值 | `as_of_date,market_cap,pe_ttm,pb,ps_ttm,total_return_1y,volatility_1y` | 同一交易日截面；记录该日期 |
| 评分输出 | `stock_code,exposure,sensitivity,financial_materiality,impact_score,risk_flags,formula_version` | 三个分项和总分均为 0–100 |

输出 `docs/WIND_DATA_DICTIONARY.md` 说明字段定义、Wind 口径、单位、频率、缺失值规则和异常值规则；输出 `data/financials.example.csv` 时仅使用公开或模拟样本。评分公式必须由代码确定性计算，不得由大模型直接编造数值。

## 孙奇衍：前端所消费的数据

前端只读取下列标准 JSON/CSV 的 mock 或接口结果，不手工捏造公司分数或证据：

- 事件：`event_id`、`event_name`、`direction`、`affected_node_ids`；
- 图谱：节点、边、`impact_direction`、`rule_id`；
- 公司卡片：`stock_code`、`company_name`、`chain_role`、`impact_score`、`risk_flags`；
- 证据卡：`evidence_id`、`source_title`、`published_date`、`quote`、`source_url`、`credibility_level`。

必须显示“数据不足/待核验”状态；来源链接应可点击；图谱、评分榜和证据卡必须能由同一个 `event_id` 关联。

## 吕洪宇：总控与数据验收

总控模块负责定义并校验跨模块 JSON：事件 ID 是否存在、图谱路径是否可追溯、公司代码是否规范、评分是否含公式版本、每条结论是否至少有一个 `evidence_id`。每次 Demo 留存输入事件、所用数据版本、计算结果和生成时间。
