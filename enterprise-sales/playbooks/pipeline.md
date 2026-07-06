# Pipeline System — stages, MEDDPICC rubric, forecast, MAP, business case

The reference for `--pipeline` and `--deal`, and the source of the stage/qualification
sections in `--playbook`. Context worth stating in artifacts: most orgs admit less than half
their CRM data is accurate, and only a small minority of teams exceed 90% forecast accuracy
(median 70–79%) — verify current benchmarks via WebSearch; these date fast.

## 1. Canonical pipeline stages with buyer-verified exit criteria

The rule that fixes happy-ears pipeline: **every exit criterion is a verifiable buyer
action, never a rep opinion.** "They're really interested" is not a criterion; "next meeting
booked with the economic buyer, invite accepted" is.

| # | Stage | Exit criteria (ALL required to advance) |
|---|-------|------------------------------------------|
| 1 | Prospecting / Identified | Account fits ICP tier 1–2 AND a live signal exists |
| 2 | Discovery / Qualifying | Pain stated by the buyer with a cost figure; initial MEDDPICC fields filled; next meeting booked with power (invite accepted) |
| 3 | Evaluation / Demo / POC | Technical validation done (demo mapped to pain, or POC passed its written success criteria); decision criteria confirmed by the buyer in writing; champion identified |
| 4 | Business case / Proposal | Economic buyer engaged (met, not just named); ROI/business case presented; mutual action plan agreed with the buyer |
| 5 | Negotiation / Procurement | Legal + security review in motion; redlines resolved or scheduled; verbal commit received |
| 6 | Closed-won / Closed-lost | Signature — or a loss reason from the taxonomy (below) |

Right-sizing: founder-led motions collapse to 4 stages (Discovery → Evaluation → Proposal →
Closed) — keep the same buyer-verified exit discipline. Close dates come from the buyer's
stated process, never from quarter-end hope.

**Loss reason taxonomy (mandatory at stage 6):** lost-to-competitor (name them),
lost-to-status-quo/no-decision, lost-on-price, lost-on-product-gap (name it),
lost-on-timing, lost-on-champion-departure, disqualified-bad-fit. "Price" requires one
sentence of evidence — it is the universal excuse and usually wrong.

## 2. MEDDPICC — field definitions and 0–3 scoring rubric

Rigorously applied MEDDPICC correlates with materially higher win rates (studies cite
18–24% — verify via WebSearch). Score every deal above the materiality line; deal reviews
interrogate the LOWEST scores, not the deal story.

Scoring scale (applies to every element):
**0** = unknown / not started · **1** = rep's belief, no buyer evidence ·
**2** = buyer-confirmed verbally · **3** = buyer-confirmed with evidence in writing/action.

