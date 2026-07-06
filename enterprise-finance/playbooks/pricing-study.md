# Playbook: Quantitative Pricing Study

Scope boundary: this is the **quantitative layer** — measurement, packaging math, revenue
impact. The strategic layer (value-metric choice rationale, market positioning, premium vs.
penetration posture) belongs to `/strategy --pricing`; if that artifact exists in
`docs/enterprise/strategy/`, inherit its decisions instead of re-litigating them.

## The 6-step study

### 1. Current-state analysis (Fatoumata)

From billing data / last ~10-20 closed deals:
- **Price realization** = realized price ÷ list price, distribution not just average.
  Realization <85% means the list price is fiction — the study should fix the fence, not
  just the number.
- Discount distribution by segment and by rep (a single rep driving discounts is a sales
  problem wearing a pricing costume — say so).
- Plan mix, ARPA by plan, NRR and churn by plan (a cheap plan with terrible retention is
  costing more than it earns).

### 2. Value metric confirmation

The unit the price scales with (seats, usage, records, revenue-share). Test: does customer
value grow with the metric? Does the metric grow without friction the customer resents?
If `/strategy --pricing` decided this, inherit it. Otherwise recommend one, decisively,
with the two tests as evidence.

### 3. Willingness-to-pay (WTP) research — pick the method by what's feasible

**Van Westendorp Price Sensitivity Meter** (survey, need n≥30 in-segment; more per segment
to cut by segment). The exact four questions, asked about the specific package:

1. At what price would this be **so expensive you would not consider it**? (Too expensive)
2. At what price would it be **getting expensive, but you'd still consider it**? (Expensive/high)
3. At what price would it be **a bargain — a great buy for the money**? (Cheap/bargain)
4. At what price would it be **so cheap you'd doubt its quality**? (Too cheap)

Analysis: plot cumulative distributions; the intersections bound the acceptable range —
Point of Marginal Cheapness (too-cheap × expensive) and Point of Marginal Expensiveness
(too-expensive × bargain) bracket the range; the Optimal Price Point sits at the
too-cheap × too-expensive intersection. Report the range, not just the OPP — packaging
decides where in the range each tier lands.

**Gabor-Granger** (survey): for a specific tier, ask purchase likelihood at a descending
price ladder (5–6 points around the hypothesis). Yields a demand curve and revenue-maximizing
point per tier. Use after Van Westendorp narrows the range.

**Conjoint / MaxDiff**: gold standard for packaging (which features drive WTP) but heavier —
recommend only when there's budget/volume for a proper panel; name a tool rather than
hand-rolling.

**Analogue method (no survey possible):** competitor pricing pages via WebSearch (capture
price, packaging, and DATE — pricing pages change), win/loss notes mentioning price, realized
prices from step 1, and expansion behavior as revealed WTP. Label the study's confidence
accordingly: `ANALOGUE-BASED — no primary WTP data`.

### 4. Packaging grid

- **Good/Better/Best**: 3 tiers (4 with enterprise "Contact us"). Each tier boundary gets
  **1–2 fence features** — capabilities the next segment up cannot live without (SSO/SAML,
  audit logs, advanced permissions are classic upmarket fences). More than 2 fences per
  boundary = a confusing grid; fewer = no reason to upgrade.
- Price spread across the grid: **~2.2–3x** from Good to Best.
- **Usage-based / hybrid** where the value metric demands it: platform fee (floor +
  predictability) + consumption rate, committed-use discounts at volume, overage handling
  (soft cap + notification beats hard cutoff for retention).
- Output: the grid as a table — tier | price | value-metric allowance | fence features |
  target segment.

### 5. Revenue impact model

Apply the proposed grid to the CURRENT customer book, row by row (or by segment cohort):

- Migration assumptions per cohort: % accepting the new price, % negotiating, % churning —
  under conservative / expected / aggressive adoption. The conservative case honors
  conservatism asymmetry: churn response AND negotiation erosion AND slower new-logo
  conversion together.
- Outputs: ΔARR, ΔNRR, Δgross margin (usage pricing changes hosting economics — pull Rashid's
  unit-cost number if a `--finops` artifact exists), and the payback timeline of the change.
- **Grandfathering plan**: who keeps old pricing and for how long (12 months is a common
  courtesy window), migration comms dates, renewal-time vs. immediate migration. Grandfathering
  forever is a silent NRR ceiling — put an end date on it.

### 6. The memo (the deliverable)

```markdown
# Pricing Study — <company> — <date>
> Review gate: Human review recommended (pricing is a CEO decision; this is the evidence)

## Recommendation (first, one paragraph, decisive: "Move to X because Y")
## Current state (realization, discounts, mix — the evidence of the problem)
## WTP findings (method, n, ranges; confidence label)
## Proposed packaging grid (the table)
## Revenue impact (3 adoption scenarios; ΔARR / ΔNRR / Δmargin)
## Migration & grandfathering plan (dates)
## Risks & rollback (what we watch post-change: churn spike threshold, win-rate floor;
   the pre-committed rollback trigger)
## Strategic-layer pointers (what /strategy --pricing owns; open questions for it)
```

## Quality bar

- Every WTP number carries its method and n (or the ANALOGUE label). Never present analogue
  inference as survey data.
- Competitor prices carry capture dates — pricing pages change; verify current via WebSearch
  before publishing.
- The revenue impact model ties to the canonical ARR schedule (`metrics.md` definitions).
- The memo leads with the recommendation, not the methodology tour.
