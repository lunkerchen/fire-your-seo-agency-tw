# TW Local — Taiwan Local Search and Citations

Taiwan is Google-first, but the Bing ecosystem is roughly a fifth of queries, and Traditional
Chinese language signals, local businesses, and forums are what overseas guides don't cover.
This lane is this skill's localization differentiator. Two goals: ① local visibility on Google,
Bing (including Yahoo Taiwan), and maps ② **your own domain getting cited** when AI answers
Taiwan users.

## 1. Market share and the Bing ecosystem

StatCounter 2026-09 (all platforms): Google 79.48%, Yahoo 11.37%, Bing 8.24%.
Source: https://gs.statcounter.com/search-engine-market-share/all/taiwan . Numbers vary by device view (desktop/mobile) — recheck before quoting.

Yahoo Taiwan search results are served by Bing, so one Bing index covers two entry points. The Bing index also feeds Copilot; checking Bing coverage is cheap insurance for AI answers.

- [ ] Verify the site in Bing Webmaster Tools (needs the user's account — walk them through it; can import from Google Search Console)
- [ ] Submit the sitemap
- [ ] Send an IndexNow ping at publish (key file at the site root); confirm it returns 200 and is not
      swallowed by an SPA catch-all route (a common gotcha with Astro/Next.js `public/`)
- [ ] Verify: search the same query on Yahoo Taiwan and on Bing, compare the results, and check
      whether your pages appear

## 2. Traditional Chinese language signals

- [ ] `<html lang="zh-Hant-TW">` (or zh-TW), consistent across the site
- [ ] When other language or region versions exist (e.g. English, zh-Hans, zh-HK), set reciprocal hreflang; don't serve auto-converted Simplified-to-Traditional duplicate pages
- [ ] Use Taiwan usage and full-width punctuation; mainland terms (視頻, 質量, 信息, 軟件) tell Taiwan
      readers the content was not written for them
- [ ] State Taiwan-specific entities plainly: 統一編號 (business ID), address with district, phone in +886
      format, NT$ prices marked tax-included or tax-excluded

## 3. Google Business Profile (when there is a physical location or service area)

Ranking factors per Google: relevance, distance, prominence.

- [ ] NAP (name/address/phone) identical across the website, the profile, and LocalBusiness JSON-LD
- [ ] Categories and services only for what is actually delivered (over-stuffing risks suspension)
- [ ] Reply to reviews with real content; never buy reviews or click-boost
- [ ] The profile needs the owner's account — walk them through it; the agent implements the website
      side (LocalBusiness schema, NAP, map embed)

## 4. Forum and community citation surface

Threads on Dcard, PTT, Mobile01 (and 巴哈姆特 for gaming) are candidate sources that Google results and AI answers may cite for Taiwan queries; whether they actually do is decided by the recorded checks below.

- [ ] Verify: search the target questions and record which forum threads get cited
- [ ] Use thread titles as a question source (titles are the real phrasing)
- [ ] Participate only as a disclosed real person or brand account

## 5. Own domain plus external platforms, two tracks

- **Own domain** — the ledger of facts, the page AI should ultimately cite
- **External platforms** (方格子 vocus, 痞客邦 PIXNET, Medium, LINE Official Account) — satellites for reach

- [ ] Link naturally from external posts back to the data page on your domain; set canonical where the platform allows
- [ ] Never mass-repost identical text

## 6. Don't

- Fake reviews, map-click boosting
- Forum self-Q&A or undisclosed paid posts; this violates platform rules, and undisclosed advertising
  can also raise Fair Trade Act (公平交易法) issues
- Mass machine-converted Simplified-to-Traditional pages
- Category stuffing on the business profile

## 7. Measurement

- [ ] Google Search Console filtered to country = Taiwan
- [ ] Bing Webmaster Tools (Bing only; check Yahoo Taiwan traffic in analytics referrers)
- [ ] Business profile performance: search/map impressions, calls, directions
- [ ] For 5–10 target questions, record AI citation O/X in ChatGPT search, Perplexity, Gemini, and Google
      AI Overviews; also record whether AI Overviews appear at all for the query in Taiwan
- [ ] Take a snapshot weekly
