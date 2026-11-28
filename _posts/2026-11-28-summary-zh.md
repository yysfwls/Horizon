---
layout: default
title: "Horizon Summary: 2026-11-28 (ZH)"
date: 2026-11-28
lang: zh
---

> 从 38 条内容中筛选出 4 条重要资讯。

---

**AI**
1. [Google Research 介绍 DeepCrossAttention：称质量相当、速度最高提升 3 倍](#item-ai-news-1) ⭐️ 7.0/10
2. [多州总检察长起诉 SpaceX，要求阻止 Grok 生成儿童性虐待与非自愿私密图像](#item-ai-news-2) ⭐️ 7.0/10

**Web 开发**
1. [购物网站支付盗刷脚本滥用 WebRTC：第三方脚本仍是核心风险](#item-web-development-1) ⭐️ 6.0/10

**开源 / 开发工具**
1. [计算机验证的证明未必为真](#item-devtools-news-1) ⭐️ 6.0/10

---

## AI

<a id="item-ai-news-1"></a>
### [Google Research 介绍 DeepCrossAttention：称质量相当、速度最高提升 3 倍](https://research.google/blog/supercharging-transformer-residual-connections/) ⭐️ 7.0/10

Google Research 在一篇关于 Transformer 残差连接的博客文章中介绍了 DeepCrossAttention，并声称在模型质量相当的情况下可实现最高 3 倍的速度提升。目前可获得的材料只有文章标题、摘要性描述和 Hacker News 讨论，未提供独立的基准测试细节、具体任务或复现结果。因此，3 倍加速仍是 Google 方面的主张，而非经外部验证的测量结论。

hackernews · ComputedCamp995 · 11月27日 23:06 · [社区讨论](https://news.ycombinator.com/item?id=50672565)

**「背景」** 残差连接是 Transformer 的基础结构，把前几层的输出直接相加后继续传递；但这种简单求和可能稀释关键信息。Google Research 在 ICML 2025 论文中提出 DeepCrossAttention（DCA），让每一层能够从前面各层的特征历史中动态选择和路由特征，从而对残差连接做出泛化，相关预印本已于 2025 年 2 月在 arXiv 公开。

**「社区讨论」** 评论区对图表形式提出异议，认为不同方法之间没有时间关系，不应使用折线图而应使用柱状图；其余讨论未给出独立的性能验证。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://research.google/blog/supercharging-transformer-residual-connections/">Supercharging transformer residual connections - Google Research</a></li>
<li><a href="https://arxiv.org/abs/2502.06785">[2502.06785] DeepCrossAttention: Supercharging Transformer ...</a></li>

</ul>
</details>

**标签**: `#transformer architecture`, `#residual connections`, `#training efficiency`, `#Google Research`, `#DeepCrossAttention`

---

<a id="item-ai-news-2"></a>
### [多州总检察长起诉 SpaceX，要求阻止 Grok 生成儿童性虐待与非自愿私密图像](https://www.oag.state.va.us/media-center/news-releases/jay-jones/3162-attorneys-general-jones-and-rayfield-file-suit-against-spacex-parent-company-of-x-xai-and-grok-over-creation-and-promotion-of-child-exploitation-and-non-consensual-images-on-platform) ⭐️ 7.0/10

弗吉尼亚州总检察长办公室发布消息称，多州总检察长（由 Jones 与 Rayfield 牵头）对 SpaceX 提起诉讼；SpaceX 是 X、xAI 及其 Grok 模型的母公司。诉状指控 Grok 被用于生成儿童性虐待材料和未经同意的私密图像，并指控相关平台对这些内容的创建与传播起到推动作用。现有材料只有总检察长办公室的公告，未披露具体诉求、受理法院、涉及州的数量以及任何独立测得的滥用规模数据，因此这些细节仍不明确。

hackernews · DeepLogin · 11月27日 19:42 · [社区讨论](https://news.ycombinator.com/item?id=50670855)

**「背景」** 此前，俄勒冈州和弗吉尼亚州总检察长已就 Grok Imagine 生成性化图像起诉 SpaceX，指其违反州消费者保护法；X Safety 当时回应称，保护儿童不可谈判，CSAM 以及未经同意制作的真实人物露骨图像都不应存在于 X 或 Grok 上。

**「影响」** 这起诉讼把图像生成模型的安全防护与内容审核责任直接推到司法层面：对提供图像生成能力的产品团队而言，滥用检测、年龄与同意相关的限制，以及在收到举报后的处置流程，都可能成为被审查的合规环节。

**「社区讨论」** 有评论者困惑的是，此类内容在其他平台已被广泛禁止，Grok 究竟是默认防护过于宽松，还是需要用户刻意“诱导”才能生成。另有评论者追问，除了平台责任，实施生成行为的用户本人是否也应被追责。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.cnbc.com/2026/11/23/oregon-virginia-spacex-grok-deepfake-lawsuits.html">SpaceX sued by 2 states over AI deepfake porn, Grok safety claims</a></li>
<li><a href="https://www.nytimes.com/2026/11/23/technology/spacex-lawsuit-ai-sexualized-images.html">SpaceX Sued By Oregon and Virginia Over A.I.-Generated...</a></li>
<li><a href="https://www.engadget.com/2325111/two-states-sue-spacex-over-sexually-explicit-grok-deepfakes/">Two States Sue SpaceX Over Sexually Explicit Grok Deepfakes</a></li>

</ul>
</details>

**标签**: `#AI safety`, `#image generation`, `#legal liability`, `#child exploitation`, `#platform moderation`

---

## Web 开发

<a id="item-web-development-1"></a>
### [购物网站支付盗刷脚本滥用 WebRTC：第三方脚本仍是核心风险](https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer) ⭐️ 6.0/10

一份安全报告称，在热门购物网站上发现支付盗刷（skimming）脚本利用 WebRTC 外传数据；现有材料仅到标题和评论层面，未给出可复现样本、受影响域名数量或具体浏览器版本。讨论中的技术判断是，问题不在于 WebRTC 本身存在独特漏洞，而在于它较少被支付页监控，攻击者同样可以用普通 HTTP 请求达到目的。对电商团队而言，这更像一次提醒：结账页嵌入的第三方 JavaScript 是主要暴露面，需要按供应链风险来审计。

hackernews · scanr · 11月27日 15:40 · [社区讨论](https://news.ycombinator.com/item?id=50668145)

**「前置背景：外传通道与 CSP 盲区」** 多数支付盗刷检测方案会关注脚本是否通过普通 HTTP 请求把数据发往陌生域名，而 CSP 的 connect-src 等规则也主要约束此类请求；WebRTC 的数据通道则是另一条外传路径，CSP 对它的覆盖方式并不相同 \[tool-2-3\]。本次报告提到的植入发生在 Lascana、Samsonite、American Tourister、Revolve 和 FWRD 等购物站点，相关公司在收到通报后采取了处置 \[tool-2-1\]。

**「工程影响」** 把结账与支付页的第三方脚本收敛到可审计的最小清单，并在上线前检查这些脚本是否会发起 WebRTC 连接或向非预期域外传数据；不要因为封禁 WebRTC 就认为风险已消除。

**「社区讨论」** 评论指出，WebRTC 只是较少被监控的外传通道，换成普通 HTTP 请求同样可行；只要站点嵌入第三方脚本，就始终存在被植入盗刷代码的暴露面。另有评论主张对广告和第三方代码做沙箱化，避免其在页面上下文中执行任意 JavaScript。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.infohawk.com/news/2026-11-27-black-friday-webrtc-skimmer">Credit card skimming scripts using WebRTC found on popular ...</a></li>
<li><a href="https://www.cosmicjs.com/rundown/cosmic-rundown-webrtc-skimmers-verified-proofs">Cosmic Rundown: WebRTC Skimmers, Verified Proofs</a></li>

</ul>
</details>

**标签**: `#web security`, `#third-party scripts`, `#WebRTC`, `#payment skimming`, `#CSP`

---

## 开源 / 开发工具

<a id="item-devtools-news-1"></a>
### [计算机验证的证明未必为真](https://cr.yp.to/proofs/falseccp.html) ⭐️ 6.0/10

这是一篇论述性文章，而非新工具或版本发布。它警告，计算机检查过的证明也可能是假的：证明检查器自身的健全性（soundness）缺陷可能让错误证明通过。文章面向形式化验证和证明检查器工作流，提醒读者不要把“机器已验证”直接等同于数学或实现上的正确性。

hackernews · \_tk\_ · 11月27日 15:26 · [社区讨论](https://news.ycombinator.com/item?id=50667989)

**「背景」** 这篇文章针对的是证明检查器的一项基础假设：只要程序逐步检查通过，证明就可信。作者援引已报告的“可靠性漏洞”（soundness bugs），这些漏洞至少可能让错误陈述绕过检查，因此需要重新审视机器验证结果的可靠性边界。

**「影响」** 对依赖形式化验证的团队，直接取舍是：只信任单一检查器的接受结果会留下残余风险；采用多套独立检查器或人工审查可降低被单个健全性缺陷误导的概率，但会增加验证成本。

**「社区讨论」** 评论者主要在为风险定界：twotwotwo 指出，一次错误验证要真正误导数学界，通常还得同时骗过多个检查器，并让输入在非形式审查中显得合理；dwheeler 则举例说，Metamath 的 set.mm 和 iset.mm 要求五个独立编写、使用不同语言的验证器全部通过。gr\_norm 认为这类健全性缺陷数量很少、对绝大多数软件已足够可靠，andai 补充了另一种风险：证明可能针对的是被误解的需求规格。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://cr.yp.to/proofs/falseccp.html">False computer - checked proofs (djb)</a></li>

</ul>
</details>

**标签**: `#formal verification`, `#proof checkers`, `#soundness bugs`, `#Metamath`, `#Lean`

---