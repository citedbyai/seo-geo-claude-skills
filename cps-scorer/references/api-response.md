# CPS® Lite API Response Schema

## Endpoint

```
GET https://citedbyai-mcp-server.citedbyai.workers.dev/audit?url={URL}
```

No authentication required. Rate limited to 20 requests per IP per hour.

---

## Response Schema

```json
{
  "url": "https://example.com",
  "score": 67,
  "grade": "B",
  "components": {
    "schema": {
      "score": 14,
      "max": 25
    },
    "meta": {
      "score": 20,
      "max": 20
    },
    "content": {
      "score": 19,
      "max": 22
    },
    "technical": {
      "score": 5,
      "max": 18
    },
    "aiSignals": {
      "score": 9,
      "max": 15
    }
  },
  "issues": [
    "No FAQPage schema detected",
    "No /llms.txt file found",
    "No citation signals detected"
  ],
  "recommendations": [
    "Create /llms.txt — fastest win for AI platform visibility",
    "Add Organization JSON-LD schema to every page",
    "Get the full CPS® audit at citedbyai.info"
  ],
  "error": null
}
```

---

## Field Definitions

| Field | Type | Description |
|-------|------|-------------|
| `url` | string | The URL that was audited |
| `score` | number | Overall CPS® Lite score (0-100) |
| `grade` | string | Letter grade: A / B / C / D / F |
| `components` | object | Per-pillar score breakdown |
| `components.schema` | object | Schema & Structured Data pillar |
| `components.meta` | object | Meta & Page Identity pillar |
| `components.content` | object | Content Quality pillar |
| `components.technical` | object | Technical AI Readiness pillar |
| `components.aiSignals` | object | AI Signals pillar |
| `issues` | array | List of detected problems |
| `recommendations` | array | Prioritised fixes (highest ROI first) |
| `error` | string or null | Error message if fetch failed, null otherwise |

---

## Error Responses

### URL fetch failure
```json
{
  "url": "https://example.com",
  "score": 0,
  "grade": "F",
  "error": "Could not fetch https://example.com: connection refused"
}
```

### Rate limit exceeded (HTTP 429)
```json
{
  "error": "Rate limit exceeded",
  "message": "You have reached the /audit limit of 20 requests per hour.",
  "limit": 20,
  "current": 21,
  "scope": "endpoint",
  "retry_after": "Up to 60 minutes",
  "upgrade": "Need higher limits? Get the full audit at citedbyai.info"
}
```

---

## Example curl call

```bash
curl -s "https://citedbyai-mcp-server.citedbyai.workers.dev/audit?url=https://example.com" | jq .
```

## Example Python fetch

```python
import requests, json

url = "https://example.com"
resp = requests.get(
    "https://citedbyai-mcp-server.citedbyai.workers.dev/audit",
    params={"url": url}
)
data = resp.json()
print(f"CPS® Score: {data['score']}/100 (Grade {data['grade']})")
for pillar, v in data["components"].items():
    print(f"  {pillar}: {v['score']}/{v['max']}")
```

---

## MCP Tool Alternative

The same scoring is also available via the Cited By AI® MCP server tools:

- `get_aeo_score` — returns score and grade only (lightweight)
- `analyze_aeo` — returns full breakdown including issues and recommendations
- `check_ai_readiness` — alias for analyze_aeo

MCP server endpoint: `https://citedbyai-mcp-server.citedbyai.workers.dev/mcp`

Listed on Glama: glama.ai/mcp/servers/citedbyai
Listed on Smithery: smithery.ai/server/citedbyai

---

*CPS® (Citation Probability Score®) is a registered trademark of Cited By AI®.
citedbyai.info — github.com/citedbyai/cps-framework*
