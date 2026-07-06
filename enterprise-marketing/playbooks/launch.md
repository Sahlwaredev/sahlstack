# Playbook: Tiered Launches

Templates for `/marketing --launch`. Tier discipline is the point of this playbook:
over-launching Tier 3s at Tier 1 volume dilutes real launches and trains the audience to
tune out. Enforce it.

---

## 1. The tier system

| Tier | What qualifies | Prep time | Channels | Example |
|---|---|---|---|---|
| **1** | New product, new market entry, major platform or pricing change | 4–6 weeks minimum | Full orchestration: press/analyst pre-brief, exec/founder social, webinar or event, paid support, website update, sales training, customer comms, blog, email, in-app | v2.0, enterprise tier, new product line |
| **2** | Significant feature with clear buyer value | 1–2 weeks | Blog post, email, in-app, sales enablement, social. No press. | SSO, a major integration, a workflow buyers asked for |
| **3** | Incremental improvement | Days | Release notes + in-app messaging only | UI polish, small options, fixes |

**Tier assignment rules:**
- The tier is justified in writing in the brief. "The founder is excited" is not a rationale.
- Budget: most quarters support at most one Tier 1. If the last three launches were Tier 1,
  the next one almost certainly is not.
- Downgrade by default: when in doubt between tiers, pick the lower one and over-deliver.
- Batching: several Tier 3s can roll up into one Tier 2 "what's new" moment monthly/quarterly.

## 2. The three phases

```
PRE-LAUNCH                          LAUNCH WEEK                POST-LAUNCH
positioning of the feature         coordinated execution      30/60/90 measurement
assets drafted & approved          per checklist              adoption, pipeline influence,
sales/CS trained 2–3 wks early                                message resonance
(T1: press/analyst pre-brief)                                 retro
```

---

## 3. Launch Brief template

```markdown
# Launch Brief — <feature/product> · Tier <1|2|3>
> Ship date: <date> · Launch date: <date> (they need not be the same)

## What's shipping
<2–3 sentences, plain language>

## Tier + rationale
Tier <n> because <maps to the tier table above>. Launches this quarter so far: <list w/ tiers>.

## Target audience
Primary: <segment/persona>. Secondary: <...>. Explicitly NOT for: <...>.

## Positioning of the feature
- Alternative it displaces: <what buyers do today instead — incl. "nothing">
- Key message: <one sentence, buyer language, passes swap test>
- Proof: <metric / quote / demo moment>
- Mini positioning block unvalidated? <yes/no — yes if no signed-off canvas exists>

## Success metrics (pre-registered — set BEFORE launch, never backfilled)
| Metric | Target | Measured how | Checkpoint |
|---|---|---|---|
| Adoption | | | 30d |
| Pipeline influence | | | 60d |
| Message resonance (replies, demo requests citing it) | | | 30d |

## Owners & timeline
| Workstream | Owner | Due |
|---|---|---|

## Risk notes
<if the change is risky (pricing, breaking change): rollback plan + customer FAQ required>
```

---

## 4. Three-layer launch checklist

Scope to tier: Tier 1 = all layers, all items. Tier 2 = all layers, trimmed. Tier 3 = the
starred items only.

### Layer 1 — Readiness (assets exist and are approved)
- [ ] ★ Release notes / changelog entry
- [ ] ★ In-app message copy
- [ ] Announcement blog post (with named author)
- [ ] Email to relevant segment(s)
- [ ] Social posts per platform (founder + company variants)
- [ ] Website/pricing page updates drafted (before/after)
- [ ] Demo assets / screenshots / video script
- [ ] (T1) Press release + media list, analyst pre-brief deck, webinar plan

### Layer 2 — Narrative (the story holds up)
- [ ] Key message approved by founder; passes swap test and banned-superlatives check
- [ ] FAQ written — including the hostile questions (pricing, migration, "how is this
      different from <competitor>")
- [ ] Competitive angle: how competitors will respond, and our counter
- [ ] Spokespeople briefed (who says what, where)

### Layer 3 — Revenue path (the launch converts)
- [ ] Sales/CS trained ≥2 weeks before customers hear (T1–2 hard requirement)
- [ ] Enablement one-pager + objection angles delivered to `/sales`
- [ ] Lead routing configured; who follows up on launch-driven interest, within what SLA
- [ ] Pricing/packaging updated everywhere it appears (site, proposals, billing)
- [ ] ★ Tracking in place: UTM-tagged links, events for the success metrics, dashboard/query
      to read them
- [ ] Support ready: docs updated, known-issues list, escalation path

### Post-launch
- [ ] 30/60/90-day metric checkpoints on the calendar, against the pre-registered targets
- [ ] Retro at 30d: what worked, what didn't, tier verdict in hindsight, template updates

---

## 5. Asset drafting standards

- Every asset uses the messaging house lines — no ad-hoc rephrasing of the key message.
- Blog post: information gain required (the "why we built this" a competitor couldn't write);
  named author; GEO basics applied (clear definition of the feature up top, FAQ block,
  schema-worthy structure).
- Email: subject ≤6 words tested against 2 variants; body leads with the buyer outcome, not
  the feature name.
- Social: per-platform native drafts (not one blast); founder-voice variant separate from
  company-voice variant.
- In-app: one sentence + one CTA; targets only the segment the feature serves.
- Everything carries `[PROOF NEEDED]` markers where evidence is missing — never invent
  numbers or customer quotes.
