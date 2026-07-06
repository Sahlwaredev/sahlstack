# Lifecycle Playbook — onboarding, QBR/EBR, renewal pipeline

Reference templates for `/customer-success --onboarding` and `--qbr`. The lifecycle thesis: retention is won in the first 14 days and confirmed every quarter — the renewal call is where you find out whether the year's work happened, not where you do it.

## 1. Onboarding program

### The first-value milestone (the program's spine)

- **Definition:** the specific, instrumented product event after which the customer would resist losing the product. An event name in the analytics system, not a feeling. Examples of the right shape: "first automated report delivered to a stakeholder," "first pipeline run in production," "5 teammates active in week 2."
- **Discipline:** "onboarded" means the customer hit first value — NEVER "we did the kickoff call." If the event isn't instrumented, instrumenting it is deliverable #1 and goes to the top of the human to-do list.
- **Why it's the spine:** customers reaching first value within ~2 weeks are roughly 3× more likely to renew and expand. Default target: first value ≤14 days from kickoff; calibrate per product.
- **Metrics:** TTFV (time to first value, kickoff → event fired) and onboarding CSAT/CES. Attached plays: TTFV over target → stall play (below); onboarding CES poor → friction review into VoC.

### Stage gates (every stage: entry criteria, exit criteria, owner both sides, target days)

| Stage | Exit criteria | Owner (us) | Owner (them) | Target |
|-------|--------------|-----------|--------------|--------|
| Kickoff | Success criteria confirmed against why-they-bought; stakeholder map done; mutual action plan co-signed | <CS function> | Champion | Day 0–2 |
| Configuration | Product configured for THEIR first-value path (skip everything else) | <CS/support> | Their admin | Day 2–5 |
| Training | Users who must act toward first value are trained — only those users, only that path | <CS function> | Champion | Day 5–8 |
| **First Value** | **The instrumented event fired** | joint | joint | ≤ Day 14 |
| Go-live | Rollout to full intended user set; go-live checklist done | <CS function> | Champion | Day 14–21 |
| Handoff to CSM | Handoff doc written; CSM function intro'd; first health score computed | <onboarding fn> | — | Day 21 |

### Onboarding plan template (per customer)

```markdown
# Onboarding plan — <account> (<YYYY-MM-DD>)
## Account summary
Why they bought (verbatim from sales handoff), success criteria, ARR, plan, renewal date.
## Stakeholder map
Champion / economic buyer / admin / end-user leads — names, roles, engagement notes.
## Success plan
Their goal → measurable first-value milestone (event: `<event_name>`) → target date.
## Milestone timeline
The stage-gate table above, dated, with named owners both sides.
## Training plan
Who, on what, when — scoped to the first-value path only.
## Risks
<e.g. champion bandwidth, data migration dependency> — each with a mitigation.
## Go-live checklist
## Handoff summary (completed at handoff)
What was achieved, open items, health score at handoff, first QBR date.
```

Anchor everything on the **mutual action plan** the customer co-signs — shared dates create shared accountability; an onboarding only we care about stalls.

### The stall play

- **Trigger:** no customer response or milestone progress for 5 business days.
- **Steps:** Day 5 — structured re-engagement (restate THEIR goal and the smallest next step, ask for 20 minutes); Day 8 — offer to do the next step FOR them (concierge the config); Day 10 — exec sponsor loops in their economic buyer: "we committed to <outcome> by <date>; we're at risk and here's the one thing needed."
- **Exit:** milestone progress resumes. 30-day checkpoint: still stalled → health score Red, onboarding-failure risk flagged on the renewal forecast.

## 2. QBR / EBR program

### Cadence by touch model (segmentation drives coverage economics)

| Touch | Accounts | Rhythm |
|-------|----------|--------|
| High-touch | Top accounts by ARR/strategic value | Live QBR quarterly; EBR (exec business review, economic buyer present) ≥2×/year |
| Mid-touch | Middle book | Live semi-annual; written value recap the other quarters |
| Tech-touch | Long tail | Automated digital value recap quarterly — no meeting |

