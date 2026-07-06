# Certifications & Trust Program Playbook

Reference templates for `/compliance --certify` and `--respond`. Language discipline
applies everywhere: SOC 2 is an **attestation report** by a licensed CPA firm — never
"certified." ISO 27001 IS a certification (by an accredited body). HIPAA and GDPR have no
certification at all. Facts as of 2026-07 — verify via WebSearch before relying.

## §1 Framework selection & sequencing

| Framework | What it is | Get it when | Who signs off |
|---|---|---|---|
| SOC 2 Type I | Attestation: control DESIGN at a point in time | A deal needs something in ~6–10 weeks | Licensed CPA firm |
| SOC 2 Type II | Attestation: OPERATING effectiveness over a window (6-month first window is the startup norm; annual after) | US SaaS buyers ask for this — the default target | Licensed CPA firm |
| ISO 27001:2022 | Certified ISMS (information security management system); 2022 revision mandatory since Oct 31, 2025 | EU/APAC enterprise buyers; 6–12 months standalone, 4–6 with SOC 2 in hand (~70–80% control overlap) | Accredited certification body; 3-year cycle, annual surveillance |
| HIPAA | Posture only — **no certification exists** | You touch PHI as a business associate. BAA before any PHI flows, including subcontractors and cloud providers | Nobody certifies it; OCR enforces. Security risk analysis is the #1 enforcement finding when missing |
| PCI-DSS 4.0.x | Self-assessment or QSA audit | Card data. Strategy = scope minimization: hosted fields/iframes (Stripe class) → SAQ A; never store or proxy PANs | Level 1 requires QSA ROC |
| ISO/IEC 42001 | Certified AI management system | AI is the product and enterprise procurement asks | Accredited body |

**Sequencing advice:** SOC 2 Type I → Type II first; build the common-controls matrix once
(one control, many frameworks); add ISO 27001 for EU/APAC enterprise; ISO 42001 if AI is
the product; HIPAA only with actual PHI; PCI-scope-minimize always.

## §2 SOC 2 readiness gap assessment structure

Trust Services Criteria: **Security (Common Criteria) is mandatory**; Availability,
Confidentiality, Processing Integrity, Privacy are optional. Startup-typical scope:
Security + Availability + Confidentiality. Take the Privacy TSC only with a real privacy
program (run `--privacy` first).

Document structure:

1. **Scope statement** — product/systems in scope, TSCs selected, rationale.
2. **Methodology** — evidence sources (repo, /cso report, interviews), evidence-status
   convention, assessment date.
3. **Per-criterion findings** across CC1–CC9:

```
CC ref | Criterion summary | Current state (+ evidence status) | Gap | Risk | Remediation | Owner | Effort/date
```

CC-series map (assess each):
- **CC1 Control environment** — org structure, board/management oversight, background
  checks, code of conduct, competence.
- **CC2 Communication & information** — policies communicated, internal reporting lines,
  customer commitments documented.
- **CC3 Risk assessment** — documented risk assessment process, fraud risk, change-driven
  re-assessment.
- **CC4 Monitoring activities** — control monitoring, internal audit/review cadence,
  deficiency remediation tracking.
- **CC5 Control activities** — controls selected/deployed to mitigate assessed risks;
  technology general controls; policies operationalized.
- **CC6 Logical & physical access** — SSO/MFA, RBAC, least privilege,
  joiner-mover-leaver, quarterly access reviews, encryption, key management,
  physical/datacenter (usually inherited from cloud provider — say so and reference their
  SOC 2).
- **CC7 System operations** — vulnerability management (SLA by severity: critical 7–15
  days, high 30), logging/alerting, incident detection and response, backup/DR.
- **CC8 Change management** — secure SDLC, code review, CI/CD controls, emergency change
  path, infrastructure change control.
- **CC9 Risk mitigation** — vendor/third-party risk management, business disruption
  mitigation, cyber insurance consideration.

4. **Maturity summary** — per CC series: operating / documented-not-operating / absent.
5. **Prioritized 90-day roadmap** (§5).
6. **Audit-timing recommendation** — Type I vs straight to Type II window; the key rule:
   **distinguish "write the policy" gaps (days) from "stand up the control" gaps
   (quarters)** — quarterly access reviews need two quarters of evidence before an auditor
   can sample them. Never recommend an audit date the evidence can't support.
7. **Tooling** — compliance automation platform (Vanta/Drata/Secureframe class) evaluation.
   Iron rule: **compliance tool ≠ compliance** — a green dashboard with controls documented
   but not operated fails audit sampling and is a named failure mode.

Cross-reference `/cso`: technical control claims (CC6, CC7) should cite a `/cso` report as
[V] evidence wherever one exists. The gap assessment consumes security findings; it never
re-scans.

