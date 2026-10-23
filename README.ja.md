# fire-your-seo-agency-tw

[English](./README.md) · [繁體中文](./README.zh-TW.md) · [简体中文](./README.zh-CN.md) · **日本語** · [한국어](./README.ko.md) · [Español](./README.es.md)

> [leopard627/fire-your-seo-agency](https://github.com/leopard627/fire-your-seo-agency)（MIT）の台湾向けローカライズ fork です。台湾の繁体字中国語を正本とし、Naver レーンを TW レーンに置き換えています。このスキルの対象は台湾市場です。

[![GitHub stars](https://img.shields.io/github/stars/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/fork)
[![Latest release](https://img.shields.io/github/v/release/lunkerchen/fire-your-seo-agency-tw?style=flat&label=release)](https://github.com/lunkerchen/fire-your-seo-agency-tw/releases/latest)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat)](./LICENSE)

![fire-your-seo-agency-tw](./assets/social-preview.png)

> **SEO や「AI 可視性」のために、毎月数万台湾ドルを代理店に払っていませんか？ 契約を切ってください。その仕事は AI エージェントができます。**

最近は、「AI 時代の検索最適化」「ChatGPT に引用されることの保証」「LLM 可視性」といった名目で
月額リテナー料金を取るサービスが増えています。その実際の作業の大半は
**公開された標準と、繰り返し実行できるチェックリスト**です。人がやればリテナー契約になり、
あなたのエージェントがやればスキルになります。

このリポジトリは [Claude Code](https://claude.com/claude-code) のスキルです。インストールすると、
エージェントがサイトを監査し、問題を修正し、結果を測定します。

## 実績に基づく数字

以下の数字は上流の作者によるもので、この fork のものではありません。同じ手法を [Chickenstock](https://www.chickstockfi.com)（個人開発の韓国株リサーチサービス）に適用した結果です。

- **30 日間で検索表示回数 154 万回**（前月比 +85,578%）、クリック 7.4K
- ページが **Naver の AI Briefing（韓国のアンサーエンジン）に段落単位で引用された**
- 広告費ゼロ。流入はすべて検索と AI からの引用

上流の作者は、その過程を [Threads @kindainvestor](https://www.threads.com/@kindainvestor) で公開しています。
この fork は、まだ独自の事例の数字を公開していません。

## 5 つのレーン

「検索最適化」の意味は、エンジンごとに異なります。このスキルは、それを
5 つの別々のレーンとして扱います。

| レーン | 対象 | 答える問い |
|---|---|---|
| **SEO** | Google と Bing のクローラー | クローラーは私のコンテンツを読み取り、インデックスできるか。 |
| **AEO**（Answer Engine） | Google AI Overviews、Bing Copilot | 検索結果の上にある AI 回答ボックスは、私を引用しているか。 |
| **GEO**（Generative Engine） | ChatGPT、Perplexity、Claude | 生成 AI がウェブを閲覧するとき、私は一次情報源になっているか。 |
| **LLMO**（LLM Optimization） | モデル自身の知識 | モデルは私のブランドを知っているか。そして正しく知っているか。 |
| **TW**（台湾ローカル） | Google、Bing / Yahoo 奇摩、Google ビジネスプロフィール、Dcard / PTT / Mobile01 | 台湾のエンジン、ローカルシグナル、コミュニティ面は、私を見つけて引用しているか。 |

**この fork の違いは TW です。** 世界向けの AEO ガイドは、英語のウェブを前提にしています。
台湾では Google が首位ですが、単独ではありません。StatCounter（2026-09）によると、
Google は 79.48%、Yahoo は 11.37%、Bing は 8.24% です。Yahoo 奇摩の検索結果は Bing が
支えているため、Bing Webmaster Tools は多くの市場より重要です。TW レーンは、
`zh-Hant-TW` の言語シグナル、ローカルビジネス向けの Google ビジネスプロフィール、
そして AI の回答が引用しうるコミュニティ面（記録した確認で検証してください）である
Dcard、PTT、Mobile01 も扱います。

**さらに、コンテンツエンジンがあります。** リテナー料金の大半は「月 N 本の記事」に対して
払われています。このスキルはそれを、パイプラインに置き換えます。自社の検索データから作る
質問バックログ、JSON-LD を生成する frontmatter のコンテンツモデル、すべての記事が通過する
公開ゲート、そして記事を腐らせないための更新・統合ポリシーです。成果は「公開した本数」ではなく、
「見られて引用された記事の割合」で測ります。

## インストール

プラグインとして（推奨。コマンド 1 つで、更新も簡単です）:

```
/plugin marketplace add lunkerchen/fire-your-seo-agency-tw
/plugin install fire-your-seo-agency-tw@fire-your-seo-agency-tw
```

または git clone で:

```bash
# As a project skill (this project only)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git .claude/skills/fire-your-seo-agency-tw

# Or as a personal skill (every project)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git ~/.claude/skills/fire-your-seo-agency-tw
```

そのうえで Claude Code で次を実行します:

```
/fire-your-seo-agency-tw audit my site
```

エージェントはまずクローラーの視点で監査し、何かを変更する前に、次のようなスコアカードを返します。

| レーン | 状態 | 根拠 |
|---|---|---|
| SEO | WARN | 本文は SSR 済みだが、詳細ページ 214 件が sitemap にない |
| AEO | FAIL | 直接回答型の冒頭段落がない。FAQ 構造化データ: 0 |
| GEO | FAIL | llms.txt がない。robots.txt で GPTBot/PerplexityBot の方針が未決定 |
| LLMO | WARN | ブランド名の表記が、各面で 3 通りある |
| TW | FAIL | Bing Webmaster Tools でサイト所有権が未確認。html の lang が zh-CN |

…そのあと優先順位を提案し、実装し、再測定を予約します。

## できること

1. **監査** — クローラーと同じ方法（JavaScript なし）でサイトを読み、5 つのレーンすべてを採点します
2. **技術基盤** — SSR での露出、sitemap、meta、構造化データを修正します
3. **検索意図別ランディングページ** — 「1 つの質問 = 1 ページ」の原則でページを設計します
4. **機械可読性** — llms.txt、JSON-LD、引用しやすい段落構造
5. **台湾ローカル** — Bing Webmaster Tools と Yahoo 奇摩、zh-Hant-TW シグナル、Google ビジネスプロフィール、Dcard / PTT / Mobile01 の引用面
6. **コンテンツエンジン** — サブブログの構築、質問バックログ、公開ゲート、更新・統合ポリシー
7. **測定ループ** — 再測定を予約し、変化を数字で証明します

## やらないこと

- 被リンクの購入、エンゲージメントポッド、コンテンツスパム — **検索エンジンとは戦いません**
- 「順位保証」の約束 — 測定なしの主張はしません
- キーワードの詰め込み、隠しテキスト、クローキング — ドメインが潰れる手法は一切使いません

この方針は一行で言えます。**AI は、うまい文章を引用するのではありません。正確なデータを引用します。**
ある数字の一次情報源になれば、引用はあとからついてきます。

## 構成

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

> `references/` 配下の繁体字中国語ドキュメントが正本です（エージェントが読むのはこちらです）。
> `references/en/` は、人間の読者向けにそれを英語で写したものです。

## リポジトリのチェック

このリポジトリは自分自身を検査します。`.github/workflows/validate.yml` が、push と
pull request のたびにすべてを実行します。

```bash
python3 tools/validate.py --strict          # 10 checks, standard library only
python3 -m unittest discover -s tests -t .  # unit tests for every check
python3 -m pip install pillow
python3 tools/optimize_assets.py --check    # flags recompressible assets
```

`tools/validate.py` は、ドキュメント中心のリポジトリで気づかないうちに劣化しやすい項目を検査します。
`SKILL.md` の frontmatter 規約（kebab-case の name、name は 64 文字まで、description は
1024 文字までの単一行）、`plugin.json` と `marketplace.json` の version と name の一致、
`CHANGELOG.md` と manifest の version の一致、相対リンクとアンカー、繁体字中国語版と
英語版の reference の対応（見出し数、表の行数、チェックボックス、セクション番号）、
アセットの容量上限とプレビュー画像の寸法、MIT ライセンスのメタデータ、
そしてすべてのテキストファイルに対するシークレットスキャンです。

## Star History

<a href="https://www.star-history.com/#lunkerchen/fire-your-seo-agency-tw&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
  </picture>
</a>

## ライセンス

MIT — 自由に使って、リテナー料金は手元に残してください。原著作物の著作権は leopard627、
台湾ローカライズの著作権は lunkerchen に帰属します。
