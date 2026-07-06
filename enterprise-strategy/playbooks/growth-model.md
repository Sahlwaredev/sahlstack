# Playbook: Growth Model (--growth)

Noor's reference for motion selection, the north-star metrics tree, and the AARRR leak
analysis. Output artifact: `growth-model-<date>.md`.

Benchmark rule: every numeric benchmark in this playbook dates fast. When citing one in
an artifact, either verify it via WebSearch (and date it) or append
`(verify — benchmark dates fast)`.

## 1. Motion selection

The motion must match the ACV (annual contract value — the yearly price of one
customer). Getting this wrong is fatal in both directions: an enterprise sales team
selling a $5K product burns CAC > LTV; pure self-serve for a $100K security product
ignores the buying committee that actually decides.

| Motion | Fits when | Funnel shape | Cost structure |
|--------|-----------|--------------|----------------|
| **PLG / self-serve** | ACV <$10K; single-player-capable; time-to-value < one session | signup → activation → habit → PQL → convert/expand | product + content; near-zero marginal sales cost |
| **Sales-led** | ACV >$25K; multi-stakeholder committee; security/procurement complexity | lead → qualified mtg → eval/POC → proposal → close | reps + SEs; CAC payback must clear the math below |
| **Hybrid (2026 default)** | ACV in between, or PLG product with team/enterprise expansion | self-serve foundation + sales-assist on PQLs + enterprise overlay | staged: product qualifies, humans close the complex |

Design rule for hybrid: **let the product qualify, let humans close the complex.**
Hybrid companies hit NRR targets more often than pure-PLG (67% vs 58% — verify,
benchmark dates fast).

**PQL note.** A PQL (product-qualified lead — an account whose product behavior predicts
purchase) converts far better than an MQL (marketing-qualified lead): roughly 25–39% vs
5–10% (verify — dates fast). If the motion is PLG or hybrid, the model MUST define the
PQL: the specific product behaviors + thresholds, e.g. "3+ users active in week 1 AND
hit the integration step". If activation is unvalidated, defining the PQL is a play,
not a given.

**Output format:**

```markdown
## Motion decision

CHOSEN: <PLG | sales-led | hybrid>
ACV MATH: ACV $<x> — <why the motion's cost structure clears at this ACV>
BOTH-WAYS CHECK: <one line each on why not the other two motions>
PQL DEFINITION (PLG/hybrid): <behaviors + thresholds, or "PLAY: instrument and derive">
WHAT WOULD CHANGE THIS CALL: <e.g. "ACV drifts above $25K in closed deals">
```

## 2. North-star metric + input metrics tree

**The north-star test — all three, in writing:**
1. **Leading indicator of value delivered to customers** — measures customers
   succeeding, not us extracting. (Revenue is an output, not a north star.)
2. **Not a vanity count** — cumulative signups, page views, and registered users are
   banned. The metric must be rate-based or active-based.
3. **Movable** — the team's weekly work can change it within a quarter.

Good shapes: "weekly active teams completing ≥1 <core action>", "documents shipped per
week", "workloads under management".

**The tree.** North-star at the root; 2–4 input branches (typically acquisition,
activation, retention/engagement, expansion); every leaf is a metric one person can
move this quarter. Every node carries `definition + current value` or `NOT INSTRUMENTED`.

```
NORTH STAR: <metric> = <current value | NOT INSTRUMENTED>
├── Acquisition: <new signups/wk> = <val>
│   ├── <channel 1 sessions × conversion> = <val>
│   └── <channel 2 ...> = <val>
├── Activation: <% reaching aha within 7d> = <val>
│   └── <onboarding step completion> = <val>
├── Retention: <wk4 cohort retention> = <val>
└── Expansion: <PQL→paid, seats/account> = <val>
```

A tree where leaves are NOT INSTRUMENTED is fine — each such leaf automatically becomes
an instrumentation play in section 3. A tree with a vanity root is not fine — Amir
blocks it.

## 3. AARRR leak analysis

