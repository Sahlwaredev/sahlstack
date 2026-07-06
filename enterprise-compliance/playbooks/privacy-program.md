# Privacy Program Playbook

Reference templates for `/compliance --privacy`. Every artifact built from these templates
follows the prime directives: evidence-status tags on every claim, as-of dates on every
regulatory fact, truth reconciliation across all artifacts before shipping.

Regulatory facts in this playbook are as of 2026-07. Verify via WebSearch before relying —
this area changed monthly through 2025–26.

## §1 Data mapping method

The map is built from evidence, refreshed quarterly and on every new vendor or feature.

**Step 1 — enumerate systems** (repo first, then confirm with the human):

| Source of evidence | What it reveals |
|---|---|
| Dependency manifests | SaaS SDKs: analytics, error tracking, payments, LLM providers, auth |
| .env.example / infra files | Vendors with credentials; hosting regions |
| docker-compose / terraform | Databases, queues, warehouses, backup targets |
| Marketing site + app UI | Tracking tags, forms, chat widgets |
| Human confirmation | CRM, support desk, spreadsheets, email tools — code can't see these |

Always include the four systems teams forget: **logs, backups, the data warehouse, and
vendor sub-systems** (your vendor's subprocessors).

**Step 2 — per-system record** (one row per system × purpose):

```
System | Data categories | Special-category flag | Data subjects | Purpose | Legal basis
| Source | Recipients/vendors | International transfer + safeguard | Retention + trigger
| Security measures ref | Deletion capability (honest: full / partial / none) | Evidence status
```

The **deletion capability** column is mandatory and honest. "Deletion runs on prod only" is
a finding, not a footnote — it drives the DSAR procedure and the retention schedule.

**Step 3 — reconcile**: every vendor in the map needs a DPA (data processing agreement) on
file and an entry on the published subprocessor list. Missing DPA = finding.

## §2 RoPA structure (GDPR Art. 30)

Maintain as a table/sheet, not prose. The RoPA is a **view over the data map** — never
invent rows the map doesn't support. The Art. 30(5) small-enterprise exemption is narrow
(non-occasional processing disqualifies) — assume the RoPA is required.

Controller record — Art. 30(1), one row per processing activity:

```
Activity ID | Activity name | Role (controller/joint/processor) | Purpose
| Legal basis (+ LIA ref if legitimate interests) | Data subject categories
| Data categories (+ special-category flag) | Source | Internal owner | Systems
| Recipients | Transfers outside EEA + safeguard (SCC module / adequacy / DPF)
| Retention period + trigger | Security measures ref | DPIA required? done? link
| Last reviewed (date)
```

Processor record — Art. 30(2) (when acting as processor for customers): controller name,
processing categories, transfers + safeguards, security measures ref.

Role accuracy check per row: are we controller or processor for THIS flow? SaaS vendors are
usually processors for customer-content data but controllers for their own billing,
marketing, and product-analytics data. Misclassification cascades into the DPA and policy.

## §3 Legal-basis assignment

One basis per purpose, assigned deliberately. **"Consent for everything" is a failure** —
consent is withdrawable, so anything the service can't function without must not rest on it.

| Purpose class | Default basis | Notes |
|---|---|---|
| Providing the service a user signed up for | Contract necessity (Art. 6(1)(b)) | Strictly necessary only — product analytics is NOT contract necessity |
| Security, fraud prevention, service improvement | Legitimate interests (Art. 6(1)(f)) | Requires a documented LIA |
| Marketing emails, non-essential cookies, sensitive data | Consent (Art. 6(1)(a)) | Must be as easy to withdraw as to give |
| Tax records, legal holds | Legal obligation (Art. 6(1)(c)) | Cite the actual obligation |

**LIA (legitimate interests assessment) — three tests, documented per purpose:**
1. Purpose test: is the interest real and articulated (not "business reasons")?
2. Necessity test: is there a less intrusive way to achieve it?
3. Balancing test: would the data subject reasonably expect this? What's the harm if it
   goes wrong? Mitigations (minimization, pseudonymization, opt-out)?
Outcome: proceed / proceed with mitigations / do not proceed. Signed, dated, filed.

US state overlay: sensitive data needs **opt-in consent** in most states vs California's
right-to-limit model. Build to the strictest common denominator (California + Maryland's
data-minimization standard) rather than per-state logic.

## §4 DSAR pipeline

DSAR = data subject access request; covers access, deletion, correction, portability,
opt-out. One procedure covering all regimes, keyed to the shortest clock.

```
1. INTAKE      Dedicated channel (privacy@ + in-product form). Monitored — a named owner
               checks it on a defined cadence. Log: date received (clock starts), channel,
               request type, regime.
2. VERIFY      Identity verification proportionate to sensitivity. Never demand more data
               than needed to verify. Authorized-agent requests (CCPA): verify agency.
3. SCOPE       Which subject, which systems (from the data map — the map IS the search
               index), which request type. Exemptions screen: legal holds, others' privacy,
               trade secrets — document any exemption relied on.
4. SEARCH      Every mapped system holding that subject's data, including warehouse and
               vendor systems (use vendor DSAR APIs/consoles). Backups: follow the
               documented roll-off policy; disclose the approach in the response.
5. REVIEW      Redact third-party data. Legal review only for edge cases.
6. RESPOND     Within the clock. Include appeal process where required (many US states).
7. LOG         Everything: dates, scope, systems searched, exemptions, response sent.
               The log is the evidence that the pipeline operates.
```

⏰ CLOCK: GDPR response — 1 month from receipt, extendable +2 months for complexity (notify
within the first month) — OWNER: assign — SOURCE: GDPR Art. 12(3).
⏰ CLOCK: CCPA response — 45 days, extendable +45 (notify) — OWNER: assign — SOURCE: CCPA
§1798.130. Opt-out of sale/share: honor within 15 business days.
⏰ CLOCK: GPC signals — treat as a valid opt-out in California and several other states;
honoring must be automatic, not ticketed.

Deletion honesty rule: the response describes what actually happens ("deleted from
production systems within X days; backup copies roll off within Y days per our retention
schedule") — never claim instant total erasure the architecture can't deliver.

## §5 Privacy policy (external notice) skeleton

Superset satisfying GDPR Arts. 13–14 + CCPA. **Quality bar: describes actual verified
practice — every claim traceable to a data-map row.** Sections:

1. Who we are — identity, contact; EU/UK representative and DPO if designated.
2. What we collect — categories (use the CCPA statutory taxonomy for the US section), with
   sources and purposes. Per-category, not a wall of "including but not limited to."
3. Legal bases per purpose (EU section) — mirrors §3 assignments exactly.
4. Who receives it — vendor categories, whether anything is "sold" or "shared" (CCPA terms
   of art — targeted advertising counts as "sharing"), link to subprocessor list.
5. International transfers — mechanisms actually in place (SCCs, DPF participation only if
   the self-certification is real and current).
6. Retention — criteria per category, consistent with the map's retention column.
7. Your rights — per regime, how to exercise, appeal process, non-discrimination.
8. Opt-outs — "Your Privacy Choices" link, GPC statement (only if actually honored).
9. Children — actual stance (COPPA if under-13 users are possible).
10. Security — accurate, modest statement. Never enumerate controls you can't evidence.
11. Changes — notice procedure for material changes; effective date + archive of prior
    versions.

Ban list: any control or practice tagged [P]; "military-grade encryption"; "we never share
your data" (you have processors); "GDPR compliant/certified" as a badge.

## §6 Cookie & consent pack

1. **Cookie audit table:** tag/cookie | provider | category (strictly necessary / functional
   / analytics / advertising) | fires pre-consent today? (test it — this is the CPPA
   settlement fact pattern) | data sent | duration.
2. **CMP config spec:** prior consent for non-essential in EU/UK (ePrivacy); reject-all as
   prominent as accept-all (no dark patterns); per-category toggles; consent state passed to
   tag manager so tags actually gate on it (banner theater = tags fire regardless — test
   post-config); re-consent on material change.
3. **GPC handling spec:** detect the header/signal, apply as opt-out of sale/share for the
   relevant states, record it like any consent event.
4. **Consent record schema:** subject/device ID, timestamp, policy version, granular
   choices, mechanism, withdrawal events. Retained as evidence.

## §7 DPIA template (GDPR Art. 35; same skeleton serves CCPA risk assessments)

Trigger screening on every new high-risk processing — BEFORE build. EDPB nine criteria:
evaluation/scoring, automated decisions with legal/significant effect, systematic
monitoring, sensitive data, large scale, matching/combining datasets, vulnerable subjects,
innovative tech, blocking rights/service access. **Two or more = DPIA required.**

```
1. SCREENING RECORD   Criteria hit, decision, date, screener.
2. DESCRIPTION        Systematic description: data flow diagram, categories, subjects,
                      recipients, retention, technology involved.
3. CONSULTATION       DPO opinion (documented, even if overridden — overrides must be
                      recorded); data subjects where appropriate.
4. NECESSITY &        Why this processing, why this much data, why no less-intrusive
   PROPORTIONALITY    alternative works.
5. RISK ASSESSMENT    Per risk: source → event → impact ON INDIVIDUALS (not corporate
                      risk) → likelihood × severity, pre-mitigation.
6. MITIGATIONS        Per risk: measure → residual risk.
7. OUTCOME            Proceed / proceed with measures / prior supervisory-authority
                      consultation required (if residual risk remains high).
8. SIGN-OFF           Named approver, date, review date.
```

CCPA deltas (as of 2026-07 — verify current CPPA regs): risk assessments required for
targeted advertising, sale/share, profiling, and sensitive-data processing; filing
obligations with the CPPA apply — the filing itself is a human officer action.
