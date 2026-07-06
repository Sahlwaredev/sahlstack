# Compliance & Privacy Team Process

Every compliance and privacy engagement at a company using AgentForce enterprise teams
follows this process. The goal is a compliance program built from verified facts — where
every external claim is true, every regime decision is documented, and every statutory
clock has a named human owner.

## Overview

```
┌─────────────┐   ┌──────────────────────────────────────────────┐   ┌───────────────┐
│ FOUNDATION  │──▶│ ENGAGEMENTS (natural order)                  │──▶│ ARTIFACTS     │
│ company +   │   │ --applicability ─▶ --privacy ─▶ --certify    │   │ dated drafts  │
│ compliance  │   │        │              │            │          │   │ in docs/      │
│ docs        │   │        └──▶ --ai      └──▶ --incident         │   │ enterprise/   │
│ (90-day     │   │                    --respond (as deals ask)  │   │ compliance/   │
│  refresh)   │   └──────────────────────────────────────────────┘   └──────┬────────┘
└─────────────┘                                                             │
                  ┌──────────────────────────┐   ┌──────────────────────────▼─────────┐
                  │ EXTERNAL EXECUTION       │◀──│ HUMAN REVIEW PR                    │
                  │ publish policy, engage   │   │ docs: compliance <mode> review     │
                  │ auditor, file, send —    │   │ package — review gates enforced    │
                  │ humans only              │   └────────────────────────────────────┘
                  └──────────────────────────┘
```

## Phase 1 — Foundation

Two foundation documents anchor every engagement:

- `docs/enterprise/foundation.md` — company foundation: product, stage, business model,
  target customer and geography, constraints.
- `docs/enterprise/compliance/foundation.md` — compliance foundation: personal-data
  footprint, data-subject geography, hosting, compliance assets actually held (attestations,
  certifications, policies, signed DPAs), vendor stack, AI usage, sensitive-sector
  triggers, current deal pressure.

Both carry a dated header and a `Last reviewed:` line. **Refresh rule: if a foundation doc
is older than 90 days, refresh it before any engagement.** Compliance foundations rot
faster than most — new vendors, new features, and new laws all invalidate them.

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|------|----------------|------------------|--------------|
| `--applicability` | First, always; and when facts change (EU launch, new vertical, AI feature, headcount/revenue threshold) | Regime applicability memo: APPLIES / DOES NOT APPLY / MONITOR per regime, with trigger facts and re-check triggers | Foundations |
| `--privacy` | Personal data is processed and no program exists; before Privacy TSC; before EU-facing launches | Data map, RoPA, privacy policy draft, DSAR pipeline, cookie/consent pack, DPIAs as triggered | Applicability memo |
| `--certify` | Buyer pressure for SOC 2 / ISO 27001; before enterprise sales motion | Gap assessment (CC1–CC9 / SoA), policy suite drafts, 90-day roadmap, audit-timing recommendation | Applicability memo; `/cso` run recommended |
| `--ai` | Any AI feature ships or is planned; EU users + AI in any combination | AI system register, EU AI Act classifications, transparency disclosure kit, NIST AI RMF-based governance policy | Applicability memo |
| `--incident` | Before you need it — ideally right after `--privacy`; refresh after any incident or new DPA | IR plan, breach notification decision tree with all clocks, notification templates, tabletop script | Applicability memo; DPA inventory |
| `--respond` | A customer sends a security questionnaire | Drafted responses from verified facts, cover memo with gap disclosures, updated answer library | Gap assessment or `/cso` report strongly recommended |

Security scanning is `/cso`'s job. Compliance engagements consume `/cso` reports as
verified evidence; they never re-scan.

## Phase 3 — Commit artifacts

Artifacts live in `docs/enterprise/compliance/` with dated filenames:

```
docs/enterprise/compliance/
  foundation.md
  INDEX.md                                  # one line per artifact: date, mode, link, review gate
  applicability-memo-2026-07-06.md
  data-map-2026-07-06.md
  ropa-2026-07-06.md
  privacy-policy-draft-2026-07-06.md
  gap-assessment-soc2-2026-07-06.md
  ai-system-register-2026-07-06.md
  incident-response-plan-2026-07-06.md
  questionnaire-library.md                  # living document, entries individually dated
```

