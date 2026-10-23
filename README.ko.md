# fire-your-seo-agency-tw

[English](./README.md) · [繁體中文](./README.zh-TW.md) · [简体中文](./README.zh-CN.md) · [日本語](./README.ja.md) · **한국어** · [Español](./README.es.md)

> [leopard627/fire-your-seo-agency](https://github.com/leopard627/fire-your-seo-agency)(MIT)를 대만 환경에 맞게 현지화한 포크입니다. 정본 언어는 번체 중국어(대만)이며, Naver 레인은 TW 레인으로 대체되었습니다.

한국 시장(Naver)이 대상이라면 업스트림 원본 [leopard627/fire-your-seo-agency](https://github.com/leopard627/fire-your-seo-agency)를 사용하세요. 이 포크는 대만을 대상으로 합니다.

[![GitHub stars](https://img.shields.io/github/stars/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/fork)
[![Latest release](https://img.shields.io/github/v/release/lunkerchen/fire-your-seo-agency-tw?style=flat&label=release)](https://github.com/lunkerchen/fire-your-seo-agency-tw/releases/latest)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat)](./LICENSE)

![fire-your-seo-agency-tw](./assets/social-preview.png)

> **SEO나 "AI 가시성"을 위해 대행사에 매달 수만 대만 달러를 내고 계신가요? 해지하세요. 일은 AI 에이전트가 할 수 있습니다.**

요즘은 "AI 시대의 검색 최적화", "ChatGPT 인용 보장", "LLM 가시성" 같은 서비스에 월 단위 리테이너 비용을
청구하는 곳이 많습니다. 하지만 실제로 하는 일의 대부분은 **공개된 표준과 반복 가능한 체크리스트**입니다.
사람이 하면 리테이너 계약이고, 에이전트가 하면 스킬입니다.

이 저장소는 [Claude Code](https://claude.com/claude-code) 스킬입니다. 설치하면 에이전트가
사이트를 감사하고, 문제를 고치고, 결과를 측정합니다.

## 실제 수치로 만들어졌습니다

아래 수치는 이 포크가 아니라 업스트림 작성자의 것입니다. 같은 플레이북을 [Chickenstock](https://www.chickstockfi.com)(1인 개발 한국 주식 리서치 서비스)에 적용한 결과입니다.

- **30일간 검색 노출 154만 회**(전월 대비 +85,578%), 클릭 7.4K
- **Naver AI 브리핑**(한국의 답변 엔진)이 문단 단위로 페이지를 인용
- 광고비 0원 - 모든 유입은 검색과 AI 인용에서 발생

업스트림 작성자는 [Threads @kindainvestor](https://www.threads.com/@kindainvestor)에서 이 과정을 공개적으로 기록하고 있습니다.
이 포크는 아직 자체 사례 수치를 공개하지 않았습니다.

## 다섯 개의 레인

"검색 최적화"는 엔진마다 의미가 다릅니다. 이 스킬은 이를 다섯 개의 별개 레인으로 다룹니다.

| 레인 | 대상 | 답하려는 질문 |
|---|---|---|
| **SEO** | Google 및 Bing 크롤러 | 크롤러가 내 콘텐츠를 읽고 색인할 수 있는가? |
| **AEO** (Answer Engine) | Google AI Overviews, Bing Copilot | 검색 결과 위의 AI 답변 상자가 나를 인용하는가? |
| **GEO** (Generative Engine) | ChatGPT, Perplexity, Claude | 생성형 AI가 웹을 탐색할 때 내가 1차 출처인가? |
| **LLMO** (LLM Optimization) | 모델 자체의 지식 | 모델이 내 브랜드를 알고 있고, 정확하게 알고 있는가? |
| **TW** (대만 현지) | Google, Bing / Yahoo 奇摩, Google 비즈니스 프로필, Dcard / PTT / Mobile01 | 대만의 엔진, 현지 신호, 커뮤니티 채널이 나를 찾고 인용하는가? |

**TW가 이 포크의 차별점입니다.** 글로벌 AEO 가이드는 영어권 웹을 전제로 합니다. 대만에서는
Google이 앞서지만 혼자가 아닙니다. StatCounter(2026-09) 기준 Google 79.48%, Yahoo 11.37%,
Bing 8.24%입니다. Yahoo 奇摩의 검색 결과는 Bing이 제공하므로 이곳에서는 Bing Webmaster Tools가
대부분의 시장보다 더 중요합니다. TW 레인은 `zh-Hant-TW` 언어 신호, 지역 사업자를 위한
Google 비즈니스 프로필, 그리고 AI 답변이 인용할 수 있는 커뮤니티 채널(기록된 점검으로 확인할 것)인
Dcard, PTT, Mobile01도 다룹니다.

**콘텐츠 엔진도 포함됩니다.** 리테이너 비용의 상당 부분은 "월 N편 게시"에 쓰입니다. 이 스킬은 이를
파이프라인으로 대체합니다. 자사 검색 데이터에서 뽑은 질문 백로그, JSON-LD를 생성하는 frontmatter
콘텐츠 모델, 모든 글이 통과해야 하는 게시 게이트, 글이 낡지 않도록 하는 갱신/병합 정책입니다.
성과는 "게시한 글 수"가 아니라 "노출되고 인용되는 글의 비율"로 측정합니다.

## 설치

플러그인으로 설치(권장 - 명령 하나, 업데이트도 간편):

```
/plugin marketplace add lunkerchen/fire-your-seo-agency-tw
/plugin install fire-your-seo-agency-tw@fire-your-seo-agency-tw
```

또는 git clone으로 설치:

```bash
# As a project skill (this project only)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git .claude/skills/fire-your-seo-agency-tw

# Or as a personal skill (every project)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git ~/.claude/skills/fire-your-seo-agency-tw
```

그런 다음 Claude Code에서 다음을 실행합니다.

```
/fire-your-seo-agency-tw audit my site
```

에이전트는 아무것도 건드리기 전에 크롤러 시점의 감사부터 시작해 다음과 같은 스코어카드를 돌려줍니다.

| 레인 | 상태 | 근거 |
|---|---|---|
| SEO | WARN | 본문은 SSR이지만 상세 페이지 214개가 사이트맵에 없음 |
| AEO | FAIL | 직접 답변형 첫 문단 없음. FAQ 구조화 데이터: 0 |
| GEO | FAIL | llms.txt 없음. robots.txt에서 GPTBot/PerplexityBot 정책 미결정 |
| LLMO | WARN | 채널마다 브랜드명 표기가 3가지로 다름 |
| TW | FAIL | Bing Webmaster Tools 미인증. html lang이 zh-CN |

...그다음 우선순위를 제안하고, 구현하고, 재측정을 예약합니다.

## 하는 일

1. **감사** - 크롤러처럼(JavaScript 없이) 사이트를 읽고 다섯 개 레인 전체를 채점
2. **기술 기반** - SSR 노출, 사이트맵, 메타, 구조화 데이터 수정
3. **의도별 랜딩 페이지** - "질문 하나 = 페이지 하나" 원칙으로 페이지 설계
4. **기계 가독성** - llms.txt, JSON-LD, 인용하기 좋은 문단 구조
5. **대만 현지** - Bing Webmaster Tools와 Yahoo 奇摩, zh-Hant-TW 신호, Google 비즈니스 프로필, Dcard / PTT / Mobile01 인용 채널
6. **콘텐츠 엔진** - 서브 블로그 구축, 질문 백로그, 게시 게이트, 갱신 및 병합 정책
7. **측정 루프** - 재측정을 예약하고 변화를 수치로 증명

## 하지 않는 일

- 백링크 구매, 인게이지먼트 팟, 콘텐츠 스팸 - **검색 엔진과 싸우지 않습니다**
- "순위 보장" 약속 - 측정 없는 주장은 하지 않습니다
- 키워드 스터핑, 숨김 텍스트, 클로킹 - 도메인이 퇴출될 만한 일은 하지 않습니다

철학 전체는 한 줄로 요약됩니다. **AI는 잘 쓴 글을 인용하지 않습니다. AI는 정확한 데이터를 인용합니다.**
어떤 수치의 1차 출처가 되면 인용은 따라옵니다.

## 구조

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

> `references/` 아래의 번체 중국어 문서가 정본입니다(에이전트는 이쪽을 읽습니다).
> `references/en/`은 사람이 읽을 수 있도록 같은 내용을 영어로 옮긴 사본입니다.

## 저장소 점검

이 저장소는 스스로를 점검합니다. `.github/workflows/validate.yml`이 모든 push와
pull request마다 아래 전체를 실행합니다.

```bash
python3 tools/validate.py --strict          # 10 checks, standard library only
python3 -m unittest discover -s tests -t .  # unit tests for every check
python3 -m pip install pillow
python3 tools/optimize_assets.py --check    # flags recompressible assets
```

`tools/validate.py`는 문서 전용 저장소에서 조용히 망가지기 쉬운 항목을 강제합니다. `SKILL.md`
frontmatter 규약(kebab-case 이름, 이름 64자 제한, 1024자 한 줄 description),
`plugin.json` ↔ `marketplace.json`의 버전 및 이름 일치, `CHANGELOG.md`와 매니페스트 버전의 일치,
상대 링크와 앵커, 번체 중국어/영어 레퍼런스 동등성(제목 수, 표 행 수, 체크박스, 섹션 번호),
에셋 용량 예산과 미리보기 크기, MIT 라이선스 메타데이터, 그리고 모든 텍스트 파일에 대한
시크릿 스캔입니다.

## Star History

<a href="https://www.star-history.com/#lunkerchen/fire-your-seo-agency-tw&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
  </picture>
</a>

## 라이선스

MIT - 자유롭게 쓰시고, 리테이너 비용은 아끼세요. 원저작물 저작권은 leopard627,
대만 현지화 저작권은 lunkerchen에게 있습니다.
