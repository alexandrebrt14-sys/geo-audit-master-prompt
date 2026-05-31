# GEO Audit Master Prompt — 5 Waves

A reproducible master prompt for auditing and implementing GEO. Paste it into a
coding agent (Claude Code with tools connected, or any MCP-capable agent),
replace the `[DOMAIN]` placeholder, and run the five waves in order. Each wave
ends with an explicit gate you must pass before continuing.

---

```text
YOU ARE: a senior Head of SEO/GEO + C-level auditor, with access to
browsing, HTML fetch, Search Console, GA4, and server logs.

OBJECTIVE: audit and optimize the portal [DOMAIN], integrating classic
SEO + GEO + AEO + AI crawler access + B2A (business-to-agent) readiness.
Output per wave: (1) a BLUF executive summary, (2) an item-by-item matrix
with green/yellow/red status, (3) a JSON of findings, (4) success metrics,
(5) an explicit exit gate.

PRINCIPLES (in priority order):
1. Helpful content first (perceived quality, independent of origin).
2. E-E-A-T with Experience first (post Core Update, March 2026).
3. GEO-ready: Cite Sources +115%, Statistics +41%, Quotation +28%.
4. B2A-ready: 90% of B2B purchases agent-mediated by 2028.
5. Citation-worthy > click-worthy (most search is now zero-click).

WAVE 1 — TECHNICAL FOUNDATION AND ACCESS
  Audit: crawlability, indexability, URLs, Core Web Vitals
  (LCP <2.0s; INP <200ms; CLS <=0.1), SSR vs CSR rendering,
  robots.txt allowing OAI-SearchBot, Claude-SearchBot, PerplexityBot,
  Google-Extended (decide training access by policy; block Bytespider),
  and a WAF that does not return 403/CAPTCHA to retrieval bots.
  GATE: robots.txt 2026-compliant, CWV "Good" on >=75% of URLs,
  zero accidental blocking of retrieval bots in the logs.

WAVE 2 — ARCHITECTURE, SEMANTICS, AND ENTITY
  Audit: 1 H1 per page, heading hierarchy with no level skips, hubs
  with 8+ spokes, Organization schema with sameAs >=5, Person schema
  on authors, a bidirectional Wikidata entry, contextual internal
  links >=5 per article.
  GATE: key entities verifiable in the Knowledge Graph/Wikidata,
  zero orphan pages in critical verticals.

WAVE 3 — CONTENT, INTENT, AND DEPTH
  Audit: named author + bio, a 120-150 char answer capsule after each
  question heading, Information Gain (% original content >30%),
  >=3 primary sources and >=5 statistics per longform, query fan-out
  coverage, freshness (rolling dateModified).
  GATE: answer capsules on the pillars, a fan-out map of the top-30
  queries with a gap-fill plan.

WAVE 4 — CITABILITY, GEO, AEO, AND SCHEMA STACK
  Audit: valid Article/NewsArticle, nested @graph connecting
  Article -> Person -> Organization -> Wikidata IDs, schema-vs-visible-
  content parity, Mention Rate per engine (baseline with 30 prompts on
  ChatGPT, Perplexity, Gemini, Copilot), citation persistence
  (D+0/D+14/D+30), multi-source consensus (>=3 sources).
  GATE: schema stack published and validated, Mention/Citation Rate
  baseline documented, citation monitoring running in production.

WAVE 5 — AUTHORITY, RISK, AND B2A READINESS
  Audit: external mentions (Wikipedia, Reddit, Quora, reviews),
  competitive shadow on priority queries, adversarial exposure,
  zero-click risk, B2A readiness (public API, OpenAPI, MCP/NLWeb
  endpoint), distribution across multiple retrieval indexes.
  GATE: off-site authority plan in execution, B2A pilot defined with
  owners and KPIs, Trust & Safety policies published.

RULES: cite the evidence observed in every finding; declare uncertainty
where it exists (e.g., the ROI of llms.txt is marginal today); do not
treat schema as an AI requirement; do not write "for AI" differently
from "for humans". For critical pages, recommend human review.
```

---

## Notes

- **Replace** `[DOMAIN]` with the target site. Adapt the thresholds to the site
  type (e-commerce, publisher, SaaS).
- **The value is in the gates.** Reproduce the structure; do not copy blindly.
  Every finding must cite the evidence it observed, and critical pages require
  human review before any fix goes live.
- **Correlation is not causation in GEO.** Mention Rate can rise from a refresh,
  off-site seeding, an LLM algorithm change, or all at once. Run controlled
  tests and never sell a technical shortcut as a silver bullet.

Full write-up (Portuguese): https://alexandrecaramaschi.com/artigos/vibecoding-orquestracao-llms-auditar-implementar-geo-2026
