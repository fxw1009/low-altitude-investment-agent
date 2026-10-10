# 参考项目与实际接入清单

> [!IMPORTANT]
> 本目录只保留**可合法复用的源码引用**与明确的接入边界。比赛核心的低空产业链、Wind 数据、事件传导规则和评分模型必须由本团队自行实现。

## 已实际加入仓库

| 项目 | 仓库位置/接入方式 | 用途 | 负责人 |
|---|---|---|---|
| [multi-agent-investment](https://github.com/flash131307/multi-agent-investment) | `third_party/multi-agent-investment` Git 子模块，固定在明确提交版本 | 复用/参考并行 Agent 的统一信号格式与确定性汇总思路 | 吕洪宇、范笑薇 |
| [react-force-graph](https://github.com/vasturiano/react-force-graph) | `frontend/package.json` 的 `react-force-graph-2d` 依赖 | 产业链节点、影响路径高亮、公司详情交互 | 孙奇衍 |
| [Neo4j GraphRAG](https://github.com/neo4j/neo4j-graphrag-python) | `backend/requirements.txt` 的 `neo4j-graphrag` 依赖 | 图谱查询、图谱检索与事件影响路径推理 | 武桐宇、刘芯妤 |

首次克隆本仓库后，初始化实际源码子模块：

```bash
git submodule update --init --recursive
```

## 仅作架构参考，不复制源码

| 项目 | 允许借鉴的内容 | 不直接纳入源码的原因 |
|---|---|---|
| [agentic-financial-rag](https://github.com/MazkaB/agentic-financial-rag) | RAG 分层、结构化数值查询、引用核验工作流 | 上游许可信息需在每次复用前再次核验；本项目仅按思路自研 |
| [multiagent-stock-research](https://github.com/chenhab03/multiagent-stock-research) | 研报章节、评分卡、多空风险呈现 | 仅参考输出结构；不复制模板/代码，避免与项目定位及许可证不匹配 |
| [low-altitude-economy-wiki](https://github.com/HirezmingD/low-altitude-economy-wiki) | 术语和资料线索 | 不将二手资料直接作为投研证据，必须回溯到政策、公告等原始来源 |
| [FinGPT](https://github.com/AI4Finance-Foundation/FinGPT) | 金融事件抽取和实体识别的任务设计 | 初期不部署/微调大模型，以免超出比赛 MVP 的工程范围 |

> [!WARNING]
> **任何第三方源码、数据集、模型权重或报告原文进入本仓库前，都必须在对应 PR 中写明许可证、来源和实际修改内容。**
