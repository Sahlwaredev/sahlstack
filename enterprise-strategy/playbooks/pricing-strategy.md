# Playbook: Pricing Strategy (--pricing)

Jordan's reference for the monetization strategy. Output artifact:
`pricing-strategy-<date>.md`.

Division of labor: **strategy decides the pricing STRATEGY** (value metric, tier
architecture, price positioning, discount policy) and writes the spec for the
quantitative study. **Finance (`/finance`) fields the willingness-to-pay study and the
revenue-impact model.** **Marketing (`/marketing`) writes the pricing page copy.** Never
fabricate survey results; never publish prices — humans do that.

## 1. Value metric selection

The value metric is the unit the price scales with (seats, workspaces, API calls,
records, revenue processed). It is the single highest-leverage pricing decision —
it determines NRR (net revenue retention — revenue kept plus expansion from existing
customers) more than the price points do.

**Four tests — a candidate must pass all four, in writing:**

1. **Scales with value received** — when the customer gets more value, the metric grows.
   (Seats fail this for single-player tools; usage fails it when usage is anxiety.)
2. **Predictable to the buyer** — the customer can forecast their bill. Unpredictable
   metering creates bill-shock churn and procurement resistance.
3. **Cheap to meter** — you can measure and bill it without building a metering platform
   before product-market fit.
4. **Grows with customer success** — expansion happens without a sales conversation
   when the customer succeeds (the PLG expansion engine).

Score each candidate PASS/FAIL per test with one line of reasoning. Recommend one
primary metric. Hybrid designs (platform fee + consumption) are legitimate when a pure
metric fails test 2 — say which component absorbs the unpredictability.

## 2. Tier architecture (good / better / best)

Standards:
- **3 tiers** (plus optional free tier/trial — see below). More than 4 paid tiers is a
  decision tax on the buyer.
- **1–2 fence features per boundary.** A fence is the feature that makes the next tier
  irresistible to the target segment of that tier — not a random feature scatter.
  Classic enterprise fences: SSO/SAML, audit logs, RBAC, SLA + support tier, security
  review support. Do not fence security table stakes that every tier needs (2FA).
- **~2.2–3x price spread** between adjacent tiers. Narrower spreads make the middle
  tier pointless; wider ones strand buyers.
- **Anchor high:** the top tier's job is partly to make the middle tier look reasonable.
- **Annual vs monthly:** offer annual at ~2 months free equivalent; annual prepay is a
  cash-flow asset (finance cares) and a churn dampener.

**Free tier / trial decision.** A free tier is growth spend, not generosity — justify it
with the growth model: it is right when the product is single-player-capable, time-to-value
is under a session, and the value metric naturally fences the free tier (PLG motion).
Otherwise use a 14-day trial or a demo. State the decision and the rationale.

**Tier table format:**

| | <Tier 1> | <Tier 2> | <Tier 3 / Enterprise> |
|---|---|---|---|
| Target segment | | | |
| Price (per <value metric>, monthly & annual) | | | |
| Fence features (what you get by upgrading) | — | <1-2> | <1-2> |
| Spread vs previous | — | <x.x>× | <x.x>× |

## 3. Price positioning

Position against the competitor price frame from `--landscape` (if missing, run a quick
frame: WebSearch every roster competitor's pricing page, dated).

- **Premium / parity / undercut** — pick one, justify with the value evidence from
  discovery. Undercutting is a strategy only with a structural cost advantage;
  otherwise it just resets the category's price floor and starves the company.
- **The underpricing check (mandatory).** Startups systematically underprice. Run the
  10x test: take the quantified value per customer from discovery (time saved × loaded
  hourly cost, or revenue enabled, or cost avoided). If price < ~10% of quantified
  annual value, the price is likely leaving money on the table — say so with the math.
  Capturing 10–25% of created value is a normal SaaS posture.
- **Gross-margin floor:** price must clear COGS (hosting/inference/support) at target
  margin — pure SaaS targets 75–85%; AI-inference-heavy products run lower, state the
  real number. Get COGS from discovery or flag `NOT KNOWN — finance to compute`.

## 4. Discount policy

Every discount has a **get**. No naked discounts.

| Discount depth | Requires (the get) | Approver |
|----------------|--------------------|----------|
| ≤10% | Annual prepay OR case study/logo rights | Founder/AE discretion |
| 11–25% | Multi-year OR ≥2 gets | Founder |
| >25% | Named strategic rationale, written | Founder + logged as exception |

Reflex discounting trains buyers to wait and marks the list price as fiction. Log every
exception; review the log at each pricing revisit (every 6–12 months).

## 5. WTP study spec (handoff to /finance)

Strategy proposes the price; the study validates it. Write this spec into the artifact:

```markdown
## Willingness-to-pay study spec (execute via /finance --pricing-study)

Segment to survey: <from foundation/ICP; n ≥ 30 per segment for direction,
  ≥ 100 for confidence>
Van Westendorp PSM (4 questions, ask about the <tier 2> offer):
  1. At what price would this be so cheap you'd doubt its quality? (too cheap)
  2. At what price is this a bargain? (cheap/good value)
  3. At what price does this start to feel expensive? (getting expensive)
  4. At what price is this too expensive to consider? (too expensive)
  → acceptable range from the curve intersections; compare proposed price to range.
Gabor-Granger (per-tier): purchase-intent at 5 price points bracketing the proposed
  price (±50%) → revenue-maximizing point per tier.
Decision rule: <what result moves the price, e.g. "if the VW acceptable range's upper
  bound exceeds proposed by >30%, raise tier 2 and re-test fences">
```

## 6. Migration & grandfathering (only when prices change for existing customers)

- Who is affected: count and ARR at old prices.
- Policy options: grandfather indefinitely / grandfather 12 months then migrate /
  migrate at renewal with notice. Recommend one; state the churn assumption.
- Communication: notice period ≥ 60 days for increases; the announcement draft is
  marketing's job — record the handoff.
- Legal note: multi-year contracts and MFN (most-favored-nation) clauses can block
  changes — flag any known contracts for legal review. Not legal advice.

## 7. Quality bar (self-check before Phase 4)

- [ ] Value metric scored against all four tests, in writing
- [ ] 3 tiers, fences named per boundary, spread computed and in ~2.2–3x range
      (or deviation justified)
- [ ] Free tier/trial decision made with growth rationale
- [ ] Positioning call (premium/parity/undercut) justified against dated competitor frame
- [ ] Underpricing 10x test run with the math shown
- [ ] Gross-margin floor checked or flagged NOT KNOWN
- [ ] Discount matrix present; every discount has a get
- [ ] WTP study spec written; zero fabricated survey numbers
- [ ] Rejected alternatives (metrics, models) named with reasons
