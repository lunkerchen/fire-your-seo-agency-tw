# GEO — 生成引擎最佳化（ChatGPT・Perplexity・Claude）

讓生成式 AI 透過瀏覽、搜尋工具讀取網路時，**把你當作第一手來源引用**的主線。
它與答案引擎（AEO）有重疊，但生成引擎 ① 爬蟲政策不同 ② 會讀取 llms.txt
③ 更強烈地偏好「原始出處」。

## 1. llms.txt

在網站根目錄放 `/llms.txt` — 這是寫給 AI 的網站導覽。格式為 Markdown：

```markdown
# 服務名稱

> 一句話說明（寫清楚你是什麼的第一手來源）

## 核心頁面
- [財報行事曆](https://example.com/earnings): 台灣上市櫃公司的財報與法說會時程
- [個股資料](https://example.com/stocks): 以公開資訊為基礎的財務與評價資料

## 資料政策
- 出處：依公開資訊觀測站原文自行計算，每日更新
- 引用時請標示：example.com
```

- [ ] `/llms.txt`（導覽）＋ 有餘力的話再加 `/llms-full.txt`（核心資料全文）
- [ ] 放進信任訊號：資料出處、更新週期、哪些內容是你的原始出處
- [ ] 用應用程式路由提供也可以（不必是靜態檔案）— 要確保永遠是最新內容

## 2. 決定 AI 爬蟲政策

AI 爬蟲依**用途分成三種**，robots.txt 政策也要依用途分開撰寫。
預設不設政策，等於交給運氣：

| 用途 | 代表 User-agent | 擋掉會失去什麼 |
|---|---|---|
| **訓練**（蒐集模型訓練資料） | GPTBot, ClaudeBot, Google-Extended, CCBot, Applebot-Extended | 未來模型對品牌的認知（LLMO） |
| **搜尋索引**（AI 搜尋自己的索引） | OAI-SearchBot, Claude-SearchBot, PerplexityBot | ChatGPT、Claude、Perplexity 搜尋中的引用 |
| **即時抓取**（使用者提問時開啟頁面） | ChatGPT-User, Perplexity-User, Claude-User | 回答當下的直接引用與流量 |

```
# 若目標是獲得引用導流，全部 Allow 是預設值
User-agent: GPTBot
Allow: /
User-agent: OAI-SearchBot
Allow: /
User-agent: ChatGPT-User
Allow: /
User-agent: ClaudeBot
Allow: /
User-agent: Claude-SearchBot
Allow: /
User-agent: Claude-User
Allow: /
User-agent: PerplexityBot
Allow: /
User-agent: Perplexity-User
Allow: /
```

如果內容本身是資產，想**只擋訓練**，就只對第一列（訓練用）設 Disallow — 連搜尋、即時抓取
一起擋掉，引用導流本身就死了。名單會變動 — 每季確認各家的爬蟲文件。

- [ ] **確認 Bing 索引**：ChatGPT 搜尋除了自家爬蟲，也依賴 Bing 索引。
      若尚未註冊 Bing Webmaster Tools，請先做 `references/aeo.md` 的第 0 節。
      台灣的 Yahoo 奇摩搜尋結果同樣由 Bing 提供，詳見 `references/tw-local.md` 第 1 節

## 3. 成為第一手來源 — GEO 的本體

生成引擎會追查「這個數字是從哪裡開始的」。整理別人資料的頁面，
引用會被原始出處搶走。

- [ ] 定義哪些數字只有你在計算、蒐集（自行計算的指標、彙整、觀測）
- [ ] 替這個數字取名，並永遠由同一個頁面提供（穩定的 URL = 引用位址）
- [ ] 段落層級的可引用性：每一段都具備［主詞＋數字＋基準日＋計算方式］時，
      就會整段被引用 — 實測 Perplexity 正是以這個單位切取內容；其他 AI 搜尋是否相同，
      請以實際搜尋驗證

## 4. 驗證

- 向 Perplexity、ChatGPT（搜尋模式）、Gemini 提出實際問題，確認來源清單中是否出現你的網域；
  並在台灣的實際搜尋中確認 Google AI 摘要、AI 模式是否出現、是否引用你 — 不要預設這些功能一定可用
- 沒出現的話，依序檢查：llms.txt 是否存在 → 是否允許爬蟲 → 該頁面是否為 SSR → 是否有競爭的原始出處
