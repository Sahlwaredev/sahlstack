# Incident Response & Breach Notification Playbook

Reference templates for `/compliance --incident`. The plan's one job under pressure:
surface the SHORTEST applicable clock, with a named human owner, before anyone starts
improvising. Statutory/contractual clocks below are as of 2026-07 — verify via WebSearch
before relying; state matrices in particular change.

## §1 IR plan structure

1. **Purpose & scope** — systems, data, and people covered; relationship to the security
   incident process (this plan owns the compliance/breach track; technical containment
   overlaps with security runbooks — cross-ref `/cso` findings for detection reality).
2. **Roles** — incident commander, technical lead, comms lead, legal/compliance lead,
   scribe. Named humans + deputies, with an on-call reference. The plan fails if roles are
   titles without names.
3. **Severity classification:**

```
SEV1  Confirmed compromise of production or customer data; service down.
SEV2  Suspected compromise; degraded service; vulnerability actively exploitable.
SEV3  Contained single-system issue; no evidence of data access.
SEV4  Near-miss / policy violation without system impact.

PERSONAL-DATA FLAG: at ANY severity, if personal data may be involved →
escalate to the BREACH TRACK (§2) immediately. The breach clocks run on
*awareness*, not on incident closure.
```

4. **Phases** — detect → triage/classify → contain → investigate → eradicate → recover →
   notify (breach track, §2) → post-incident review (§4).
5. **Evidence preservation** — from first triage: preserve logs (snapshot before rotation),
   record timeline in UTC, no destructive remediation before imaging affected systems if
   compromise is suspected. Chain of custody if law enforcement is plausible.
6. **Privilege discipline** — engage counsel BEFORE forensics; counsel retains the
   forensics firm so the report has a shot at privilege. Written comms during an incident:
   facts, not speculation ("possible unauthorized access to X" not "we got owned").
   Retainers for outside counsel and a forensics firm are established in peacetime —
   human to-do, flagged in the handoff.
7. **Communication matrix** — who may speak to whom: customers (only approved statements),
   press (comms lead only), regulator (counsel), insurer (per policy terms), internal
   (sitrep cadence).

## §2 Breach notification decision tree — all the clocks

Every clock is human-owned. The tree runs top-down at incident awareness and re-runs as
facts develop. Document every step even when the answer is "no notification required" —
GDPR requires recording non-notified breaches too (Art. 33(5)).

```
START: security incident confirmed or suspected
  │
  ├─ Q1: Is personal data involved (any system in the data map)? 
  │      NO → standard IR; document the analysis and STOP here.
  │      UNKNOWN → treat as YES until ruled out; clocks may already be running.
  │
  ├─ Q2: Is it a "personal data breach" (GDPR Art. 4(12): breach of security leading to
  │      destruction, loss, alteration, unauthorized disclosure or access)?
  │      YES ↓
  │
  ├─ Q3: CONTRACTUAL CLOCKS FIRST — check the signed-DPA inventory.
  │      ⏰ CLOCK: customer breach notice — often 24–48h from awareness, per each DPA —
  │      OWNER: <name> — SOURCE: each signed DPA §. Usually the SHORTEST clock in play.
  │
  ├─ Q4: GDPR risk assessment — risk to individuals' rights and freedoms?
  │      Unlikely risk → no SA notice; DOCUMENT the assessment (Art. 33(5)).
  │      Risk        → ⏰ CLOCK: notify supervisory authority within 72 HOURS of
  │                    awareness — OWNER: <name> + counsel — SOURCE: GDPR Art. 33.
  │                    Phased notification is allowed if facts incomplete — never wait
  │                    for the full picture past 72h.
  │      HIGH risk   → also notify individuals "without undue delay" — Art. 34 —
  │                    unless an exception applies (effective encryption, subsequent
  │                    measures, disproportionate effort → public notice).
  │
  ├─ Q5: US state matrix — for each state with affected residents: AG notice thresholds
  │      (many at 500+/1000+ residents), individual notice timing (ranges from "most
  │      expedient" to fixed 30/45/60-day outer bounds), content requirements.
  │      ⏰ CLOCK: per-state — OWNER: <name> + counsel — SOURCE: state statutes.
  │      Build the affected-resident count by state early; it drives everything.
  │
  ├─ Q6: Sector clocks —
  │      HIPAA (as business associate): ⏰ notify the covered entity without unreasonable
  │      delay, ≤60 days — SOURCE: 45 CFR 164.410. Covered entity handles HHS/individuals.
  │      PCI: notify acquirer/card brands per program rules if card data involved.
  │      Publicly-listed customers may have their own SEC-driven timelines — their
  │      problem, but your notice enables it.
  │
  ├─ Q7: Cyber insurer — ⏰ notice per policy (late notice can void coverage) —
  │      OWNER: <name> — SOURCE: policy. Use panel vendors if required by the policy.
  │
  └─ Q8: Law enforcement — counsel's call; may lawfully delay some individual notices
         (document the request).
```

