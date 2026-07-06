# SaaS Paper Playbook — the five-document contract stack

Reference for `/legal --paper`. Structures and market-standard positions for each document.
The positions table in `contract-review.md` §4 governs all commercial terms; this file adds
document architecture and section-level content. Every generated document carries inline
`[ASSUMPTION: ...]` and `[JURISDICTION: ...]` flags plus the review-gate footer.

## 0. Stack architecture

```
Order Form (commercial: SKUs, fees, term)          ← signed per deal
   └─ incorporates MSA (legal terms)               ← signed once, or referenced by URL
        └─ incorporates policies: SLA, DPA, AUP, Support Policy
```

Order of precedence clause is REQUIRED: **Order Form > MSA > policies, except the DPA
prevails on anything concerning personal data.** Sales-led motion → MSA is primary.
Self-serve/PLG → ToS is primary (clickwrap), with the MSA offered for enterprise upgrades.
Both motions → both documents, kept consistent (same liability architecture, same data terms).

## 1. Mutual NDA

Structure:
1. Definition of Confidential Information — marked or reasonably understood to be
   confidential from context.
2. Exclusions — public; already known; independently developed; rightfully received from a
   third party.
3. Obligations — reasonable care (no less than own information); use solely for the defined
   Purpose (state the Purpose concretely — "evaluating a business relationship").
4. Compelled disclosure — notice + cooperation, disclose only what's required.
5. Term — 2–3 years; trade secrets survive as long as they remain secret.
6. No license granted; no obligation to proceed with any transaction; no warranty on
   accuracy of information.
7. Return/destruction on request; one archival copy for legal compliance permitted.
8. Injunctive relief available (irreparable harm acknowledgment).

**Resist from larger counterparties:** residuals clauses (their staff freely use whatever
they remember); non-solicits buried in an NDA; assignment of ideas disclosed during
discussions. Each of these gets flagged, not silently accepted.

## 2. MSA + Order Form

MSA section order (each with the market position from `contract-review.md` §4):
1. Definitions.
2. Access grant — subscription framing: "right to access and use," NOT a software license.
3. Customer obligations + AUP incorporation (or inline AUP for a short stack).
4. Fees — per Order Form; Net 30; taxes on customer; suspension for non-payment after
   notice; no fee obligations contingent on subjective acceptance.
5. Term, termination, effects — for-cause with 30-day cure; data export window 30–60 days
   post-termination, then deletion with written certification on request.
6. Proprietary rights — vendor owns the service and all improvements; feedback license to
   vendor; **customer owns Customer Data**; telemetry/usage-data rights defined explicitly
   and de-identified; AI position stated (default: no training on Customer Data without
   opt-in).
7. Confidentiality (mirrors the NDA terms).
8. Warranties and disclaimers — material conformance with documentation, 30–90 day remedy;
   disclaim implied warranties **conspicuously (CAPS)**.
9. Indemnities — vendor: third-party IP infringement (exclusions + remedies ladder);
   customer: their data, their use, their instructions.
10. Limitation of liability — mutual 12-month cap; carve-outs and any super-cap per the
    positions table; consequential damages waiver, **conspicuous**.
11. Insurance (commercially reasonable; certificates on request).
12. Publicity — logo/name use with approval.
13. Governing law + venue.
14. Boilerplate — assignment (consent, change-of-control carve-out), force majeure, notices
    (email permitted with confirmation), severability, entire agreement, counterparts,
    order of precedence.

Order Form contents: parties + MSA reference/date; SKUs/plan; users/usage limits; fees and
billing frequency; initial term + renewal; special terms (any negotiated deviations — these
live HERE, not as MSA edits); signature blocks.

## 3. Terms of Service (self-serve / B2C / PLG)

1. Acceptance — **clickwrap**: affirmative act (checkbox/button "I agree") + conspicuous
   notice at signup. Browsewrap ("by using this site...") is presumptively unenforceable —
   never rely on it. Eligibility/age gates (13+ COPPA floor; 16/18 per feature risk).
2. Accounts — credential responsibility, accurate info, one person per seat.
3. License/access grant — same subscription framing as the MSA.
4. Acceptable use — abuse, scraping, resale, security testing without consent, unlawful
   content.
5. User content — license scoped "solely to provide and improve the service"; NOT a
   perpetual, irrevocable, sublicensable everything-grant. Copying a big platform's content
   clause into a SaaS tool is a trust-destroying error.
