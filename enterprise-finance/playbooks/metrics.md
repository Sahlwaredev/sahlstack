# Playbook: Canonical SaaS Metric Definitions + KPI Page

These are THE definitions. Every `/finance` artifact uses these, states them inline, and never
lets two artifacts carry two versions of the same metric. When the user's existing definition
differs, record theirs, recommend the canonical one, and get an explicit decision — then that
decision is binding everywhere.

Benchmark ranges below are encoded as of the 2024–2025 benchmark cycle. **Verify current
benchmarks via WebSearch before publishing — these date fast.** Sources to search: Bessemer
(State of the Cloud / Cloud 100), a16z growth guides, KeyBanc/Sapphire SaaS survey,
OpenView/High Alpha SaaS Benchmarks, Benchmarkit, RevOps Squared. Cite source + year next to
every benchmark you print.

## The three revenue concepts (never interchangeable)

| Concept | Definition | What it is NOT |
|---------|-----------|----------------|
| **Bookings** | Total contract value (TCV) signed in the period | Not ARR (a 3-year $300K deal is $300K bookings, $100K ARR); not revenue |
| **ARR** | Annualized recurring run-rate at a point in time. Excludes services, one-time fees, non-recurring items | Not bookings; not GAAP revenue; MRR×12 is a snapshot, not "annual revenue" |
| **Revenue (GAAP)** | Recognized ratably over the service period (ASC 606) | Not cash collected; annual-prepay cash ≠ revenue |

**CARR vs. live ARR:** contracted ARR includes signed-not-live deals; live ARR only what's
deployed/billing. Either is defensible — **undefined mixing of the two is not.** Pick one,
label it, keep it.

## Unit economics

- **ARPA** = ARR ÷ active customer count. State which customer count (paying accounts, not
  logos with free plans). Monthly ARPA = ARPA ÷ 12.
- **Gross margin** = (revenue − COGS) ÷ revenue. COGS = hosting + support + DevOps share.
  Pure-SaaS healthy range: **75–85%**. Hosting sitting in opex overstates this — check.
- **CAC** = fully-loaded S&M cost ÷ new customers acquired in period. Fully-loaded = salaries
  + commissions + programs + tools. **Specify blended vs. paid-only**, and never blend PLG and
  enterprise motions into one CAC — segment it.
- **CAC payback (months)** = CAC ÷ (new-customer monthly ARPA × gross margin). 2025 median
  ≈ **15 months**; **<12 strong**; >24 alarming (verify current).
- **LTV** = ARPA × gross margin ÷ gross dollar churn rate (annual ARPA with annual churn, or
  monthly with monthly — same units, say which). **LTV:CAC ≥ 3:1** target.
  **Iron rule: with <12 months of churn history, LTV is unreliable — compute it if asked, but
  label it UNRELIABLE — <12MO CHURN HISTORY. An expert says so; so do we.**

## Retention

- **NRR (net revenue retention)** — revenue kept plus expansion from existing customers:
  (starting cohort ARR + expansion − contraction − churn) ÷ starting cohort ARR, trailing
  12 months, cohort-based (only customers who existed at period start).
  Benchmarks: SMB **~95–105%**; mid-market/enterprise **105–120%+** (verify current).
- **GRR (gross revenue retention)** — same formula WITHOUT expansion, capped at 100%.
  Measures pure retention. **Report both, always** — NRR alone can hide churn behind a few
  big expansions.
- **Logo churn vs. dollar churn** — different denominators; small-logo churn with dollar
  retention intact is a different problem than enterprise dollar churn. Report dollar churn
  for economics, logo churn for product signal.

## Efficiency

- **Rule of 40** = ARR growth % + FCF margin % (or EBITDA margin — **specify which** and keep
  it fixed). ≥40 is the classic bar; weight growth heavier pre-$10M ARR.
- **Burn multiple** (Sacks) = net burn ÷ net new ARR, same period. **<1x elite; 1–1.5x good;
  1.5–2x mediocre; >2x alarming at Series A+.** Top VC screening metric — compute it in every
  metrics/board artifact once the company is post-revenue.
- **Magic number** = (quarterly recognized revenue − prior quarter's) × 4 ÷ prior quarter S&M.
  ARR variant: net new ARR in quarter ÷ prior quarter S&M — no ×4, ARR is already annualized.
  **State which variant.** >1 = pour fuel on the motion; **0.5–0.75 = examine before scaling**;
  <0.5 = the GTM engine is broken, fix before hiring reps.

## Burn & runway

- **Gross burn** = total cash out per month. **Net burn** = cash out − cash in (collections,
  not bookings).
- Both computed on a **3-month average — never a single month**. One good collections month
  is not a trend.
- **Runway (months)** = cash ÷ 3-month average net burn. Zero-cash date under base AND
  downside. **Fundraise-by date** = zero-cash − 6–9 months.
- **DSO** = accounts receivable ÷ billings × days in period. Rising DSO eats runway silently.

## KPI page template (the `--metrics` deliverable)

```markdown
# KPI Page — <company> — <date>
> Definitions: canonical per /finance metrics playbook. ARR basis: <live | CARR — as decided>.
> Data sources: <billing export / model / bank statements>, as of <date>.

| Metric | Value | Definition used (one line) | Benchmark (source, yr) | Verdict | Trend |
|--------|-------|----------------------------|------------------------|---------|-------|
| ARR / growth % | | | | 🟢/🟡/🔴 | ↑/→/↓ |
| NRR / GRR | | | | | |
| Gross margin | | | | | |
| CAC / CAC payback | | | | | |
| LTV:CAC | | (flag if <12mo churn history) | | | |
| Burn multiple | | | | | |
| Magic number | | (state variant) | | | |
| Rule of 40 | | (state FCF vs EBITDA) | | | |
| Net burn / runway | | (3-mo avg) | n/a | | |
| Revenue per employee | | | $150–300K (verify) | | |

## Computations (show every one: inputs → formula → result)
## NOT COMPUTABLE (metric → missing input → how to capture it)
## Definition decisions made this run (and where they now bind)
```

Rules: a metric with missing inputs is `NOT COMPUTABLE`, never an estimate dressed as a
computation. Every benchmark cell cites source + year and carries the "verify current" flag.
Verdicts are decisive — 🟡 requires a one-line "what turns this green."
