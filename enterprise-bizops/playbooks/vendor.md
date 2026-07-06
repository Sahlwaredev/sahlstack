# Vendor Playbook — evaluation, RFP, negotiation, register, renewals

Reference for `/bizops --vendor`. Read before drafting any procurement artifact.

## Right-sizing gate (apply before anything else)

Process weight ∝ contract cost × reversibility.

| Annual contract value | Process |
|---|---|
| <$5k/yr, month-to-month | Owner picks from a 3-row comparison; no memo needed |
| $5–25k/yr | Lightweight comparison matrix + 1-pager decision memo. **No formal RFP.** |
| $25–100k/yr | Full matrix + RFP to shortlist + negotiation brief + reference calls |
| >$100k/yr or hard-to-exit (data gravity, deep integration) | All of the above + security/legal review + POC with written success criteria |

A 6-week RFP for an $8k tool is process theater; one demo for a $200k platform is
negligence. State which tier applies and why before starting.

## Vendor comparison matrix

Columns = vendors (3–5 max) **plus one column for "do nothing / build / reuse what we
own"** — this baseline is genuinely scored, not a strawman. Always start the market scan
with the duplicate-tool check: "what do we already own that does this?"

Row groups:
1. **Must-have requirements** — pass/fail gates. Failing ANY must-have eliminates the
   vendor BEFORE scoring. (This is what stops "buying off a demo.")
2. **Should-have requirements** — scored 1–5 × weight.
3. **Pricing** — year-1 cost AND 3-year TCO including implementation, training,
   integration engineering, and internal people time. Year-1 price is bait.
4. **Security & compliance** — pass/fail: SOC 2 / ISO 27001, DPA available, data
   residency, subprocessor list, SSO/SCIM (and whether SSO is paywalled), breach
   notification terms.
5. **Support & SLA** — tiers, response commitments, who you actually get.
6. **Integration fit** — native connectors to the existing stack, API quality.
7. **Vendor viability** — funding/profitability, customer count at your scale, roadmap
   credibility.
8. **References** — 2–3 calls with customers AT YOUR SCALE (a Fortune 500 reference is
   irrelevant to a 20-person startup).

Footer: weighted totals, decisive recommendation, dissents noted by name.

**Scoring weights are fixed BEFORE seeing any vendor response.** Defaults (tune to
context, then freeze):

| Criterion | Weight |
|---|---|
| Functionality fit | 30–40% |
| Total cost (3-yr TCO) | 15–25% |
| Security & compliance | 15–20% |
| Integration fit | 10–15% |
| Vendor viability & support | 10–15% |
| Implementation effort | 5–10% |

Independent scoring by each evaluator, then calibrate divergences >1 point.

## RFP template (≥$25k/yr only)

1. **Background** — who we are, current state, why we're buying.
2. **Scope & objectives** — the problem in outcome terms; success criteria.
3. **Functional requirements** — numbered, tagged must/should; vendor responds per line:
   `comply / partial / roadmap (date) / no`. "Roadmap" answers score as "no" for
   must-haves.
4. **Non-functional requirements** — security, performance, availability, data
   handling/export.
5. **Implementation & support expectations** — timeline, migration help, training,
   support tier.
6. **Pricing structure** — line-item, 3-year view, all assumptions stated (seats, usage
   tiers, overage rates, implementation fees).
7. **Vendor information** — company financials/viability, references at our scale,
   product roadmap.
8. **Evaluation criteria & weights** — DISCLOSE them. Honest vendors calibrate their
   response; evasive ones self-select out.
9. **Timeline & logistics** — response deadline, demo window, decision date, contacts.
10. **Terms** — confidentiality, no-obligation, our paper vs theirs where possible.

## Demo / POC discipline

- Script the demo with YOUR worst-case scenarios (messiest data, weirdest workflow,
  biggest scale day) — never let the vendor run their scripted best case.
- POC has written success criteria and an end date before it starts. A POC without exit
  criteria is a sale in progress.
- Reference call questions: "What broke in the first 90 days?" "What did implementation
  actually cost vs quote?" "If you were buying again, what would you negotiate?"

## Negotiation brief format

Prepared by the AI; a human makes the call. Contents:

1. **Deal summary** — vendor, product, proposed price, term, decision deadline.
2. **Leverage checklist** (tick what applies):
   - [ ] Their fiscal quarter/year-end within 45 days (verify via WebSearch — discounts
         concentrate there)
   - [ ] Live competitive alternative (name it; a real one, not a bluff)
   - [ ] Credible "do nothing / build / reuse" fallback
   - [ ] Growth story (they want the logo before the growth)
   - [ ] Case study / logo rights / reference-ability as trade goods
   - [ ] Multi-year commitment available IF priced for it
   - [ ] Timing flexibility (we can walk and revisit next quarter)
3. **Price targets** — list price is fiction. Open / target / walk-away numbers.
   10–30% off list is routine with timing leverage; verify current benchmarks for this
   category via WebSearch — these date fast.
4. **Terms to demand** (often worth more than the discount):
   - Renewal uplift cap 3–7% written into the contract (kills the +20% renewal ambush)
   - Termination for convenience, or at minimum a short cure/exit window
   - Data export guarantee (format + assistance) — the exit path
   - Price lock for the term; growth-tier pricing pre-agreed
   - SLA credits if they claim an SLA; net-30/45 payment terms
5. **BATNA** — what we do if talks fail, and its real cost. The brief states whether the
   walk-away is credible; if it isn't, say so — negotiating without a BATNA is begging.
6. **Concession ladder** — what we give in what order (term length before price, logo
   rights before term), and what we never give (auto-renew without notice cap).

## Vendor register format

One row per vendor. The **auto-renew notice window is the trap field** — contracts renew
at +20% because nobody tracked the 60-day notice deadline.

| Field | Notes |
|---|---|
| Vendor / product | |
| What it does | one line, plain English |
| Business owner | exactly one named person |
| Cost/yr | current actuals, not quoted price |
| Contract start / end | |
| Auto-renew? + notice window | 30/60/90 days — compute the LAST SAFE CANCEL DATE and record it |
| Seats bought vs used | flag <60% utilization |
| Security review date | + DPA on file y/n |
| Criticality tier | 1 = company stops without it / 2 = painful / 3 = convenience |
| Exit difficulty | data gravity, integration depth, retraining cost |
| Renewal posture | renew-as-is / negotiate / consolidate / churn — pre-assigned |

## Renewal calendar

Sorted view of the register: everything renewing (or hitting its notice deadline) in the
next 90 days, each with its pre-assigned posture and the negotiation brief queued for
"negotiate" rows. Standing rule: renewal work starts at the 90-day mark, not when the
invoice arrives. Recommend a recurring reminder keyed to notice deadlines, not renewal
dates.

## Spend audit method

1. **Inventory** — SSO app list + card/expense export + accounting; interview the user
   for the rest. Shadow IT surfaces here; list it without blame.
2. **Rationalize** — duplicates (two PM tools, two analytics platforms), seats <60%
   utilized, zombie subscriptions (paid, zero logins 90 days).
3. **Register + calendar** — build both from findings.
4. **Quantify recovery** — typical startup recovers 20–30% of SaaS spend via dedup,
   seat right-sizing, and negotiation. Show the math for THIS portfolio, line by line,
   labeled estimate vs confirmed.
