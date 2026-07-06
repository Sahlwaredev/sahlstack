# Playbook: Market Category & TAM (--market)

Maya and Noor's reference for the category decision, bottom-up sizing, and the trends
layer. Output artifact: `market-category-tam-<date>.md`.

## 1. The category decision (Maya)

The market category is the frame of reference that makes the product's value obvious —
the mental shelf the buyer puts you on, which sets who you're compared to and what you
can charge. Three options, in rising order of risk:

| Option | What it means | When it's right | Cost/risk |
|--------|---------------|-----------------|-----------|
| **Existing category** | Enter a shelf buyers already budget for | Buyers search for it; incumbents are beatable on a dimension we own | Compared to incumbents feature-by-feature; must win a "why switch" argument |
| **Subsegment** | "X, but for <segment/situation>" | The big category underserves a specific buyer we can dominate | Smaller initial TAM; must resist pressure to blur back into the parent category |
| **New category** | Teach the market a new shelf exists | Rare — see preconditions | Highest cost: you fund the education; usually wrong for startups |

**New-category preconditions (all three, in writing, before recommending it):**
1. The best customers genuinely cannot describe the product in any existing category's
   words (evidence: their verbatim language from calls/reviews).
2. Funding and time horizon support 2+ years of category education spend.
3. Winning the existing category or a subsegment is provably not available (an
   incumbent owns the exact dimension we'd differentiate on).

If any precondition fails → recommend existing category or subsegment. Say which and why.

**Decision output format:**

```markdown
## Category decision

CHOSEN: <category name> (<existing | subsegment | new>)
BECAUSE: <2-3 sentences: the frame that makes our value obvious, with the buyer
evidence>
REJECTED: <each alternative frame> — <one line why>
COMPARED-TO SET THIS IMPLIES: <who buyers will now benchmark us against>
WHAT WOULD CHANGE THIS CALL: <the evidence that would reopen the decision>
```

The category decision feeds `/marketing`'s positioning canvas (Dunford step 7) — record
the handoff in the artifact.

## 2. Bottom-up TAM / SAM / SOM (Noor)

**Iron law: bottom-up only.** "1% of a $50B Gartner market" is banned. Every number is
countable-units × realistic-price, with the arithmetic shown and every count sourced
and dated. Analyst top-down numbers may appear ONLY as a sanity cross-check, labeled
as such.

Definitions (state them in the artifact; they get misused constantly):
- **TAM** — total addressable market: everyone who could ever buy this product category.
- **SAM** — serviceable addressable market: the slice reachable with THIS product,
  motion, geography, and language, today.
- **SOM** — serviceable obtainable market: the realistic 3-year share of SAM, with the
  assumptions that produce it stated.

**Template (fill every line; show the math):**

```markdown
## TAM (bottom-up)

Unit of purchase: <company | team | seat | workload — pick the one that pays>
Countable population: <N> <units> (source: <url/method>, checked <date>)
  Counting method: <e.g. "LinkedIn: companies 11-200 employees in <industry>, US+EU"
  or "industry association registry" — show the query>
Realistic annual price: $<ACV> (basis: <pricing artifact | comparable competitor entry
  price, sourced>)
TAM = <N> × $<ACV> = $<X>/yr

## SAM

Filters applied to TAM population (each with the fraction and its basis):
  - <e.g. English-language product → ×0.6 (source)>
  - <e.g. requires <tech stack> → ×0.4 (source: job-posting/tech-install counts)>
  - <e.g. motion reaches only self-serve buyers → ×0.7 (assumption, flagged)>
SAM = <N'> units × $<ACV> = $<Y>/yr

## SOM (3-year)

Assumptions: <win rate on in-market buyers, ramp, churn — each stated>
SOM = $<Z>/yr by <year>
Sanity checks:
  - Implied customers by year 3: <n> — plausible at <n/36> new customers/month? <yes/no>
  - Cross-check vs analyst top-down (label only): <number, source, date>
  - Revenue per employee implied: <check vs $150-300K SaaS benchmark — verify current
    benchmark via WebSearch, these date fast>
```

**The in-market number (95:5 rule).** Ehrenberg-Bass: roughly 95% of a category's
buyers are out-of-market at any given time; only ~5% are actively buying. Compute
`SAM units × ~5% ÷ 4` = plausibly in-market buyers per quarter, and state it. This is
the ceiling on near-term capture and the number the growth model (`--growth`) consumes.
If that number is under ~50 buyers/quarter, say plainly: this is a patient,
relationship-driven market — a paid-acquisition growth plan would be spending against
people who cannot buy yet.

## 3. Trends layer (Maya)

Trends earn a place only if genuinely connected to the value prop. Max 3. Format each:

- **Trend:** <named, specific — "SOC 2 required in mid-market procurement", not "AI">
  **Evidence:** <source, checked date>
  **So what for us:** <the concrete way it enlarges SAM, shortens sales cycles, or
  weakens an incumbent — one of those three, or cut it>

Trend-surfing (attaching to a hot trend with no causal link) is a named failure mode —
Amir checks for it in Phase 4.

## 4. Quality bar (self-check before Phase 4)

- [ ] Category decision uses the format, names rejections, and states the reopen trigger
- [ ] If new category: all three preconditions shown met with evidence
- [ ] Zero top-down sizing; every count sourced + dated; arithmetic reproducible
- [ ] SAM filters each carry a basis (source or flagged assumption)
- [ ] SOM sanity checks run, including implied customers/month
- [ ] In-market-per-quarter number computed and stated
- [ ] Each trend has evidence and a concrete "so what"; max 3
