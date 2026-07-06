# Playbook: Driver-Based SaaS Operating Model (tab-by-tab spec + build guide)

The `--model` artifact is a **specification the user implements in a spreadsheet**, plus a
ready-to-import Assumptions CSV. Every tab below gets: purpose, column layout, row-by-row
formula logic (described so it translates to Excel or Google Sheets), and its sanity checks.

## Conventions (state these in the spec's README tab)

- **Blue = input, black = formula.** No hardcoded numbers inside formulas — every constant
  lives on the Assumptions tab and is referenced.
- **Monthly columns × 24 months**, then annual for years 3–5. One column per period, periods
  only ever go left→right.
- **Three scenarios (Base / Upside / Downside) via ONE toggle cell** on Assumptions; scenario
  deltas live in a small block (e.g. churn multiplier, new-logo multiplier, DSO add-on), and
  driver rows read `=CHOOSE(toggle, base, upside, downside)`. Never three copies of the model.
- No circular references. If a formula needs last period's output, reference the prior column,
  never the same column.
- Every metric formula documented on the Metrics tab in a text column next to the number.

## Build order and tabs

Build in this order — each tab reads only from tabs above it:

1. **README** — conventions, color key, scenario toggle location, changelog.
2. **Assumptions** — every input in one place (see driver catalog below).
3. **Headcount** — roster drives ~70–80% of startup opex.
4. **Revenue build** — bookings → ARR → recognized revenue → deferred revenue.
5. **OpEx** — by department, headcount + non-headcount.
6. **P&L** — revenue − COGS = gross profit; opex by function; operating income.
7. **Balance Sheet** — working capital is where SaaS models break.
8. **Cash Flow** — indirect method; ending cash MUST equal BS cash.
9. **Metrics** — all SaaS metrics with formulas (definitions per `metrics.md`).
10. **Scenarios** — side-by-side outputs of the three cases (ARR, burn, zero-cash date).
11. **Cap table** — current fully diluted + next-round dilution scenarios (method in
    `fundraise.md`).

## Driver catalog (Assumptions tab — the interview checklist)

Group by section; each row = driver, unit, source tag (USER / REPO / ASSUMED / BENCHMARK-src-yr).

**Sales & revenue drivers**
- New logos per month, by segment (self-serve / SMB / mid-market / enterprise as applicable)
- ACV (annual contract value) per segment; pricing tiers and mix
- Sales cycle length per segment (months) — lags bookings behind pipeline
- Rep count by start month; quota per ramped rep; ramp curve (e.g. 0%/33%/66%/100% over 4
  months) — **ramp-adjusted quota capacity is the ceiling on bookings; a model whose bookings
  exceed it is fiction**
- Pipeline coverage assumption (3–4x is standard); win rate
- Gross churn (monthly or annual — record which and convert explicitly)
- Expansion rate (same-cohort upsell %, monthly or annual)
- Billing terms mix: % annual-upfront vs. monthly (drives deferred revenue and cash timing)

**Cost drivers**
- Headcount plan: role, department, start month, base salary
- Fully-loaded multiplier: salary × 1.25–1.4 (taxes, benefits, equipment, software)
- Commission % of new + expansion bookings (accrue when booked; note ASC 340-40
  capitalization if material — flag for CPA)
- Hosting/COGS as % of revenue (must scale with usage — a flat dollar amount is a red flag)
- Support & DevOps allocation to COGS (people who serve customers, not build product)
- Non-headcount opex by department: tools, marketing programs, rent, insurance, legal/audit

**Working capital & cash drivers**
- DSO (days sales outstanding) for invoiced revenue
- Prepaid expenses and amortization schedule
- Payroll timing; annual vendor renewals (month + amount); bonus accrual
- Starting cash; any debt (rate, covenants — covenants escalate to human review)

**Scenario block** — Downside is NOT base −10%. Set simultaneously: churn multiplier up
(e.g. 1.5×), new-logo multiplier down (e.g. 0.7×), sales cycle +1 month, DSO +15 days.
Upside symmetric but modest.

## Tab specs

