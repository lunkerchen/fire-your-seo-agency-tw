# TW 在地 — 台灣在地搜尋與引用

台灣以 Google 為主，但 Bing 生態約兩成，而繁中語言訊號、在地商家、論壇是海外指南不處理的部分。
本章是這個 skill 的在地化差異點。兩個目標：① 在 Google、Bing（含 Yahoo 奇摩）與地圖的在地能見度
② 讓 AI 回答台灣使用者時，引用你的自有網域。

## 1. 市佔與 Bing 生態

StatCounter 2026-09（所有平台）：Google 79.48%、Yahoo 11.37%、Bing 8.24%。
來源：https://gs.statcounter.com/search-engine-market-share/all/taiwan 。數字會因裝置檢視（桌機／手機）而異，引用前先重查。

Yahoo 奇摩搜尋結果由 Bing 提供，所以 Bing 索引等於兩個入口。Bing 索引同時餵給 Copilot，檢查 Bing 收錄是 AI 回答的低成本保險。

- [ ] 在 Bing Webmaster Tools 驗證網站（需要使用者帳號，由 agent 帶著走；可從 Google Search Console 匯入）
- [ ] 提交 sitemap
- [ ] 發布時送 IndexNow ping（金鑰檔放網站根目錄）；確認該檔回傳 200，且沒被 SPA 的 catch-all 路由吞掉
      （Astro／Next.js 的 `public/` 是常見陷阱）
- [ ] 驗證：同一個查詢分別在 Yahoo 奇摩與 Bing 搜尋，比對結果是否一致、自己的頁面是否出現

## 2. 繁中語言訊號

- [ ] `<html lang="zh-Hant-TW">`（或 zh-TW）全站一致
- [ ] 有其他語言或地區的對應版本（例如英文、zh-Hans、zh-HK）時，設定互相參照的 hreflang；不要放自動簡轉繁的重複頁
- [ ] 用台灣用語與全形標點；中國用語（視頻、質量、信息、軟件）會讓台灣讀者覺得內容不是寫給他們看的
- [ ] 台灣特有實體要寫明：統一編號、地址（含行政區）、電話 +886 格式、NT$ 價格並標示含稅／未稅

## 3. Google 商家檔案（有實體據點或服務區域時）

Google 公開的排名因素：相關性、距離、顯著性。

- [ ] NAP（名稱／地址／電話）在網站、商家檔案、LocalBusiness JSON-LD 三處完全一致
- [ ] 類別與服務只填實際提供的項目（濫填有停權風險）
- [ ] 評論用實質內容回覆；不買評論、不刷點擊
- [ ] 商家檔案需要店家本人的帳號，由 agent 帶著走；網站端由 agent 實作
      （LocalBusiness schema、NAP、嵌入地圖）

## 4. 論壇與社群引用面

Dcard、PTT、Mobile01（遊戲領域加巴哈姆特）的討論串，是台灣查詢中 Google 結果與 AI 回答可能引用的候選來源；是否真的被引用，以下面的實測紀錄為準。

- [ ] 驗證：搜尋目標問題，記錄哪些論壇討論串被引用
- [ ] 把討論串標題當問題來源（標題就是使用者的真實說法）
- [ ] 參與只用已揭露身分的真人或品牌帳號

## 5. 自有網域與外部平台雙軌

- **自有網域** — 事實原帳，是 AI 最終該引用的頁面
- **外部平台**（方格子 vocus、痞客邦 PIXNET、Medium、LINE 官方帳號）— 擴散用的衛星

- [ ] 外部文章自然連回自有網域的資料頁，平台允許時設 canonical
- [ ] 不大量轉貼相同文字

## 6. 不做的事

- 假評論、刷地圖點擊
- 論壇自問自答、未揭露的業配；違反平台規則，未揭露的廣告也可能牽涉公平交易法
- 大量簡轉繁機翻頁
- 商家檔案類別濫填

## 7. 測量

- [ ] Google Search Console 篩選國家 = 台灣
- [ ] Bing Webmaster Tools（只算 Bing；Yahoo 奇摩流量看分析工具的來源報表）
- [ ] Google 商家檔案成效：搜尋／地圖曝光、通話、路線
- [ ] 選 5–10 個目標問題，在 ChatGPT search、Perplexity、Gemini、Google AI Overviews 記錄 AI 引用 O/X；
      同時記錄該查詢在台灣是否出現 AI Overviews
- [ ] 每週快照一次
