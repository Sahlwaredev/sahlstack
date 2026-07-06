# Contract Review Playbook — three-position method, market positions, memo format

Reference for `/legal --review` (and the positions table backs `--paper`). Read fully before
reviewing any contract.

## 1. Intake metadata (extract before analysis)

| Field | Notes |
|---|---|
| Parties | Exact legal names + entity type + state. Mismatch with our actual entity = Critical finding. |
| Our role | Vendor / customer / both (reseller)? Processor / controller for data terms? |
| Paper origin | Our template, their template, or negotiated hybrid? Note template version if ours. |
| Deal value | ACV and TCV (total contract value). Materiality calibrates to this. |
| Term | Initial term, renewal mechanics, auto-renewal notice window (calendar it). |
| Governing law / venue | Note if it breaks enforceability assumptions (see §5 jurisdiction traps). |
| Signature authority | Who signs on each side; does our signer have authority at this dollar value? |

## 2. Counterparty-role sanity check (do this before any position work)

State plainly: "We are the [vendor/customer] here." Then invert positions accordingly.
The table in §4 is written from the **vendor** seat. When we are the **customer** (vendor
procurement review), flip it:

| Clause | As vendor we want | As customer we want |
|---|---|---|
| Liability cap | Low, mutual, 12 months fees | Higher or asymmetric; super-cap for data breach |
| IP indemnity | Narrow, with exclusions | Broad vendor indemnity, few exclusions |
| Warranty | Conformance-to-docs only, disclaim the rest | Meaningful performance warranty |
| Termination for convenience | Resist, or paid out | Want it, short notice |
| Auto-renewal | Long notice window binds customer | Short notice window, price-increase cap |
| Audit/security terms | Questionnaire + SOC 2 report suffices | Real audit and breach-notice rights |

Applying vendor-favorable positions while sitting in the customer seat is the classic AI
review failure. Confirm role with the user; re-confirm if the document is ambiguous.

## 3. Risk-tier routing

- **Tier 1 — automated approval.** Their NDA materially matches our template; vendor
  click-through below the spend threshold (default $5k/yr; foundation may override). Output:
  one-paragraph approval memo, obligations calendared. Done.
- **Tier 2 — playbook review.** Standard MSA/order-form negotiation on either paper. Full
  clause-by-clause pass, memo, redline issue list.
- **Tier 3 — human counsel escalation (review still done, flags added).** Any of:
  non-standard indemnities, assignment/transfer of our IP, exclusivity, source-code escrow,
  MFN (most-favored-nation pricing), uncapped liability for ordinary breach, non-standard
  insurance demands, regulatory reps we can't verify. Do the full analysis, then flag each
  Tier 3 clause: "escalate — requires human counsel sign-off before agreeing."

## 4. Market-standard positions table (2025–2026 SaaS center of gravity, vendor seat)

For each clause: **P** = preferred, **F** = fallback (with acceptance conditions),
**W** = walk-away / escalation trigger. Verify current market drift via WebSearch when a
counterparty claims "this is market" — these positions date.