### Headcount
One row per hire (current + planned). Columns: name/req, role, dept (COGS/S&M/R&D/G&A),
start month, base salary, loaded cost = base × multiplier / 12 per active month. Monthly cost
row per department = SUMIFS over active hires. Sanity: revenue per employee at month 24 within
$150–300K annualized (verify current benchmark via WebSearch — these date fast).

### Revenue build (the heart — 5 stacked blocks, one row-group per segment)
1. **Bookings**: new logos × ACV, capped at ramp-adjusted rep capacity for sales-led
   segments; self-serve from funnel drivers instead.
2. **ARR walk**: beginning ARR + new + expansion − contraction − churned = ending ARR.
   Churned = beginning × gross churn rate; expansion = beginning × expansion rate. This block
   IS the ARR waterfall the board sees.
3. **Recognized (GAAP) revenue**: ARR ÷ 12 recognized ratably from contract start —
   bookings are NOT revenue; a contract signed on the 20th recognizes a partial month if you
   want that precision, otherwise state the start-of-month simplification.
4. **Billings & deferred revenue**: annual-upfront contracts bill 12 months at start →
   deferred revenue = billings − recognized, rolled forward (beginning + billings −
   recognized = ending). Monthly contracts bill = recognize.
5. **Cash collections**: billings shifted by DSO.

### OpEx
By department: headcount cost (from Headcount) + non-headcount lines. COGS = hosting +
support/DevOps allocation. Everything else S&M / R&D / G&A. Commission expense accrued in the
booking month.

### P&L
Revenue − COGS = gross profit (pure SaaS target 75–85% gross margin) → opex by function →
operating income → (interest) → net income. A gross margin above 90% usually means hosting or
support is hiding in opex — check.

### Balance Sheet
Cash (from CF tab), AR = trailing billings not yet collected (DSO-driven), prepaids, fixed
assets (usually immaterial — say so) | AP, accrued payroll/bonus/commissions, **deferred
revenue** (from revenue build), debt | equity = prior equity + net income + raises.
**Check row on every period: Assets − Liabilities − Equity = 0.** A model shipped with a
non-zero check row is wrong, not "almost done."

### Cash Flow (indirect)
Net income + non-cash items ± working capital deltas (ΔAR, Δdeferred revenue — annual prepay
is a cash-flow ASSET, Δprepaids, Δaccruals) = operating CF; investing; financing (raises,
debt). **Ending cash must equal BS cash every period — this is the #1 mechanical gate.**

### Metrics
Compute from the tabs above using the canonical definitions in `metrics.md` — never re-derive
a metric from different inputs than the definition states. Include: ARR + growth, gross/net
burn, runway (3-mo avg), NRR/GRR, CAC, CAC payback, LTV:CAC, Rule of 40, burn multiple, magic
number, gross margin, revenue per employee.

### Scenarios
Toggle-driven summary: for each case — ending ARR (mo 12/24), total burn, zero-cash date,
headcount supported. The downside zero-cash date is the number the founder plans around.

## Assumptions CSV (emit with the artifact)

Write `docs/enterprise/finance/model-assumptions-<date>.csv` with columns:
`section,driver,value,unit,scenario_base,scenario_upside,scenario_downside,source,notes`
— one row per driver from the catalog, values from the interview. This imports directly as
the Assumptions tab.

## Sanity checks (run against the spec's implied outputs; print PASS/FAIL/N-A + evidence)

1. BS balances every period; CF ending cash = BS cash; no plugs, no circular refs.
2. Sensitivity: ±20% on one driver (e.g. churn) moves outputs in the right direction and
   plausible magnitude.
3. Growth decelerates with scale — flat 15% MoM for 36 months is an auto-reject.
4. Implied rep productivity ≤ ramp-adjusted quota capacity.
5. Revenue per employee trends into $150–300K annualized by month 24 (verify benchmark).
6. Churn assumption reconciles with actual cohort history; if history <12 months, label the
   churn driver LOW CONFIDENCE.
7. Hosting COGS scales with usage/revenue, not flat.
8. Commissions accrued when booked; deferred revenue moves opposite to annual-prepay mix.
9. S&M % of revenue vs. growth rate is coherent (Rule of 40 lens).
10. Downside case satisfies conservatism asymmetry (three levers moved together).
