# CPS® Score Interpretation Guide

## How to interpret scores for clients and stakeholders

Use this reference when explaining CPS® results to business owners, marketers,
and non-technical stakeholders.

---

## Grade A (80-100) — Highly Citable

**What it means:**
The page has strong structured data, well-formed meta signals, substantial content,
technical AI access, and clear authorship and freshness signals. AI systems can
confidently retrieve and cite this page for relevant queries.

**Typical profile:**
- JSON-LD schema present and correct
- Meta description 150+ characters, informative
- 1,000+ words of substantive content
- FAQ section present
- /llms.txt file configured
- Date markers and citation language throughout

**Next steps:**
Run the full Cited By AI® audit to identify block-level improvements and measure
Share of Voice across all five AI platforms.

---

## Grade B (65-79) — Regularly Cited

**What it means:**
The page has solid foundations but specific gaps that reduce citation probability
for some query types. Likely appearing in AI answers for branded queries but missing
some unbranded discovery opportunities.

**Typical gaps:**
- llms.txt missing or incomplete
- FAQ content absent
- Some freshness signals missing
- Schema present but incomplete (e.g., missing FAQPage)

**Next steps:**
Fix the Technical AI Readiness pillar first (/llms.txt). Then add FAQ content.
These two changes typically move a B to an A within 2-4 weeks.

---

## Grade C (50-64) — Occasionally Cited

**What it means:**
The page appears in AI answers inconsistently. Branded queries may return it;
unbranded queries typically will not. This is the most common score for business
websites that have not been specifically optimised for AI citation.

**Airdrie Auto Haus baseline (March 2026): 52.7 — Grade C**
This is the documented starting point from the Cited By AI® pilot case study.
It represents a typical SMB website with good content but no AI-specific optimisation.

**Typical gaps:**
- No JSON-LD schema or schema incomplete
- No /llms.txt file
- Content lacks FAQ sections
- No freshness or citation signals
- Word count borderline

**Next steps:**
Use schema-markup-generator to add JSON-LD. Create /llms.txt. Add FAQ sections
to key pages. These three changes typically move a C to a B within 4-6 weeks.

---

## Grade D (35-49) — Rarely Cited

**What it means:**
The page has fundamental gaps that prevent AI systems from reliably identifying
and citing it. May appear in AI answers only when specifically named (branded query)
and even then inconsistently.

**Typical gaps:**
- No structured data of any kind
- No meta description or very short description
- Thin content (under 300 words)
- No technical AI access signals

**Next steps:**
Address Schema and Meta pillars first — these are the fastest wins. Then build
content depth to at least 500 words per key page.

---

## Grade F (0-34) — Not Cited

**What it means:**
The page is effectively invisible to AI retrieval systems. Even if the business
is well-known, AI systems cannot reliably identify and cite its content for
relevant queries.

**Common causes:**
- JavaScript-rendered content (AI crawlers cannot execute JavaScript)
- Blocked in robots.txt
- No HTML content readable by crawlers
- Extremely thin pages (under 100 words)
- Missing title and description entirely

**Next steps:**
Audit robots.txt with technical-seo-checker. Ensure core content is in HTML,
not JavaScript. Run Cited By AI® full audit to identify crawler barriers.

---

## Pillar-by-Pillar Priority Guide

When advising which pillar to fix first, use this priority order:

| Priority | Pillar | Why first |
|----------|--------|-----------|
| 1st | Technical AI Readiness | /llms.txt is the fastest single win. One file, immediate signal to all AI crawlers. |
| 2nd | Schema & Structured Data | JSON-LD unlocks schema-aware retrieval. Without it, the page is invisible to structured queries. |
| 3rd | Content Quality | FAQ sections directly match AI response format. Each FAQ answer is a pre-formatted citation. |
| 4th | AI Signals | Freshness signals are especially important for Perplexity. Add "as of 2026" language throughout. |
| 5th | Meta & Page Identity | Usually already present. If score is low here, it's a quick fix — just update title and description. |

---

## CPS® Lite vs Full Audit — What's Missing

CPS® Lite scores 5 page-level dimensions. The full Cited By AI® audit adds:

| Full Audit Feature | Why it matters |
|-------------------|----------------|
| Block-level scoring | Scores every 134-167 word extract individually — identifies exactly which sentences to rewrite |
| Hallucination detection | Flags where AI invents false information about the business |
| Share of Voice | Measures how often the business appears across all 5 AI platforms for 375+ prompts |
| Funnel-stage SOV | Awareness / Consideration / Decision breakdown — shows where in the buyer journey AI is citing you |
| Competitor visibility | Shows which competitors are being cited instead of you, and why |
| Content generation | Produces publish-ready, pre-scored content blocks to fill identified gaps |

---

*CPS® (Citation Probability Score®) is a registered trademark of Cited By AI®.
Full audit: citedbyai.info — Framework: github.com/citedbyai/cps-framework*
