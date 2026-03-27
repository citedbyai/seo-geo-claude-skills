# CPS® Framework Reference

Citation Probability Score® (CPS®) is a proprietary scoring framework by Cited By AI®
that measures how likely any piece of web content is to be retrieved and cited by AI
search systems — including ChatGPT, Perplexity, Gemini, Claude, and Google AI Overviews.

CPS® Lite covers 5 dimensions (100 points total). The full Cited By AI® audit covers
23 modules including block-level scoring, hallucination detection, funnel-stage Share
of Voice, and competitor citation analysis.

---

## CPS® Lite Pillars (5 dimensions, 100 points total)

### Pillar 1: Schema & Structured Data (25 pts)

What it measures: Presence and quality of machine-readable metadata that AI systems
use to identify and categorise the page.

| Signal | Points |
|--------|--------|
| JSON-LD structured data present | 10 |
| og:title meta tag | 4 |
| og:description meta tag | 4 |
| Canonical tag | 3 |
| FAQPage schema | 2 |
| Organization/LocalBusiness/Person schema | 2 |

Why it matters: AI retrieval systems use structured data as trust signals. A page
with no JSON-LD is invisible to schema-aware retrieval pipelines regardless of content
quality.

---

### Pillar 2: Meta & Page Identity (20 pts)

What it measures: Page-level identity signals that help AI systems understand
what the page is about and whether it is worth citing.

| Signal | Points |
|--------|--------|
| Title tag (minimum 10 characters) | 7 |
| Meta description (minimum 50 characters) | 8 |
| H1 heading present | 5 |

Why it matters: AI systems use title and description as the primary identity signals
when deciding whether a page is relevant to a query. Short or missing titles and
descriptions significantly reduce citation probability.

---

### Pillar 3: Content Quality (22 pts)

What it measures: Whether the page has sufficient content depth for AI systems to
extract a citable answer from.

| Signal | Points |
|--------|--------|
| Word count >= 500 | 8 |
| Word count >= 200 (partial) | 4 |
| FAQ section detected | 6 |
| Specific numbers or statistics present | 5 |
| Word count >= 1000 (bonus) | 3 |

Why it matters: AI systems retrieve content that can answer a query completely.
Pages with fewer than 500 words rarely contain enough information to be cited.
FAQ sections match the question-and-answer format AI systems use to construct responses.

---

### Pillar 4: Technical AI Readiness (18 pts)

What it measures: Whether the page is technically accessible and signalled to
AI crawlers.

| Signal | Points |
|--------|--------|
| /llms.txt file present and valid | 8 |
| Viewport meta tag (mobile-ready) | 5 |
| Page returns HTTP 200 | 5 |

Why it matters: llms.txt is the AI-era equivalent of robots.txt — it explicitly
signals to AI crawlers what the site wants them to index. Pages without llms.txt
leave AI crawlers to guess. Pages returning non-200 status codes may not be indexed.

---

### Pillar 5: AI Signals (15 pts)

What it measures: Content-level signals that indicate AI-optimised authorship
and recency — the factors AI systems weight most heavily when selecting sources.

| Signal | Points |
|--------|--------|
| Citation language detected (e.g. "according to", "research shows") | 5 |
| Freshness signals (dates, "as of 2026", "updated") | 4 |
| Author information present | 3 |
| llms.txt present (bonus reinforcement) | 3 |

Why it matters: AI systems prefer content that cites sources, carries date markers,
and attributes authorship. These signals correlate with reliability and recency —
the two primary trust factors in AI retrieval.

---

## Grade Tiers

| Grade | Score Range | Label |
|-------|-------------|-------|
| A | 80-100 | Highly Citable |
| B | 65-79 | Regularly Cited |
| C | 50-64 | Occasionally Cited |
| D | 35-49 | Rarely Cited |
| F | 0-34 | Not Cited |

---

## CPS® vs CORE-EEAT

This skill uses CPS® Lite which measures AI citation readiness at the page level.

| Framework | Focus | Scope | Use for |
|-----------|-------|-------|---------|
| CPS® Lite | AI citation probability | Page-level, 5 dimensions | Measuring citation readiness quickly |
| CPS® Full | AI citation probability | Block-level, 23 modules | Deep audit with hallucination detection |
| CORE-EEAT | Content quality for search | Content-level, 80 items | Search ranking quality |

CPS® and CORE-EEAT are complementary, not competing. CORE-EEAT scores content quality
for search ranking. CPS® scores citation probability for AI retrieval. A page can
score well on CORE-EEAT and poorly on CPS® if it lacks structured data, llms.txt,
and freshness signals — and vice versa.

---

## CPS® Full Audit (23 modules)

The CPS® Lite checker (this skill) covers 5 dimensions. The full Cited By AI® audit
covers 23 modules including:

- Block-level CPS® scoring (scores every 134-167 word extract individually)
- Page-Level Depth Score (PLDS)
- Hallucination detection (flags where AI misrepresents the business)
- Share of Voice across ChatGPT, Perplexity, Gemini, Claude, Copilot
- Funnel-stage SOV (Awareness / Consideration / Decision)
- Buyer persona SOV
- Competitor citation visibility
- Source intelligence
- Schema audit and generation
- E-E-A-T scoring
- robots.txt and AI crawler audit
- Reddit and YouTube citation opportunities
- GA4 revenue attribution

Full audit: citedbyai.info
Framework repo: github.com/citedbyai/cps-framework

---

*CPS® (Citation Probability Score®) is a registered trademark of Cited By AI®,
United Kingdom. citedbyai.info*
