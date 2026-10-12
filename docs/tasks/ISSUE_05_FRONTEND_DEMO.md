# Issue #5｜前端、可视化与比赛 Demo

**负责人：孙奇衍**

## 开始前必读

1. [README](../../README.md)
2. [团队分工](../TEAM_WORK.md)
3. [数据收集与交付标准](../DATA_COLLECTION_STANDARD.md)，重点看“孙奇衍”部分；
4. [GitHub 协作工作流](../GITHUB_WORKFLOW.md)

## 开发前确认的数据

先读取 `contracts/` 与 `data/mock/`；只能消费下列标准字段，不能在页面里手写公司分数、产业关系或证据：

- 事件：`event_id,event_name,direction,affected_node_ids`；
- 图谱：节点、边、`impact_direction,rule_id`；
- 公司：`stock_code,company_name,chain_role,impact_score,risk_flags`；
- 证据：`evidence_id,source_title,published_date,quote,source_url,credibility_level`。

## 必做功能

1. 事件输入/选择，至少支持“动力电池价格下降 15%”；
2. 结果总览：事件方向、影响环节数、候选公司数、证据数和数据版本；
3. 产业链图谱：正/负/不确定路径可区分，点击节点显示公司与规则；
4. 公司评分榜：按 `impact_score` 排序，显示三个分项、风险提示和“数据不足”；
5. 证据抽屉：展示标题、日期、短摘录、可信度和可点击原始链接；
6. Demo 可靠性：加载、空数据、错误状态和 3 分钟演示脚本。

## 注意事项与验收

- 必须用 mock JSON 先做，不等待真实后端；接口访问放在 adapter 层；
- `pending_verification`、缺失评分、无证据均需可视化，不能隐藏；
- 不把 Wind 受限数据写入前端仓库。

交付 `frontend/`、`frontend/src/adapters/`、可启动说明、截图和 `docs/FRONTEND_DEMO.md`。新克隆仓库后可启动，选择示例事件后能连续查看路径、公司评分和至少一条证据。
