# Playbook: Content Engine (Strategy · Calendar · GEO)

Templates for `/marketing --content`. Governing rules: content is 20% creation / 80%
distribution; information gain is the entry ticket (something not already in the top 10
results and in every LLM's training data); measure citations and pipeline, not traffic.

---

## 1. Content Strategy doc template

```markdown
# Content Strategy — <Product>

## Audience & jobs per funnel stage
| Stage | Buyer question (Google phrasing) | Same question (ChatGPT/AI phrasing) | JTBD | Content job |
|---|---|---|---|---|
| Problem-aware | | | | teach/name the problem |
| Solution-shopping | | | | comparison, evaluation criteria |
| Decision | | | | proof, pricing clarity, objections |
| Customer | | | | activation, expansion |

## Differentiation thesis (information gain)
What we can say that nobody else can: <proprietary data / first-hand operating experience /
contrarian position with receipts>. If this section is empty, do not start producing —
commodity content earns neither rankings nor citations.

## Topic cluster map
| Pillar page | Supporting cluster pieces | Funnel stage | Business value (H/M/L) | Priority |
|---|---|---|---|---|
Prioritize by revenue-per-topic, not traffic-per-keyword. Demand-capture topics first:
"<product> vs <competitor>", "<competitor> alternatives", "best <category> for <ICP>",
pricing/cost explainers.

## Distribution plan (per channel)
| Channel | Why it fits our buyer | Owner | Cadence | Success signal |
|---|---|---|---|---|
Founder/employee social, newsletter, communities (Reddit/Slack/Discord where the ICP lives),
review sites, syndication/guest posts. Every published piece gets a distribution checklist
BEFORE it is written.

## Voice guide
<3–5 rules + words-we-ban list, inherited from the messaging house>

## Production workflow & roles
Brief → draft → SME/expert review → edit → publish → distribute → repurpose → refresh.
Named humans per step. Named credible author(s) with credentials (E-E-A-T) — no ghost bylines.

## KPIs
Primary: AI-citation share of voice on the category question set; organic-sourced pipeline
($ or signups). Secondary: qualified organic traffic, newsletter growth, third-party mentions.
Traffic alone is explicitly not a KPI.
```

---

## 2. GEO requirements (attach to EVERY brief)

GEO (Generative Engine Optimization) = being retrieved and cited when AI assistants answer
the category's questions. In 2026 the target is "one of the few domains an LLM cites", not
ten blue links. Requirements per piece:

- [ ] **Clear definitions** — the core term defined plainly in the first screen; LLMs lift
      clean definitional passages.
- [ ] **Structured FAQ block** — the real questions buyers ask AI, answered atomically.
- [ ] **Quotable atomic passages** — self-contained 1–3 sentence statements that survive
      extraction out of context.
- [ ] **Cited claims** — every statistic linked to a primary source; uncited numbers removed.
- [ ] **Original data where possible** — LLMs disproportionately cite original statistics;
      even a small survey or product-data analysis beats paraphrased research.
- [ ] **Named author with credentials** — real person, bio, first-hand experience signals
      (E-E-A-T: experience, expertise, authoritativeness, trust).
- [ ] **Schema markup spec** — Article/FAQPage/HowTo/Product as appropriate.
- [ ] **AI crawler access** — GPTBot, PerplexityBot, ClaudeBot etc. not blocked in robots.txt
      (a deliberate policy choice — surface it to the founder, don't assume).
- [ ] **Third-party surface presence** — plan the mentions LLMs trust: Reddit threads, review
      sites (G2 etc.), industry publications. On-domain content alone under-performs for
      citations.

---

## 3. Content Brief template (one per piece)

```markdown
# Brief: <working title>
- Audience & funnel stage:
- Job of the piece (what changes in the reader's head):
- Target query: <Google phrasing> · AI-prompt phrasing: <how it's asked to ChatGPT>
- Cluster / pillar:
- Angle & information gain: <what this says that the current top results and LLM answers do not>
- Proof & SME input: <data, quotes, who reviews for accuracy>
- Named author:
- Format & length:
- CTA (must match funnel stage — no demo CTA on problem-aware pieces):
- Distribution plan: <specific channels + owner — required before drafting>
- GEO checklist: attached (section 2)
- Publish date / Refresh date:
```

---

## 4. Editorial calendar format

One row per piece:

| Title/angle | Cluster | Stage | Target query + AI phrasing | Format | SME | Owner | Brief | Publish | Distribution ✓ | Refresh due |
|---|---|---|---|---|---|---|---|---|---|---|

Sizing rule: calendar volume = real production capacity from discovery, not ambition.
A sustainable 2 pieces/month with full distribution beats 8 drafted and dumped.

## 5. Repurposing matrix (1 pillar → derivatives)

| Source | Derivatives |
|---|---|
| Pillar article | 3–5 social posts (founder voice) · newsletter section · short video/talk outline · FAQ entries · community answer (Reddit/forum, non-promotional) · sales enablement snippet · guest-post pitch |

Rule: derivatives are adapted per platform, never copy-pasted.

## 6. Refresh & pruning cadence

- Quarterly decay audit: list pages by traffic/conversion trend; classify update / merge /
  prune. Thin or superseded pages get pruned — slop inventory drags the whole domain.
- Winners get refreshed (new data, updated year, expanded FAQ) before new topics are added.
- Every piece has a `Refresh due` date at publish time.