**Role check:** if we are the PROCESSOR for the affected data, our statutory GDPR duty is
Art. 33(2): notify the controller (our customer) without undue delay — the customer runs
the SA/individual analysis. The contractual clock (Q3) still binds. If we are the
CONTROLLER, the full tree applies to us.

## §3 Notification templates (draft skeletons — counsel reviews before ANY send)

1. **SA notification (Art. 33 content):** nature of the breach (categories + approximate
   numbers of subjects and records); DPO/contact point; likely consequences; measures
   taken/proposed. Phased-notification header if facts incomplete.
2. **Individual notice (Art. 34 / state statutes):** plain language; what happened, what
   data, what we did, what they should do (specific: password reset, credit monitoring
   offer where customary), contact channel. State statutes add content requirements —
   counsel merges per state.
3. **Customer (DPA) notice:** facts known, systems/data affected as relates to THEIR data,
   containment status, point of contact, commitment to updates. Send within the
   contractual window even if investigation is early — "initial notice, investigation
   ongoing."
4. **Internal sitrep:** UTC timeline, current severity, clock dashboard (every ⏰ with
   owner and time remaining), next update time.

## §4 Post-incident review (blameless)

Within 2 weeks of closure: timeline reconstruction; root cause (5-whys, no names attached
to blame); what worked / what didn't; clock performance (did we meet every deadline —
if not, why); control gaps → fed into the gap assessment and risk register; plan updates;
follow-up owners and dates. File as `docs/enterprise/compliance/postmortem-<date>.md` and
reference from INDEX.md.

## §5 Tabletop exercise script (AI scripts it, humans run it)

Cadence: 2x/year minimum; run one within 30 days of adopting this plan. 60–90 minutes.

**Format:** facilitator (human) reads injects; participants respond in role; scribe logs
decisions and time-to-decision; no screens-shared heroics — decisions and comms only.

**Scenario skeleton (customize to the actual stack from the data map):**

```
T+0    INJECT 1: Support ticket — a customer says another tenant's data appeared in
       their export. (Tests: triage, severity call, personal-data flag.)
T+15   INJECT 2: Engineer confirms a query bug exposed rows across tenants for ~3 weeks.
       Logs exist for 14 days only. (Tests: awareness moment — clocks start NOW;
       evidence preservation; scope estimation with imperfect logs.)
T+30   INJECT 3: Affected data includes EU residents and two enterprise customers whose
       DPAs require 24h notice. (Tests: shortest-clock discipline, counsel engagement,
       customer-notice drafting under time pressure.)
T+45   INJECT 4: A customer tweets about it. (Tests: comms matrix, holding statement,
       who speaks.)
T+60   DEBRIEF: every clock — met? owner knew they owned it? counsel in before
       forensics? notice drafts usable? plan gaps → action items with owners.
```

**Scorecard:** time to severity call · time to counsel · time to clock inventory ·
quality of first customer notice · gaps found. File results with the post-incident
review template.
