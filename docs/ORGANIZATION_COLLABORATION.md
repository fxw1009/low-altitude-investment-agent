# Koukou is King Organization 协作指南

## 为什么使用 Organization

> [!IMPORTANT]
> **Organization 是团队共同拥有 GitHub 资产的空间。** 仓库、Issue、Project 看板、Discussion、Actions 和成员权限均由组织管理；即使某位同学更换电脑或不再负责某模块，项目仍归团队而非个人账号。

当前比赛项目仓库：`Koukou-is-King/low-altitude-investment-agent`。

## 推荐权限

| 身份 | 建议权限 | 适用人员 | 能做什么 |
|---|---|---|---|
| Organization Owner | Owner | 吕洪宇 | 管理成员、仓库可见性、GitHub Project、密钥和比赛最终提交 |
| Repository Maintainer | Maintain | 队长或后续指定技术负责人 | 管理 Issues、PR、标签和 Actions，不管理组织账单/成员 |
| Repository Contributor | Write | 武桐宇、刘芯妤、孙奇衍、范笑薇 | 创建分支、推送代码、创建 Issue/PR、评论和领取任务 |

> [!WARNING]
> **只保留一名 Owner；队员默认使用 `Write`，不授予 `Admin`。** 账户邀请应使用每位成员确认过的 GitHub 用户名或 GitHub 页面中的邮箱邀请功能。

## 推荐 Teams

当成员均加入组织后，在 **Organization → Teams** 创建以下 Teams。即使每个 Team 目前只有一人，也能让职责和访问范围一目了然。

| Team | 初始成员 | 对本仓库权限 | 负责范围 |
|---|---|---|---|
| `maintainers` | 吕洪宇 | Maintain | 合并 PR、管理看板与版本 |
| `knowledge-graph` | 武桐宇 | Write | 产业链节点、关系与传导规则 |
| `wind-quant` | 孙奇衍 | Write | Wind 字段、清洗与影响评分 |
| `event-evidence` | 刘芯妤 | Write | 政策、公告、证据库与测试集 |
| `frontend-demo` | 范笑薇 | Write | 前端、图谱可视化与 Demo |

后续增加新成员时，直接加入对应 Team；不要逐个为每个仓库重复配置权限。

## 一张 Project 看板管理全队

在 Organization 的 **Projects** 新建项目：`低空智研｜比赛协作看板`，并关联本仓库。推荐字段：

| 字段 | 选项 |
|---|---|
| Status | 待领取、进行中、待审查、阻塞、已完成 |
| Owner | 负责人 |
| Workstream | 架构、图谱、Wind、证据、前端 |
| Milestone | M1 并行底座、M2 MVP、M3 比赛交付 |
| Priority | P0、P1、P2 |

每个 Issue 都应加入看板。成员只需移动自己的 Issue 状态；队长通过看板判断 **是否有阻塞、哪些模块可以合并，以及 MVP 是否具备端到端演示条件**。

## 日常协作约定

```text
Issue（任务）
  → 成员把 Issue 交给 Codex
  → Codex 在 feat/模块-名称 分支完成并推送
  → Pull Request（写 Closes #编号）
  → GitHub Actions 自动检查
  → 队长/维护者评审并合并
  → Issue 自动关闭，看板同步为已完成
```

### 成员的标准提示词

```text
处理 Koukou-is-King/low-altitude-investment-agent 的 Issue #编号。
在指定 feat 分支完成实现，不改动无关文件；完成后运行检查、提交 commit、创建 PR。
PR 中写明 Closes #编号、实现内容、验证方式、数据来源和风险。
```

## Discussion 的使用边界

使用 **Discussions** 记录不会直接产出代码的团队决策，例如：

- “首批 30 家公司清单是否通过”；
- “ImpactScore 权重是否调整”；
- “决赛演示案例选哪个”；
- “Wind 某字段采用哪种口径”。

> [!TIP]
> **结论一旦确定，应转化为 Issue 或提交到仓库文档；不要在聊天记录里遗失关键决定。**

## 安全与比赛合规

- 不上传 Wind 原始导出、账户密码、API Key、未获授权的研报全文；
- 密钥仅存放在 GitHub Actions Secrets 或本地 `.env`，绝不提交；
- 每条投研结论都应保留来源、日期、图谱规则和计算过程；
- 开源项目只复用许可证允许的部分，并在比赛材料中披露参考项目和自研部分。
