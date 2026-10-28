# AEO — Answer Engine Optimization (Google AI Overviews · Bing Copilot)

The lane that makes the AI answer box above the search results cite you. Answer engines
don't "read and summarize" your page — they **find and extract the sentence that is the
answer**. Being extraction-friendly is everything.

## 0. Bing registration — the forgotten half

Most sites watch GSC and skip Bing entirely, but **Copilot pulls answers from the Bing
index, and ChatGPT search leans heavily on it too.** In Taiwan, Yahoo search results are
also served by Bing (verify with the side-by-side check in `references/tw-local.md` section 1). No Bing registration = throwing
away half of AEO and GEO, plus your Yahoo exposure.

- [ ] Register at [Bing Webmaster Tools](https://www.bing.com/webmasters) — supports
      one-click import from GSC (brings over verification and sitemaps). A 10-minute job
- [ ] Confirm sitemap submission + wire up IndexNow (Bing consumes IndexNow directly)
- [ ] Verify indexing with `site:yourdomain` on Bing itself; Yahoo results come from Bing,
      so spot-check there too. See section 1 of `references/tw-local.md`

## Principle: one question = one page

- Every question people actually type ("when is X's earnings call", "X dividend date")
  gets a dedicated page. A page covering ten questions gets extracted for none of them.
- URL, h1, and title mirror the question verbatim.

## The shape of an extractable sentence

- [ ] **Direct answer in the first paragraph**: one sentence (~40 chars), top of the page.
      "Bottom line: X's next earnings release is November 14, 2026 (after market close)."
- [ ] **Each sentence states facts independently**: context-dependent sentences like
      "the figure mentioned above" become meaningless when extracted. Every paragraph
      carries its own subject, number, and as-of date.
- [ ] **State the basis and date**: "P/E 13.8 (2026-08-26, trailing four quarters)" —
      numbers without a basis get docked in the engine's trust scoring.
- [ ] Use tables: engines parse tables into structured facts reliably.

## FAQ block

- [ ] Real search questions as an FAQ section at the bottom of the page; the number follows the actual questions
- [ ] Attach FAQPage JSON-LD, **character-identical to the visible text** — divergence
      risks a spam verdict
- [ ] Only answers settled by data. No prediction or recommendation Q&A (especially in
      regulated industries)
- NOTE — **Expectation management**: since August 2023, Google restricts FAQ rich results
      (the collapsible Q&A UI in search) to authoritative government/health sites, and
      HowTo rich results were removed entirely. You still attach FAQPage LD — not for
      rich results but to keep the content and the markup consistent and machine-readable.
      Don't rip it out because "the stars don't show."
- NOTE — **Don't expect an FAQ to earn citations by itself**: a large observational study
      (arXiv 2610.15033; two markets, 90 days, 158,099 answers, 468,037 citations; single
      study) found no significant association between FAQ blocks or structured data and how
      often pages were cited within one site. Cross-site comparisons looked positive,
      mostly because the sites differ. So an FAQ does not mean a citation gain.
      The main value of an FAQ is **answering real questions**. What was associated with
      more citations is paragraphs that answer the question directly (observational; see
      section 4 of `references/en/geo.md`).

## Trust signals (E-E-A-T)

Answer engines weigh *who is speaking*. Given identical data, the page with a verifiable
operator beats the anonymous one:

- [ ] **Visible operator**: an About page saying who built this and why, linked to your
      Organization JSON-LD
- [ ] **Author/source attribution**: data pages state where the data comes from and how
      it's processed (e.g. "computed from official filings, refreshed daily")
- [ ] **Reachability**: a contact channel (email/form) scores above a ghost site
- [ ] **Honest dateModified**: put the real update time in structured data — bumping the
      date without changing content backfires when detected

## Verification

- After deploy, actually search the target questions on Google and Bing and record
  whether the AI answer cites you. Do this in a real Taiwan search environment
  (Traditional Chinese, Taiwan region) and check whether Google AI Overviews, AI Mode,
  and Copilot appear at all; never assume a feature is available.
- Not cited? Check in order: ① is the direct-answer sentence above the fold
  ② data freshness vs. competing pages ③ page trust (domain age, a verifiable operator).
  Structured data helps machines read the page; it does not guarantee more citations
  (arXiv 2610.15033, single study).
