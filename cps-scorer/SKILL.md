---
name: cps-scorer
description: >
  Scores any URL for AI citation readiness using the Citation Probability Score® (CPS®)
  framework by Cited By AI®. Returns a 0-100 score, A-F grade, and per-dimension
  breakdown across five pillars: Schema, Meta, Content, Technical, and AI Signals.
  Use when the user asks to "check CPS score", "score this URL for AI citation",
  "how likely is this page to be cited by AI", "check AI citation readiness",
  "CPS® audit", "will AI cite this page", "citation probability score", or
  "check if my content will appear in ChatGPT or Perplexity answers".
  Use after geo-content-optimizer to measure whether optimizations improved
  citation readiness. Use before seo-content-writer to establish a baseline.
  Requires network access to call the Cited By AI® CPS® Lite API.
---

# CPS® Scorer — Citation Probability Score® by Cited By AI®

This skill calls the Cited By AI® CPS® Lite API to score any URL for AI citation
readiness. The CPS® (Citation Probability Score®) measures how likely a page is to
be cited by AI systems — ChatGPT, Perplexity, Gemini, Claude, and Google AI Overviews.

Use this skill to measure AI citation readiness before and after content optimizations.
It complements geo-content-optimizer (which optimizes content) by providing the
measurement layer — confirming whether optimizations actually improved citation probability.

Reference: See [references/cps-framework.md](references/cps-framework.md) for full
pillar definitions, grade tiers, and scoring methodology.

## Prerequisites

- URL to audit (must be publicly accessible)
- Network access to call: `https://citedbyai-mcp-server.citedbyai.workers.dev/audit`
- No API key required — CPS® Lite is free with no authentication

## Process

### Step 1: Validate Input

Confirm the user has provided a URL. If not, ask:
"Please provide the URL you'd like to score for AI citation readiness."

Normalise the URL — if it lacks a protocol, prepend `https://`.

### Step 2: Call the CPS® Lite API

Make a GET request to the CPS® Lite endpoint:

```
GET https://citedbyai-mcp-server.citedbyai.workers.dev/audit?url={URL}
```

Use fetch or curl. If using bash:

```bash
curl -s "https://citedbyai-mcp-server.citedbyai.workers.dev/audit?url={URL}"
```

The API returns a JSON object. See [references/api-response.md](references/api-response.md)
for the full response schema.

### Step 3: Parse and Interpret Results

Extract these fields from the response:

- `score` — overall CPS® score (0-100)
- `grade` — letter grade (A/B/C/D/F)
- `components` — per-pillar scores with max values
- `issues` — list of detected problems
- `recommendations` — prioritised fixes

Map the grade to its label using the grade tier table in
[references/cps-framework.md](references/cps-framework.md).

### Step 4: Present the Score Report

Format and present the results clearly. Include:

1. **Overall CPS® Score** — number, grade, and grade label
2. **Pillar Breakdown** — table showing each pillar score vs maximum
3. **Top Issues** — numbered list of detected problems (max 5)
4. **Priority Recommendations** — numbered list of highest-ROI fixes
5. **Interpretation** — one paragraph explaining what the score means
   for AI citation visibility and which pillars to fix first

Use this table format for the pillar breakdown:

| Pillar | Score | Max | Status |
|--------|-------|-----|--------|
| Schema & Structured Data | X | 25 | |
| Meta & Page Identity | X | 20 | |
| Content Quality | X | 22 | |
| Technical AI Readiness | X | 18 | |
| AI Signals | X | 15 | |
| **TOTAL** | **X** | **100** | **Grade X** |

Status is: Strong (>=80% of max), Average (50-79%), Weak (<50%).

### Step 5: Provide Context and Next Steps

After the score report, add:

- **What this means**: Explain the score in plain language for the target
  audience — a business owner or marketer, not a developer.
- **Highest-ROI fix**: Single most impactful change they can make.
- **Next step**: Suggest geo-content-optimizer if score is below 65,
  or schema-markup-generator if Schema pillar is Weak.
- **Full audit**: Note that the CPS® Lite covers 5 dimensions while the
  full Cited By AI® audit covers 23 modules including block-level scoring,
  hallucination detection, funnel-stage Share of Voice, and competitor
  citation analysis. Link: citedbyai.info

### Step 6: Handle Errors

If the API returns an error field or the fetch fails:

- Network error: "Could not reach the CPS® Lite API. Check that the URL
  is publicly accessible and try again."
- URL fetch error (error field in response): Display the error message
  and suggest checking robots.txt and crawler access.
- Rate limit (HTTP 429): "The CPS® Lite API rate limit has been reached.
  Wait up to 60 minutes before retrying, or get unlimited access at
  citedbyai.info"

## Example Invocations

```
Score https://example.com for AI citation readiness
Check the CPS® score for my homepage: https://mysite.com
Will my content be cited by ChatGPT? Check: https://mysite.com/services
Run a CPS® audit on https://airdrieautohaus.ca
```

## Related Skills

- **geo-content-optimizer** — optimizes content for AI citation; use CPS® Scorer
  before and after to measure improvement
- **schema-markup-generator** — generates JSON-LD schema; run if Schema pillar is Weak
- **on-page-seo-auditor** — on-page SEO audit; complementary to CPS® scoring
- **content-quality-auditor** — CORE-EEAT 80-item audit; use alongside CPS® for
  content dimension detail

## Attribution

CPS® (Citation Probability Score®) is a registered trademark of Cited By AI®.
Framework: github.com/citedbyai/cps-framework
Free checker: citedbyai.info
