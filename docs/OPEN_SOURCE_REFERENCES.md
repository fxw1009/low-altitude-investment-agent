# 可复用开源项目与使用边界

本项目不整套复制外部仓库，而是仅借鉴架构、组件或许可证允许的代码；低空产业链、Wind 接入、事件传导规则和评分模型由团队自行完成。

| 项目 | 许可/定位 | 本项目用途 | 负责人 |
|---|---|---|---|
| [agentic-financial-rag](https://github.com/MazkaB/agentic-financial-rag) | 架构参考；复用前需复核许可证 | 参考文档检索、数值/文本分层和引用验证架构 | 吕洪宇、孙奇衍 |
| [multi-agent-investment](https://github.com/flash131307/multi-agent-investment) | MIT；已作为 Git 子模块接入 | 参考并行 Agent 返回格式与确定性信号融合 | 吕洪宇、刘芯妤 |
| [neo4j-graphrag-python](https://github.com/neo4j/neo4j-graphrag-python) | 官方 GraphRAG 工具包；以 Python 依赖接入 | 储存、查询“公司—产品—产业—事件—证据”关系 | 武桐宇 |
| [react-force-graph](https://github.com/vasturiano/react-force-graph) | MIT；以前端依赖接入 | 产业链路径高亮、节点详情与交互图 | 范笑薇 |
| [multiagent-stock-research](https://github.com/chenhab03/multiagent-stock-research) | 输出结构参考；复用前需复核许可证 | 参考报告结构、评分卡和风险呈现 | 范笑薇、吕洪宇 |
| [low-altitude-economy-wiki](https://github.com/HirezmingD/low-altitude-economy-wiki) | 低空经济资料库 | 仅作为术语和资料线索；结论必须回溯至原始来源 | 武桐宇、孙奇衍 |
| [FinGPT](https://github.com/AI4Finance-Foundation/FinGPT) | 金融语言模型项目 | 参考金融事件抽取、实体识别和文本分类思路 | 孙奇衍 |

## 合规要求

1. 每次复用前检查目标仓库的 `LICENSE` 与依赖许可；
2. 保留 MIT/Apache-2.0 等许可证要求的版权与许可声明；
3. 在比赛文档中列出外部开源项目、实际借鉴内容及自研模块；
4. 不上传 Wind 终端导出的受限原始数据、账户凭据或未经许可发布的研报全文；
5. 所有最终投研结论均由本项目的图谱、数据和规则产生，外部项目不构成结论来源。
