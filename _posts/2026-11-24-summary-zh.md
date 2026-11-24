---
layout: default
title: "Horizon Summary: 2026-11-24 (ZH)"
date: 2026-11-24
lang: zh
---

> 从 48 条内容中筛选出 8 条重要资讯。

---

**AI**
1. [智谱发布 GLM-5.4，首次采用循环 Transformer](#item-ai-news-1) ⭐️ 8.0/10
2. [NariQ 发布 Qwen3.8-27B 的 3 位及以下 GGUF 量化](#item-ai-news-2) ⭐️ 7.0/10
3. [vLLM 为 ERNIE 5.5 Flash Preview 提供 Day-0 插件支持](#item-ai-news-3) ⭐️ 7.0/10
4. [Codex2api 被指遭供应链投毒，3.1.10–3.1.12 版本受影响](#item-ai-news-4) ⭐️ 7.0/10

**Web 开发**
1. [Ladybird 浏览器进入 Alpha 阶段](#item-web-development-1) ⭐️ 9.0/10

**开源 / 开发工具**
1. [GitHub Issues 新增状态与仓库看板公开预览](#item-devtools-news-1) ⭐️ 7.0/10
2. [Stalwart 宣称成为 Microsoft Exchange 的直接替代品](#item-devtools-news-2) ⭐️ 6.0/10
3. [GPUI 将拆分为独立仓库](#item-devtools-news-3) ⭐️ 6.0/10

---

## AI

<a id="item-ai-news-1"></a>
### [智谱发布 GLM-5.4，首次采用循环 Transformer](https://z.ai/blog/glm-5.4) ⭐️ 8.0/10

智谱 AI 发布 GLM-5.4，并将其描述为首个采用循环 Transformer 架构、面向通用编程的模型。现有材料没有提供可独立核验的基准或速度数据；社区用户称该模型暂未通过 OpenRouter 或常规 Z.ai API 套餐开放，需使用 Coding Plan 才能获得可用的 API 密钥。有评论者还抱怨此类中国模型存在长时间“反复思考”，在简单任务上也会拖长完成时间。

hackernews · foohis · 11月23日 10:06 · [社区讨论](https://news.ycombinator.com/item?id=50609685)

**「背景」** 循环 Transformer（Loop Transformer）指在推理中多次复用同一组层权重、以迭代方式增加有效计算深度的架构，而不是为每一层都配置独立参数。Z.ai 称 GLM-5.4 是其首个基于该架构的旗舰模型，并称其智能水平可对标 2T–3T 参数模型。

**「影响」** 对开发者而言，当前尝鲜需要通过 Coding Plan 获取访问权限，而报告中的长思考时间可能影响交互式编码和批量生成的工作流；循环 Transformer 若真能缓解权重搬运带来的内存带宽瓶颈，才会转化为实际推理成本优势，但目前尚无独立测量支持这一点。

**「社区讨论」** 评论者赞赏智谱公开较多技术细节，认为这比西方公司的封闭做法更透明，并把循环 Transformer 视为复用权重、缓解推理内存带宽瓶颈的合理方向。也有用户用鹈鹕 SVG 生成做对比，称 GLM-5.4 与 GLM-5.3 的输出看起来相近，同时对简单任务耗时变长表示不满。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://z.ai/blog/glm-5.4">GLM-5.4: Toward Generalized Coding with Our First Loop ... - z.ai</a></li>
<li><a href="https://docs.z.ai/guides/llm/glm-5.4">GLM-5.4 - Overview - Z.AI DEVELOPER DOCUMENT</a></li>

</ul>
</details>

**标签**: `#GLM-5.4`, `#looped transformers`, `#coding models`, `#model release`, `#Zhipu AI`

---

<a id="item-ai-news-2"></a>
### [NariQ 发布 Qwen3.8-27B 的 3 位及以下 GGUF 量化](https://huggingface.co/nari-labs/Qwen3.8-27B-NariQ-GGUF) ⭐️ 7.0/10

NariQ 在 Hugging Face 发布了 Qwen3.8-27B 的 3 位及以下 GGUF 量化版本，称能在 10 GB 文件中保留接近 BF16 的质量，覆盖代理任务、数学、多语言推理和图像理解。其自报基准显示，3 位版本在 DeepSWE（41.0 对 BF16 39.8）、Terminal-Bench 2.1（63.8 对 62.6）和 AIME（98.3 对 97.7）上不低于 BF16，2.5 位大体接近，而 2 位在 DeepSWE 降至 28.6、Terminal-Bench 降至 52.4。在 RTX PRO 6000 上，3 位、2.5 位、2 位版本在 4K 上下文下的解码速度为 88.9、99.2、111.7 tok/s，在 64K 时为 70.7、77.5、85.0 tok/s。运行目前需要 NariQ 的 llama.cpp 分支；有评论者报告在 M3 Pro（18 GB）上 3.0bpw 文件约 3.8 tok/s，且上述质量与速度数据均为项目自报。

hackernews · toebee · 11月23日 13:42 · [社区讨论](https://news.ycombinator.com/item?id=50611402)

**「背景：GGUF 量化与运行依赖」** 这些 NariQ 文件是 3.0、2.5 和 2.0 比特/权重的 GGUF 模型，采用 trellis 编码；位宽越低，文件通常越小，但需要对应的推理支持。Nari Labs 表示，原版 llama.cpp、Ollama 和 LM Studio 目前还不能加载这些文件，必须使用其 llama.cpp 分支。

**「影响」** 对开发者的直接后果是：要在本地试用，需从 nari-llama.cpp 分支源码构建；在 16GB 级设备上，3.0bpw 文件在 M3 Pro 上仅约 3.8 tok/s，2 位版本虽更快但在代理与终端任务上分数大幅下滑，因此若自报数据成立，2.5 位或 3 位更可能是质量与速度的折中点。

**「社区讨论」** 评论者肯定该项目在多种长程任务和“held out”设置上做了基本检查，但也担心这类高算力量化会过拟合基准，并认为图表中的部分提升可能来自测试框架差异。另有评论者追问文件变小时究竟丢失了什么信息，而非只是减少噪声。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://github.com/nari-labs/nari-llama.cpp">GitHub - nari -labs/ nari - llama . cpp : llama . cpp fork that runs NariQ ...</a></li>

</ul>
</details>

**标签**: `#quantization`, `#GGUF`, `#Qwen3.8-27B`, `#llama.cpp`, `#local inference`

---

<a id="item-ai-news-3"></a>
### [vLLM 为 ERNIE 5.5 Flash Preview 提供 Day-0 插件支持](https://vllm.ai/blog/2026-11-24-ernie-5-5-flash-preview) ⭐️ 7.0/10

百度 ERNIE 团队与 vLLM 团队宣布，ERNIE 5.5 Flash Preview 在发布当天通过独立的 vLLM-ERNIE 插件获得 vLLM 支持；用户把插件安装到与官方 vllm==0.32.0 wheel 相同的环境中即可，vLLM 会通过 vllm.general\_plugins 入口自动发现插件。该模型是 280B 总参数、每 token 激活 14B 的稀疏 MoE，支持 1M token 上下文、先思考后回答以及面向长程 Agent 任务的工具调用；默认 checkpoint 将路由专家存为 MXFP4（W4A8），其余权重为 FP8，KV cache 为 FP8。双方称，随权重发布的 FlashIndexer 在 1M 上下文下带来 40% 的索引加速，DSpark 草稿模型每步最多提议 7 个 token、在真实编码与 Agent 工作负载上平均接受长度超过 4.0，融合 kernel 相比逐算子实现快 1.55× 到 6.53×。这些加速数字来自团队自述，所给内容未包含独立基准或端到端量化结果，且原文在 FlashIndexer 部署部分被截断。

rss · vLLM Blog · 11月24日 00:00

**「背景」** ERNIE 5.5 Flash Preview 是百度的稀疏混合专家（MoE）模型：总参数 280B，每个 token 激活 14B，并提供 100 万 token 上下文。此次 vLLM 的首日支持以独立 vLLM-ERNIE 插件形式提供，需与官方 vllm==0.32.0 wheel 安装在同一环境中，无需维护模型专用分支或等待专用镜像。

**「影响」** 对开发者而言，最直接的变化是部署环节变简单了：不用维护 vLLM fork、专用 Docker 镜像，也不用等 nightly wheel；在 vllm==0.32.0 环境中安装 vLLM-ERNIE 插件后，即可在单台 4-GPU 节点上以默认 FP4 权重启动服务，并由 DSpark 每步草拟最多 7 个 token。由于 1M 上下文、思考模式与工具调用都落在同一套 vLLM 栈内，长程 Agent 应用的试用门槛主要取决于硬件与效果验证；社区转述的 Terminal-Bench v4.0 16%、DeepSWE v1.1 15% 等分数也提示，它能否替代现有模型仍要看具体任务表现。

<details><summary>参考链接</summary>
<ul>
<li>New Model &quot;Ernie 5.5 Flash Preview&quot; hits strongly at a low parameter count (280B, 14B Active) : r/LocalLLaMA - Reddit</li>

</ul>
</details>

**标签**: `#vLLM`, `#ERNIE`, `#mixture-of-experts`, `#long-context`, `#inference-infrastructure`

---

<a id="item-ai-news-4"></a>
### [Codex2api 被指遭供应链投毒，3.1.10–3.1.12 版本受影响](https://github.com/WormW/codex2api-incident-2026-11) ⭐️ 7.0/10

据 Telegram 频道 zaihuapd 转述的一份事件复盘，Codex2api 作者账号被黑，攻击者绕过 main 分支推送 tag，使 Release 构建出带后门的 v3.1.10–v3.1.12 版本；其中 v3.1.11 被指移除鉴权，可能导致未认证的远程命令执行，另有 workflow 外传仓库的 16 个 Actions secrets，波及同账号下至少 21 个仓库。该报告建议已安装或更新至上述版本的用户立即停用、回退到 3.1.9，并轮换 GitHub token、SSH key、数据库及 DeepSeek 等相关密钥。上述内容来自单一 Telegram 转述，所引用的原始复盘和报告未在条目中展开，也未见独立验证。

telegram · zaihuapd · 11月23日 11:21

**「背景」** 供应链投毒通常指攻击者不直接攻击最终用户，而是入侵依赖、发布账号或构建流程，让带恶意代码的版本被下游正常安装。此事件的关键前提是 Release 由 CI/Workflow 构建，且仓库 secrets 可被工作流读取；一旦发布权限或工作流被篡改，影响就会沿构建产物和凭据扩散。

**「实际影响」** 对部署过 v3.1.10–v3.1.12 的用户来说，最直接的后果是应当把运行这些版本的主机视为已被入侵：v3.1.11 取消鉴权后，只要能访问该服务，就能远程执行命令；同时，workflow 外传了 Actions secrets，环境中配置的 GitHub token、SSH key、数据库和 DeepSeek 密钥都应视为已泄露并全部轮换，并隔离旧实例，保留日志以便排查。三个恶意版本已从 GitHub 移除，维护者于 11 月 23 日 10:50 UTC 发布 v3.2.0 作为紧急安全更新，因此靠版本号锁定的部署需要重新核对来源后再升级。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://ccnavx.com/blog/codex2api-supply-chain-incident">Codex2API Supply Chain Attack: Affected Versions &amp; Fix</a></li>

</ul>
</details>

**标签**: `#supply-chain-attack`, `#security-incident`, `#github-actions`, `#credential-rotation`, `#ai-dev-tooling`

---

## Web 开发

<a id="item-web-development-1"></a>
### [Ladybird 浏览器进入 Alpha 阶段](https://ladybird.org/posts/alpha/) ⭐️ 9.0/10

Ladybird 浏览器项目宣布进入 alpha 阶段，标志着从零实现的浏览器引擎已达到可在真实网站上试用的里程碑。当前阶段更适合兼容性测试与早期反馈，尚不等于稳定日常使用；所给信息未披露具体版本号、支持平台或性能数据。

hackernews · janvdberg · 11月23日 16:13 · [社区讨论](https://news.ycombinator.com/item?id=50614249)

**「背景：从零实现的浏览器引擎与 alpha 阶段」** Ladybird 是一个不基于 Chromium 或 Gecko 内核、从零编写的浏览器引擎，因此它的每一次可用性提升都意味着需要自行补齐解析、布局、渲染与 Web 平台 API 等大量基础实现。对浏览器引擎而言，进入 alpha 通常表示引擎与浏览器外壳已能在真实网站上运行，但兼容性覆盖、性能细节和接口稳定性仍不完整，尚未达到日常使用的成熟度。

**「影响与行动」** 当前可执行的步骤是：在 macOS 或 Linux 上安装 Ladybird alpha（目前仅提供这两个平台的版本），并用现有站点做一轮渲染与交互的冒烟测试。由于 Ladybird 是完全自研、与 Chromium、Gecko、WebKit 没有继承关系的引擎，站点兼容性差异应按“新引擎适配”来处理，而不是当作现有浏览器的小版本升级；alpha 阶段也不宜作为生产或日常主力浏览器，需保留原浏览器以便回退。

**「社区实测与关注点」** 社区评论中，有用户称在新闻站点、Proxmox/NoVNC 等实际页面上渲染正常，NoVNC 的响应甚至优于 Firefox，但页面滚动仍有轻微卡顿；也有人提到改用 SQLite、Skia 等成熟库显著提升了浏览器，并呼吁重视指纹防护、细化权限，同时提醒 alpha 阶段的安全风险。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://ladybird.org/">Ladybird is a truly independent web browser , backed by a non-profit.</a></li>
<li><a href="https://blog.openreplay.com/ladybird-non-chromium-browser/">Exploring Ladybird , the Non-Chromium Browser Project</a></li>

</ul>
</details>

**标签**: `#Ladybird`, `#browser-engine`, `#alpha-release`, `#web-compatibility`, `#open-source`

---

## 开源 / 开发工具

<a id="item-devtools-news-1"></a>
### [GitHub Issues 新增状态与仓库看板公开预览](https://github.blog/changelog/2026-11-23-issue-statuses-and-repository-boards-are-in-public-preview) ⭐️ 7.0/10

GitHub 于 2026 年 11 月 23 日宣布，Issues 状态和仓库看板进入公开预览。每个 issue 可设为 Backlog、Todo、In progress、In review、Done、Not planned 或 Duplicate，并在仓库 Issues 页、Issues 仪表盘和仓库看板中显示，支持用 \`status:\` 筛选。关联草稿 PR、将 PR 标记为可审查、分配用户或代理等操作会自动更新状态；GraphQL、REST API 和 MCP server 支持读取、设置及创建时指定状态，仓库保存视图也新增了可拖拽更新状态的看板布局。

rss · GitHub Changelog · 11月23日 20:37

**「背景」** 此前 GitHub Issues 主要用“打开/关闭”表达状态，难以直接说明工作处于待办、进行中还是评审中；仓库内的保存视图也没有看板布局。此次预览把这些状态和看板能力引入 Issues 本身，同时保留 GitHub Projects 供更复杂的规划使用。

**「影响」** 仓库看板让团队不必离开仓库即可按状态查看和更新 issue，适合轻量分诊；更复杂的规划仍应使用 GitHub Projects。由于关联 PR、分配人员和代理等操作会自动改变状态，团队需要提前约定状态流转规则，避免自动更新与手工维护不一致。

**标签**: `#GitHub Issues`, `#repository boards`, `#workflow tracking`, `#project management`, `#public preview`

---

<a id="item-devtools-news-2"></a>
### [Stalwart 宣称成为 Microsoft Exchange 的直接替代品](https://stalw.art/blog/microsoft-exchange-replacement/) ⭐️ 6.0/10

Stalwart 是一个开源邮件服务器，其博客文章宣称已成为 Microsoft Exchange 的直接替代品（drop-in replacement），面向希望自建邮件系统并沿用现有 Exchange/Outlook 工作流的组织。提供的页面正文缺失，因此该替代方案覆盖的协议、客户端、版本、许可和迁移路径都没有可核对的细节。仅从现有材料看，这是一项聚焦邮件基础设施兼容性的发布，而非已经得到独立验证的完整 Exchange 替代。

hackernews · shaunpud · 11月23日 22:32 · [社区讨论](https://news.ycombinator.com/item?id=50620349)

**「背景」** Stalwart 1.2.0 支持 MAPI over HTTP、Exchange Web Services（EWS）、ActiveSync 和 Autodiscover，使 Outlook、Apple Mail 与移动设备能够像连接 Exchange 一样连接它，目标是降低从 Exchange 迁移到开源邮件服务器时的客户端改造负担\[tool-2-1\]。这一兼容层出现时，Exchange Online 的 EWS 据称将于 2027 年 4 月完全停用，而新版 Outlook for Windows 仅通过微软云工作，使自建邮件系统的客户端兼容问题更加突出\[tool-2-3\]。

**「实际影响」** Stalwart 的实际价值在于，为希望降低 Exchange 授权成本的自建团队提供协议层替代方案；但迁移能否成功，取决于客户端，而不取决于服务器端。微软社区答复显示，新版 Outlook for Windows 尚不支持本地 Exchange 邮箱，该能力仍只保留在经典 Outlook 中，因此“直接替换”通常意味着需要保留或更换客户端。对于受德国 GoBD 约束的组织，评论还指出标准版和开源版不包含合规归档功能，需要单独评估。

**「社区讨论」** 评论者质疑“直接替代”的说法：有人指出，如果新版 Outlook 不再支持本地 Exchange 而只连接云端，那么替换的前提就值得怀疑；另有评论认为 Outlook/Exchange 集成和 Office 365 捆绑才是迁移的真正难点。还有德国用户提到，GoBD 要求邮件不可篡改地保存并可供税务部门访问最长 10 年，而 Stalwart 的常规计划或开源版本未包含该功能。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://stalw.art/blog/microsoft-exchange-replacement/">Stalwart is now a drop-in replacement for Microsoft Exchange</a></li>
<li><a href="https://www.startuphub.ai/ai-news/technology/2026/stalwart-1-2-0-replaces-exchange-and-keeps-outlook-working">Stalwart 1.2.0 replaces Exchange and keeps Outlook…</a></li>
<li><a href="https://learn.microsoft.com/en-us/answers/questions/4707738/unable-to-connect-on-premise-exchange-server-to-ne">unable to connect on-premise exchange server to new outlook</a></li>
<li><a href="https://learn.microsoft.com/en-us/answers/questions/2337260/unable-to-connect-on-premise-exchange-2016-2019-se">unable to connect on-premise exchange 2016/2019 server to new ...</a></li>

</ul>
</details>

**标签**: `#open-source email`, `#Microsoft Exchange`, `#mail server`, `#self-hosting`, `#interoperability`

---

<a id="item-devtools-news-3"></a>
### [GPUI 将拆分为独立仓库](https://github.com/zed-industries/gpui) ⭐️ 6.0/10

Zed 的 Rust UI 框架 GPUI 正在从编辑器代码库中分离出来，迁入独立仓库。条目说明称，这样做是为了让开发者更容易在编辑器项目之外发现和使用该框架。目前没有提供关于 API 稳定性、文档、发布节奏或采用情况的细节。

hackernews · EvilGoose · 11月23日 20:52 · [社区讨论](https://news.ycombinator.com/item?id=50619103)

**「背景」** GPUI 是驱动 Zed 编辑器的 GPU 加速 Rust UI 框架，此前它与编辑器代码同处一个 monorepo，外部开发者若要单独查找和使用它并不方便（tool-2-1、tool-2-2）。此次拆分将框架从编辑器仓库中解耦；现有信息显示，新仓库刚建立时内容还很少，后续发布与 API 稳定性尚不明确（tool-2-2）。

**「影响」** 拆分仓库后，实际使用成本主要在版本对齐上：gpui-kit 这类组件库需要锁定与之匹配的 GPUI 版本，并再导出 GPUI、base、component 和 assets 等模块，使应用只需声明一个依赖。这简化了应用侧的依赖清单，但也意味着 GPUI 的发布节奏会直接传导到组件库。

**「社区讨论」** 有评论者表示，GPUI 此前放在编辑器仓库里让人用起来不顺手，拆分后更愿意尝试；也有人称 gpui-kit 的组件丰富程度令人印象深刻，并拿自己用 iced 编写桌面应用的经历作对比。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://aicrier.com/post/x1889thidczie239557t">Zed splits GPUI into standalone repository — AICrier</a></li>
<li><a href="https://zeli.app/story/50619103">Zed spins GPUI out into its own repository · Hacker News | Zeli</a></li>
<li><a href="https://github.com/longbridge/gpui-kit">GitHub - longbridge/ gpui -kit: Rust GUI components for building...</a></li>

</ul>
</details>

**标签**: `#Rust`, `#GPUI`, `#UI framework`, `#Zed`, `#repository split`

---