# Playbook: Greenfield Deployment Design

Templates for `/deployment --design`. The output is the **Deployment Plan** — the plan of
record every other deployment artifact, the readiness gate, and the AgentForce
deploy-manager workflow read. `--audit` produces the same plan template (§5) from a
verified current state instead of a green field.

---

## 1. Stack decision matrix

Two to three real candidates, scored 1–5 per criterion. Weights are set by the foundation
(blast radius and team reality outweigh unit cost at small scale).

```markdown
## Stack decision — <date>

| Criterion (weight) | <Candidate A> | <Candidate B> | <Candidate C> |
|---|---|---|---|
| Workload fit (×3) — runs the actual shape (web/API/workers/static/jobs) | | | |
| Team operability (×3) — can THIS team debug it at 2 a.m.? | | | |
| Cost at launch (×2) — from §2 table | | | |
| Cost at 10× (×2) — from §2 table | | | |
| Lock-in / exit cost (×1) — what does leaving cost? | | | |
| Ecosystem fit (×1) — existing accounts, credits, tooling | | | |
| **Weighted total** | | | |

**Recommendation:** <candidate> because <one sentence per decisive criterion>.
**Rejected:** <candidate> — <reason>. <candidate> — <reason>.
(Recorded so "why aren't we on X?" has an answer a year from now.)
```

Candidate-set heuristics (eliminate before scoring):

| Workload shape | Natural candidate class |
|---|---|
| Static site / SPA + light API | Vercel/Netlify/Cloudflare Pages class |
| Web app + DB + background jobs | Fly/Render/Railway PaaS class |
| Long-running compute, custom networking, compliance isolation | A cloud provider (only with the named requirement written down) |
| Already containerized, team runs Docker daily | PaaS-with-Dockerfile first; k8s only past a named scale/isolation requirement |

Rules: no candidate enters the matrix without current WebSearch-verified pricing; "we
might need k8s later" is not a requirement; managed beats self-hosted until a named
requirement says otherwise.

## 2. Cost model template

Prices dated, from published pricing pages — never from memory.

```markdown
## Cost model — prices as of <date>

| Line item | Launch scale | 10× scale | Notes / traps |
|---|---|---|---|
| Compute (app) | $ /mo | $ /mo | instance class × count |
| Database | $ /mo | $ /mo | per-environment DBs multiply this |
| Bandwidth / egress | $ /mo | $ /mo | the classic surprise — state the GB assumption |
| CI minutes | $ /mo | $ /mo | private-repo minutes; per-seat charges |
| Standing non-prod environments | $ /mo | $ /mo | each standing env ≈ <n>% of prod cost |
| Monitoring / logs | $ /mo | $ /mo | log volume pricing at 10× |
| **Total** | **$ /mo** | **$ /mo** | Foundation ceiling: $<n>/mo — <within / over, argued below> |
```

## 3. Environments & branching

**Right-sizing default by stage** (deviate only with a named reason):

| Stage | Environment set | Why |
|---|---|---|
| Pre-revenue, ≤3 people | Local dev + PR preview deploys + prod | Standing envs cost money and drift; previews give per-change isolation free |
| First customers | + one staging/beta (prod-shaped, prod-sized-down) | A place for migration rehearsal and beta users |
| Growing, 10+ people | dev/test/beta/prod as the plan demands | Parallel workstreams justify standing envs |

**Branching default:** trunk-based / GitHub Flow — short-lived branches → PR (review + CI
green enforced by branch protection) → `main` → promotion by deploy, not by long-lived
branches. GitFlow-style release branches only for a named constraint (regulated release
trains, versioned on-prem releases). Record the branch→environment map:

```markdown
| Branch / event | Environment | Deploy trigger |
|---|---|---|
| PR opened/updated | preview | automatic |
| merge to main | dev (or staging) | automatic |
| <promotion event per plan> | beta | <gate per §4> |
| <promotion event per plan> | prod | <gate per §4> |
```

## 4. Promotion gates template

Every promotion gets a row. **Prod approval is a blocking human by default**; relaxing it
is an explicit, dated plan revision.

```markdown
| Promotion | Entry criteria | Verification | Approval | Rollback trigger |
|---|---|---|---|---|
| PR → main | /review pass, CI green, /qa when UI | branch protection | automatic (the PR review IS the gate) | revert PR |
| main → beta | CI green on main | smoke suite, /canary --quick | automatic OR <name> | redeploy previous release |
| beta → prod | readiness verdict GO (for classed releases) | /canary vs baseline, health endpoint | **BLOCKING: <named human>** | runbook rollback tree |
```

**Break-glass:** for a production emergency, <named role> may bypass <which gate> by
<mechanism>; the bypass MUST be recorded as an issue titled `break-glass: <what> <date>`
within 24h, and the next `--audit` reviews every break-glass. A gate nobody can bypass in
an outage is an outage prolonger; a bypass nobody records is not a gate.

**Release classification** (calibrates which gates apply):

| Class | Definition | Gates |
|---|---|---|
| Standard | routine change | the table above |
| Hotfix | prod is broken now | break-glass path; retroactive readiness note |
| Major | migration, pricing, launch-worthy, or claims-changing | + `--readiness` mandatory before prod |

## 5. Deployment Plan template (the plan of record)

```markdown
# Deployment Plan — <product>
> Generated by `/deployment` (Deployment Team) — <YYYY-MM-DD>
> Engagement: <--design | --audit> · Status: DRAFT — pending human review
> Review gate: Human review recommended

## Summary
<3–5 sentences: stack, environments, promotion shape, the one risk the founder must own>

## Stack decision
<§1 matrix + recommendation + rejected candidates>

## Cost model
<§2 table + ceiling verdict>

## Environments
<per environment: purpose, platform target, config/secrets source, data isolation rule>

## Branching & promotion
<§3 map + §4 gates table + break-glass + release classification>

## Rollback design
<per change class (code / config / migration): the path; migration rule: expand/contract —
destructive migrations ship in two releases, never one>

## Verification & monitoring
<post-deploy verification bound to /canary; day-one monitoring: uptime, error rate, the
one business metric; where alerts land>

## Execution wiring
| Stage | Executor |
|---|---|
| Deploy config persisted | /setup-deploy → CLAUDE.md |
| PR creation | /ship |
| Pre-merge quality | /review, /qa, /cso (per class) |
| Merge + deploy + verify | /land-and-deploy (human-run) or AgentForce deploy-manager (Company tier, gated) |
| Post-deploy watch | /canary |
| Release gate | /deployment --readiness (major class) |

## Revisit triggers
- <date +90d> — plan review (or on: platform pricing change, first 10× traffic day,
  first paying SLA, team size doubling)

## Human to-do
- [ ] Approve this plan (risk posture)
- [ ] <accounts, billing, secrets, branch protection, DNS — per engagement>
- [ ] First supervised deploy + first rollback drill
```