Acquisition → Activation → Retention → Referral → Revenue (Dave McClure's pirate
metrics). For a PLG product, weight Retention first: acquisition poured into a leaky
retention bucket is the premature-scaling death.

**The funnel table:**

| Stage | Metric (defined) | Current | Benchmark (dated) | Status |
|-------|------------------|---------|-------------------|--------|
| Acquisition | e.g. visitor→signup % | | ~2–5% self-serve (verify) | 🟢/🟡/🔴/⚫ |
| Activation | signup→aha within 7d | | ~40–60% target (verify) | |
| Retention | week-4 cohort retention | | product-dependent — pull comparable via WebSearch | |
| Referral | % of new signups from referral/word-of-mouth | | | |
| Revenue | free→paid or PQL→paid % | | PQL 25–39% / MQL 5–10% (verify) | |

⚫ = NOT INSTRUMENTED. An un-instrumented stage cannot be declared healthy.

**Then: name THE biggest leak. One.** The discipline is focus — a growth plan that
attacks five leaks attacks none. State why this leak (largest downstream impact per the
tree), and route the quarter's experiments there.

**Sequencing rule:** capture existing demand before creating it. High-intent surfaces
first — category search terms, "<competitor> alternative" comparisons, AI-assistant
answers citing the category — before brand content and paid demand creation. Startups
routinely invert this and buy attention while free in-market demand goes uncaptured.

## 4. Leak → play table

No metric without an attached play. Standard plays by leak location:

| Leak | Standard plays |
|------|----------------|
| Acquisition | demand-capture pass (SEO/GEO for category + comparison terms — spec to `/marketing`); one channel to proficiency with kill criteria, not five at 15% |
| Activation | shorten time-to-aha (remove steps before the core action); onboarding checklist to the aha; instrument the drop-off step first |
| Retention | validate the habit loop (trigger → action → reward); lifecycle nudges at the natural usage cadence; exit-interview the churned (humans conduct; we draft the guide) |
| Referral | make sharing a natural output of use (artifact links, invites-to-collaborate); referral incentive only AFTER organic referral is nonzero |
| Revenue | PQL-triggered sales-assist; pricing fence review with Jordan (`--pricing`) if free tier cannibalizes; annual-plan prompt at habit formation |
| ⚫ anywhere | instrumentation play: define the event, wire analytics, baseline for 2 weeks — this play precedes all others at that stage |

Each attached play gets: owner (human or team skill), expected direction of the metric,
review date.

## 5. Growth-efficiency gates (Jordan's economics sanity check)

Run whenever there is revenue; otherwise mark `PRE-REVENUE — gates deferred`.

- **CAC payback** = CAC ÷ (new-customer monthly revenue × gross margin), in months.
  2025 median ≈ 15; <12 strong (verify — dates fast). Fully-loaded CAC: include
  salaries and tools, not just ad spend.
- **Burn multiple** = net burn ÷ net new ARR. <1x elite; 1–1.5x good; >2x alarming at
  Series A+ (verify).
- **Magic number** = net new ARR in quarter ÷ prior quarter S&M spend. >1 = pour fuel;
  <0.75 = fix the machine before scaling spend.
- **Rule of 40** (growth % + margin %) is a later-stage gate; compute it only past
  ~$1M ARR, and state which margin (FCF or EBITDA) is used.
- **The premature-scaling gate:** no scaled acquisition spend until week-4+ retention
  is flat-lining above zero for recent cohorts (the curve bends, not just decays).
  This gate overrides all growth enthusiasm.

## 6. Quality bar (self-check before Phase 4)

- [ ] Motion decision uses the format; both-ways ACV check present
- [ ] PQL defined (or explicitly made a play) for PLG/hybrid
- [ ] North-star passes all three tests in writing; no vanity root
- [ ] Every tree node: definition + value or NOT INSTRUMENTED
- [ ] Funnel table complete; ⚫ stages named; benchmarks dated or marked verify
- [ ] ONE biggest leak named with reasoning
- [ ] Every 🔴/⚫ metric has an attached play with owner and review date
- [ ] Efficiency gates computed or marked PRE-REVENUE
- [ ] Demand-capture-first sequencing stated