Rules of thumb: no QBR *program* under ~10 customers (do ad-hoc value reviews instead); no $5k account gets $15k of CSM time.

### The deck (8–10 slides) — the ≤30% rule

**Hard rule: at most 30% of the deck is about your product; at least 70% is about their business.** A QBR that is a usage readout gets the meeting declined next quarter — outcome-based agenda or kill the meeting.

1. **Agenda + attendees** — confirm the economic buyer's presence cadence is being met.
2. **Their stated goals, recapped** — from the success plan; in their words. This slide is why the meeting exists.
3. **Outcomes achieved** — business-metric evidence with ROI math: "resolution time down 35% ≈ 15 hrs/week ≈ $<X>/yr at your loaded cost." Never "you logged in 1,200 times." Every number must survive their CFO reading it.
4. **Adoption vs benchmark** — the one product-ish slide; frame as risk/opportunity for THEIR outcome, not feature marketing.
5. **Support & service summary** — tickets, escalations, what we fixed systemically (proof that escalations produce fixes).
6. **Health & risks — honest** — what we're worried about, jointly; each risk with a mitigation owner. Hiding risk here guarantees a surprise at renewal.
7. **Roadmap alignment** — only items mapped to THEIR goals; commit only what product committed.
8. **Recommendations & growth** — expansion framed strictly as customer value ("your team X has the same workflow problem"), never as a quota push.
9. **Mutual action plan, next quarter** — dated, owned both sides; opens the next QBR as slide 2's evidence.

**The customer's-CFO test:** if their finance leader saw only slide 3, would they re-approve the spend? If no, the QBR isn't ready — and neither is the renewal.

## 3. Renewal management pipeline

Run renewals like a sales pipeline — stages, forecast categories, and inspection. The renewal is a lagging indicator; the pipeline makes the leading work visible.

### Stages (days to renewal)

| Stage | Window | Exit criteria |
|-------|--------|--------------|
| 120-day health check | T-120 | Health score current; driver diagnosis done if not Green; value evidence inventory started |
| 90-day kickoff | T-90 | Renewal owner named; stakeholder/champion status verified; **iron rule: no account enters this window Red without an active save play AND manager visibility** |
| 60-day commercial proposal | T-60 | Proposal delivered (pricing, term, any right-sizing); expansion attached only if health supports it |
| 30-day close plan | T-30 | Signature path mapped (who signs, procurement steps, dates); open objections named with owners |
| Signed | T-0 | Countersigned; post-renewal notes logged (what almost went wrong feeds next cycle) |

### Forecast categories & the honesty rule

| Category | Meaning | Discipline |
|----------|---------|-----------|
| Commit | Verbal or better; no open risk | Named account list |
| Best case | Path to yes exists; one open variable | Variable named per account |
| **At risk** | Red/Yellow health, open driver, or stakeholder gap | **Named accounts, each with the active save play and its 30-day checkpoint date** |

**A forecast with no red is a lie.** Every forecast ships with the at-risk column populated or with an explicit, evidenced statement of why zero accounts qualify (rare; treat with suspicion). Forecast reviews inspect the at-risk column FIRST — that's where the quarter is won or lost, 90+ days before it shows up in the churn number.

### Renewal brief (per account entering T-90)

```markdown
# Renewal brief — <account> (renewal <date>)
Health: <band + driver> · ARR: <x> · Forecast: <commit/best case/at risk>
## Value evidence (QBR slide-3 math, current)
## Stakeholders (champion, economic buyer, procurement — status of each)
## Risks & active plays (play, start date, 30-day checkpoint)
## Commercial recommendation (term, price, right-sizing, concession floor + who approves)
## Negotiation notes for the human (what they'll push on, our walk-away, trade goods)
```

The AI writes the brief; **the human negotiates.** Concessions above the authority limits require named approval before the call, not after.
