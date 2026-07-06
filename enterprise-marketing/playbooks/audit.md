# Playbook: SEO/GEO + Funnel + Messaging Audit

Report structure for `/marketing --audit`. Iron rule: every finding cites observed evidence
(URL, quoted text, response, screenshot the user pasted). A finding without evidence is a
hypothesis and is labeled as one. Where the user has no analytics, say so, and make
instrumentation the #1 roadmap item.

---

## Audit report structure

```markdown
# SEO/GEO + Funnel + Messaging Audit — <domain>
> Scope: <pages examined> · Method: WebFetch/WebSearch point-in-time sample on <date>

## 0. Executive summary
Top 5 findings by business impact, one line each, with a severity (CRITICAL / HIGH / MEDIUM).

## 1. Technical
| Check | Observed | Verdict | Fix |
|---|---|---|---|
- Crawlability & indexation: robots.txt rules, sitemap present/valid, noindex surprises
- AI-bot access policy: GPTBot / PerplexityBot / ClaudeBot / Google-Extended allowed or
  blocked (flag as a deliberate business decision either way)
- Rendering: is primary content visible without JS execution (affects both crawlers and
  LLM retrieval)
- Core Web Vitals / page weight: observable signals only unless the user provides field data
- Schema/structured data: present, valid, appropriate types
- Titles/metas: unique, buyer-language, not truncated
- Internal linking: pillar↔cluster links, orphan pages, anchor quality

## 2. Content inventory
- Pages by role: commercial / editorial / docs / dead weight
- Decay candidates and thin/duplicative pages (prune or merge list)
- Cannibalization: multiple pages targeting one query
- Information-gain spot check on the top 3 editorial pages: does each say anything the
  current top results don't? (quote the evidence)

## 3. Authority
- Backlink profile signals (observable: who references them — WebSearch)
- Third-party surface presence: review sites, Reddit/community threads, industry pubs —
  present and accurate, or absent
- Digital PR opportunities (original data candidates, expert-comment angles)

## 4. AI visibility (GEO)
Method: for each of the top 10–20 category questions (agreed in discovery), WebSearch and
record who is cited/surfaced.
| Category question | Who is cited/surfaced | Us? | Gap owner |
|---|---|---|---|
- Citation share summary: us vs top 2 competitors
- Honesty clause: this is a point-in-time sample of retrieval surfaces, not a measurement of
  every AI assistant; label it so.
- Competitor citation gap: which content earns their citations that we lack

## 5. Messaging & funnel
Walk: landing → pricing → signup/CTA (WebFetch each).
- Message clarity per the gates: swap test, buyer-language test, banned superlatives count
  (list them, quoted), "so what?" chain on the hero claim
- 5-second test: can a stranger say what it is, who it's for, why switch? (quote the hero)
- CTA-to-stage match: what the page asks for vs. where the visitor is
- Pricing page: value metric legible? tiers mapped to segments? objections addressed?
- Friction inventory: forms, dead ends, broken links, mobile issues observed
- Funnel numbers: user-provided analytics vs. observed structure; leaks identified where data
  exists, `NO DATA` marked where it doesn't
- Instrumentation check: UTM taxonomy in use? events defined for
  visitor→lead→MQL/PQL→SQL→opp? If not: instrumentation is roadmap item #1.

## 6. Opportunity model
| Topic/fix | Intent | Difficulty | Business value | Type (capture/create/technical) |
|---|---|---|---|---|
Ranked by revenue relevance. Demand capture (comparisons, alternatives, pricing queries,
AI-citation gaps on decision questions) outranks demand creation.

## 7. Roadmap
| # | Action | Impact | Effort | Owner | Depends on |
|---|---|---|---|---|---|
Ordered by impact/effort. First items are almost always: instrumentation gaps, CRITICAL
technical fixes, hero message rewrite (if it failed the gates), top-3 capture topics.
```

---

## Severity rubric

- **CRITICAL** — blocks the funnel or blinds measurement: broken signup path, noindex on
  commercial pages, zero instrumentation, hero message a stranger cannot parse.
- **HIGH** — materially suppresses acquisition or conversion: AI bots blocked unintentionally,
  no schema, pricing page hides the value metric, zero citation share on decision questions.
- **MEDIUM** — compounding drag: decayed content, weak internal linking, missing FAQ blocks,
  superlative-laden copy.

## Common traps (check yourself before delivering)

- Reporting traffic opportunities with no pipeline linkage — every opportunity row carries
  business value, not search volume worship.
- Auditing 2019-style SEO only — the AI-visibility section is mandatory, not optional.
- Inventing Core Web Vitals or ranking numbers — observable evidence or user-provided data
  only; otherwise write `verify with Search Console / field data`.
- A 40-item roadmap — cap at ~12 items; the rest go in an appendix as "later".
