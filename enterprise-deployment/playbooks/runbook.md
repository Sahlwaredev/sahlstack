# Playbook: Deploy, Rollback & Incident Runbook

Templates for `/deployment --runbook`. The runbook's law: **executable by one sleepy
person**. Every step is a copy-paste command or an unambiguous decision with the answer
precomputed. Generic advice ("check the logs") is a defect; `fly logs -a <app> | grep
ERROR` is the bar. Bind every step to the real stack from the Deployment Plan.

---

## 1. Deploy runbook template (per environment)

```markdown
## Deploy: <environment>

**Standard path:** /land-and-deploy #<PR> <prod-url> — merge, CI wait, deploy wait,
canary verification. Use it unless it is unavailable.

**Manual fallback:**
1. Preconditions: <CI green on main · readiness GO if major class · approver sign-off per plan>
2. Deploy: `<exact command — e.g. fly deploy -a <app> --strategy rolling>`
3. Expected timing: <n> min build, <n> min rollout. If >2× expected → §2 tree, do not re-run blindly.
4. Verify: `curl -sf <health-url>` · /canary <url> --quick · <the one business-metric check>
5. Record: deploy time, SHA, who watched. First <n> hours: <named watcher>.
```

## 2. Rollback decision tree

Precompute the decision — 2 a.m. is not when you weigh trade-offs.

```
Symptom detected (alert, canary, customer report)
│
├─ Is prod down or actively corrupting data?
│   ├─ YES → ROLL BACK NOW (§3, by change class). Break-glass applies. Announce (§5).
│   └─ NO ↓
├─ Did the last deploy plausibly cause it? (deploy < 24h ago, symptom matches surface)
│   ├─ NO → not a rollback situation → incident path (§5), investigate
│   └─ YES ↓
└─ Is a fix obvious, tiny, and testable in < 30 min?
    ├─ YES → roll FORWARD (hotfix class per plan) — but set a 30-min timer;
    │        timer fires with no fix shipped → ROLL BACK.
    └─ NO → ROLL BACK (§3).
```

## 3. Rollback steps by change class

```markdown
| Class | Path | Command | Caveats |
|---|---|---|---|
| Code-only | redeploy previous release | `<e.g. fly releases rollback / vercel rollback / redeploy prior image tag>` | safe; do it early |
| Config/env | restore previous value | `<platform secret/config command>` | record what changed; drift is a finding |
| Migration (expand phase) | roll back code only | code path above | expand-phase schema is backward-compatible BY DESIGN — verify plan followed |
| Migration (contract/destructive) | **no clean rollback** | restore-from-backup path: `<exact restore command + expected duration>` | this is why destructive migrations ship in their own release, after the code release is proven |
```

**Rollback drill rule:** a rollback that has never been executed is a hypothesis. The
plan's human to-do includes one supervised drill per class; the runbook records the date
each path was last exercised — `Last drilled: <date | NEVER (flagged)>`.

## 4. Canary & monitoring plan template

```markdown
| What | Tool | Threshold | Where alerts land |
|---|---|---|---|
| Pre-deploy baseline | /canary <url> --baseline | — | .gstack/canary-reports/ |
| Post-deploy check | /canary <url> (or --quick) | console errors 0 · perf within <n>% of baseline | run output; watcher |
| Uptime | <uptime tool per plan> | <n> failures in <n> min | <channel> |
| Error rate | <log/APM tool per plan> | > <n>/min sustained <n> min | <channel> |
| The business metric | <e.g. signups, checkouts per hour> | drop > <n>% vs same hour last week | <channel> |
```

Day-one minimum: uptime + error rate + one business metric. More dashboards than the team
will look at is decoration.

## 5. Incident basics (right-sized)

**Severity — small-team version:**

| Sev | Definition | Response |
|---|---|---|
| 1 | prod down / data at risk / security breach | drop everything; §2 tree; announce within 30 min |
| 2 | degraded for many users | fix or roll back same day; announce if customer-visible |
| 3 | annoying, contained | issue + next release |

**Comms template (Sev 1–2, customer-visible):**

```
[<time>] We're investigating <symptom> affecting <who>. Updates every <n> min.
[<time>] Cause identified: <one line>. Fix: <rolling back | deploying fix>. ETA <time>.
[<time>] Resolved as of <time>. Root cause and prevention to follow.
```

**After every Sev 1–2:** post-mortem in `docs/postmortems/<YYYY-MM-DD>-<slug>.md` (company
convention — blameless, timeline, root cause, prevention items as issues). Deploy-caused
incidents feed the next `/deployment --audit`; two incidents from the same cause with no
prevention shipped is itself a BLOCKING audit finding.

## 6. Runbook assembly

Order: §1 per environment (prod first), §2 tree, §3 table, §4 monitoring, §5 incidents.
Header per Phase 6 (`runbook-<date>.md`, review gate: AI-final). Every `<...>` placeholder
resolved from the Deployment Plan and the real stack — a runbook with unresolved
placeholders fails the 2 a.m. test and does not ship.
