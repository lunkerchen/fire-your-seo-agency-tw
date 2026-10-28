# GEO — Generative Engine Optimization (ChatGPT · Perplexity · Claude)

The lane that makes generative AI **cite you as the primary source** when it reads the web
through browsing/search tools. It overlaps with AEO, but generative engines ① run different
crawlers ② read llms.txt ③ reward the *original source* much more strongly.

## 1. llms.txt

`/llms.txt` at the site root — a site guide addressed to AI. Format is markdown:

```markdown
# Service Name

> One-sentence description (state what you are the primary source of)

## Key pages
- [Earnings calendar](https://example.com/earnings): earnings and investor-conference schedule for Taiwan-listed companies
- [Stock data](https://example.com/stocks): filings-based financials & valuation

## Data policy
- Source: computed in-house from official filings (MOPS), refreshed daily
- Cite as: example.com
```

- [ ] `/llms.txt` (the guide) + `/llms-full.txt` (full key data) if you can afford it
- [ ] Pack it with trust signals: data source, refresh cadence, what you originate
- [ ] Serving it from an app route is fine (it doesn't have to be a static file) —
      keep it always current

## 2. Decide your AI crawler policy

AI crawlers come in **three kinds by purpose**, and your robots.txt policy should be
written per purpose. No policy = leaving it to chance:

| Purpose | Representative User-agents | What blocking costs you |
|---|---|---|
| **Training** (model training data) | GPTBot, ClaudeBot, Google-Extended, CCBot, Applebot-Extended | future models knowing your brand (LLMO) |
| **Search indexing** (AI search's own index) | OAI-SearchBot, Claude-SearchBot, PerplexityBot | citations in ChatGPT/Claude/Perplexity search |
| **Live fetch** (page loads at question time) | ChatGPT-User, Perplexity-User, Claude-User | direct citations & traffic at answer time |

```
# If citations are the goal, Allow across the board is the default
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

If your content is an asset and you only want to block **training**, Disallow only the
first row — blocking search/fetch along with it kills citation traffic itself.
The roster changes — recheck each vendor's crawler docs quarterly.

- [ ] **Check your Bing index**: ChatGPT search relies on the Bing index on top of its own
      crawler. If you're not in Bing Webmaster Tools, start with section 0 of
      `references/aeo.md` (or `references/en/aeo.md`). Yahoo search results in Taiwan are
      also served by Bing; see section 1 of `references/tw-local.md`

## 3. Becoming the primary source — the heart of GEO

Generative engines trace "where did this number originate." A page summarizing someone
else's data loses the citation to the original.

- [ ] Define which numbers only you compute or collect (in-house metrics, aggregations,
      observations)
- [ ] Name that number and always serve it from the same page (stable URL = citation address)
- [ ] Paragraph-level citability: when each paragraph carries
      [subject + number + as-of date + methodology], it gets cited as a unit — measured:
      Perplexity clips at exactly this granularity; verify with real searches whether
      other AI search products do the same

## 4. Sub-query alignment — make paragraphs answer the question directly

arXiv 2610.15033 (single study, observational association, not causal): within one site,
paragraphs that answer the question directly are associated with more citations (per 1 SD better match: ChatGPT
+9.5%, Gemini +7.8%, Perplexity +4.8%). Title matching the question is positive only on
Gemini (+16.8%) and Perplexity (+4.7%); on ChatGPT it is −0.2%. FAQ blocks, structured
data, summary boxes, and page speed showed no significant association between pages of
the same site. Also, which pages
the engine's own rewritten sub-queries retrieve explains far more variance than page
attributes do (ChatGPT, comparing pages within the same site: 32% vs. 2.8%; the second
dataset gave 30% vs. 10.0%, a difference that was not significant), and those sub-queries rarely overlap with Google or Bing
results. So watching Google rankings alone does not show what the AI retrieves.

- [ ] List the questions customers ask (GSC/Bing query lists, support logs, the question
      backlog in section 4-1 of `references/en/content.md`)
- [ ] For each question, list the sub-queries an AI may split it into (for example, "best X"
      may become "X price", "X reviews", "who X suits")
- [ ] Make the paragraph **answer each sub-query directly**: put the answer in the first
      paragraph. Use the words of the question in the title and H2 too, but the title
      association differs by engine, so do not only rewrite titles
- [ ] One sub-query = one clear paragraph or page; do not bury it in one long block
- [ ] Verify with section 8: ask the AI the same thing in several phrasings and check
      whether your page is retrieved

## 5. Brand presence on third-party sources

arXiv 2610.15033 (single study) measured the models' existing brand knowledge: models
name brands they already know and prefer familiar sites. It did not test the effect of
adding exposure, so "the more you are mentioned, the more the AI names you" is not
guaranteed. A well-written own site is not enough; the practice is to organize the real
facts about you on third-party sources and track whether the AI mentions you.

- [ ] Inventory third-party sources: Google Business Profile, trade media, review and
      directory sites, forums such as Dcard and PTT (see `references/en/tw-local.md`)
- [ ] Keep the brand name, address, and service description consistent everywhere
- [ ] Organize real facts on third-party sources (real coverage, customer reviews, partner mentions); do not buy or fake them
- [ ] This is long-term work. Track "does the AI answer name you" with the method in section 8

## 6. Write image content as text

arXiv 2511.04080 (single study): adding a text version can raise the chance that text
retrieval and extraction pipelines pick up the information in an image. In the study the
figures are relative changes in G-Eval subjective visibility (text-only −1.01%,
multimodal +1.12%), not citation rate, so do not promise a gain. The paper also admits it
did not compare against VLMs that read images directly.

- [ ] Write alt text for every informative image: describe what it shows and the key
      point, not just keywords
- [ ] For charts, price tables, and flow diagrams, write the numbers and the conclusion
      as text in a caption or in the body
- [ ] Text inside an image (price, spec, date) must also appear in the page text
- [ ] Decorative images get empty alt; do not stuff them

## 7. Do not do this (white-hat line)

C-SEO Bench (arXiv 2506.11097, single study) found that conversational-SEO rewrite tricks
did not show statistically significant positive ranking gains in most tested settings (some
settings ranked significantly worse), that getting the page found and ranked near the front works better than rewriting the text (the paper moved documents earlier in the LLM context; it did not test Google rankings, so do not cite it as evidence for Google SEO), and that gains shrink
once competitors adopt the same tricks (zero-sum). Another study (arXiv 2402.11782) found
LLMs mainly weigh relevance and largely ignore style features such as scientific
citations or a neutral tone, so do not rewrite your voice just to "sound authoritative."

These count as manipulation. Do not do them (see arXiv 2606.28356 SafeGEO, 2404.07981,
2504.05804):

- Hidden prompt injection: invisible text or instructions to the AI telling it to recommend you
- Strategic text that manipulates ranking: sentences written only to push the AI's ordering
- Overstating a flawed product: presenting a product with known defects as the best
- Rewriting into an unnatural chat-style voice just to please the AI

## 8. Verification

- Ask real questions in Perplexity, ChatGPT (search mode), and Gemini and check whether your
  domain appears in the source list; also check in a real Taiwan search whether Google AI
  Overviews and AI Mode appear and cite you — never assume these features are available
- Not appearing? Check in order: llms.txt exists → crawlers allowed → that page is SSR →
  a competing original source exists