6. AI features disclosure — what inputs/outputs are; no-reliance statement (outputs may be
   wrong); training-use position stated plainly (B2B default 2025–26: "we do not train
   models on your content without opt-in"); `[ASSUMPTION]` flag if product behavior is
   unverified — reconcile with the actual product before publishing (FTC deception risk).
7. Fees, trials, refunds, plan changes.
8. DMCA — designated agent + takedown/counter-notice process (register the agent with the
   Copyright Office — human to-do).
9. Third-party services.
10. Termination — by user anytime; by us for breach; data export window.
11. Disclaimers (conspicuous) + liability cap — B2C position: greater of $100 or fees paid
    in the last 12 months.
12. Dispute resolution — arbitration + class-action waiver with a 30-day opt-out;
    **mass-arbitration batching provisions** (bellwether/batching procedure — post-2023
    standard); small-claims carve-out. `[JURISDICTION: consumer arbitration rules vary —
    attorney review essential]`.
13. Changes to terms — notice for material changes (email + in-app), continued use ≠
    consent for material changes to dispute terms without fresh assent.
14. Export controls / government use; governing law; contact.

## 4. SLA

1. Uptime commitment — 99.9% monthly (SMB standard); 99.95–99.99% only if the architecture
   actually supports it (never paper above reality). Define the measurement: monthly
   uptime % = (total minutes − downtime minutes) / total minutes.
2. Downtime definition + exclusions — scheduled maintenance (with notice window), force
   majeure, customer-caused, third-party ISPs/upstream providers, beta features.
3. Service credits ladder (credits off the monthly fee):

| Monthly uptime | Credit |
|---|---|
| < 99.9% | 10% |
| < 99.0% | 25% |
| < 95.0% | 50% |

4. Claim procedure — customer requests within 30 days of the incident month; credits applied
   to future invoices; credits are the **sole and exclusive remedy** for availability
   failures.
5. Chronic-failure termination right — customer may terminate (with pro-rata refund) if
   below commitment 3 consecutive months or any 3 months in a rolling 6.
6. Support tiers — P1 (production down): 1-hour response; P2 (major degradation): 4 hours;
   P3 (minor/how-to): next business day. Define response ≠ resolution.

## 5. DPA (Data Processing Addendum)

Jointly owned with the `/compliance` team: compliance owns the privacy program (data map,
RoPA, subprocessor list — the facts); legal owns this contract document. **Annexes must match
the compliance team's data map exactly.** If no compliance artifacts exist in
`docs/enterprise/compliance/`, draft annexes with `[ASSUMPTION]` flags and recommend running
`/compliance` before this DPA is sent to any customer.

1. Roles — customer = controller, vendor = processor (adjust if reality differs; role
   misclassification cascades).
2. Annex I — description of processing: subject matter, duration, nature/purpose, data
   categories, data subject categories. Source: the compliance data map.
3. Processor obligations mirroring GDPR Art. 28(3):
   - process only on documented instructions;
   - confidentiality commitments from personnel;
   - Art. 32 security measures (Annex II — technical and organizational measures, from
     verified practice only);
   - subprocessor regime — general written authorization + published list + advance change
     notice + customer objection right;
   - assist with data subject requests and Arts. 32–36 obligations;
   - deletion or return at end of services;
   - audits — market position: SOC 2 report + security questionnaire satisfies audit rights;
     on-site audits only after a breach or regulator demand, max once/year, at customer cost.
4. International transfers — EU SCCs (2021/914, correct module: typically Module 2
   controller→processor); UK IDTA/Addendum; Swiss addendum; note DPF participation status
   if applicable (verify current — `[JURISDICTION]`).
5. US state addendum — CCPA "service provider" certifications: no sell, no share, no
   combine outside the business purpose.
6. Breach notice — market: "without undue delay"; customers ask 24–48h; vendor fallback:
   72 hours after confirmation. Whatever is signed becomes the IR team's clock — tell
   `/compliance`.
7. Liability — tie back to the MSA cap (or the negotiated super-cap); the DPA must not
   silently create uncapped data liability.

## 6. Cross-stack consistency checklist (run after all documents are drafted)

- [ ] Defined terms identical across documents ("Customer Data" means one thing everywhere).
- [ ] Order-of-precedence clause present and correct in the MSA and referenced in policies.
- [ ] Liability carve-outs in the MSA mirror the indemnity structure and the DPA tie-back.
- [ ] SLA credits declared sole-and-exclusive in both SLA and MSA warranty section.
- [ ] ToS and MSA state the same AI-training position.
- [ ] Every practice described (security, deletion, telemetry, training) is something the
      product verifiably does — no aspirational claims (FTC deception exposure).
- [ ] Disclaimers and arbitration conspicuous (caps/bold).
- [ ] Exact legal entity name on every document.
