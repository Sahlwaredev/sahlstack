# Sales Playbook — structure, battle card, discovery guide

The playbook is the document that turns one founder's selling instinct into a system a new
rep can execute in week one. Right-size it: founder-led / first-rep companies get a lean
version (4 stages, 1–2 battle cards, one discovery guide); a scaling team gets the full set.

## Playbook document structure (13 sections)

1. **Company & product story** — positioning summary in 5 lines (inherit from
   `docs/enterprise/marketing/` positioning doc if it exists; never re-invent positioning
   inside the sales playbook). The 10-second and 30-second pitches.
2. **ICP & personas** — a one-page summary of the ICP doc with a link to it. Do not fork the
   ICP; summarize and point.
3. **Sales process** — stages with entry/exit criteria (pull the stage table from
   `pipeline.md` and adapt stage count to motion), plus what must be in the CRM at each stage.
4. **Qualification framework** — MEDDPICC per-field definitions and the 0–3 scoring rubric
   (both defined in `pipeline.md` — reference, don't duplicate). State the materiality line:
   deals above $X get full scoring; below it, a BANT-lite triage is enough.
5. **Core plays** — one per motion, each with steps, assets needed, and a talk-track skeleton:
   - *Inbound response*: SLA <5 minutes to first touch (verify current benchmark via
     WebSearch), triage questions, first-call deck.
   - *Outbound cold*: pointer to the outbound system (`outbound.md` artifacts).
   - *Expansion/upsell*: trigger signals, who initiates, play steps.
   - *Renewal*: T-90/T-60/T-30 checkpoints.
6. **Discovery guide** — full template below.
7. **Demo framework** — below.
8. **Objection library** — top 8–10 objections, format below.
9. **Competitive section** — one battle card per real competitor, template below.
10. **Pricing & discounting** — tier table summary, discount authority matrix
    (e.g. rep ≤10% with a get; founder approval above; nothing >25% ever). Every discount
    has a get: longer term, case study, reference, prepay.
11. **Tools & hygiene rules** — CRM required fields per stage, staleness rules (14-day
    activity rule), loss-reason taxonomy (from `pipeline.md`).
12. **Comp plan summary** — if one exists; otherwise mark "TBD — human decision".
13. **Glossary** — every acronym used, one line each (MEDDPICC, SQO, MAP, EB, POC...).

## Discovery guide template (SPIN-structured)

The combo that works: SPIN for the conversation, MEDDPICC for what you must leave with.

```
### Pre-call research checklist (10 min, mandatory)
- [ ] Company: what they do, size, recent news/trigger events
- [ ] Person: role, tenure, background, anything they've published
- [ ] Signal: WHY are we talking to them now? (write one sentence)
- [ ] Hypothesis: which of our top 3 pains do we expect? (pick one)

### Opening (2 min)
- Agenda + upfront contract: "By the end, we'll both know if it makes sense to
  keep talking. If not, we'll say so. Fair?"

### Situation questions — MAX 2–3 (you did homework instead)
- e.g. "How does <process> work today — who touches it?"

### Problem → Implication → Need-payoff flows (one per top pain)
Pain: <name it>
- Problem:      "Where does <process> break down today?"
- Implication:  "When that happens, what does it cost — time, money, risk?
                 What does that add up to per month?"          ← quantify, always
- Implication:  "Who else feels it when this goes wrong?"      ← multi-thread seed
- Need-payoff:  "If that went away, what would that let your team do?"
                 (the buyer articulates the value — never do it for them)

### Buying-process questions
- "Walk me through how you bought the last tool like this — who was involved,
  what did legal/security need, how long did it take?"          ← paper process, early
- "If this evaluation goes well, what happens next on your side?"

### Champion & EB access
- "Who, besides you, has to be convinced?"
- Champion-test ask: "Could you set up 20 minutes with <EB> next week?"

### Close (never skip)
- Summarize the pain IN THEIR WORDS, confirm the cost figure they gave.
- Agree the next step with a date on the call.
- Within 1 hour: fill MEDDPICC fields in CRM; anything you can't fill is your
  question list for the next call.
```

## Demo framework

Rule zero: **no demo before documented pain.** A demo request before discovery gets a
"happy to — let me ask 3 questions first so I show you what matters" deflection (script it).

```
| Demo moment | Discovery finding it answers | Persona watching | Proof shown |
|-------------|------------------------------|------------------|-------------|
```
Every row must have a non-empty second column. If a feature has no discovered pain to map
to, it is cut from the demo. Open with their workflow (their data/vocabulary if possible),
not your menu. Close every demo with the next step scheduled.

**POC rules (Tomás's law):** never start a POC without a one-page doc containing
(1) written success criteria the buyer agreed to, (2) a timeline with an end date,
(3) the answer to "if we pass, then what?" confirmed by the economic buyer. No doc, no POC.

## Objection library format

One entry per objection, buyer language first:

```
### "<Objection verbatim, as buyers actually say it>"
- What it usually means: <the real concern underneath>
- Respond: <2–4 sentence talk track — acknowledge, reframe, evidence>
- Proof point: <specific customer result, metric, or demo moment>
- Do NOT: <the tempting bad answer reps give>
```

Must include: price/budget, "we'll build it", "not a priority right now", incumbent/competitor,
security/compliance, "send me info", plus the 2–4 most heard in real deals from discovery.

## Battle card template (one per competitor, one screen max)

```
# Battle card: <Competitor>                    Last verified: <YYYY-MM-DD>

**Their pitch in one sentence:** <steelman it — what they honestly do well>
**They win with:** <segment/persona where they beat us>

## When we win / when we lose
- We win when: <2–3 honest conditions>
- We lose when: <2–3 honest conditions — mandatory; reps distrust cards without this>

## Proof points (ours)
1. <specific, verifiable>
2. <specific, verifiable>

## Landmines to plant early (questions that expose their weakness, asked innocently)
1. "Ask them how <X> works when <condition>..."
2. ...

## Their likely traps + defusals
- They'll say: "<their landmine>" → Defuse: "<response>"

## Pricing & packaging intel
<what's known, source and date; mark estimates as estimates>

## SDR cut (the 30-second version)
3 landmines · 2 discovery questions · 1 proof point
```

Rules: a card >90 days old is flagged stale at every playbook/pipeline engagement — stale
cards are worse than none. "Do nothing" and "build it ourselves" each get a card too; they
are the most common competitors in startup deals.

## Assembly & consistency checks (before Phase 4)

- Stage names identical across sections 3, 4, 11 and everything in `pipeline.md` artifacts.
- Every play references assets that exist or are explicitly listed as "to create".
- No unfalsifiable superlatives anywhere in talk tracks — every claim carries a proof point.
- A new rep test: could someone who has never met the founder run a first call from
  sections 5–8 alone? If not, name what's missing.
