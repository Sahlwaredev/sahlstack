# Compensation Playbook — leveling, bands, equity, philosophy

Reference for `/people --comp`. The goal state: every offer is a lookup, not a negotiation.
No bands → ad hoc offers → compression and inequity that is expensive to remediate later.

## 1. Job architecture (P/M leveling)

Two tracks, explicitly parallel so management is not the only promotion path:

| IC track | Management track | Scope anchor |
|----------|------------------|--------------|
| P1 — Entry | — | Executes well-defined tasks with guidance |
| P2 — Developing | — | Owns tasks end-to-end; needs direction on approach |
| P3 — Career | — | Owns projects; independent within team scope |
| P4 — Senior | M3 — Manager | Owns problem areas; influences team direction / manages a team |
| P5 — Staff | M4 — Senior Manager | Cross-team scope; sets technical/functional direction |
| P6 — Principal | M5 — Director | Org-level scope; company-critical bets |
| — | M6 — VP | Function-level ownership |

Level dimensions (rate each level against all four; these are the anchors, not titles):
1. **Scope** — task → project → problem area → cross-team → org
2. **Autonomy** — needs direction → independent → sets direction for others
3. **Complexity** — well-defined → ambiguous → undefined/novel
4. **Influence** — self → team → cross-team → company

Right-size to stage:
- Under ~20 people: 3–4 levels total (e.g. P2/P3/P4 + one manager level). More is theater.
- 20–50: introduce the full P1–P5 spine; M3–M4.
- 50+: full architecture, written per-level expectations per function.

**Mapping caveat (write it down):** vendor levels are not interchangeable — Pave P4 ≠
Radford L4 ≠ levels.fyi L4. The architecture doc must include an explicit mapping table from
company levels to each benchmark source used. References: Radford job-leveling, Pave levels,
public ladders (levels.fyi, progression.fyi, Dropbox and GitLab public frameworks).

## 2. Benchmark data sources (state the bias)

| Source | Nature | Bias / caveat |
|--------|--------|---------------|
| Pave, Ravio | Real-time, HRIS-derived | Tech-skewed; best for venture-backed software |
| Carta Total Comp | Startup cap-table-derived | Startup-specific; good equity data |
| Radford, Mercer | Survey-based, rigorous | 6–12 months stale; enterprise-skewed |
| levels.fyi, public ladders | Self-reported | Big-tech-skewed, unverified; directional only |

If the company has no paid source: build from public data via WebSearch, and mark every band
`VERIFY BEFORE USE IN OFFERS`. Never fabricate a number; never present a stale or public
number as authoritative. Benchmark refresh: annually minimum, plus after any repricing event
in the market segment.

## 3. Band construction

Per level × job family × geo:

```
Band = midpoint ± width
  Midpoint  = target percentile of benchmark data for level×family×geo
  Width     = ±10% junior levels, up to ±15% senior (senior skills vary more)
  Overlap   = adjacent bands overlap 30–50% (a strong P3 can out-earn a new P4 — that is correct)
```

Positioning within band (give managers the rule):
- Bottom third: new to level, meets some expectations
- Middle third: fully performing at level (the default for a solid hire)
- Top third: exceeding, approaching promotion — if someone sits at top-of-band for 2+ cycles,
  the question is promotion, not another raise

Target percentile posture (pick and write down):
- Common startup default: **50th percentile cash / 75th percentile equity** — pay market cash,
  win on upside. Fits most seed–Series B companies.
- Cash-rich alternative: 75th cash for critical families only (state which and why).
- Never "we pay top of market" without data — that phrase in a philosophy doc with 50th
  percentile bands is the credibility killer.

Geo strategy (pick one, document rationale):
1. **Single national band** — simplest, most defensible, costs most. Recommended under ~20
   people: the admin savings outweigh the payroll premium.
2. **Tiered zones** — 2–3 tiers (e.g. Tier 1 = SF/NYC/Seattle at 100%, Tier 2 = 90%,
   Tier 3 = 80%). The startup workhorse at 20–100 people.
3. **Location-based** — per-metro pricing. Cheapest, highest admin cost, hardest to explain.

## 4. Equity grant matrix

```markdown
| Level | New-hire grant | Refresh guideline |
|-------|----------------|-------------------|
| P2    | <$ value or % of FD shares> | ~25% of new-hire grant / yr, from yr 2–3 |
| P3    | ... | ... |
...
```

Rules:
- State the denomination: **$ value via the latest 409A** (preferred once a 409A exists — it
  survives dilution math) or **% of fully-diluted shares** (early stage). Never mix silently.
- Standard vesting: 4 years, 1-year cliff, monthly thereafter. Deviations are exceptions with
  written rationale.
- Refresh grants: begin year 2–3, target ~25% of the current new-hire grant for the level
  annually, weighted by performance. Model the pool burn: new-hire grants + refreshes vs. pool
  remaining; flag when the pool needs a top-up (a board/dilution event).
- Two policy decisions to force explicitly (both counsel-adjacent):
  1. **Early exercise** allowed? (83(b) upside for employees; admin burden for the company.)
  2. **Post-termination exercise window**: 90-day standard vs. extended (employee-friendly;
     converts ISOs to NSOs after 90 days — disclose this).
- Equity communication kit ships with the matrix: what an option is, ISO vs. NSO in plain
  language, what the 90-day window means, what taxes can hit at exercise. Failure to explain
  this is a top-5 startup equity failure. Never state or promise a strike price.

## 5. Comp philosophy doc structure (one page)

```markdown
# Compensation Philosophy — <Company>
Last reviewed: <date>

1. Objectives — what comp must achieve (attract at our stage, retain through
   vesting, be explainable in one sentence to any employee).
2. Market definition — comparator set (stage, sector, geo), data sources used,
   the level-mapping table, refresh cadence (annual minimum).
3. Target position — percentile by element (cash / equity / benefits) and why.
4. Geo strategy — which model and the rationale.
5. Band architecture — levels × families × geos covered; width and overlap rules.
6. Transparency posture — what employees can see: philosophy only / own band /
   all bands. (Posting ranges is already law in several states — decide how far
   past the legal floor to go, and be consistent.)
7. Exception governance — who can approve out-of-band, written rationale
   required, logged in the exception register, reviewed quarterly. An exception
   without an expiry and a remediation plan is just inequity with paperwork.
8. Equity philosophy — matrix denomination, refresh approach, the two policy
   decisions (early exercise, exercise window).
9. Review cadence — annual benchmark refresh; comp review cycle linkage.
```

## 6. Pay-equity check (run with every banding exercise)

1. Table every employee: level, role family, geo, tenure, performance rating, base, equity.
2. Within each level×family×geo cell: flag any gap >5% not explained by tenure, performance,
   or a logged exception.
3. At 50+ employees: run a regression of comp on level/tenure/location/performance; any
   residual gap correlated with a protected characteristic is a BLOCKING finding →
   remediation plan (raise the underpaid; never cut the overpaid) + counsel review.
4. Compression check when new bands land: list everyone below their new band with the cost to
   bring them in. Present it as a one-time remediation budget with a deadline — dragging it
   out multiplies both cost and risk.

Output artifacts and review gates: architecture + bands + philosophy → `Human review
recommended`; anything feeding a pay-equity remediation or classification change →
`Licensed professional required (employment attorney)`.
