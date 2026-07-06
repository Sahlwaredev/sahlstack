# Metrics System Playbook — KPI dictionary, metric tree, dashboard, WBR

Reference for `/bizops --metrics`. Read before drafting any metrics artifact.

## The KPI dictionary entry format

One entry per outcome and driver metric. This is the single highest-leverage bizops
artifact — it ends the "sales says churn is 5%, finance says 8%" wars. Diagnostics get
entries only when someone has actually disputed their definition.

```markdown
### <Metric name>
- **Plain-English definition:** one sentence a new hire understands.
- **Exact formula:** the arithmetic, with every term defined. Include the SQL or the
  source-report reference if one exists. ("Churn = customers lost in month / customers
  at start of month. Excludes accounts in trial. Downgrades are NOT churn — see NRR.")
- **Grain & segments:** measured per what (account, user, seat, $) and split by what
  (plan, segment, cohort, geography).
- **Source & refresh:** system of record + how often it updates.
- **Owner:** exactly one named person accountable for this number and its movement.
- **Target & how it was set:** the number, and its derivation (historical 80th
  percentile, benchmark with citation, plan math). No target without a baseline.
- **Level:** outcome / driver / diagnostic.
- **Counter-metric:** the guardrail that catches Goodharting of this metric.
- **Caveats:** known blind spots, seasonality, small-n warnings, mix-shift risks.
- **Change history:** date + what changed in the definition + why. Definitions are
  versioned; silently changing a formula is how trust dies.
```

Entry-quality checks:
- Two teams computing this differently today? Their variants are documented in caveats
  with the ruling: which definition wins and from when.
- Formula uses another metric? Link to that entry — no shadow definitions.
- A rate must name its denominator explicitly. Most metric wars are denominator wars.

## The KPI tree method

Three levels. Build top-down, validate bottom-up.

```
LEVEL 1 — OUTCOMES (5–10 max, exec-reviewed weekly)
  North Star (value delivered to customers, countable)  +  Revenue outcome
  e.g. "weekly active workspaces"                          "net new ARR"
        |
LEVEL 2 — DRIVERS (what moves the outcomes; each has one owner)
  North Star = f(new activations, retention of actives, depth per active)
  Revenue    = f(pipeline created, win rate, ACV, NRR)
        |
LEVEL 3 — DIAGNOSTICS (pulled only during investigation; NOT on any dashboard)
  activation = f(signup→setup completion, time-to-first-value, onboarding drop step 3...)
```

Rules:
1. **The keep-test:** every metric either measures an outcome, explains a driver, or
   triggers an action. Anything else is deleted, in front of the user, by name.
2. **Decision-linkage:** each Level 1 and Level 2 metric names the decision it informs
   and who owns that decision. "Interesting" is not a pass.
3. **Exactly one owner per metric.** A metric owned by "the team" is owned by nobody.
4. **Pair every rate with its volume, every average with its distribution.** A 90%
   conversion rate on 10 visitors is not a 90% conversion rate.
5. **The North Star counts delivered value, not activity.** Logins are activity;
   completed workflows are value. If in doubt: would the customer's CFO recognize it as
   the thing they pay for?

## The counter-metric rule

Every metric with a target attached (anything incentivized, reviewed, or bonused) gets a
named counter-metric watched alongside it. This prevents Goodharting — hitting the number
by breaking the thing the number was a proxy for.

| If you target... | Guard it with... |
|---|---|
| Support deflection % | CSAT / repeat-contact rate within 7 days |
| Response speed | Resolution accuracy / reopen rate |
| Pipeline created | Win rate / pipeline-to-close conversion |
| Signups | Activation rate |
| Feature velocity | Defect escape rate / rollback count |
| Cost per X | Quality-of-X metric |

The counter-metric appears in the same dashboard tile / WBR chart as its primary, never
on a separate page. No vanity metrics anywhere in exec material — cumulative charts
("total signups ever") only go up and inform no decision; ban them.

## Exec dashboard spec

- **One screen.** If it scrolls, it's a report, not a dashboard.
- **Outcome metrics only** (Level 1). Drivers live in the WBR; diagnostics live in the
  BI tool behind a documented drill path.
- Every number shows: current value, **vs target**, **vs prior period**, a trend
  sparkline, and RAG status (Red/Amber/Green with numeric thresholds written down —
  "red = >10% below plan", never vibes).
- **Freshness timestamp** on the dashboard. A stale dashboard is worse than none.
- Each tile names its owner and its counter-metric.
- Anti-pattern to refuse: the 40-tile "everything dashboard." That is wallpaper.
  Cap at ~8–10 tiles; fight for every addition.

## WBR (Weekly Business Review) mechanics — Amazon-style, right-sized

The two disciplines that make a WBR work, at any size:
1. **Same format, same order, every single week.** Consistency is the anomaly-detection
   mechanism — a human scanning a familiar page spots the weird line in seconds.
2. **Variance explanations are written BEFORE the meeting.** The meeting discusses
   exceptions; it never watches someone discover their own numbers live.

Structure:
- **Page 1 — scorecard:** Level 1 outcomes vs plan and vs prior year, RAG.
- **Pages 2–n — one chart per driver:** trailing 6-week AND trailing 12-month views on
  the same chart, vs plan and prior year. Owner annotates any variance beyond the agreed
  threshold (default ±10% vs plan) in writing, in advance.
- **Final page — exceptions:** each red metric gets cause + action + owner + date.
  Plus **last week's action list with statuses — reviewed FIRST in the meeting.**
  Follow-through is the entire point; same metric red 4 weeks with the same explanation
  is an escalation failure, and the skill says so.
- Owners speak only to exceptions. Green metrics get zero airtime.

Right-sizing (Prime Directive 3):
| Company size | WBR shape |
|---|---|
| <30 people | ONE page, 10–20 charts, 30 minutes, weekly. No deck. |
| 30–100 | 3–5 pages, 45 min, driver owners present their own variances |
| >100 | Full deck per function + monthly MBR layer |

Under ~10 people, a WBR may be async: the page is written and commented, no meeting.
Keep the two disciplines regardless.

## Build order for a metrics engagement

1. Fix the disputed numbers first — dictionary entries for any metric two teams compute
   differently.
2. KPI tree (Level 1 + Level 2 with owners).
3. Dictionary entries for everything in the tree.
4. Dashboard spec, then WBR template pre-filled with the tree's drivers.
5. Hand off with the human to-do: owners accept their metrics by name; RAG thresholds
   agreed; first WBR scheduled.
