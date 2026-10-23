# fire-your-seo-agency-tw

**English** · [繁體中文](./README.zh-TW.md) · [简体中文](./README.zh-CN.md) · [日本語](./README.ja.md) · [한국어](./README.ko.md) · [Español](./README.es.md)

> Taiwan-localized fork of [leopard627/fire-your-seo-agency](https://github.com/leopard627/fire-your-seo-agency) (MIT). Traditional Chinese (Taiwan) is the canonical language; the Naver lane is replaced by a TW lane.

[![GitHub stars](https://img.shields.io/github/stars/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/fork)
[![Latest release](https://img.shields.io/github/v/release/lunkerchen/fire-your-seo-agency-tw?style=flat&label=release)](https://github.com/lunkerchen/fire-your-seo-agency-tw/releases/latest)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat)](./LICENSE)

![fire-your-seo-agency-tw](./assets/social-preview.png)

> **Paying an agency tens of thousands of NT dollars a month for SEO or "AI visibility"? Fire them. Your AI agent can do the work.**

A wave of services now charges monthly retainers for "AI-era search optimization",
"guaranteed ChatGPT citations", and "LLM visibility". Most of what they actually do is
**public standards and repeatable checklists**. When a human does it, it's a retainer.
When your agent does it, it's a skill.

This repository is a [Claude Code](https://claude.com/claude-code) skill. Install it and
your agent audits your site, fixes what's broken, and measures the results.

## Built on real numbers

These numbers come from the upstream author, not from this fork. The same playbook, applied to [Chickenstock](https://www.chickstockfi.com) — a solo-built Korean stock research service:

- **1.54M search impressions in 30 days** (+85,578% MoM), 7.4K clicks
- Pages **cited paragraph-by-paragraph by Naver's AI Briefing** (Korea's answer engine)
- Zero ad spend — all inbound from search and AI citations

The upstream author documents the journey publicly on [Threads @kindainvestor](https://www.threads.com/@kindainvestor).
This fork has not published its own case numbers yet.

## The five lanes

"Search optimization" means different things to different engines. This skill treats them
as five distinct lanes:

| Lane | Target | The question it answers |
|---|---|---|
| **SEO** | Google & Bing crawlers | Can crawlers read and index my content at all? |
| **AEO** (Answer Engine) | Google AI Overviews, Bing Copilot | Does the AI answer box above the results cite me? |
| **GEO** (Generative Engine) | ChatGPT, Perplexity, Claude | When generative AI browses, am I the primary source? |
| **LLMO** (LLM Optimization) | The model's own knowledge | Does the model know my brand — and know it correctly? |
| **TW** (Taiwan local) | Google, Bing / Yahoo 奇摩, Google Business Profile, Dcard / PTT / Mobile01 | Do the Taiwan engines, local signals and community surfaces find and cite me? |

**TW is what makes this fork different.** Global AEO guides assume an English-language
web. In Taiwan, Google leads but is not alone: StatCounter (2026-09) shows Google at
79.48%, Yahoo at 11.37% and Bing at 8.24%. Yahoo 奇摩 results are powered by Bing, so
Bing Webmaster Tools matters more here than in most markets. The TW lane also covers
`zh-Hant-TW` language signals, Google Business Profile for local businesses, and the
community surfaces AI answers may cite (verify by recorded checks): Dcard, PTT and Mobile01.

**Plus a content engine.** Most of a retainer pays for "N posts a month". This skill
replaces that with a pipeline: a question backlog pulled from your own search data, a
frontmatter content model that generates the JSON-LD, a publish gate every post must pass,
and a refresh/merge policy so posts don't rot. Output is measured as "the share of posts that get seen
and cited", not "posts published".

## Install

As a plugin (recommended — one command, easy updates):

```
/plugin marketplace add lunkerchen/fire-your-seo-agency-tw
/plugin install fire-your-seo-agency-tw@fire-your-seo-agency-tw
```

Or via git clone:

```bash
# As a project skill (this project only)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git .claude/skills/fire-your-seo-agency-tw

# Or as a personal skill (every project)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git ~/.claude/skills/fire-your-seo-agency-tw
```

Then in Claude Code:

```
/fire-your-seo-agency-tw audit my site
```

Your agent starts with a crawler-eye audit and returns a scorecard like this before
touching anything:

| Lane | Status | Evidence |
|---|---|---|
| SEO | WARN | Body is SSR'd, but 214 detail pages missing from sitemap |
| AEO | FAIL | No direct-answer first paragraphs; FAQ structured data: 0 |
| GEO | FAIL | No llms.txt; GPTBot/PerplexityBot policy undecided in robots.txt |
| LLMO | WARN | Brand name spelled 3 different ways across surfaces |
| TW | FAIL | Not verified in Bing Webmaster Tools; html lang is zh-CN |

…then proposes priorities, implements them, and schedules the re-measurement.

## What it does

1. **Audit** — reads your site the way a crawler does (no JavaScript) and scores all five lanes
2. **Technical base** — fixes SSR exposure, sitemaps, meta, structured data
3. **Intent landing pages** — designs pages on the "one question = one page" principle
4. **Machine readability** — llms.txt, JSON-LD, citation-ready paragraph structure
5. **Taiwan local** — Bing Webmaster Tools and Yahoo 奇摩, zh-Hant-TW signals, Google Business Profile, Dcard / PTT / Mobile01 citation surfaces
6. **Content engine** — sub-blog setup, question backlog, publish gate, refresh & merge policy
7. **Measurement loop** — schedules a re-measurement and proves the change with numbers

## What it refuses to do

- Buying backlinks, engagement pods, content spam — **we don't fight the search engine**
- "Guaranteed rankings" promises — no claims without measurement
- Keyword stuffing, hidden text, cloaking — nothing that gets your domain killed

The whole philosophy fits in one line: **AI doesn't cite good writing. AI cites accurate data.**
Become the primary source for a number, and the citations follow.

## Structure

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

> The Traditional Chinese documents under `references/` are canonical (the agent reads those);
> `references/en/` mirrors them in English for human readers.

## Repository checks

This repo checks itself — `.github/workflows/validate.yml` runs all of it on every push
and pull request:

```bash
python3 tools/validate.py --strict          # 10 checks, standard library only
python3 -m unittest discover -s tests -t .  # unit tests for every check
python3 -m pip install pillow
python3 tools/optimize_assets.py --check    # flags recompressible assets
```

`tools/validate.py` enforces the things that rot silently in a docs-only repo: the
`SKILL.md` frontmatter contract (kebab-case name, 64-character name limit, 1024-character
single-line description), `plugin.json` ↔ `marketplace.json` version and name agreement,
`CHANGELOG.md` matching the manifest version, relative links and anchors, Traditional
Chinese/English reference parity (heading counts, table rows, checkboxes, section
numbering), the asset budget and preview dimensions, the MIT license metadata, and a
secret scan over every text file.

## Star History

<a href="https://www.star-history.com/#lunkerchen/fire-your-seo-agency-tw&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
  </picture>
</a>

## License

MIT — use it freely, and keep the retainer money. Original work copyright leopard627;
Taiwan localization copyright lunkerchen.