| Clause | P — Preferred | F — Fallback (conditions) | W — Walk-away / escalate |
|---|---|---|---|
| Liability cap | Mutual, 12 months of fees paid/payable | 1.5–2x fees if ACV > $100k or strategic logo | Uncapped liability for ordinary breach; one-sided cap |
| Super-cap (data breach / security) | None (general cap applies) | 2–5x fees or cyber-insurance-limit-tied super-cap for breach of security/DPA obligations | Uncapped data liability |
| Cap carve-outs (uncapped) | Gross negligence/willful misconduct; breach of confidentiality; payment obligations; IP infringement indemnity | Party's indemnity obligations carved out (contested — push to super-cap instead) | Carve-outs that swallow the cap (e.g. "any breach of contract") |
| Consequential damages waiver | Mutual, carve-outs mirroring the cap carve-outs | Narrower mutual carve-outs | One-sided waiver (only they're protected) |
| IP indemnity (we give) | Vendor indemnifies third-party IP infringement claims; exclusions: combinations, modifications, use of old versions; remedies ladder: procure right → modify → replace → terminate + refund prepaid unused fees | Drop some exclusions for enterprise ACV | Indemnity for customer's own content/use; assignment of our IP |
| Warranty | Material conformance with documentation; 30–90 day remedy period; disclaim implied warranties | Longer remedy window | "Error-free/uninterrupted" promises; fitness-for-purpose warranty |
| Termination | For cause with 30-day cure; effects: data export window 30–60 days then deletion | Customer convenience termination WITH payment of remaining term | Unpaid convenience termination on annual prepaid deals |
| Auto-renewal | 1-year renewals; 30–60 day non-renewal notice | Price-increase cap (CPI or 5–7%) — common customer ask, acceptable | Evergreen with 6+ month notice trap (either direction) |
| Payment | Net 30; suspension for non-payment after notice; taxes on customer | Net 45–60 for enterprise | Payment contingent on subjective acceptance |
| Governing law | Our home state, or DE/NY/CA | Their state if enforceability assumptions hold | Foreign law + venue we can't realistically litigate |
| Confidentiality | Mutual; 2–3 year term; trade secrets survive while secret | — | Residuals clause (their people freely use what they remember) |
| Data terms | DPA as exhibit prevails on data; customer owns Customer Data; we get defined telemetry + de-identified use | Tighter telemetry definitions | Customer ownership of our models/improvements; training rights we don't need |
| Assignment | Consent required, carve-out for change of control / merger / asset sale | Mutual consent-not-unreasonably-withheld | Their free assignment + our prohibition |
| Insurance | Commercially reasonable; certificates on request | Specific limits scaled to ACV | Limits wildly above deal size (e.g. $10M cyber on a $20k deal) — negotiate down |
| Publicity | Logo/name use with approval | Mutual press release on close | Broad endorsement rights |

## 5. Jurisdiction traps (check against governing law)

- Non-competes: void in CA; many states void or compensation-gate. Never assume enforceable.
- Warranty disclaimers and arbitration clauses: conspicuousness rules (caps/bold) in many
  states — an inconspicuous disclaimer can be no disclaimer.
- Auto-renewal statutes: several states require advance renewal notices to customers
  (esp. B2C) — verify per state before relying on evergreen renewals.
- Liquidated damages: enforceable only as reasonable pre-estimate, not penalty.

## 6. Three-position playbook method (per clause)

For each clause that deviates from P:

```
CLAUSE: <name> (§ ref)
WHY IT MATTERS: <business translation — dollars, probability, reversibility>
THEIR ASK: "<quoted text>"
MARKET CONTEXT: <where this sits vs the table above>
OUR POSITION: P / F1 / F2 / W — <which and why>
PROPOSED LANGUAGE: "<verbatim replacement text, paste-ready>"
TALKING POINT: <one sentence to say in negotiation>
APPROVAL: <who must approve if this deviates below F — from the foundation's signing matrix>
```

Rules: concessions are logged (see §8); never trade below W without documented human
approval; check precedent — a concession to this customer may create MFN or template-drift
problems across the base.

## 7. Review memo format

```markdown
# Contract Review Memo — <Counterparty> <Document type>
> Generated by /legal (Legal Team) — <date>
> Engagement: --review · Status: DRAFT — pending human review
> Review gate: Licensed professional required (attorney)

## Executive summary
- Deal: <one line — parties, value, term>
- Our role: <vendor/customer>; paper: <ours/theirs>; tier: <1/2/3>
- Top 3 risks: <one line each, in dollars/probability terms>
- RECOMMENDATION: <sign as-is | counter with issues 1–N | escalate issues X,Y to human counsel>

## Issues table
| # | Clause | Severity | Their ask | Our response | Approval needed |
|---|--------|----------|-----------|--------------|-----------------|
(Critical / High / Medium / Low — rate honestly; most contracts have 3–8 real issues)

## Not fighting about
<Clauses that deviate from our template but are market and immaterial at this deal size — list them so the business knows review was complete, not lazy.>

## Clause-by-clause analysis
<§6 blocks for each open issue>

## Obligations to calendar on signature
| Obligation | Clause | Date/window | Owner |

## Open questions for the business owner
<numbered>

## Concession log entry
<what we gave, to whom, why, approved by whom>
```

## 8. Concession log

Maintain `docs/enterprise/legal/concession-log.md`: date, counterparty, clause, standard
position, what we accepted, condition, approver. Check it during every intake — "what did we
give this customer last time" is precedent management, and precedent is how templates drift.
