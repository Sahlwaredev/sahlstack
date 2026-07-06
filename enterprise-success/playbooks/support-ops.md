# Support Operations Playbook — tiers, SLAs, escalation, macros, QA

Reference templates for `/customer-success --support`. Fill every `<angle>` slot from foundation docs and Phase 2 answers. Right-size to stage: at a 3-person startup, L1/L2 are the same human wearing labeled hats — write the tiers anyway so escalation criteria exist before headcount does.

## 1. Tier model (L0–L3)

| Tier | Who | Handles | Must attempt before escalating | Key metrics (each with attached play) |
|------|-----|---------|-------------------------------|----------------------------------------|
| **L0** | Self-service: KB, in-product help, AI agent, community | The long tail: how-to, known issues, config questions | n/a | Deflection **success** (resolved AND no repeat contact ≤7 days), target 30–70% by product complexity — falling success on a top article fires a rewrite play |
| **L1** | First responder | First response, triage, known-issue matching, basic troubleshooting | KB search (KCS Reuse), known-issue tracker, standard diagnostics | FCR 60–75%; CSAT; SLA response — FCR below floor fires a coaching + KB-gap review play |
| **L2** | Deep product knowledge | Complex troubleshooting, log analysis, reproduction | Full repro attempt, log review, environment isolation | Resolution time (realistic, NOT mirroring L1 targets — deep investigation needs its own clock); escalation quality; mean time to escalate |
| **L3** | Engineering | Product defects, infra issues | n/a (receives only complete escalation packets) | **The L3 rule: every L3 fix flows back down** — each produces a KB article or runbook so the issue never reaches L3 again. Track: repeat-escalation types trending down |

**Triage decision (L1 runs on every ticket):** product defect / config issue / docs gap / user error → each has a different owner. Docs gap → Lena's writing queue; user error at volume → UX feedback into the VoC report; defect → escalation packet.

2025–26 default is AI-first L0: AI resolves the long tail; humans handle judgment, emotion, and novelty. Measure deflection quality, never deflection count.

## 2. SLA policy

### Priority matrix (severity × impact) — with product-specific examples

