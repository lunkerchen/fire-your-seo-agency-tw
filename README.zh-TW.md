# fire-your-seo-agency-tw

**繁體中文** · [English](./README.md)

> 這是 [leopard627/fire-your-seo-agency](https://github.com/leopard627/fire-your-seo-agency)（MIT）的台灣在地化 fork。以台灣繁體中文為正本，並將 Naver 通道換成 TW 在地通道。

[![GitHub stars](https://img.shields.io/github/stars/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/fork)
[![Latest release](https://img.shields.io/github/v/release/lunkerchen/fire-your-seo-agency-tw?style=flat&label=release)](https://github.com/lunkerchen/fire-your-seo-agency-tw/releases/latest)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat)](./LICENSE)

![fire-your-seo-agency-tw](./assets/social-preview.png)

> **每月花數萬元請人代操 SEO、AEO？把他們換掉吧。你的 AI agent 可以自己做。**

「AI 時代搜尋優化」「保證 ChatGPT 引用」「LLM 能見度」——打著這類名號按月收費的代操服務越來越多。
但他們做的事，大部分是**公開的標準文件與可重複的檢查清單**。
人來做，是委外服務；AI agent 來做，就是一個 skill。

這個儲存庫是一個 [Claude Code](https://claude.com/claude-code) skill。安裝之後，你的 agent 會
替網站做診斷、直接修掉該修的問題，並量測成果。

## 實際數字

以下數字來自上游作者，不是這個 fork 的成果。同一套作法用在 [Chickenstock](https://www.chickstockfi.com)（一人開發的韓國股票研究服務）上：

- 30 天搜尋曝光 **154 萬次**（月增 +85,578%），點擊 7.4 千次
- 頁面被 **Naver AI 簡報逐段引用**（韓國的答案引擎）
- 廣告費為零——流量全部來自搜尋與 AI 引用

上游作者在 [Threads @kindainvestor](https://www.threads.com/@kindainvestor) 公開記錄整個過程。
這個 fork 目前還沒有自己的案例數字。

## 五條通道

同樣叫「搜尋優化」，面對的引擎卻不同。這個 skill 把它拆成五條通道，各自優化。

| 通道 | 對象 | 核心問題 |
|---|---|---|
| **SEO** | Google、Bing 爬蟲 | 爬蟲能不能讀到並收錄我的內容？ |
| **AEO**（Answer Engine） | Google AI 摘要、Bing Copilot | 搜尋結果上方的 AI 答案有沒有引用我？ |
| **GEO**（Generative Engine） | ChatGPT、Perplexity、Claude | 生成式 AI 瀏覽網頁時，我是不是第一手來源？ |
| **LLMO**（LLM Optimization） | 模型本身的知識 | 模型認得我的品牌嗎？認得對嗎？ |
| **TW**（台灣在地） | Google、Bing／Yahoo 奇摩、Google 商家檔案、Dcard／PTT／Mobile01 | 台灣的搜尋引擎、在地訊號與社群平台，找得到我、引用我嗎？ |

**TW 是這個 fork 的差異點。** 國際的 AEO 指南預設的是英文網路。台灣雖然以 Google 為主，
但不是只有 Google：StatCounter（2026-09）顯示 Google 79.48%、Yahoo 11.37%、Bing 8.24%。
Yahoo 奇摩的搜尋結果由 Bing 提供，所以 Bing Webmaster Tools 在台灣比在多數市場更重要。
TW 通道還涵蓋 `zh-Hant-TW` 語言訊號、在地店家的 Google 商家檔案，
以及 AI 答案可能引用的社群平台：Dcard、PTT、Mobile01（以實測紀錄為準）。

**另外還有內容引擎。** 代操費用大多買的是「每月 N 篇文章」。這個 skill 改用一條流程取代：
從你自己的搜尋資料產生問題清單（backlog）、用 frontmatter 內容模型自動產生 JSON-LD、
每篇文章都要過的發布關卡，以及避免文章過期的更新與合併政策。
成果的衡量標準是「被看見、被引用的文章比例」，不是「發了幾篇」。

## 安裝

用外掛安裝（推薦，一行指令、更新方便）：

```
/plugin marketplace add lunkerchen/fire-your-seo-agency-tw
/plugin install fire-your-seo-agency-tw@fire-your-seo-agency-tw
```

或用 git clone：

```bash
# 安裝成專案 skill（只用在這個專案）
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git .claude/skills/fire-your-seo-agency-tw

# 或安裝成個人 skill（所有專案共用）
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git ~/.claude/skills/fire-your-seo-agency-tw
```

接著在 Claude Code 輸入：

```
/fire-your-seo-agency-tw audit my site
```

agent 會先用爬蟲視角做診斷，在動手修改之前先交出像這樣的評分表：

| 通道 | 狀態 | 證據 |
|---|---|---|
| SEO | 注意 | 內文有伺服器端渲染（SSR），但 214 個詳情頁沒進 sitemap |
| AEO | 未通過 | 首段沒有直接回答；FAQ 結構化資料：0 |
| GEO | 未通過 | 沒有 llms.txt；robots.txt 尚未決定 GPTBot／PerplexityBot 政策 |
| LLMO | 注意 | 品牌名稱在各平台有 3 種不同寫法 |
| TW | 未通過 | 尚未在 Bing Webmaster Tools 驗證；html lang 是 zh-CN |

……接著提出優先順序、實際動手修改，並排定重新量測的時間。

## 它做什麼

1. **診斷**：用爬蟲的方式（不執行 JavaScript）讀你的網站，替五條通道打分
2. **技術基礎**：修正 SSR 曝光、sitemap、meta、結構化資料
3. **意圖著陸頁**：依「一個問題 = 一個頁面」的原則設計頁面
4. **機器可讀性**：llms.txt、JSON-LD、適合被引用的段落結構
5. **台灣在地**：Bing Webmaster Tools 與 Yahoo 奇摩、zh-Hant-TW 訊號、Google 商家檔案、Dcard／PTT／Mobile01 引用來源
6. **內容引擎**：子部落格設定、問題清單、發布關卡、更新與合併政策
7. **量測循環**：排定重新量測，用數字證明改動有效

## 它拒絕做的事

- 買外部連結、互刷互動社團、內容垃圾——**不跟搜尋引擎對著幹**
- 「保證排名」的承諾——沒有量測就不下結論
- 關鍵字堆砌、隱藏文字、cloaking——任何會讓網域被處罰的做法

整套理念一句話：**AI 不引用寫得漂亮的文章，AI 引用正確的資料。**
成為某個數字的第一手來源，引用自然會來。

## 目錄結構

```
SKILL.md              ← agent 操作程序（診斷 → 實作 → 量測）
references/
  seo.md              ← 技術 SEO 檢查清單與實戰陷阱
  aeo.md              ← 答案引擎優化（Bing WMT · AI 摘要 · Copilot · E-E-A-T）
  geo.md              ← 生成式引擎優化（AI 爬蟲政策 · llms.txt · 第一手來源）
  llmo.md             ← 模型知識優化（品牌實體）
  tw-local.md         ← 台灣在地（Bing／Yahoo 奇摩 · zh-Hant-TW · Google 商家檔案 · Dcard／PTT／Mobile01）
  content.md          ← 內容營運（子部落格 · 內容模型 · 問題清單 · 發布關卡 · 更新）
  measure.md          ← 量測循環（修好不是終點）
  en/                 ← 所有參考文件的英文鏡像（給人類讀者）
.claude-plugin/       ← 外掛與 marketplace 清單（支援 /plugin install）
tools/                ← 儲存庫檢查（validate.py）與無損圖檔最佳化工具
tests/                ← 檢查工具的單元測試
.github/workflows/    ← CI：每次 push／PR 都跑檢查、測試與圖檔檢查
```

> `references/` 底下的繁體中文文件是正本（agent 讀的是這些）；
> `references/en/` 是給人類讀者的英文鏡像。

## 儲存庫檢查

這個儲存庫會自己檢查自己——`.github/workflows/validate.yml` 在每次 push 與 pull request 都會全部跑一遍：

```bash
python3 tools/validate.py --strict          # 10 項檢查，只用標準函式庫
python3 -m unittest discover -s tests -t .  # 每項檢查的單元測試
python3 -m pip install pillow
python3 tools/optimize_assets.py --check    # 標出可再壓縮的圖檔
```

`tools/validate.py` 檢查純文件儲存庫最容易悄悄壞掉的地方：`SKILL.md` frontmatter 規範
（kebab-case 名稱、名稱 64 字元上限、description 單行 1024 字元上限）、`plugin.json` 與
`marketplace.json` 的版本和名稱一致、`CHANGELOG.md` 與清單版本相符、相對連結與錨點、
繁體中文與英文參考文件的對應（標題數、表格列、checkbox、章節編號）、圖檔體積預算與預覽圖尺寸、
MIT 授權中繼資料，以及對所有文字檔做的密鑰掃描。

## Star History

<a href="https://www.star-history.com/#lunkerchen/fire-your-seo-agency-tw&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
  </picture>
</a>

## 授權

MIT——自由使用，把代操費用留給自己。原始作品著作權屬 leopard627，台灣在地化部分著作權屬 lunkerchen。
