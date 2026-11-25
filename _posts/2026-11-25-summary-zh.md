---
layout: default
title: "Horizon Summary: 2026-11-25 (ZH)"
date: 2026-11-25
lang: zh
---

> 从 32 条内容中筛选出 3 条重要资讯。

---

**AI**
1. [Ternary Bonsai 2.5 27B 本地推理表现引发讨论](#item-ai-news-1) ⭐️ 7.0/10

**开源 / 开发工具**
1. [GitHub.com 通知订阅规则将于 12 月 1 日调整](#item-devtools-news-1) ⭐️ 7.0/10
2. [uv 0.13.10 发布：修复安全公告并强化 uv.lock 校验](#item-devtools-news-2) ⭐️ 6.0/10

---

## AI

<a id="item-ai-news-1"></a>
### [Ternary Bonsai 2.5 27B 本地推理表现引发讨论](https://prismml.com/news/bonsai-2-5-27b) ⭐️ 7.0/10

PrismML 的 Ternary Bonsai 2.5 27B 新模型成为 Hacker News 讨论对象，但条目未附原文正文，目前可见的技术细节主要来自评论者。一名用户称，在 24GB 内存的 Mac Mini M5 Pro 上以 Q2 GGUF 运行该模型时，生成速度约 22.3 tok/s，首 token 约 2.12 秒，并可轻松容纳 128k 上下文。另有评论者称其在 SWE-bench Verified 上得分与 Opus 4.6 相当，但该说法被质疑可能混合了基准追逐、基准漂移和小模型进步。还有用户用自建长程任务基准测得 5/8 通过、296 步、76 分钟，较 Bonsai2 的 5/8、358 步、107 分钟有所改善。

hackernews · b0m · 11月24日 20:08 · [社区讨论](https://news.ycombinator.com/item?id=50633922)

**「背景」** 三值量化把模型权重压缩到三个离散取值，目标是在明显降低模型体积和内存需求的同时维持可用的推理质量；GGUF 则是本地推理工具常用的模型文件格式。对 27B 级模型而言，这类量化是让模型能在消费级设备上运行的关键前提，因此本地吞吐和长上下文开销会成为评估重点。

**「对本地开发者的影响」** 对开发者而言，最直接的后果是：一个 27B 级别的模型可以在约 5.9 GB 的三元权重占用下本地运行，并保留 262K token 上下文与厂商所称的「FP16 级」工具调用能力，从而使消费级硬件上的本地 agent 工作流更具可行性（\[tool-2-1\], \[tool-2-3\]）。社区用户报告，在 24 GB 内存的 Mac Mini 上生成速度约为 22–25 tok/s，并且内存可轻松容纳 128k 上下文；不过这些是个人实测，并非独立基准测试。

**「社区讨论」** 评论的主要分歧在于基准可信度：有人追问它与 Qwen3.8 等 1B–10B 级模型或同尺寸 Q1/Q2 量化版的直接对比，并怀疑 SWE-bench 成绩可能来自“benchmaxxing”或基准漂移。也有用户提供了自建长程任务基准的前后代对比，认为任务完成时间明显缩短。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://prismml.com/news/bonsai-2-5-27b">PrismML — Introducing Ternary Bonsai 2.5 27B: Powering ...</a></li>
<li><a href="https://docs.prismml.com/models/bonsai-2-5-27b">Ternary Bonsai 2.5 27B - Bonsai - docs.prismml.com</a></li>

</ul>
</details>

**标签**: `#ternary-quantization`, `#local-inference`, `#27b-model`, `#gguf`, `#swe-bench`

---

## 开源 / 开发工具

<a id="item-devtools-news-1"></a>
### [GitHub.com 通知订阅规则将于 12 月 1 日调整](https://github.blog/changelog/2026-11-24-more-predictable-notifications-on-github-com) ⭐️ 7.0/10

GitHub.com 将从 2026 年 12 月 1 日起用约一周时间逐步迁移通知订阅行为，目标是让订阅更可预测、纠正意外重新订阅并支持活动规模增长；此次变更不适用于 GitHub Enterprise Server，用户无需采取操作。迁移后，手动取消订阅不会再因评论、提交拉取请求评审、更改线程状态或合并队列活动而自动恢复，只有被提及、被指派或收到评审请求才会重新订阅。团队提及通知将依据当前团队成员关系，Subscriptions 页面只列出手动订阅，通知原因改为按固定优先级显示，邮件头则会包含所有适用原因。逐步推出期间，不同用户可能看到不同行为。

rss · GitHub Changelog · 11月24日 16:40

**「背景」** 此前，GitHub.com 用户在手动取消订阅后，评论、提交拉取请求审查、更改线程状态或合并队列活动仍会使其重新订阅；团队提及通知也可能因成员变动而不再反映当前团队关系。此次调整旨在纠正这些不符合预期的行为，使订阅页面和通知原因更可预测，并支持不断增长的活动规模。

**「影响」** 依赖通知原因过滤或自动化的用户应在迁移前审查规则：原因可能因优先级而改变，邮件头将同时包含多个原因；需要批量退订评论、指派或提及产生的通知时，也应改用通知收件箱，而不是仅显示手动订阅的 Subscriptions 页面。

**标签**: `#github`, `#notifications`, `#developer-workflow`, `#platform-changelog`, `#subscriptions`

---

<a id="item-devtools-news-2"></a>
### [uv 0.13.10 发布：修复安全公告并强化 uv.lock 校验](https://github.com/astral-sh/uv/releases/tag/0.13.10) ⭐️ 6.0/10

uv 0.13.10 于 2026 年 11 月 24 日发布，是一个针对 GHSA-vjvj-3m3f-fgmm 安全公告的维护版本。该版本会校验 uv.lock 中的依赖要求是否与锁定版本一致，在 --locked 拒绝锁文件时解释原因，并报告 uv.lock 中缺失的依赖包条目。它还更新了受管理的 CPython 3.11.18、3.12.16、3.13.18、3.14.10、3.15.2、3.16.0a2 以及 GraalPy 3.13.0 构建，并包含代理索引预览功能和若干缺陷修复。发布说明未详述该安全公告的严重性和实际影响。

github · astral-releases-bot\[bot\] · 11月24日 21:15

**「背景」** uv 0.13.10 在发布说明中仅写明修复安全公告 GHSA-vjvj-3m3f-fgmm，未披露严重程度或实际影响范围；同一版本还收紧了 \`uv.lock\` 的一致性校验，并在 \`--locked\` 拒绝锁文件时补充更新原因。uv 此前曾就 ZIP 载荷混淆与解析器差异发布安全公告，给出“中等”严重性建议，而本次更新也包含拒绝 ZIP 数据描述符与中央目录所记压缩大小不一致的 wheel 的修复。

**「影响」** 现有项目升级后可获得更严格的锁文件一致性检查和更清晰的 --locked 失败诊断；在 CI 中依赖 --locked 的团队应预期，此前被忽略的版本不匹配或缺失包条目可能开始显式报错。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://astral.sh/blog/uv-security-advisory-cve-2025-54368">uv security advisory: ZIP payload obfuscation</a></li>

</ul>
</details>

**标签**: `#uv`, `#python`, `#package-management`, `#lockfile`, `#security`

---