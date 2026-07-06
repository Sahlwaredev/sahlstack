# Health & Retention Playbook — health score spec, save plays, churn system

Reference templates for `/customer-success --health` (and churn taxonomy for `--voc`). Iron law of this file: **a score without an attached action is decoration.** Every band maps to a play; every play has a trigger, owner, steps with timings, exit criteria, and a 30-day checkpoint.

## 1. Health Score Model Spec (template)

```markdown
# Health Score Model — <segment or "all customers">

## Purpose & decisions it drives
<Which decisions change based on this score: save-play triggering, renewal forecast
category, CSM attention allocation. If a decision isn't listed, the score doesn't serve it.>

## Segments
<One model per meaningfully different segment (enterprise vs self-serve). A blended
score across segments predicts nothing for either.>

## Signal inventory
| Signal | Family | Source system | Refresh | Available today? |
|--------|--------|--------------|---------|------------------|
| Login frequency (WAU/seat) | Usage | <analytics> | daily | yes/no |
| Feature adoption breadth (of top-N features) | Usage | <analytics> | weekly | |
| Feature adoption depth (core workflow completions) | Usage | <analytics> | weekly | |
| Seat utilization (active/purchased) | Usage | <billing+analytics> | weekly | |
| Ticket volume & severity trend | Relationship | <helpdesk> | weekly | |
| CSAT/NPS last response | Relationship | <survey tool> | per response | |
| QBR attendance / exec engagement | Relationship | <CRM/manual> | per event | |
| Champion status (named, active, at company) | Relationship | <CRM/manual> | monthly | |
| Payment history | Commercial | <billing> | monthly | |
| Contract timing (days to renewal) | Commercial | <CRM> | daily | |
| Expansion conversations open | Commercial | <CRM> | weekly | |

Signals not available today → "Instrument next" list (top of human to-do). NEVER fake a signal.

## Weights & formula
<Weighted composite, weights summing to 100. Starting point: Usage 50 / Relationship 30 /
Commercial 20 for product-led; shift toward Relationship for high-touch enterprise.
State the formula explicitly so two people compute the same number.>

## Bands & thresholds
Red < <X> ≤ Yellow < <Y> ≤ Green   — thresholds set so history back-tests cleanly (below).

## Band → playbook mapping (mandatory)
| Band | Fires | Owner | Within |
|------|-------|-------|--------|
| Red | Driver diagnosis (§3) → matching save play (§4) | <CSM function> | 3 business days |
| Yellow | Watch play: signal review + 1 proactive outreach | <CSM function> | 10 business days |
| Green | Expansion scan + advocacy ask (case study, reference) | <CSM function> | quarterly |

## Override rules
CSM manual override allowed with written justification (e.g. "score Green but champion
resigned Friday"). Overrides logged; >20% override rate means the model is wrong — re-weight.

## Back-testing results
Scored the last <N> churned accounts as of 90 days pre-churn: <k>/<N> were Red, <m>/<N>
Yellow, <j>/<N> Green (misses). Hit rate reported honestly; Green misses analyzed below.
Usage signals typically show risk 45–60 days pre-cancellation — if ours didn't, the usage
signals are wrong or under-weighted.

## Calibration cadence
Quarterly: re-run back-test on the trailing 4 quarters of churn, re-weight, re-threshold.

## Known blind spots
- **Watermelon accounts** (green outside, red inside): high usage but the champion is
  leaving, or the wrong personas use it (admins, not the buyers' team). Countermeasure:
  champion status is a hard signal, and any account with usage-Green + relationship-Red
  gets flagged watermelon and treated as Yellow.
- <others found during back-testing>
```

## 2. Churn taxonomy — classify BEFORE analyzing

| Class | Drivers | Treatment |
|-------|---------|-----------|
| **Controllable** | Poor onboarding / never reached first value · unresolved product gaps · no value realization or proof · bad support experience · price/value mismatch | Full post-mortem; feeds process fixes, health model re-weighting, save-play library |
| **Uncontrollable** | Company died · acquired · budget line eliminated · champion departed irreplaceably | Log it, count it, move on. Analyzing uncontrollable churn for process fixes wastes the quarter |

Only controllable churn justifies process change. But classify honestly: "champion left" is uncontrollable only if multi-threading was genuinely attempted; "budget cut" often hides "we couldn't prove value when budgets tightened" — which is controllable.

## 3. Driver diagnosis (Red account → which play?)

Ask in order; first strong yes wins:

1. Usage collapsed or never started? → **Low adoption** play.
2. Champion gone quiet, left, or was replaced? → **Champion loss** play.
3. Blocked on a missing capability they've asked about? → **Product gap** play.
4. Pushback on price, seat cuts requested? → **Price sensitivity** play.
5. Competitor evaluation signals (feature-comparison questions, security questionnaire for a rival, sudden export activity)? → **Competitive threat** play.
6. Escalations, repeated tickets, CSAT 1–2s? → **Support frustration** play.

Multiple drivers → run the primary, note the secondary in the play log. Diagnosis unclear → the play IS a discovery call; never guess a driver and burn the play on it.

