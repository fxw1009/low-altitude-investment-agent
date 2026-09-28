# 零基础队员指南：用 GitHub + Codex 协作完成比赛

> [!IMPORTANT]
> **你不需要先学会写代码。** 你需要学会把一个清晰任务交给 Codex、把成果放进正确的 GitHub 流程，并让队友能够检查和使用它。

本指南适用于武桐宇、刘芯妤、孙奇衍、范笑薇，以及之后加入的每位成员。

## 先理解：我们怎么协作

```text
队长创建 Issue（任务卡）
        ↓
成员领取 Issue，并把任务交给 Codex
        ↓
Codex 在独立分支修改代码/数据/文档
        ↓
成员创建 Pull Request（PR，申请把成果合进主项目）
        ↓
队长或对应负责人检查 → 合并到 main
        ↓
Issue 自动关闭，成果成为项目正式版本
```

> [!WARNING]
> **不要直接修改或推送 `main` 分支。** `main` 是已经验收、可展示的比赛版本；每个人都应通过 PR 提交成果。

---

## 第一部分：10 分钟完成准备

### 1. 注册并确认 GitHub 账号

1. 打开 [GitHub](https://github.com/) 并登录；
2. 点击右上角头像，记下你的 **GitHub 用户名（username）**；
3. 将用户名发给队长。用户名不是邮箱，也不一定是你的中文姓名；
4. 接受队长发来的 **Koukou is King Organization** 邀请；
5. 打开项目仓库：[low-altitude-investment-agent](https://github.com/Koukou-is-King/low-altitude-investment-agent)。

### 2. 认识仓库首页

| 页面/按钮 | 它是什么 | 你什么时候使用 |
|---|---|---|
| **Code** | 项目的文件和代码 | 查看 README、文档、下载或克隆项目 |
| **Issues** | 任务卡片列表 | 领取任务、提问、报告阻塞 |
| **Pull requests** | 等待合并的成果 | 创建 PR、查看队长/自动检查意见 |
| **Actions** | 自动检查记录 | 查看“检查通过/失败”的原因 |
| **Projects** | 团队任务看板 | 查看任务处于待领取、进行中或已完成 |
| **Discussions** | 团队决策区 | 讨论公司名单、评分口径、Demo 方案等非代码问题 |

---

## 第二部分：必须认识的 9 个词

| 名词 | 用人话解释 | 本项目中的例子 |
|---|---|---|
| **GitHub** | 团队文件、代码、任务和修改记录的在线协作平台 | 本比赛项目的唯一正式协作平台 |
| **Organization** | 团队共同拥有项目的空间，不属于某个个人 | `Koukou is King` |
| **Repository / 仓库** | 一个完整项目的文件夹和历史记录 | `low-altitude-investment-agent` |
| **Issue** | 一张可领取的任务卡 | “建立低空经济产业链 V1” |
| **Branch / 分支** | 在不影响正式版本的前提下独立工作的一条副本 | `feat/knowledge-graph-v1` |
| **Commit / 提交** | 对某一批修改的带说明的存档 | “新增电池—eVTOL 传导关系” |
| **Pull Request / PR** | “请把我的分支成果合入正式项目”的申请单 | “完成图谱节点 V1，Closes #2” |
| **Review / 审查** | 队友检查 PR 的逻辑、数据、风险和格式 | 队长要求补充证据来源 |
| **Merge / 合并** | 审查通过后，将 PR 内容放进 `main` 正式版本 | 该 Issue 变为已完成 |

> [!TIP]
> **一句话记忆：Issue 是任务，Branch 是独立工作区，PR 是交作业申请，Merge 是作业正式入库。**

---

## 第三部分：每次做任务的标准动作

### 第 1 步：领取 Issue

1. 打开仓库的 **Issues**；
2. 找到带有你角色标签的任务：
   - `role:graph`：武桐宇；
   - `role:wind`：刘芯妤；
   - `role:evidence`：孙奇衍；
   - `role:frontend`：范笑薇；
3. 打开任务，完整阅读 **目标、交付物、验收标准、数据来源**；
4. 在右侧选择 **Assignees → Assign yourself**；
5. 留一条评论：`我已领取，计划在 feat/xxx 分支完成。`

> [!WARNING]
> **若任务描述不清楚，不要猜。** 直接在 Issue 评论区提问，让问题和答案留在任务卡里。

### 第 2 步：把任务交给 Codex

在 Codex 中打开本项目工作目录，然后复制下面的模板，把 `#编号` 换成你领取的 Issue 编号：

```text
请处理 GitHub 仓库 Koukou-is-King/low-altitude-investment-agent 的 Issue #编号。

你的目标是：<复制 Issue 中的目标>。
请在分支 feat/模块-简短名称 中完成，不要直接修改 main，也不要改动无关文件。

交付物必须包含：<复制 Issue 中的交付物>。
完成后请：
1. 运行适当的检查；
2. 用清晰的中文 commit message 提交；
3. 推送分支；
4. 创建 Pull Request，描述中写 Closes #编号、验证方式、数据来源和未解决风险。
```

### 第 3 步：检查 Codex 的成果

在点击合并前，你至少要检查四件事：

- **文件是否放对位置**：例如图谱数据在 `graph/`，Wind 样本在 `data/`；
- **是否满足 Issue 验收标准**：不要只看“Codex 说完成了”；
- **是否有数据来源**：政策、公告、公司业务映射均需链接或证据编号；
- **是否泄露敏感信息**：不能提交 Wind 原始导出、账号、密码、API Key、个人隐私信息。

### 第 4 步：创建 PR

当 Codex 已推送分支后，在 GitHub 通常会看到 **Compare & pull request** 按钮。点击后：

1. 标题写成：`[图谱] 完成产业链节点与传导规则 V1`；
2. 正文保留模板，并写上 `Closes #编号`；
3. 填写“实现内容、验证、数据与证据、风险或待办”；
4. 点击 **Create pull request**；
5. 等待 Actions 检查；若失败，打开 **Actions** 查看错误，并把错误交给 Codex 修复；
6. 请求队长或对应负责人 Review。通过后由队长合并。

> [!IMPORTANT]
> **创建 PR 不等于合并。** PR 是请队友检查的申请；只有审查、自动检查和数据口径都通过后，才能 Merge。

---

## 第四部分：不同角色要让 Codex 做什么

| 成员 | 从哪个 Issue 开始 | 给 Codex 的关键要求 |
|---|---|---|
| 武桐宇 | #2 图谱 | “建立可读 CSV/JSON；每条关系有来源或待核验标记；覆盖完整传导路径。” |
| 刘芯妤 | #3 Wind | “不提交受限原始数据；提供字段口径、模拟样例、确定性评分公式和测试。” |
| 孙奇衍 | #4 证据 | “每条事件记录来源、日期、链接、可信度；用原始政策/公告，不用二手结论。” |
| 范笑薇 | #5 前端 | “使用标准 JSON mock 数据；不等待真实后端；展示事件、路径、公司评分和证据。” |
| 吕洪宇 | #1 架构 | “先跑通模拟端到端链路；统一接口；让后续模块可替换接入。” |

---

## 第五部分：遇到这些情况怎么办

| 情况 | 正确处理 |
|---|---|
| 不知道任务是什么意思 | 在 Issue 评论区提问，不要私下猜测 |
| Codex 修改了很多无关文件 | 让它撤回无关修改，只保留本 Issue 所需变更 |
| Actions 显示红色失败 | 把失败日志复制给 Codex，要求它定位并修复后更新 PR |
| 两个人改到同一文件 | 先在 Issue 评论区协调，由队长决定谁保留主责 |
| 不确定数据能否上传 | 默认不要上传；先在 Issue 中问队长 |
| PR 被要求修改 | 这不是失败；把 Review 意见交给 Codex，修复后推送到原分支即可 |

---

## 第六部分：可选的 GitHub 内 Codex 协作

如果仓库已在 Codex Cloud 中连接并启用了相关功能，可以在 Issue 或 PR 评论中提及 `@codex` 发起任务，或在 PR 中使用 `@codex review` 请求检查。该能力需要仓库连接和相应权限；即使未配置，团队仍可通过桌面版 Codex 完整执行上述流程。

官方说明：

- [从 GitHub Issue/PR 发起 Codex 任务](https://learn.chatgpt.com/docs/cloud)
- [让 Codex 审查 GitHub Pull Request](https://learn.chatgpt.com/docs/third-party/github)

## 最后检查清单

在说“我完成了”之前，确认：

- [ ] 我领取了一个 Issue；
- [ ] 我没有直接修改 `main`；
- [ ] 我让 Codex 创建了清晰的 commit 和 PR；
- [ ] PR 写了 `Closes #编号`；
- [ ] 我检查了 Actions；
- [ ] 我标注了数据来源与风险；
- [ ] 我没有上传任何账号、密钥、Wind 原始受限数据或个人信息。
