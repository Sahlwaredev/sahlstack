# ICP Definition Doc — template & method

The ICP (ideal customer profile) is the GTM keystone. Every other sales artifact — playbook,
sequences, pipeline stages, forecast — inherits from it. Two iron rules:

1. **Derived from evidence, not aspiration.** The primary input is analysis of the best
   closed-won customers (fastest close, highest retention, happiest). If fewer than ~5
   closed-won customers exist, produce an **ICP Hypothesis** instead — same structure, but
   the header says HYPOTHESIS and section 7 lists the validation criteria that will confirm
   or kill it.
2. **A disqualification list is mandatory.** An ICP that only says who to sell to is a wish.
   The "we do NOT sell to" list is what actually saves the pipeline.

## Document structure (all 8 sections, in order)

### 1. Firmographics
Company size (employees AND revenue band), industry/vertical, geography, funding stage,
growth signals. State the range observed in closed-won data, not a guess.
Format: a table with `Attribute | Ideal range | Evidence (which customers)`.

### 2. Technographics
Tools whose presence predicts fit: the stack they run, what you integrate with or replace,
and disqualifying tech (e.g. locked into a competitor's suite). Note which signals are
publicly observable (job posts, BuiltWith, docs) — those feed outbound.

### 3. Situational triggers
The events that open a buying window. This is what makes an ICP actionable. For each won
deal, name the trigger: new leader hired, funding round, tool migration, security incident,
compliance deadline, scaling pain threshold crossed. List the 3–5 recurring triggers with
the evidence deal(s) beside each.

### 4. Buying committee map
One row per role, with typical titles from the evidence:

| Role | Typical title | What they care about | Typical objection |
|------|--------------|----------------------|-------------------|
| Champion | | personal win + pain relief | |
| Economic buyer | | metrics, payback | |
| Technical evaluator | | integration, security | |
| Procurement/legal | | terms, risk | |
| Likely blocker | | status quo, ownership | |

### 5. Qualification / disqualification criteria
Two explicit lists:
- **Qualify when:** 4–6 checkable conditions (firmographic fit + a live trigger).
- **We do NOT sell to:** built from churned customers, discount-heavy regret deals, and
  loss patterns. Each entry gets a one-line reason ("<50 employees — no budget owner,
  3 of 3 churned in year one").

### 6. Pains & JTBD per persona — in customer language
For each buying-committee role that talks to sales: the job statement
("When [situation], I want to [motivation], so I can [outcome]") and 2–3 pains as
**verbatim or near-verbatim quotes** with sources (call notes, win-loss interviews,
G2/review-site language). Founder-paraphrase is a last resort and must be marked as such.

### 7. Evidence basis
- Which customers were analyzed (list them), date of analysis.
- Loss patterns considered (last N losses, stated vs suspected reasons).
- For a HYPOTHESIS doc: the validation criteria — e.g. "confirmed when 5 closed-won
  customers match sections 1–3" — and what disconfirms it.
- Refresh rule: **re-derive quarterly** from the latest closed-won/lost data. Stale ICPs
  quietly rot every downstream artifact.

### 8. Account tiering & coverage model

| Tier | Definition | Coverage model |
|------|-----------|----------------|
| Tier 1 | Named perfect-fit accounts (20–50 at startup stage — every one listed by name) | 1:1 — researched, personalized, multi-threaded outreach |
| Tier 2 | Strong-fit segment filters (not named — a definition) | 1:few — signal-triggered sequences per sub-segment |
| Tier 3 | Opportunistic fit | 1:many — inbound + light-touch capture only |

Tier 1 gets a literal account list in the doc (or an appendix file). If the user can't name
20 accounts, that itself is a finding — the ICP is too vague to prospect against.

## Persona card sub-template (one per selling-relevant persona)

```
## Persona: <Role title>
- Seniority & reports to:
- JTBD statement:
- Pains (their words, sourced):
- Buying trigger events:
- Success metrics they're judged on:
- Objections/anxieties:
- Messaging do's / don'ts:
```

## Method notes for the ICP sprint

- **Cluster before you conclude.** Lay out the closed-won table first (segment, ACV, cycle
  length, source, retention), then name the pattern in one sentence. If two distinct
  clusters exist, say so — a primary and secondary ICP beats a mushy average of both.
- **Weight by quality, not count.** One fast-closing, expanding customer outweighs three
  discounted, support-heavy ones. The regret list is negative evidence, use it.
- **Sales and marketing share ONE ICP doc.** If `docs/enterprise/marketing/` has an ICP or
  positioning doc, reconcile — divergent ICPs between teams is a named failure mode.
  Inherit their positioning language for section 6; flag conflicts rather than silently
  overwriting.
- **Triggers beat attributes.** Firmographics say who *could* buy; triggers say who might
  buy *now*. Outbound (see `outbound.md`) is built on section 3, not section 1.
- **Anti-pattern check before shipping:** does every section trace to evidence or a marked
  hypothesis? Is there at least one disqualifier that will genuinely turn deals away? Would
  an SDR reading only this doc know which 30 accounts to work first?
