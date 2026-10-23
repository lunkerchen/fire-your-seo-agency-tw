# fire-your-seo-agency-tw

[English](./README.md) · [繁體中文](./README.zh-TW.md) · [简体中文](./README.zh-CN.md) · [日本語](./README.ja.md) · [한국어](./README.ko.md) · **Español**

> Fork localizado para Taiwán de [leopard627/fire-your-seo-agency](https://github.com/leopard627/fire-your-seo-agency) (MIT). El chino tradicional (Taiwán) es el idioma canónico; el carril de Naver se sustituye por un carril TW. Este skill está pensado para el mercado de Taiwán.

[![GitHub stars](https://img.shields.io/github/stars/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/lunkerchen/fire-your-seo-agency-tw?style=flat&logo=github)](https://github.com/lunkerchen/fire-your-seo-agency-tw/fork)
[![Latest release](https://img.shields.io/github/v/release/lunkerchen/fire-your-seo-agency-tw?style=flat&label=release)](https://github.com/lunkerchen/fire-your-seo-agency-tw/releases/latest)
[![License: MIT](https://img.shields.io/badge/license-MIT-green?style=flat)](./LICENSE)

![fire-your-seo-agency-tw](./assets/social-preview.png)

> **¿Pagas a una agencia decenas de miles de dólares taiwaneses al mes por SEO o por "visibilidad en IA"? Despídela. Tu agente de IA puede hacer el trabajo.**

Una ola de servicios cobra ahora cuotas mensuales por "optimización de búsqueda para la era de la IA",
"citas garantizadas en ChatGPT" y "visibilidad en LLM". La mayor parte de lo que hacen en realidad son
**estándares públicos y listas de verificación repetibles**. Cuando lo hace una persona, es una cuota mensual.
Cuando lo hace tu agente, es un skill.

Este repositorio es un skill de [Claude Code](https://claude.com/claude-code). Instálalo y
tu agente audita tu sitio, corrige lo que esté roto y mide los resultados.

## Basado en números reales

Estos números provienen del autor original, no de este fork. El mismo método, aplicado a [Chickenstock](https://www.chickstockfi.com), un servicio coreano de análisis bursátil creado por una sola persona:

- **1,54 M de impresiones de búsqueda en 30 días** (+85.578 % intermensual), 7,4 K clics
- Páginas **citadas párrafo por párrafo por el AI Briefing de Naver** (el motor de respuestas de Corea)
- Cero gasto publicitario: todo el tráfico entrante viene de la búsqueda y de las citas de IA

El autor original documenta el recorrido en público en [Threads @kindainvestor](https://www.threads.com/@kindainvestor).
Este fork aún no ha publicado cifras de casos propios.

## Los cinco carriles

"Optimización de búsqueda" significa cosas distintas para cada motor. Este skill los trata
como cinco carriles diferentes:

| Carril | Objetivo | La pregunta que responde |
|---|---|---|
| **SEO** | Rastreadores de Google y Bing | ¿Pueden los rastreadores leer e indexar mi contenido? |
| **AEO** (Answer Engine) | Google AI Overviews, Bing Copilot | ¿Me cita el cuadro de respuesta de IA que aparece sobre los resultados? |
| **GEO** (Generative Engine) | ChatGPT, Perplexity, Claude | Cuando la IA generativa navega, ¿soy la fuente primaria? |
| **LLMO** (LLM Optimization) | El conocimiento propio del modelo | ¿Conoce el modelo mi marca, y la conoce correctamente? |
| **TW** (local de Taiwán) | Google, Bing / Yahoo 奇摩, Perfil de Empresa de Google, Dcard / PTT / Mobile01 | ¿Los motores de Taiwán, las señales locales y las superficies de comunidad me encuentran y me citan? |

**TW es lo que distingue a este fork.** Las guías globales de AEO asumen una web en inglés.
En Taiwán, Google lidera pero no está solo: StatCounter (2026-09) muestra a Google con
79,48 %, a Yahoo con 11,37 % y a Bing con 8,24 %. Los resultados de Yahoo 奇摩 funcionan con Bing, así que
Bing Webmaster Tools importa aquí más que en la mayoría de los mercados. El carril TW también cubre
las señales de idioma `zh-Hant-TW`, el Perfil de Empresa de Google para negocios locales y las
superficies de comunidad que las respuestas de IA pueden citar (verifícalo con comprobaciones registradas): Dcard, PTT y Mobile01.

**Y además, un motor de contenido.** Gran parte de una cuota mensual paga "N artículos al mes". Este skill
lo sustituye por un flujo de trabajo: una lista de preguntas pendientes extraída de tus propios datos de búsqueda, un
modelo de contenido con frontmatter que genera el JSON-LD, una puerta de publicación que todo artículo debe superar,
y una política de actualización y fusión para que los artículos no se pudran. El resultado se mide como "la proporción de artículos que se ven
y se citan", no como "artículos publicados".

## Instalación

Como plugin (recomendado: un solo comando y actualizaciones sencillas):

```
/plugin marketplace add lunkerchen/fire-your-seo-agency-tw
/plugin install fire-your-seo-agency-tw@fire-your-seo-agency-tw
```

O mediante git clone:

```bash
# As a project skill (this project only)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git .claude/skills/fire-your-seo-agency-tw

# Or as a personal skill (every project)
git clone https://github.com/lunkerchen/fire-your-seo-agency-tw.git ~/.claude/skills/fire-your-seo-agency-tw
```

Después, en Claude Code:

```
/fire-your-seo-agency-tw audit my site
```

Tu agente empieza con una auditoría desde el punto de vista del rastreador y, antes de
tocar nada, devuelve un cuadro de mando como este:

| Carril | Estado | Evidencia |
|---|---|---|
| SEO | WARN | El cuerpo se renderiza en el servidor (SSR), pero faltan 214 páginas de detalle en el sitemap |
| AEO | FAIL | Sin primeros párrafos con respuesta directa; datos estructurados de FAQ: 0 |
| GEO | FAIL | Sin llms.txt; política de GPTBot/PerplexityBot sin decidir en robots.txt |
| LLMO | WARN | El nombre de la marca se escribe de 3 formas distintas en las diferentes superficies |
| TW | FAIL | Sin verificar en Bing Webmaster Tools; el html lang es zh-CN |

…y luego propone prioridades, las implementa y programa la nueva medición.

## Qué hace

1. **Auditoría**: lee tu sitio como lo hace un rastreador (sin JavaScript) y puntúa los cinco carriles
2. **Base técnica**: corrige la exposición por SSR, los sitemaps, los meta y los datos estructurados
3. **Páginas de aterrizaje por intención**: diseña páginas con el principio "una pregunta = una página"
4. **Legibilidad por máquinas**: llms.txt, JSON-LD, estructura de párrafos lista para ser citada
5. **Local de Taiwán**: Bing Webmaster Tools y Yahoo 奇摩, señales zh-Hant-TW, Perfil de Empresa de Google, superficies de citación Dcard / PTT / Mobile01
6. **Motor de contenido**: configuración del subblog, lista de preguntas pendientes, puerta de publicación, política de actualización y fusión
7. **Ciclo de medición**: programa una nueva medición y demuestra el cambio con números

## Qué se niega a hacer

- Comprar backlinks, grupos de interacción, spam de contenido: **no luchamos contra el motor de búsqueda**
- Promesas de "posiciones garantizadas": ninguna afirmación sin medición
- Relleno de palabras clave, texto oculto, cloaking: nada que haga que tu dominio sea penalizado

Toda la filosofía cabe en una línea: **la IA no cita la buena redacción. La IA cita datos exactos.**
Conviértete en la fuente primaria de una cifra y las citas llegarán.

## Estructura

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

> Los documentos en chino tradicional de `references/` son los canónicos (los lee el agente);
> `references/en/` los replica en inglés para lectores humanos.

## Comprobaciones del repositorio

Este repositorio se comprueba a sí mismo: `.github/workflows/validate.yml` ejecuta todo en cada push
y pull request:

```bash
python3 tools/validate.py --strict          # 10 checks, standard library only
python3 -m unittest discover -s tests -t .  # unit tests for every check
python3 -m pip install pillow
python3 tools/optimize_assets.py --check    # flags recompressible assets
```

`tools/validate.py` vigila lo que se degrada en silencio en un repositorio solo de documentación: el
contrato del frontmatter de `SKILL.md` (nombre en kebab-case, límite de 64 caracteres para el nombre, descripción
de una sola línea de hasta 1024 caracteres), la coincidencia de versión y nombre entre `plugin.json` y `marketplace.json`,
que `CHANGELOG.md` coincida con la versión del manifiesto, los enlaces relativos y las anclas, la paridad entre las referencias en chino
tradicional y en inglés (número de encabezados, filas de tablas, casillas, numeración de secciones), el presupuesto de recursos y las dimensiones de la imagen de vista previa, los metadatos de la licencia MIT y un análisis
de secretos sobre todos los archivos de texto.

## Star History

<a href="https://www.star-history.com/#lunkerchen/fire-your-seo-agency-tw&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=lunkerchen/fire-your-seo-agency-tw&type=Date" />
  </picture>
</a>

## Licencia

MIT: úsalo libremente y quédate con el dinero de la cuota mensual. Obra original con copyright de leopard627;
localización para Taiwán con copyright de lunkerchen.
