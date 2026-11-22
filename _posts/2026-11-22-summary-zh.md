---
layout: default
title: "Horizon Summary: 2026-11-22 (ZH)"
date: 2026-11-22
lang: zh
---

> 从 32 条内容中筛选出 5 条重要资讯。

---

**AI**
1. [微软发布 RDMA over USB4 Windows 开发者预览](#item-ai-news-1) ⭐️ 7.0/10
2. [浙江大学团队称在“天目 2 号”超导芯片上首次真机实现 QRAM](#item-ai-news-2) ⭐️ 7.0/10
3. [daraxonrasib 一线联合化疗早期数据：61 例胰腺癌患者确认 ORR 60.7%](#item-ai-news-3) ⭐️ 7.0/10

**开源 / 开发工具**
1. [GPGME 2.3.0 之前版本漏洞披露](#item-devtools-news-1) ⭐️ 7.0/10
2. [显示器 USB 网卡为何把下载速度削减 75%](#item-devtools-news-2) ⭐️ 6.0/10

---

## AI

<a id="item-ai-news-1"></a>
### [微软发布 RDMA over USB4 Windows 开发者预览](https://videocardz.com/newz/microsoft-brings-rdma-over-usb4-to-windows-allowing-multiple-pcs-to-run-one-local-ai-model) ⭐️ 7.0/10

微软发布了 Windows 的 RDMA over USB4 开发者预览，让多台 PC 通过普通 USB4 连接共享内存与 GPU 算力，共同运行同一个本地 AI 大模型，无需专用网卡或交换机。演示中，三台搭载 AMD Ryzen AI Max+ 395 的 PC 以 4-bit 量化运行 Qwen3-235B-A22B，速度约为 18.5 token/s。该功能将通过 Windows Insider 推送，目前仍属于开发者预览。

telegram · zaihuapd · 11月21日 06:13

**「背景」** 本地大模型通常必须装入单台 PC 的内存与 GPU 显存，模型规模因此受单机容量限制。分布式推理会把模型拆分到多台机器，通过高速互联交换中间数据；RDMA 让机器之间直接访问内存，减少传统网络协议带来的额外开销。普通 USB4 连接可作为这种互联的物理通道，因此不必依赖专用网卡或交换机。

**「影响」** 对拥有多台 USB4 PC 的开发者而言，这条路径可能在不添置专用网络设备的情况下，把分散的内存和 GPU 资源用于运行更大的本地模型；但当前仍是开发者预览，且演示依赖特定硬件平台。

**标签**: `#RDMA over USB4`, `#distributed inference`, `#local LLMs`, `#Windows`, `#Qwen3-235B-A22B`

---

<a id="item-ai-news-2"></a>
### [浙江大学团队称在“天目 2 号”超导芯片上首次真机实现 QRAM](https://finance.sina.com.cn/stock/2026-11-21/doc-iniznhsk3530826.shtml) ⭐️ 7.0/10

浙江大学团队据报在自主制备的超导量子芯片“天目 2 号”上首次于真机实现 QRAM（量子随机存储器），并运行了可调取 4 位和 8 位数据的原型。报道给出的准确率分别为 80.9%和 60.4%，线路深度较未优化方案降低 30%以上，团队还称首次验证了该架构的局部抗噪特性。成果据称发表于《自然·物理》，但现有转述未提供论文链接或实验细节，8 位原型的准确率也显示该工作仍处早期。

telegram · zaihuapd · 11月21日 08:31

**「背景：什么是 QRAM」** QRAM（量子随机存储器）被设想为量子计算机的数据读取部件：它允许以量子叠加的地址同时查询多个存储单元，从而把数据以叠加态取出。许多需要访问大规模数据的量子算法（如部分量子机器学习与数据库搜索方案）都依赖这一能力。其物理实现长期受限于线路深度和噪声敏感性，因为地址与数据的纠缠必须在大规模线路中保持相干。

**「影响」** 对量子计算研究者而言，这项工作的直接意义是提供了一个超导平台上的 QRAM 真机验证节点；但 8 位准确率仅 60.4%，说明它目前更像架构可行性演示，而非可直接用于量子机器学习数据加载的成熟内存。

**标签**: `#量子计算`, `#QRAM`, `#超导量子芯片`, `#Nature Physics`, `#量子硬件`

---

<a id="item-ai-news-3"></a>
### [daraxonrasib 一线联合化疗早期数据：61 例胰腺癌患者确认 ORR 60.7%](https://event.eortc.org/ena2026/2026/11/20/metastatic-pancreatic-cancer-responds-well-to-initial-treatment/) ⭐️ 7.0/10

在 ENA 2026 大会上公布的 late-breaking I/II 期单臂研究显示，口服 daraxonrasib（200 mg 每日一次）联合吉西他滨/白蛋白紫杉醇，用于 61 例既往未治疗的转移性胰腺导管腺癌患者，研究者报告确认客观缓解率 60.7%、完全缓解率 8.2%、疾病控制率 90.2%，中位无进展生存 12.8 个月，12 个月总生存率 76.6%，中位随访 18.3 个月。该研究没有化疗对照组，主要研究者表示与化疗的疗效比较仍需正在进行的 III 期试验验证；来源同时提醒，化疗历史 1 年生存率区间为 22%–48%（MPACT 35%、mFOLFIRINOX 48%），不宜直接称其“远高于化疗”。daraxonrasib 是口服 RAS\(ON\) 多选择性抑制剂，覆盖多种 KRAS/NRAS 突变；该药已于 8 月 26 日获 FDA 批准（商品名 RASONQUE）用于既往治疗后患者，依据是 III 期 RMC-302 的中位总生存 13.2 对 6.7 个月。

telegram · zaihuapd · 11月21日 11:24

**「背景」** 转移性胰腺导管腺癌的一线治疗以化疗为主，来源给出的历史参照为 1 年生存率 22%–48%（MPACT 试验 35%，mFOLFIRINOX 48%），因此单臂早期数据需要放在这一疗效区间内解读。Daraxonrasib 是口服 RAS\(ON\) 多选择性抑制剂，作用于活跃态 RAS，覆盖多种 KRAS/NRAS 突变，并非只针对单一 KRAS G12C 突变。

**「影响」** daraxonrasib 已于 2026 年 8 月获 FDA 批准，用于既往治疗后的转移性胰腺癌患者。因此，这批一线早期数据短期内不会改变现有的一线治疗路径。对临床研究者而言，正在进行的 III 期随机对照试验才是决定该药能否进入一线方案的关键。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://daraxon.com/news/fda-approves-daraxonrasib-rasonque">FDA Approves Daraxonrasib ( RASONQUE ) | Daraxon</a></li>
<li><a href="https://kolpulse.com/kol-pulse-trial-profile-rasolute302">RASolute 302 : FDA Approves Rasonque ( Daraxonrasib )... | KOL Pulse</a></li>

</ul>
</details>

**标签**: `#pancreatic cancer`, `#daraxonrasib`, `#RAS\(ON\) inhibitor`, `#phase I/II trial`, `#oncology`

---

## 开源 / 开发工具

<a id="item-devtools-news-1"></a>
### [GPGME 2.3.0 之前版本漏洞披露](https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html) ⭐️ 7.0/10

GPGME 2.3.0 之前的版本存在内存安全漏洞，影响以共享库、DLL 或静态链接方式使用它的下游软件。公告标题称其为 GnuPG RCE，但社区讨论认为实际是 double free，是否能构成 RCE 仍有争议。GitLab 因支持签名提交而受到关注，并已发布 Omnibus 相关补丁；披露时间从原定的 2026-11-25 提前到 2026-11-20。

hackernews · gdgghhhhh · 11月21日 08:32 · [社区讨论](https://news.ycombinator.com/item?id=50587208)

**「背景」** GPGME 2.3.0 之前的版本存在内存安全漏洞；社区评论指出它实际是 double free，而非标题所称的完整 RCE 链，因此“GnuPG RCE”的说法仍有争议。受影响范围不限于 GnuPG 本身：按评论列举，使用旧版 GPGME 共享库、DLL 或静态链接的邮件客户端、XMPP 客户端、Samba 等下游软件都可能受波及，GitLab 也发布了相关补丁。

**「影响」** 兼容性影响很直接：所有使用 2.3.0 之前 GPGME 的软件都受影响，无论 GPGME 以共享库、Windows DLL 还是静态链接方式集成；首个修复版本为 2.3.1。依赖 GPGME 的签名提交和其他下游工作流需要升级并重新构建验证，而且公告称该双重释放可用于数据外泄，不能排除 RCE。

**「社区讨论」** 评论对漏洞定性存在分歧：有人指出这是 double free 而非 RCE 链，质疑标题夸大；也有用户称 Red Hat 五年前已修复，但上游遗漏了该修复。另有评论称漏洞由 Johan Carlsson 发现，GitLab 于 2026-11-12 获悉，原定 2026-11-25 协调披露，因 Ruby2Shell 事件提前至 2026-11-20，并给出了 GitLab Omnibus 补丁链接。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://thehackernews.com/2026/11/gnupg-warns-critical-gpgme-flaw-could.html">GnuPG Warns Critical GPGME Flaw Could Expose App Data via...</a></li>
<li><a href="https://lists.gnupg.org/pipermail/gnupg-announce/2026q4/000517.html">[Announce] GnuPG Security Advisory for GPGME ...</a></li>
<li><a href="https://www.phoronix.com/news/GnuPG-GPGME-Critical">GnuPG&#x27;s GPGME Affected By Critical Security Bug In Turn... - Phoronix</a></li>

</ul>
</details>

**标签**: `#security-vulnerability`, `#GPGME`, `#GnuPG`, `#memory-safety`, `#downstream-impact`

---

<a id="item-devtools-news-2"></a>
### [显示器 USB 网卡为何把下载速度削减 75%](https://blog.tymscar.com/posts/studiodisplayethernet/) ⭐️ 6.0/10

一位开发者记录了排查下载速度骤降的过程，最终将问题指向显示器内置的 USB 以太网集线器，而非宽带线路或路由器。数据经过这条路径时额外延迟增加，以太网适配器缓冲区被填满并开始丢包，下载吞吐量因此下降约 75%。换成对确认频率要求更低的适配器后，速度恢复正常。

hackernews · soheilpro · 11月21日 10:36 · [社区讨论](https://news.ycombinator.com/item?id=50587875)

**「背景」** USB 以太网适配器和集线器把网络接入塞进共享的 USB 链路，平时看起来像一条透明网线，出问题时却很难定位。文章把故障范围缩小到显示器自带的 USB 网络路径，说明延迟和缓冲行为可能比接口标称速率更关键。

**「影响」** 对使用显示器或扩展坞内置网口的用户，排查吞吐问题时应先绕过该链路，用独立适配器或直连路由器端口做对比；若必须保留集线器，可尝试对确认频率要求更低的适配器并检查流控设置。代价是失去一根线同时连接显示器和网口的便利，但能快速区分线路问题与 USB 链路问题。

**「社区讨论」** 有评论者认为更准确的描述是“USB 网络交换机拖慢了下载速度”，显示器本身只是载体。另一位评论者解释，额外延迟使笔记本无法及时确认数据包，适配器缓冲被填满后触发丢包；还有人报告在 MacBook 加 Thunderbolt 扩展坞上遇到类似问题，最终靠启用流控缓解。

**标签**: `#USB networking`, `#hardware debugging`, `#ethernet throughput`, `#packet loss`, `#latency`

---