# Deployment Team Process

Every deployment engagement at a company using AgentForce enterprise teams follows this
process. The goal is plan-first, gated shipping: an agreed deployment plan before any
pipeline work, blocking human approvals on production until the plan says otherwise, a
rollback path designed before every deploy — and execution that reuses the engineering
skills (`/setup-deploy`, `/ship`, `/land-and-deploy`, `/canary`) instead of duplicating
them.

## Overview

```
                          ┌──────────────────────────────────────────┐
                          │ FOUNDATION                               │
                          │ docs/enterprise/foundation.md            │
                          │ docs/enterprise/deployment/foundation.md │
                          └───────────────┬──────────────────────────┘
                                          │
              ┌───────────────────────────┼────────────────────────────┐
              │                 ENGAGEMENTS (natural order)             │
              │                                                        │
              │   --design (greenfield)  OR  --audit (existing) ──┐    │
              │            │      (both produce the plan of record)│   │
              │            ▼                                       │   │
              │       --runbook ◄──────────────────────────────────┘   │
              │            │                                           │
              │       --readiness (per major release, recurring)       │
              └───────────────────────────┬────────────────────────────┘
                                          │
                          ┌───────────────▼──────────────────────────┐
                          │ ARTIFACTS                                │
                          │ docs/enterprise/deployment/<slug>-<date> │
                          │ + INDEX.md entry + review-gate header    │
                          └───────────────┬──────────────────────────┘
                                          │
                          ┌───────────────▼──────────────────────────┐
                          │ HUMAN REVIEW PR                          │
                          │ "docs: deployment <mode> review package" │
                          └───────────────┬──────────────────────────┘
                                          │
                          ┌───────────────▼──────────────────────────┐
                          │ EXECUTION (gated)                        │
                          │ /setup-deploy · /ship · /land-and-deploy │
                          │ /canary · AgentForce deploy-manager      │
                          │ (Company tier — human-enabled, gated)    │
                          └──────────────────────────────────────────┘
```

## Phase 1 — Foundation

Two docs anchor every engagement:

- `docs/enterprise/foundation.md` — company foundation: product, stage, business model,
  geography, constraints (budget, compliance exposure, uptime commitments).
- `docs/enterprise/deployment/foundation.md` — deployment baseline: what runs where
  today, stack and platform, environment inventory, release cadence and blast radius
  (what breaks if a deploy goes bad), team and deploy access, constraints (infra budget
  ceiling, data residency, promised SLAs, cloud credits).

Both carry a dated header and a `Last reviewed: <date>` line. **Refresh rule:** any
foundation doc older than 90 days gets flagged at the start of the next engagement and
offered a refresh. Stack changes, a first paying SLA, or a team-size doubling trigger an
immediate refresh.

## Phase 2 — Engagements

| Mode | When to run it | What it produces | Prerequisite |
|---|---|---|---|
| `--design` | Nothing (or only a prototype) is live; no plan of record | Deployment Plan: stack decision with cost math, environments, branching, promotion gates with named approvers, rollback design, execution wiring | Foundation docs |
| `--audit` | A pipeline exists but no plan of record; quarterly refresh; after a deploy-caused incident | Verified current-state doc, DORA + quality-bar scoring, improvement roadmap, finalized Deployment Plan | A repo to read |
| `--readiness` | Before every **major-class** release (migration, pricing, launch-worthy, claims-changing) | Readiness Report: three-layer gate results with routes, GO / NO-GO verdict | Plan of record (soft — warns and gates against defaults) |
| `--runbook` | Right after the plan exists; after any stack change | Deploy runbook, rollback decision tree, canary/monitoring plan, incident basics | Plan of record (soft) |

Prerequisites are soft: the skill warns and proceeds, never hard-blocks. But the natural
order is real — pipeline work before an agreed plan is the deployment analogue of
channels-before-positioning, and the team will say so.

**Two ways in, one plan out.** Greenfield customers enter through `--design` (the stack
dialog: candidates, cost at launch and 10×, environment topology, branching, gates).
Customers with a working pipeline enter through `--audit` (document it, **verify it with
the customer**, suggest improvements, finalize). Both end in the same Deployment Plan
artifact — the plan of record that `--readiness`, `--runbook`, the human approvers, and
the AgentForce deploy-manager workflow all read.

## Phase 3 — Commit artifacts

All artifacts live under `docs/enterprise/deployment/`:

```
docs/enterprise/deployment/
  foundation.md
  INDEX.md                                  # one line per artifact: date · mode · link · gate
  deployment-plan-2026-07-12.md
  pipeline-audit-2026-07-12.md
  release-readiness-v2-launch-2026-07-12.md
  runbook-2026-07-12.md
  ...
```

The date in each filename and document header is the audit trail. Revisions are new dated
files, never edits — for a deployment plan this matters doubly, because the plan records
who may approve what; its history is a permissions history.

## Phase 4 — Human review & approval

Artifacts are committed on a branch and opened as a PR titled
`docs: deployment <mode> review package`.

**Review-gate legend** (every artifact header declares one):

- **AI-final** — usable as-is once merged: pipeline current-state docs, runbooks,
  monitoring plans.
- **Human review recommended** — needs founder/owner sign-off before use: the Deployment
  Plan (the approval-gate table is a risk-posture decision), readiness reports (the
  GO/NO-GO), anything that grants, moves, or relaxes an approval gate.
- **Licensed professional required** — rare here; SLA/uptime language headed into
  customer contracts routes to `/legal` (attorney before anything is signed).

**Rule:** no production promotion path goes live — and the AgentForce deploy-manager
workflow is never enabled — before the plan's review PR is approved. Merging the PR is
the approval record.

## Phase 5 — Execution (gated)

The plan binds execution to the engineering skills; this team never re-implements them:

| Plan stage | Executed by | Human involvement |
|---|---|---|
| Deploy config persisted | `/setup-deploy` (writes CLAUDE.md) | confirms detection |
| PR creation, tests, changelog | `/ship` | reviews the PR |
| Pre-merge quality gates | `/review`, `/qa`, `/cso` | reads verdicts |
| Merge → deploy → verify | `/land-and-deploy`, or the AgentForce deploy-manager workflow (Company tier) | **the plan's named approver signs off on prod — always, until the plan explicitly relaxes it** |
| Post-deploy watch | `/canary` | watcher named per deploy |
| Release gate (major class) | `/deployment --readiness` | approver reads the report |

The deploy-manager workflow is **off by default** and fail-closed: enabling it is an
explicit Control Tower decision by the repo owner (like auto-merge), and even enabled it
executes only what the plan of record allows, stopping at every blocking gate. Humans
hold: platform accounts, billing, secret values, branch protection, IAM, DNS.

## Operating cadence

- **Per deploy** — post-deploy verification per the runbook; first-N-hours watcher named.
- **Per major release** — `--readiness` before, post-release checkpoints at 24h/7d after.
- **Quarterly** — `--audit` refresh: DORA re-score, break-glass log review, cost model
  re-check against current pricing; feeds the board's quarterly pass.
- **Per incident (Sev 1–2)** — post-mortem in `docs/postmortems/`; deploy-caused incidents
  queue an `--audit` finding.
- **90 days** — foundation doc refresh check (automatic at engagement start).

## FAQ

**Q: We already deploy fine. Why document it?**
Because "fine" lives in one person's head. The `--audit` writes it down, verifies it with
you, and scores it — usually finding one untested rollback and one secrets smell. The plan
of record is also what lets the readiness gate and the deploy-manager workflow act on
your behalf without guessing.

**Q: Can the AI deploy to production?**
Only through the gated path: `/land-and-deploy` run by a human, or the deploy-manager
workflow — which a human enabled, reading a plan a human approved, stopping at every
blocking gate a human defined. The team itself never deploys inline.

**Q: Do I need all four environments?**
Probably not. The plan right-sizes: pre-revenue teams usually get local + PR previews +
prod. Standing environments cost money and drift — each one must pay rent in a named use.

**Q: Who decides the stack?**
You do. The team builds the decision matrix (candidates, real dated costs at launch and
10×, operability, lock-in), makes a recommendation with reasons, and records what was
rejected and why. The pick is a dialog, and it's yours.

**Q: What about ongoing production monitoring?**
This team designs the monitoring plan and the canary checks. Continuous live-site
operation as a service is a separate (Enterprise-tier) team — when it exists, it inherits
this team's runbook and monitoring plan as its starting contract.

**Q: A release is on fire — can we skip the readiness review?**
Hotfix class exists for exactly this: the break-glass path applies, and a retroactive
readiness note is due within 24h. Skipping the gate silently is the one thing the process
can't absorb — the break-glass log is reviewed at the next audit.