## 4. Save-play library (driver-specific — the generic "check-in" play saves 20–30%; these save 40–60%)

Each play: **Trigger · Owner · Steps with timings · Exit criteria · 30-day checkpoint (no improvement → escalate to founder + renewal forecast moves to At Risk).**

### Play A — Low adoption → re-onboarding
- **Trigger:** usage < <threshold> for 3+ weeks, or first value never reached.
- **Steps:** Day 0 diagnose (blocked vs no need); Day 3 offer structured re-onboarding (2 sessions max, outcome-focused: their goal, not your features); Day 14 verify the first-value event fired; Day 21 usage re-check.
- **Exit:** first-value event fired AND usage above threshold for 2 consecutive weeks.

### Play B — Champion loss → multi-thread within 30 days
- **Trigger:** champion departed, demoted, or 3+ unanswered touches.
- **Steps:** Day 0 map remaining stakeholders; Day 5 exec-to-exec intro (draft the email for the founder); Day 10 offer new-stakeholder onboarding; Day 20 secure a named replacement champion; Day 30 confirm 2+ active threads.
- **Exit:** ≥2 engaged contacts, one of whom owns the renewal decision.

### Play C — Product gap → roadmap alignment + workaround
- **Trigger:** stated blocker on missing capability.
- **Steps:** Day 0 document the underlying need (not the requested feature) into VoC; Day 3 deliver the best current workaround with honest limits; Day 7 roadmap conversation — commit only what product has actually committed; Day 14 close the loop in writing.
- **Exit:** customer accepts workaround-plus-timeline in writing, or the gap is confirmed a lost cause (then prep an honest offboarding — a clean exit beats a resentful renewal).

### Play D — Price sensitivity → value recap + right-size (discount LAST)
- **Trigger:** price pushback, seat-cut request, procurement squeeze.
- **Steps:** Day 0 build the value recap (their outcomes, their numbers — QBR math); Day 5 right-size honestly: cut unused seats/tier BEFORE discounting (downgrade-to-save keeps the logo and the honesty); Day 10 if still short, concession within authority limits, term-for-discount trade only.
- **Exit:** renewal committed at a price the value recap supports.
- **Never:** discount as the opening move — it trains customers to threaten churn annually.

### Play E — Competitive threat → exec engagement + differentiation
- **Trigger:** rival evaluation signals.
- **Steps:** Day 0 assess what's genuinely better over there (honesty first); Day 3 exec sponsor call — business relationship, not feature war; Day 7 differentiation brief on THEIR use cases; Day 14 switching-cost/risk analysis delivered as helpful diligence, not FUD.
- **Exit:** renewal commit, or a real bake-off with agreed criteria (then win it or learn).

### Play F — Support frustration → escalation swarm + service recovery
- **Trigger:** repeated escalations, CSAT 1–2 pattern, "considering alternatives because of support."
- **Steps:** Day 0 swarm: one senior owner for ALL their open tickets; Day 2 human apology call with specifics (what failed, what changes); Day 7 all open tickets resolved or dated; Day 14 follow-up CSAT check.
- **Exit:** open-ticket count at zero-or-dated AND next CSAT ≥4.

**Play completion tracking:** every fired play logged (account, driver, play, outcome). A play nobody can say fired last week is shelf-ware — review the log monthly.

## 5. Churn post-mortem template (every controllable loss ≥ <ARR threshold>)

```markdown
# Churn post-mortem — <account> (<YYYY-MM-DD>)
## Account snapshot
ARR, tenure, segment, plan, seats bought vs active at exit.
## Signal timeline
Health-score history (what did the score say 30/60/90/120 days out — did the model see it?).
Key events: escalations, champion changes, usage inflections.
## Plays run and outcomes
Which plays fired, when, what happened. "None fired" is a finding about the trigger system.
## Root cause (5-whys against the taxonomy)
Stated reason → actual reason (usually 2 layers deeper — "price" is rarely price).
## Controllable? (y/n and why)
## Exit verbatims
Their words, from the exit interview (human-conducted).
## Systemic recommendations
Each with an owner and a date. Process/model fixes, not blame.
## Fed back into
Health model re-weighting? Save-play library? Onboarding? Name the artifact updated.
```

Quarterly: churn-reasons Pareto across post-mortems. The top 2 controllable reasons get roadmap-level attention; everything else is noise management.

## 6. Survey program (relationship signals feeding the score)

- **CSAT** (1–5, post-ticket): closed loop on every 1–2 within 24 h. Good = 75–85%; top quartile ≥90% (verify current benchmarks via WebSearch — these date fast).
- **CES** (1–7 "how easy was it"): post-interaction and post-onboarding; the best loyalty predictor for support experiences; identifies friction for the VoC report.
- **NPS** (0–10): relational, quarterly or biannual, **sampled** — max one relational survey per user per quarter (fatigue cap). Segment by role and lifecycle stage; report trend + verbatim themes, never one blended vanity number.
- Detractor workflow: outreach within 48 h → root-cause tag → theme taxonomy → VoC.
- At scale: AI-scored sentiment across 100% of conversations supplements low survey response rates.