The date in each filename and document header is the audit trail — it proves the work
happened and when. Do not remove or change these dates. Superseded artifacts stay in place;
new versions get new dated files (regulators and auditors ask "what did you know and
when" — the file history answers).

Every artifact carries the evidence-basis footer (counts of verified / asserted /
aspirational claims) and a "regulatory facts as of <date>" line.

## Phase 4 — Human review & approval

Open a PR titled `docs: compliance <mode> review package`.

Review-gate legend (every artifact declares one in its header):

- **AI-final** — internal working documents (data map, control matrix, answer-library
  internals). Merge on maintainer review.
- **Human review recommended** — anything a customer or employee will see or that commits
  the company operationally (policy suite, DSAR procedure, tabletop script, roadmap).
- **Licensed professional required** — anything touching statutory duty or attestation:
  privacy policy (attorney), breach plan clocks and notification templates (counsel),
  gap assessment before an audit engagement (CPA firm chooses its own procedures), EU AI
  Act classifications where prohibited/high-risk is arguable (counsel).

Rule: **nothing externally binding — publish, send, sign, file, or attest — happens until
the PR is approved.** A merged PR is approval of the drafts, not execution of them.

## Phase 5 — External execution

After PR approval, the human to-do checklist from the engagement handoff drives execution:

- Privacy policy → published to the site (after attorney review); CMP configured per the
  consent-pack spec; DSAR intake channel live and monitored by its named owner.
- Gap assessment + roadmap → controls stood up per the 90-day plan; auditor engaged
  (licensed CPA firm / accredited body — humans sign the engagement letter).
- AI register → transparency disclosures implemented in-product (verify placement with
  `/qa`); vendor AI terms confirmed.
- IR plan → counsel and forensics retainers signed; every ⏰ CLOCK owner confirmed and
  calendared; tabletop scheduled and run by humans.
- Questionnaire responses → human confirms asserted items, human sends.

The team monitors afterwards: quarterly data-map refresh, DSAR log review, control-evidence
cadence, subprocessor-list currency, and regulatory-change watch (WebSearch — this area
changed monthly through 2025–26).

## Operating cadence

- **Weekly (during a certification push):** roadmap standup — control stand-up progress,
  evidence gaps, blockers.
- **Monthly:** DSAR log review (clocks met? volumes trending?); exception register review;
  subprocessor list check against actual vendor changes.
- **Quarterly:** data-map and AI-register refresh; access-review evidence check;
  regulatory-change scan → re-run `--applicability` if any MONITOR trigger fired.
- **Semi-annually:** tabletop exercise (humans run it); policy-suite review-date sweep.
- **Annually:** full policy suite re-approval; audit cycle (Type II window / ISO
  surveillance); foundation docs rewrite.

## FAQ

**When do I actually need a human lawyer?**
Whenever a statutory duty is triggered or arguable: any breach (counsel in before
forensics, for privilege), regulator contact, publishing the privacy policy, an arguable
EU AI Act high-risk classification, and any enforcement letter. The skill drafts the
analysis; counsel decides and communicates.

**Can I skip the review PR?**
Only for internal-only drafts (data map iterations, answer-library housekeeping). Never
for anything customer-facing or authority-facing — policy, notices, questionnaire
responses, filings.

**Can we say "SOC 2 certified" once the gap assessment is clean?**
No — twice over. SOC 2 is an attestation, not a certification, and you have neither until
a licensed CPA firm issues a report. Until then the honest sentence is "SOC 2 Type II
readiness program in progress, audit window opening <date>."

**A customer wants the questionnaire back today. Can the skill just send it?**
No. It drafts from verified facts and produces a cover memo of gaps and asserted claims; a
human confirms and sends. Questionnaire answers are contractual representations.

**We got a DSAR and the deadline math is confusing. Which clock applies?**
The shortest one that fits the requester's regime — the DSAR procedure computes it, but the
named intake owner is accountable for meeting it. If the owner is unclear, that is the
finding; fix ownership first.

**Do we need all this at 4 people, pre-revenue?**
You need `--applicability` (an afternoon) and honest answers. The memo will right-size
everything else — usually a thin privacy program if you touch personal data, and nothing
else until buyers ask. Statutory minimums (GDPR if you target EU users, breach clocks in
signed DPAs) apply at any size.