| Priority | Definition | Two concrete examples (write in THIS product's terms) |
|----------|------------|------------------------------------------------------|
| **P1 / Urgent** | Production down or data at risk, no workaround, many users affected | e.g. `<login completely broken for all users>`, `<data pipeline dropping records>` |
| **P2 / High** | Major function degraded, workaround exists | e.g. `<exports failing but API path works>` |
| **P3 / Normal** | Single-user issue, minor function, non-blocking | e.g. `<UI glitch, one integration flaky>` |
| **P4 / Low** | Feature request, cosmetic, documentation | e.g. `<label typo, "would be nice" request>` |

### Response & update commitments (priority × plan tier)

Industry-typical anchors — **set actual targets at the 80th percentile of the team's measured historical response times, then ratchet quarterly.** Never publish an aspirational target.

| Priority | First response (Enterprise) | First response (Standard) | Update cadence |
|----------|---------------------------|--------------------------|----------------|
| P1 | 15–60 min | 1–4 bus. hrs | Every 1–2 h until mitigated |
| P2 | 2–4 bus. hrs | 8 bus. hrs | Daily |
| P3 | 8 bus. hrs / 1 bus. day | 2 bus. days | On change |
| P4 | 2 bus. days | 5 bus. days | On change |

Tiering SLAs by plan is a monetization lever — price the Enterprise column.

### Policy clauses (customer-facing SLA doc must define ALL of these)

1. **Business hours**: timezone, days, holiday calendar.
2. **Response vs resolution**: response SLA is the commitment; resolution times are internal targets only — never promise resolution for undiagnosed bugs.
3. **Clock pauses**: pending-customer stops the clock; state resumption rules.
4. **Breach handling**: auto-escalation to `<support lead>`, then `<founder>` (hierarchical path below).
5. **Exclusions**: beta features, third-party outages, force majeure.
6. **Scope**: what support covers vs professional services.
7. **Measurement & reporting**: how attainment is computed and where it's reported.
8. **Credits/remedies**: enterprise-only, and only after you can measure attainment. Startups: do NOT offer SLA credits until you have ≥1 quarter of measured attainment.

## 3. Escalation matrix

Two orthogonal escalation types — never conflate them:

- **Functional** (complexity): L1 → L2 → L3.
- **Hierarchical** (temperature / revenue / breach): agent → support lead → founder/CEO.

| Trigger | Who engages | Within | Who owns customer comms | Informed |
|---------|-------------|--------|------------------------|----------|
| SLA breach (any priority) | Support lead | 1 h of breach | Original agent | Founder if P1/P2 |
| P1 declared | L2 + support lead | 15 min | Support lead | Founder, on-call eng |
| ARR > `<$X>` at risk | CSM function + founder | Same day | CSM | — |
| Exec complaint | Founder | 4 bus. hrs | Founder | Support lead |
| Legal / security mention | Founder + legal counsel | 1 h | Founder (human-only comms) | — |
| Social media threat | Founder | 4 bus. hrs | Founder | — |

**Minimum escalation packet** (an escalation without it bounces back to sender): repro steps, environment (version/browser/OS/config), logs or error output, screenshots, account ID, business impact statement ("3 enterprise users blocked from `<core workflow>`").

**De-escalation criteria**: workaround delivered and accepted, OR root cause identified with committed fix date, OR customer confirms resolved. Record who de-escalated and why.

**Exec-sponsor path**: each top-`<N>` account gets a named exec sponsor; sponsor engaged on any hierarchical escalation for their account.

The anti-pattern this matrix kills: "escalation = Slack the founder." No matrix, no packet standard, engineers interrupted constantly — the matrix plus the packet spec is the fix.

## 4. Incident process (multi-customer outages)

| SEV | Definition | Comms cadence |
|-----|-----------|---------------|
| SEV1 | Full outage or data loss, all/most customers | Status page ≤30 min; updates every hour; human-reviewed |
| SEV2 | Partial outage, degraded core function | Status page ≤1 h; updates every 2 h |
| SEV3 | Minor degradation | Status page optional; note in next release comms |

Roles: **incident commander** (owns the process, not the fix), comms owner, fixer(s). Post-incident: customer-facing summary within 3 business days (what happened, impact, prevention — no internal blame detail), plus internal post-mortem to `docs/postmortems/`. Data-loss and security incidents: ALL customer comms human-approved — legal exposure.

## 5. Macro library — intent taxonomy

Organize by intent. Per macro define: **trigger conditions · personalization slots (never send unpersonalized) · tone notes · linked KB article · forbidden phrases**.

| Intent | Macros | Forbidden phrases (examples) |
|--------|--------|------------------------------|
| Billing | invoice copy, payment failed, plan change | "just" ("it's just a billing hold") |
| Bug acknowledgment | ack + packet request, known-issue match, fix shipped | "should work now" (verify first), promised fix dates for undiagnosed bugs |
| Feature request | logged + linked to VoC theme | "it's on the roadmap" (unless it truly is) |
| How-to | KB-link-first answer with the article's key steps inline | bare links with no inline answer |
| Outage | initial ack, update, resolution | "we take this seriously" without specifics |
| Churn / cancellation | see hard cases | guilt-tripping |
| Refund | approve (within authority), escalate above limit | ad-hoc amounts outside the authority table |
| Security question | acknowledgment + routing to human | any compliance/certification claim |

### The hard-case set (draft all six — these are the ones that get botched at 2am)

1. **Outage apology**: specific impact, specific timeline, specific prevention step. No "inconvenience this may have caused."
2. **Data-loss incident**: facts only, human-approved before sending, legal review if enterprise accounts affected. Never speculate about cause mid-incident.
3. **Security disclosure response**: thank the reporter, no confirmation/denial of specifics, route to `<security contact>`, committed response date. Human sends.
4. **Saying no to a feature**: honest no beats fake maybe. State the underlying need you heard, why it doesn't fit now, the nearest workaround, and log it to VoC.
5. **Price increase notice**: what changes, when, grandfathering terms, the value added since last price. Send well before renewal — never inside the 30-day window.
6. **Cancellation confirmation with win-back hook**: confirm cleanly and completely (date, data export path, what they keep), then ONE line inviting them back with a named reason to return. Never make cancellation hard — the exit experience is the last impression and the first win-back touch.

## 6. Support QA program

Weekly sampled review — 4–10 tickets per agent per month — against this rubric:

| Dimension | Weight | What good looks like |
|-----------|--------|----------------------|
| Accuracy of resolution | 40% | Right answer; verified, not guessed |
| Process compliance | 25% | Correct tagging, escalation packet complete, KB article linked (KCS) |
| Communication quality | 20% | Clear, matches tone guide, personalized |
| Customer effort caused | 15% | No unnecessary back-and-forth; anticipated the next question |

Scores feed **coaching, not punishment**. Calibrate reviewers monthly on a shared sample. At scale: auto-QA 100% of conversations with AI, human calibration on samples. Fast wrong answers are the failure mode this catches — speed metrics alone hide them.

## 7. Metrics definitions (each with its attached play — no metric without one)

| Metric | Definition | Target basis | Attached play when off-target |
|--------|-----------|--------------|-------------------------------|
| First response time | Ticket created → first human/AI substantive reply | 80th pct of history, ratchet | Staffing/queue review |
| FCR | Resolved in one contact, no reopen ≤7 days | 60–75% at L1 | KB-gap review + coaching |
| Reopen rate | Reopened ≤7 days / resolved | <10% | QA deep-dive on reopened set |
| CSAT | Post-ticket 1–5; good = 75–85%, top quartile ≥90% | Own baseline first | Closed loop on every 1–2 rating within 24 h |
| Deflection success | L0 sessions with no contact ≤7 days | 30–70% by complexity | Article rewrite / bot-scope trim |
| SLA attainment | % responses within commitment | ≥95% before any contractual SLA | Breach auto-escalation + target review |

Verify current benchmark numbers via WebSearch when drafting — these date fast.