## §3 ISO 27001:2022 Statement of Applicability (SoA)

The SoA covers all **93 Annex A controls** in 4 themes: organizational (37), people (8),
physical (14), technological (34). New-in-2022 controls auditors probe: threat
intelligence (5.7), cloud security (5.23), ICT readiness for business continuity (5.30),
data leakage prevention (8.12), secure coding (8.28), web filtering (8.23), configuration
management (8.9), information deletion (8.10), data masking (8.11), monitoring activities
(8.16).

SoA row format:

```
Control ref | Control name | Applicable? (Y/N) | Justification (for inclusion AND exclusion)
| Implementation status | Evidence ref | Common-controls matrix link (SOC 2 CC ref)
```

Exclusions need real justification ("no physical offices — controls 7.x scoped to home
working policy" is fine; "N/A" alone fails Stage 1).

Mandatory ISMS documents beyond the SoA: ISMS scope; information security policy; risk
assessment methodology + results; risk treatment plan; objectives; competence/awareness
evidence; internal audit programme + results; management review minutes; nonconformity and
corrective action records.

Path: ISMS scope → risk methodology → risk treatment plan → SoA → mandatory docs →
internal audit + management review → Stage 1 (documentation) → Stage 2 (implementation) →
certificate → surveillance audits annually.

## §4 Information security policy suite (12–18 documents)

Baseline list — draft only statements matching verified/asserted practice; unmet
statements are [P] with target dates, and the document ships flagged "aspirational
sections present — not audit-ready":

1. Master information security policy
2. Acceptable use policy
3. Access control policy (RBAC, least privilege, joiner-mover-leaver, quarterly reviews)
4. Data classification & handling policy
5. Encryption & key management policy (TLS 1.2+, AES-256, key rotation)
6. Secure development policy (code review, dependency management, secrets handling)
7. Change management policy
8. Vulnerability management policy (severity SLAs)
9. Incident response policy (summary — the full plan lives in incident-response.md)
10. Business continuity & disaster recovery policy (RTO/RPO defined, tested annually)
11. Vendor / third-party risk management policy
12. Data retention & disposal policy
13. Physical security policy (right-sized: remote-first = home working + device controls)
14. HR security policy (background checks, onboarding/offboarding, training)
15. AI acceptable use policy (2025+ standard: approved tools, no confidential data into
    unapproved models, output review)

**Metadata block on every policy — auditors check this as much as content:** purpose,
scope, roles & responsibilities, policy statements, exceptions process (with an exception
register), review cadence (annual minimum), named owner, version history, approval
signature line.

## §5 90-day roadmap skeleton

- **Weeks 1–2:** policy suite drafts approved; quick technical wins (enforce MFA
  everywhere, enable audit logging, endpoint management rollout begins); open the
  exception register.
- **Weeks 3–8:** stand up operating controls — access review #1 executed, vulnerability
  scanning + SLAs live, vendor review process run against the current vendor list,
  background-check process live, DR test scheduled, security awareness training delivered.
- **Weeks 9–12:** evidence accumulation and hygiene (screenshots, exports, tickets —
  dated, owner-attributed); auditor selection (licensed CPA firm — get 2–3 quotes; confirm
  AICPA peer review); system description draft (Section III — describe only what
  engineering actually does; overpromising here is the classic audit failure); Type II
  observation window opens.

Every roadmap item: owner, date, evidence artifact it will produce.

## §6 Security questionnaire answer library (`--respond`)

Canonical answer library keyed to SIG Lite / CAIQ v4 topic areas, stored at
`docs/enterprise/compliance/questionnaire-library.md`. Per entry:

```
Topic key | Canonical question | Canonical answer | Evidence status + source | Last verified | Notes/variants
```

**Answering rules (iron laws):**
1. **Never aspirational as present tense.** "Planned Q3 2026" when it's planned — never
   "yes." Misstatements become contractual representations and post-breach fraud exposure.
2. Gap answers use the three-part form: honest state + compensating control + remediation
   date. Buyers accept gaps; they don't forgive fiction.
3. Every answer's evidence status is tagged; [A] answers go on the human sign-off list in
   the cover memo.
4. Truth reconciliation: answers must match the privacy policy, DPA, trust center, and
   system description. One inconsistency undermines the whole response.
5. Certifications section: exact language only — "SOC 2 Type II report available under
   NDA, period ending <date>" / "ISO 27001:2022 certificate, <body>, expires <date>" /
   "HIPAA: no certification exists; safeguards aligned to the Security Rule, BAA
   available." Never pad this section.
6. A human sends the response. Always.

**Trust center content set** (when asked): subprocessor list with change-notification
signup, certifications/attestations actually held, pen test summary (not the report),
policy list, uptime/status page link, security contact.
