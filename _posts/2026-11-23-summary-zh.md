---
layout: default
title: "Horizon Summary: 2026-11-23 (ZH)"
date: 2026-11-23
lang: zh
---

> 从 34 条内容中筛选出 1 条重要资讯。

---

**AI**
1. [OpenAI 探讨困惑度与模型智能的关系](#item-ai-news-1) ⭐️ 7.0/10

---

## AI

<a id="item-ai-news-1"></a>
### [OpenAI 探讨困惑度与模型智能的关系](https://openai.com/index/perplexity-and-intelligence/) ⭐️ 7.0/10

OpenAI 发布文章《Perplexity and Intelligence》，讨论作为下一词预测指标的困惑度能否反映模型智能，并延伸到交叉熵损失、基准测试和推理模型。现有材料未包含文章正文，因此无法核实其具体数据、方法和结论，只能确认文章主题及 Hacker News 上的讨论。社区评论补充了困惑度的定义和取值范围，并围绕该指标与模型能力的关系展开争论。

hackernews · acossta · 11月22日 17:06 · [社区讨论](https://news.ycombinator.com/item?id=50601525)

**「背景」** 困惑度（perplexity）衡量语言模型在给定上下文下预测下一个 token 时的平均“惊讶程度”，数值越低表示预测越确定；它可由交叉熵损失取指数得到，因此在比较模型时二者等价。OpenAI 首席科学家 Jakub Pachocki 在 2026 年 11 月 22 日的文章中主张，把在固定留出集上测得的预训练交叉熵或对数困惑度作为跨实验室比较模型进展、并服务于共同安全标准的指标。

**「影响」** 据外部报道，OpenAI 首席科学家 Jakub Pachocki 公开了内部 log-perplexity 曲线，并呼吁前沿实验室采用固定留出集上的交叉熵损失作为共同指标，以比较预训练进展并协调安全节奏。若这一倡议被跟进，研究者和实验室将获得一个比现有基准更简单、可跨模型比较的进度指标；但目前它仍是倡议和单家披露，尚非行业标准。

**「社区讨论」** 有评论者认为，在强化学习使用日益增多之后，交叉熵损失仍与模型能力呈现清晰趋势令人意外，并称这种简单基准比不断增多的复杂评测更有价值；另一评论者则从“预测即压缩”的角度论证这种对应关系并不意外。也有人指出，文章本身没有定义困惑度。

<details><summary>参考链接</summary>
<ul>
<li><a href="https://www.explainx.ai/blog/openai-pachocki-perplexity-intelligence-pacing-safety-november-2026">OpenAI Perplexity Metric: GPT Log-Loss Curve (Nov 2026 ...</a></li>
<li><a href="https://community.openai.com/t/perplexity-and-intelligence/1419510">Perplexity and Intelligence - Community - OpenAI Developer ...</a></li>
<li><a href="https://blockchain.news/news/openai-perplexity-metric-ai-progress">OpenAI Advocates Perplexity as Key Metric for AI Progress and ...</a></li>
<li><a href="https://www.explainx.ai/blog/openai-pachocki-perplexity-intelligence-pacing-safety-november-2026">OpenAI Perplexity Metric: GPT Log-Loss Curve (Nov 2026 ...</a></li>

</ul>
</details>

**标签**: `#perplexity`, `#language-model-evaluation`, `#cross-entropy`, `#OpenAI`, `#benchmarks`

---