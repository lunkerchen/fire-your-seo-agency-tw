# fire-your-seo-agency-tw

[English](./README.md) · [繁體中文](./README.zh-TW.md) · **简体中文** · [日本語](./README.ja.md) · [한국어](./README.ko.md) · [Español](./README.es.md)

> [leopard627/fire-your-seo-agency](https://github.com/leopard627/fire-your-seo-agency)（MIT）的台湾本地化分支。本技能面向台湾市场：以繁体中文（台湾）为准，并将 Naver 通道替换为 TW 通道。

[![GitHub stars](https://img.shields.io/github/stars/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/fork)
[![Latest release](https://img.shields.io/github/v/release/lunkerchen/fire-your-seo-agency-tw?style=flat&label=release)](https://github.com/lunkerchen/fire-your-seo-agency-tw/releases/latest)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat)](./LICENSE)

![fire-your-seo-agency-tw](./assets/social-preview.png)

> **每月给代理商付几万新台币做 SEO 或"AI 可见度"？炒掉他们。你的 AI 代理可以把这些活干完。**

现在有一波服务，按月收取服务费，卖的是"AI 时代的搜索优化""保证被 ChatGPT 引用"和"LLM 可见度"。
它们实际做的事，大多是**公开的标准和可重复的检查清单**。由人来做，就是服务费；
由你的 AI 代理来做，就是一个技能。

本仓库是一个 [Claude Code](https://claude.com/claude-code) 技能。安装之后，
你的 AI 代理会审计网站、修复问题，并衡量成效。

## 建立在真实数字之上

以下数字来自上游作者，并非本分支。同一套方法，应用在 [Chickenstock](https://www.chickstockfi.com) 上——一个由个人独立开发的韩国股票研究服务：

- **30 天内 154 万次搜索曝光**（环比 +85,578%），7.4K 次点击
- 页面被 **Naver AI Briefing（韩国的答案引擎）逐段引用**
- 零广告支出——所有流量均来自搜索和 AI 引用

上游作者在 [Threads @kindainvestor](https://www.threads.com/@kindainvestor) 上公开记录了整个过程。
本分支尚未发布自己的案例数字。

## 五条通道

"搜索优化"对不同的引擎意味着不同的事。本技能将其视为五条彼此独立的通道：

| 通道 | 目标 | 它回答的问题 |
|---|---|---|
| **SEO** | Google 和 Bing 的爬虫 | 爬虫到底能不能读取并收录我的内容？ |
| **AEO**（答案引擎） | Google AI 概览、Bing Copilot | 搜索结果上方的 AI 答案框会引用我吗？ |
| **GEO**（生成式引擎） | ChatGPT、Perplexity、Claude | 生成式 AI 联网浏览时，我是一手来源吗？ |
| **LLMO**（LLM 优化） | 模型自身的知识 | 模型认识我的品牌吗，而且认识得对吗？ |
| **TW**（台湾本地） | Google、Bing / Yahoo 奇摩、Google 商家资料（Google Business Profile）、Dcard / PTT / Mobile01 | 台湾的搜索引擎、本地信号和社区平台，能找到并引用我吗？ |

**TW 通道是本分支的不同之处。** 全球通行的 AEO 指南默认以英文网络为前提。
在台湾，Google 领先但并非一家独大：StatCounter（2026-09）显示 Google 为 79.48%、
Yahoo 为 11.37%、Bing 为 8.24%。Yahoo 奇摩的搜索结果由 Bing 提供，
因此 Bing Webmaster Tools 在这里比在大多数市场更重要。TW 通道还涵盖
`zh-Hant-TW` 语言信号、面向本地商家的 Google 商家资料，以及 AI 回答可能引用的
社区平台（需通过留档的检查来验证）：Dcard、PTT 和 Mobile01。

**另外还有内容引擎。** 服务费的大头通常花在"每月 N 篇文章"上。本技能用一条流水线取而代之：
基于你自己的搜索数据整理出的问题待办清单、能生成 JSON-LD 的 frontmatter 内容模型、
每篇文章都必须通过的发布前检查，以及避免文章过时的更新与合并策略。产出的衡量标准是
"被看到并被引用的文章占比"，而不是"发布了多少篇"。

## 安装

作为插件安装（推荐——一条命令，更新方便）：

```
/plugin marketplace add lunkerchen/fire-your-seo-agency-tw
/plugin install fire-your-seo-agency-tw@fire-your-seo-agency-tw
```

或通过 git clone：

```bash
# As a project skill (this project only)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git .claude/skills/fire-your-seo-agency-tw

# Or as a personal skill (every project)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git ~/.claude/skills/fire-your-seo-agency-tw
```

然后在 Claude Code 中：

```
/fire-your-seo-agency-tw audit my site
```

你的 AI 代理会先以爬虫的视角做一次审计，并在动手修改任何内容之前，返回类似下面的评分表：

| 通道 | 状态 | 依据 |
|---|---|---|
| SEO | WARN | 正文已做服务端渲染（SSR），但 214 个详情页未列入站点地图 |
| AEO | FAIL | 没有直接回答问题的首段；FAQ 结构化数据：0 |
| GEO | FAIL | 没有 llms.txt；robots.txt 中尚未决定 GPTBot/PerplexityBot 的策略 |
| LLMO | WARN | 品牌名称在各个平台上有 3 种不同写法 |
| TW | FAIL | 未在 Bing Webmaster Tools 中验证；html lang 为 zh-CN |

……接着提出优先级建议、动手实施，并安排重新测量。

## 它能做什么

1. **审计**——以爬虫的方式（不执行 JavaScript）读取你的网站，并为五条通道打分
2. **技术基础**——修复 SSR 暴露、站点地图、meta、结构化数据
3. **意图落地页**——按"一个问题 = 一个页面"的原则设计页面
4. **机器可读性**——llms.txt、JSON-LD、便于引用的段落结构
5. **台湾本地**——Bing Webmaster Tools 与 Yahoo 奇摩、zh-Hant-TW 信号、Google 商家资料、Dcard / PTT / Mobile01 引用渠道
6. **内容引擎**——子博客搭建、问题待办清单、发布前检查、更新与合并策略
7. **衡量闭环**——安排重新测量，并用数字证明改动的效果

## 它拒绝做的事

- 购买外链、互刷互动群、内容垃圾——**我们不与搜索引擎对抗**
- "保证排名"的承诺——没有测量数据，就不做任何声明
- 关键词堆砌、隐藏文字、伪装（cloaking）——任何会让你的域名被处罚的做法

整套理念可以浓缩成一句话：**AI 不会引用写得好的文章，AI 引用的是准确的数据。**
成为某个数字的一手来源，引用自然会随之而来。

## 目录结构

```
SKILL.md              ← agent operating procedure (audit → implement → measure)
references/
  seo.md              ← technical SEO checklist + real-world traps
  aeo.md              ← answer engine optimization (Bing WMT · AI Overviews · Copilot · E-E-A-T)
  geo.md              ← generative engine optimization (AI crawler policy · llms.txt · primary source)
  llmo.md             ← model-knowledge optimization (brand entity)
  tw-local.md         ← Taiwan local (Bing/Yahoo 奇摩 · zh-Hant-TW · Google Business Profile · Dcard/PTT/Mobile01)
  content.md          ← content ops (sub-blog · content model · backlog · publish gate · refresh)
  measure.md          ← the measurement loop (fixing it is not the finish line)
  en/                 ← English mirrors of all reference docs (for human readers)
.claude-plugin/       ← plugin & marketplace manifests (/plugin install support)
tools/                ← repository checks (validate.py) + lossless asset optimizer
tests/                ← unit tests for the checks
.github/workflows/    ← CI: checks, tests and the asset check on every push/PR
```

> `references/` 下的繁体中文文档是权威版本（代理读取的是这些文档）；
> `references/en/` 是其英文镜像，供人类读者阅读。

## 仓库检查

本仓库会自我检查——`.github/workflows/validate.yml` 在每次 push 和 pull request 时运行全部检查：

```bash
python3 tools/validate.py --strict          # 10 checks, standard library only
python3 -m unittest discover -s tests -t .  # unit tests for every check
python3 -m pip install pillow
python3 tools/optimize_assets.py --check    # flags recompressible assets
```

`tools/validate.py` 负责把守纯文档仓库里容易悄悄腐烂的内容：`SKILL.md` 的 frontmatter 约定
（kebab-case 名称、名称不超过 64 个字符、description 为不超过 1024 个字符的单行文本）、
`plugin.json` 与 `marketplace.json` 的版本和名称一致、`CHANGELOG.md` 与清单版本一致、
相对链接与锚点、繁体中文与英文参考文档的对等性（标题数量、表格行数、复选框、章节编号）、
资源体积预算与预览图尺寸、MIT 许可证元数据，以及对所有文本文件的密钥扫描。

## Star History

<a href="https://www.star-history.com/#lunkerchen/fire-your-seo-agency-tw&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
  </picture>
</a>

## 许可证

MIT——随意使用，把服务费省下来。原始作品版权归 leopard627 所有；
台湾本地化部分版权归 lunkerchen 所有。
