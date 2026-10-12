# Issue #3｜Wind 数据、财务验证与量化评分

**负责人：范笑薇**

## 一眼看懂：你今天具体要找什么

先复制 [Wind 模板](../../data/templates/wind_financials.template.csv) 和 [评分模板](../../data/templates/impact_score.template.csv)。你要填的是 **20 家公司 × 3 年年度数据 + 8 季度核心数据 + 1 个统一交易日的估值数据**，不是寻找新闻。

### 先建 20 家样本名单

从武桐宇的公司映射中选；若他尚未交付，就按五组各临时选 4 家：材料/动力、电子/控制、无人机/eVTOL、基础设施、运营应用。每行先填写 `stock_code,company_name`，名单一经确定写入 PR。

### 每家公司必须导出的数字

1. **近三年年度（每年一行）**：营业收入、营收同比、归母净利润、毛利率、经营活动现金流、研发费用、存货、应收账款、资本开支、资产负债率。
2. **最近八季度（每季一行）**：营业收入、归母净利润、毛利率、经营活动现金流。
3. **同一交易日（每家公司一行）**：总市值、PE(TTM)、PB、PS(TTM)、近一年收益率、近一年波动率；所有公司必须使用同一个 `as_of_date`。

金额统一换算为“人民币百万元”；空缺写 `null + missing_reason`。完成一家公司后立即跑一次评分，不要等 20 家全部查完。

## 开始前必读

1. [README](../../README.md)
2. [团队分工](../TEAM_WORK.md)
3. [数据收集与交付标准](../DATA_COLLECTION_STANDARD.md)，重点看“范笑薇”部分；
4. [GitHub 协作工作流](../GITHUB_WORKFLOW.md)

## 需要找的数据

以武桐宇的公司清单为准；未完成前可先选 20 家代表公司并记录名单。

| 数据组 | 必查字段 | 时间范围 |
|---|---|---|
| 年度财务 | 营收、营收同比、归母净利、毛利率、经营现金流、研发费用、存货、应收、资本开支、资产负债率 | 近 3 个完整年度 |
| 季度财务 | 营收、归母净利、毛利率、经营现金流 | 最近 8 个季度 |
| 市场估值 | 总市值、PE(TTM)、PB、PS(TTM)、1 年收益率、1 年波动率 | 同一交易日截面 |

字段名、单位和标准格式以 [数据标准](../DATA_COLLECTION_STANDARD.md) 为准：金额为 `CNY_million`，比例为 0–100，代码为 `000001.SZ`。

## 注意事项

- 不上传 Wind 原始导出、账号、Cookie 或受限内容；仅上传字段字典、公开/模拟/脱敏样例和处理代码；
- 缺失写 `null` 并给出 `missing_reason`，不得用 0 补；
- 每个市场指标保留 `as_of_date`；每个评分保留 `formula_version`。

## 评分与交付

实现 `Impact = Exposure × Sensitivity × FinancialMateriality`。三个分项和总分均归一到 0–100，并写明来源、权重、边界条件和“不足以判断”的情况。

交付 `docs/WIND_DATA_DICTIONARY.md`、`data/financials.example.csv`、`backend/scoring.py`、`data/company_impact.example.json`、`docs/SCORING_METHOD.md`。

验收：20 家样本、三年年度口径、八季度核心指标、同日估值截面；三种典型事件的排序结果可复算；无 Wind 账号时可用 mock 测试。
