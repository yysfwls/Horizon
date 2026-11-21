---
layout: default
title: "Horizon Summary: 2026-11-21 (ZH)"
date: 2026-11-21
lang: zh
---

> 从 45 条内容中筛选出 6 条重要资讯。

---

**AI**
1. [陶哲轩博客：无外力 Navier-Stokes 奇点与广义黎曼猜想](#item-ai-news-1) ⭐️ 8.0/10
2. [Thinking Machines 发布开放权重模型 Inkling 2 Mini](#item-ai-news-2) ⭐️ 7.0/10
3. [台积电据报暂停中国公司 16nm 及以下订单](#item-ai-news-3) ⭐️ 7.0/10
4. [ChatGPT Space 协作空间向 Plus 用户开放](#item-ai-news-4) ⭐️ 7.0/10

**开源 / 开发工具**
1. [GitHub Enterprise Server 3.23 发布候选版](#item-devtools-news-1) ⭐️ 7.0/10
2. [GitHub 安全公告权限正式可用](#item-devtools-news-2) ⭐️ 6.0/10

---

## AI

<a id="item-ai-news-1"></a>
### [陶哲轩博客：无外力 Navier-Stokes 奇点与广义黎曼猜想](https://terrytao.wordpress.com/2026/11/20/unforced-euler-singularity-unforced-navier-stokes-singularity-and-the-generalized-riemann-hypothesis/) ⭐️ 8.0/10

陶哲轩在博客文章中讨论了无外力 Navier-Stokes 奇点与广义黎曼猜想，Hacker News 上的讨论随后聚焦于 Lean 形式化验证以及 AI 在数学中的角色。评论称该结果已被两个独立内核接受，但这只是社区说法；由于条目未提供博客正文，本文无法核实证明范围、假设条件或 AI 的实际参与程度。

hackernews · archon1410 · 11月20日 17:21 · [社区讨论](https://news.ycombinator.com/item?id=50578358)

**「背景」** 无粘的欧拉方程与带粘性的纳维-斯托克斯方程是否会在有限时间内产生奇点（即解爆破），是流体偏微分方程理论中长期未决的核心问题；三维纳维-斯托克斯方程解的存在性与光滑性也位列千禧年大奖难题。广义黎曼猜想（GRH）则是黎曼猜想在狄利克雷 L 函数等更一般对象上的推广。Tao 的这篇博文把欧拉方程奇点、纳维-斯托克斯方程奇点与 GRH 放在同一标题下，标签中含 AI，并列出 Levent Alpöge、Matei Coiculescu、Tristan Buckmaster 等名字；评论中关注的 Lean 验证，依赖近年在 mathlib 等库上积累的交互式定理证明基础设施。

**「社区讨论」** 评论区有人追问：现有抽象加上大规模生成与验证能推进证明，但“朗兰兹纲领”这类新抽象如何产生；另有人报告两个独立内核接受结果，并同时表达对 AI 数学能力的兴奋与不安。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://terrytao.wordpress.com/2026/11/20/unforced-euler-singularity-unforced-navier-stokes-singularity-and-the-generalized-riemann-hypothesis/">Unforced Euler singularity, unforced Navier-Stokes ...</a></li>

</ul>
</details>

**标签**: `#mathematics`, `#Navier-Stokes`, `#generalized Riemann hypothesis`, `#formal verification`, `#Lean`

---

<a id="item-ai-news-2"></a>
### [Thinking Machines 发布开放权重模型 Inkling 2 Mini](https://thinkingmachines.ai/news/inkling-2-mini/) ⭐️ 7.0/10

Thinking Machines Lab 发布开放权重模型 Inkling 2 Mini，采用循环 Transformer 架构，将中间 12 层每个 token 运行三次；总参数 26.4B、激活 3.4B，内存占用约 20GB，可在 32GB 以上内存的 Mac 本地运行。社区评论称其在快速编码测试中表现不错，并在 Ryzen 395 搭配 llama.cpp Vulkan 的环境下达到 27 tokens/s 解码，另有 M1 Pro/32GB 用户报告约 10 tokens/s。这些速度与基准比较来自评论，尚未独立验证；有评论将其与 Qwen3.8-27B 相提并论，但明确以基准在真实场景中成立为前提。

hackernews · jasondavies · 11月20日 20:12 · [社区讨论](https://news.ycombinator.com/item?id=50581260)

**「循环 Transformer 与 Inkling 系列背景」** Inkling 2 Mini 属于 Thinking Machines Lab 的 Inkling 系列；据该系列页面介绍，这一系列中最小的一款就是“能在笔记本上运行、擅长智能体编程”的循环 Transformer，而 Inkling 2 Mini 是该公司第二代模型。据官方发布页说明，它采用混合专家（MoE）结构，总参数 26.4B、每 token 激活 3.4B；若把循环部分计入，每 token 的权重激活量为 5.4B。官方还称，循环让模型可以在不把推理过程写出来的情况下思考更久，而这一点与其可监控性相关，即通过阅读思维链来监督和理解模型的行为。

**「影响」** 对希望本地运行模型的开发者，约 20GB 的内存需求使 32GB 内存的 Mac 成为可尝试的配置；但评论中的 10–27 tokens/s 表明实际可用性取决于硬件、量化方式和 llama.cpp 补丁状态。

**「社区讨论」** 评论中既有 Ryzen 395 上 27 tokens/s、M1 Pro 上约 10 tokens/s 的本地实测，也有对其基准能否在真实场景成立的保留；还有人指出 llama.cpp 多个 PR 尚未合并，并给出约 30% 提速的临时补丁。另有评论认为开放权重的循环架构可能带动更多模型采用类似设计，同时追问其安全与可解释性影响。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thinkingmachines.ai/news/inkling-2-mini/">Introducing Inkling 2 Mini - Thinking Machines Lab</a></li>
<li><a href="https://thinkingmachines.ai/inkling/">Inkling - Thinking Machines Lab</a></li>

</ul>
</details>

**标签**: `#open-weight models`, `#looped transformers`, `#local inference`, `#model release`, `#benchmarks`

---

<a id="item-ai-news-3"></a>
### [台积电据报暂停中国公司 16nm 及以下订单](https://appleinsider.com/articles/26/11/20/apple-supplier-tsmc-cuts-off-china-chip-orders-amid-tighter-export-controls) ⭐️ 7.0/10

据 AppleInsider 报道，台积电已通知客户暂停接受中国公司 16nm 及以下先进制程订单，并称将遵守收紧后的美国半导体出口新规。新规要求，除非事先取得美国出口许可或豁免，否则不得供货；此前台积电可自行评估客户设计是否符合豁免条件，现在客户须提前申请。报道还称，美国获批名单中有苹果、AMD 和英伟达，尚无中国公司，中国企业因此只能使用 28nm、40nm 等较旧制程。

telegram · zaihuapd · 11月21日 02:01

**「背景」** 此前，台积电可依据算力等技术规格自行评估客户芯片设计是否落在美国出口管制范围之外，再决定是否接单。收紧后的规则要求客户事先取得美国出口许可或豁免，台积电因此暂停中国公司 16nm 及以下制程订单。

**「对中国芯片设计公司的影响」** 对中国芯片设计公司而言，直接影响是：在未获得美国出口许可前，16nm 及以下的订单需要暂停，客户只能转向 28nm、40nm 等旧制程，产品规划与流片节奏因此取决于许可审批。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.trendforce.com/news/2026/11/20/news-tsmc-samsung-reportedly-pause-china-consumer-chip-shipments-under-new-u-s-rules-16nm-orders-affected/">[News] TSMC , Samsung Reportedly Pause China Consumer Chip...</a></li>
<li><a href="https://www.reuters.com/world/china/tsmc-tightens-china-ai-chip-curbs-new-us-rules-close-manufacturing-loophole-2026-11-19/">TSMC tightens China AI chip curbs as new US rules close ...</a></li>
<li><a href="https://www.trendforce.com/news/2026/11/20/news-tsmc-samsung-reportedly-pause-china-consumer-chip-shipments-under-new-u-s-rules-16nm-orders-affected/">[News] TSMC, Samsung Reportedly Pause China Consumer Chip ...</a></li>
<li><a href="https://finance.yahoo.com/technology/ai/articles/tsmc-halting-china-chip-orders-131332877.html?fr=sycsrp_catchall">TSMC Is Halting Some China Chip Orders as a New U.S. Rule ...</a></li>

</ul>
</details>

**标签**: `#TSMC`, `#US export controls`, `#China semiconductors`, `#AI chips`, `#advanced nodes`

---

<a id="item-ai-news-4"></a>
### [ChatGPT Space 协作空间向 Plus 用户开放](https://x.com/ChatGPT/status/2123850912867471807) ⭐️ 7.0/10

ChatGPT 宣布，Space 协作空间已向 Plus 用户开放。该功能可用于与他人共同创建交互式页面、幻灯片和网站，支持手机端编辑，页面与幻灯片还能设置为从已连接工具自动更新。Space 位于侧边栏，集中存放页面、幻灯片、图片、文件和上传内容，并可邀请他人共同编辑；官方称整体更流畅稳定，但未提供独立验证结果。

telegram · zaihuapd · 11月21日 02:30

**「背景」** Space 是 ChatGPT 内用于集中存放页面、上传文件、幻灯片等内容的工作区，用户可与 ChatGPT 一起创建和编辑页面，并将作品分享给他人协作。OpenAI 的说明文档称，Space 前身为 Library，其定位是让人与智能体在同一处基于已有内容继续协作。

**「影响」** Plus 用户可在手机端参与编辑，并邀请他人共同维护页面或幻灯片；官方尚未披露并发编辑、权限控制或自动更新失败时的处理细节。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://chatgpt.com/features/space/">ChatGPT Space | Create and collaborate with AI</a></li>
<li><a href="https://help.openai.com/en/articles/20001549-getting-started-with-space-in-chatgpt">Getting started with Space in ChatGPT - OpenAI Help Center</a></li>
<li><a href="https://learn.chatgpt.com/docs/enterprise/chatgpt-space">Manage ChatGPT Space, pages, and slides | ChatGPT Learn</a></li>

</ul>
</details>

**标签**: `#ChatGPT`, `#Space feature`, `#collaboration`, `#product update`, `#Plus users`

---

## 开源 / 开发工具

<a id="item-devtools-news-1"></a>
### [GitHub Enterprise Server 3.23 发布候选版](https://github.blog/changelog/2026-11-20-github-enterprise-server-3-23-release-candidate) ⭐️ 7.0/10

GitHub Enterprise Server（GHES）3.23 发布候选版现已开放试用，这是正式版前的预览版本。该版本为 Projects 增加逻辑 OR、显式 AND 和括号分组过滤；在启用 GitHub Secret Protection 时，可预览基于本地 CPU 模型、无需 GPU 或外联的 AI 秘密检测；并扩展 GitHub Advisory Database 对 PyPI、Maven、RubyGems、NuGet、Go、Rust、Composer 中恶意包的识别。发布说明还提到 Dependabot 默认等待新版本发布三天再开 PR、OAuth 应用可选 8 小时访问令牌和刷新令牌，以及集群可将 Redis 主节点迁至专用节点。

rss · GitHub Changelog · 11月20日 20:41

**「背景」** GHES 是自托管的企业版 GitHub。3.23 以发布候选版形式提供，目的是让管理员在正式版前提前试用并反馈；该候选版同时列出 Projects 查询、AI 密钥检测、恶意包识别、Dependabot 冷却和 OAuth 令牌过期等改动。

**「影响」** 对 OAuth 应用开发者而言，启用令牌过期前必须让所有客户端支持请求、保存并使用刷新令牌，否则访问令牌 8 小时后失效会中断登录；该能力目前为公开预览，可作为渐进迁移的测试项。

**标签**: `#GitHub Enterprise Server`, `#self-hosted`, `#secret scanning`, `#GitHub Projects`, `#release candidate`

---

<a id="item-devtools-news-2"></a>
### [GitHub 安全公告权限正式可用](https://github.blog/changelog/2026-11-20-security-advisory-permissions-are-now-generally-available) ⭐️ 6.0/10

GitHub 宣布安全公告权限正式可用：组织所有者可以通过自定义仓库角色，让成员处理仓库安全公告和私有漏洞报告，而不必授予他们仓库管理员或组织级安全管理器角色。新增的四项权限分别覆盖查看公告；创建、编辑和管理公告；接受私有漏洞报告并关闭或重新打开公告；发布公告和申请 CVE。其中，接受报告和发布公告这两项权限需要配合“查看”或“创建、编辑和管理”权限使用，角色也可以只分配到成员需要访问的仓库。该功能适用于支持自定义仓库角色的组织，包括 GitHub Enterprise Cloud。

rss · GitHub Changelog · 11月20日 21:49

**「背景」** 此前，组织若要让人处理仓库安全公告和私有漏洞报告，往往只能授予仓库管理员或组织级安全管理角色，权限范围过大。此次变更将相关能力拆分为自定义仓库角色中的安全权限，使访问范围可以限定在特定仓库。

**「影响」** 这能让安全团队按仓库授予公告处理权限，减少对仓库管理员或组织级安全管理器角色的依赖；但合并临时私有 fork 仍需要仓库管理员或安全管理器，且拥有这些新权限的人不能删除临时私有 fork。机密评论仅对同时拥有仓库写权限和“创建、编辑和管理”权限的人开放。

**标签**: `#GitHub`, `#security advisories`, `#access control`, `#custom repository roles`, `#permissions`

---