| Element | What it is | What a 3 looks like | Killer test |
|---------|-----------|---------------------|-------------|
| **M**etrics | The quantified business outcome the buyer expects | Buyer's own number in an email/deck ("cut close time from 9 days to 3") | Can your champion recite it unprompted? |
| **E**conomic Buyer | The person with budget veto/discretion | You've met them; you know their personal win; they've stated support | Have we met the EB, or only heard about them? |
| **D**ecision Criteria | The requirements list they'll judge on | Written criteria you helped shape before competitors did | Did we influence/co-author it, or just receive it? |
| **D**ecision Process | Steps, evaluators, dates from evaluation → signature | Process mapped and confirmed by the buyer in writing | Do we know the date of each remaining step? |
| **P**aper Process | Legal, security review, procurement, signature chain | Named contacts, known SLAs, security questionnaire in hand | Mapped by mid-funnel? (#1 cause of slipped quarter-end deals) |
| **I**dentify Pain | The concrete pain with cost of inaction | Pain quantified in buyer's words with a monthly/annual cost | No quantified pain = no deal, whatever the enthusiasm |
| **C**hampion | Power + personal motivation, sells internally for you | Passed the champion test: given a task (e.g. book the EB meeting) and did it | If they can't/won't do a task, they're a coach, not a champion |
| **C**ompetition | Every alternative incl. "build" and "do nothing" | Known evaluation set; our traps set; their landmines defused | What does the buyer do if they pick nobody? |

**Deal-review protocol:** total 0–24. Sort review time by (deal amount × number of elements
≤1). Single-threaded deals (one buyer contact) are auto-flagged regardless of score.

## 3. Forecast categories — evidence standards

Category is justified by MEDDPICC completeness, not optimism:

| Category | Evidence standard |
|----------|-------------------|
| Pipeline | Stage ≥2; pain identified (I ≥2) |
| Best Case | Stage ≥3; M, I ≥2; champion identified (C ≥1); close date buyer-sourced |
| Commit | EB engaged (E ≥2) AND paper process mapped (P ≥2) AND champion tested (Ch = 3) AND MAP dates holding |
| Closed | Signature. Nothing else. Verbal commit is Commit, not Closed |

Forecast review outputs: category-by-category walk with the evidence standard applied deal
by deal; the delta between rep-stated and evidence-based categories; slipped-deal analysis
(which element was weak — it's usually P); trailing forecast-vs-actual accuracy once ≥2
quarters of history exist.

**Coverage math:** pipeline ÷ next-period target, overall and by segment. B2B SaaS target:
4–5x, quality-weighted — discount stale (no activity 14+ days) and single-threaded deals by
50% in the weighted view, and show both raw and weighted coverage.

**Hygiene flags (run on every deal):** close date in the past · no activity 14+ days ·
close date = last day of quarter with no buyer-sourced basis · single-threaded · amount
missing or default · stage regression without a note · created >2× median cycle length ago.
Gate: >10% of pipeline stale fails the hygiene gate.

## 4. Mutual Action Plan (MAP) template — buyer-facing

The single best slipped-deal detector: a shared doc where a buyer letting dates slip tells
you the truth long before the forecast call does. Written in the buyer's language, shared
from stage 3 onward, updated after every call.

```
# Mutual Action Plan — <Buyer company> + <Your company>
Goal: <the buyer's outcome in the buyer's words>
Target go-live: <date, buyer-sourced>

| # | Workstream | Step | Owner (buyer side) | Owner (our side) | Due | Status |
|---|-----------|------|--------------------|------------------|-----|--------|
| 1 | Evaluation | Demo to eval team / POC per success criteria | | | | |
| 2 | Evaluation | Decision-criteria review vs results | | | | |
| 3 | Security | Questionnaire + review | | | | |
| 4 | Legal | Contract redlines | | | | |
| 5 | Procurement | Vendor onboarding, PO | | | | |
| 6 | Signature | Signatory: <name> | | | | |
| 7 | Kickoff | Implementation start | | | | |

## Decision criteria checklist
- [ ] <criterion 1 — from the buyer's written criteria>

## Risks / slip notes
- <dated notes when any date moves, with the stated reason>
```

Rule: a MAP where the buyer has no owner names on their side isn't mutual — it's your
wishlist. Flag it.

## 5. Business case / ROI doc structure (for the economic buyer)

1. **Current state cost** — quantified from discovery, in the buyer's own figures. Every
   number cites where it came from ("stated by <champion>, <date> call"). Gaps are marked
   `[NEEDED FROM DISCOVERY]`, never invented.
2. **Future state** — the metrics that change and by how much, tied to the buyer's stated
   Metrics element. Conservative/expected ranges, not a single rosy point.
3. **Investment & payback** — price, implementation effort, time-to-value; payback period
   in months. Show the arithmetic.
4. **Risk mitigation** — what could go wrong in adoption and what contains it (pilot scope,
   success criteria, support model).
5. **Decision timeline alignment** — mirrors the MAP dates; ties cost-of-delay to the
   current-state cost per month from section 1 (honest urgency, not manufactured).

One page if possible. The EB reads the first table and the payback line; everything else is
backup.
