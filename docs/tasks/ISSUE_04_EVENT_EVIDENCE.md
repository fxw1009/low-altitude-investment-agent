# Issue #4｜政策事件、原始证据与评测集

**负责人：刘芯妤**

## 一眼看懂：你今天具体要找什么

先复制 [事件模板](../../data/templates/events.template.csv) 和 [证据模板](../../data/templates/evidence.template.csv)。你的目标是 **30 条事件 + 至少 30 条能点开的原始证据**；一条事件不是一篇新闻，而是“发生了什么”的一行记录。

### 必须完成的 30 个数据格

| 类别 | 要找的条数 | 优先去哪里找 |
|---|---:|---|
| 国家/省市政策、规划、补贴、基础设施方案 | 8 | 国务院部委、民航管理部门、省市政府官网 |
| 上市公司订单、合作、融资、产品发布、产能建设公告 | 8 | 巨潮资讯、上交所/深交所、公司 IR |
| 适航、空域开放、试点航线/运营许可 | 4 | 民航主管部门、地方政府、公司公告 |
| 碳纤维、电池等关键投入品价格或供给变化 | 4 | 官方价格数据、上市公司公告、权威行业协会 |
| 物流、巡检、应急、文旅等应用落地 | 6 | 政府试点公告、运营方公告、公司官网 |

### 每找到一个网页，按这个顺序填

1. `events.csv` 填事件名称、事件类别、日期、地区、利好/利空/不确定、受影响节点、原始链接；
2. `evidence.csv` 填发布机构、标题、发布日期、链接、**一句能支撑结论的短摘录**、该句话所在的小标题或公告页码；
3. 判断来源等级 A/B/C；找不到一手来源就标 `pending_verification`，不能写“已证实”。

## 开始前必读

1. [README](../../README.md)
2. [团队分工](../TEAM_WORK.md)
3. [数据收集与交付标准](../DATA_COLLECTION_STANDARD.md)，重点看“刘芯妤”部分和来源优先级；
4. [GitHub 协作工作流](../GITHUB_WORKFLOW.md)

## 需要找的数据

建立至少 30 条事件库：政策/规划至少 8 条；公司公告、订单、合作至少 8 条；适航、空域、试点至少 4 条；原材料或关键零部件价格至少 4 条；物流、巡检、应急、文旅等场景落地至少 6 条。

每条事件填写：`event_id,event_name,event_type,event_date,region,direction,affected_node_ids,source_title,source_url,source_level,verification_status`。

每条证据填写：`evidence_id,event_id,source_title,publisher,published_date,source_url,quote,location,claim_supported,credibility_level`。

## 来源与注意事项

- 优先级为政府/交易所/公司公告/民航主管部门（A）→ 公司官网或 IR（B）→ 权威媒体（C）；
- 新闻仅用于找线索，关键结论需尽量回到 A/B 级来源；
- `quote` 只保留必要短摘录，`location` 写清段落标题、公告页码或表格位置；
- 未找到原始依据时标 `pending_verification`，不作为评分关键证据；每条事件至少关联一个产业链节点。

## 交付与验收

交付 `data/events.csv`、`data/evidence.csv`、`tests/test_cases.json`、`docs/EVIDENCE_STANDARD.md`。

建立 30 个问题；每题写问题、`event_id`、预期路径、目标公司类型和必需 `evidence_id`。首批 10 条须有 A/B 级可复核来源；随机抽取 10 条均能通过 URL 和 `location` 找到依据。
