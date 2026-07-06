# Knowledge Playbook — KCS v6, KB architecture, article template, content gaps

Reference templates for `/customer-success --knowledge` (and theme coding for `--voc`). The knowledge program's economic claim: ticket-per-customer declines as link rate and self-service success rise. If those curves aren't moving, the program is shelf-ware.

## 1. The KCS v6 operating loop (Knowledge-Centered Service)

**Solve loop** (every ticket, every agent):

1. **Capture** — write the knowledge in the moment of solving, in the customer's words. Knowledge reconstructed later is wrong: the symptom phrasing, the environment details, and the actual fix all drift within hours.
2. **Structure** — pour it into the consistent template below (Issue / Environment / Cause / Resolution). Structure is what makes 500 articles searchable instead of a swamp.
3. **Reuse** — search the KB *before* solving every ticket. If an article exists, use it and **link it to the ticket** (link rate is the program's pulse). If it half-exists, improve it.
4. **Improve** — **UFFA: Use it, Flag it, Fix it, Add it.** Every agent who touches an article either uses it as-is, flags it as wrong/stale, fixes it on the spot, or adds the missing article. Nobody walks past a broken article.

**Evolve loop** (double-loop, monthly/quarterly): content health audits (stale, low-rated, unused articles → fix or retire), KB architecture review (do categories still match how customers search?), leadership metrics review.

**The quality bar is deliberate:** articles must be *sufficient to solve*, not polished prose. Speed of capture beats editorial perfection; **demand (reuse) determines what gets polished.** An article read 200×/month earns an editing pass; an article read twice a year earns nothing.

**KCS adoption order for startups:** capture discipline BEFORE hiring more agents. Hero-based support (one engineer knows everything, zero KB, bus-factor 1) is the failure mode; every hero-solved ticket that doesn't produce an article deepens it.

## 2. KB architecture

- **Categories** map to the ticket-driver taxonomy (from `--support` or Phase 2), not to your org chart or code modules. Customers search by symptom, not by microservice.
- **Article types**: how-to · troubleshooting · FAQ · known issue · release note.
- **Lifecycle states**: draft → published → flagged → retired. Every article carries `last-verified` metadata; anything unverified >6 months gets auto-flagged.
- **Audience split**: customer-facing content and internal-only notes live in the SAME article, clearly separated (see template) — never fork into two articles that drift apart.
- **Ownership**: every category has one owner (at a startup: the same human, named anyway).

## 3. KB article template (KCS)

```markdown
# <Title: the user's question or symptom, in customer language>
<!-- "Exports fail with 'timeout' on large workspaces" — NOT "Export service timeout handling" -->

**Type:** how-to | troubleshooting | FAQ | known issue | release note
**Audience:** customer | internal
**Lifecycle:** draft | published | flagged | retired
**Owner:** <name> · **Last verified:** <YYYY-MM-DD>

## Issue / Symptom
<What the user sees, in their words. Include the exact error text — that's what they paste into search.>

## Environment
<Product version, plan tier, platform/browser/OS, relevant configuration.>

## Cause
<Why it happens. One paragraph. "Unknown — under investigation" is honest and allowed for known issues.>

## Resolution
1. <Numbered steps. Each step one action. Include expected result of the final step.>

## Workaround
<If the resolution requires a fix that hasn't shipped. Delete this section otherwise.>

## Related articles
- <links>

---
## Internal-only notes
<Escalation path, account-specific context, links to the bug ticket. Never shown to customers.>
```

Seeding rule (for `--knowledge` step 4): seed articles describe only behavior evidenced in the repo's README/docs/code. Where actual behavior is unverifiable, write `[VERIFY: <what to check and where>]` — a wrong KB article is worse than no article, because it burns trust in the whole KB.

## 4. Content gap analysis method

1. **Build the driver list**: top 20 ticket drivers by volume (from helpdesk tags, or `gh issue list` labels, or the Phase 2 gut-feel list — state which source, and its reliability).
2. **For each driver, test findability like a customer would**: search the KB with the customer's phrasing (the words from real tickets, not internal jargon). Three outcomes: findable + current / exists but stale or unfindable / missing.
3. **The gap list is the writing queue**, ordered by ticket volume × searchability failure. Missing articles for high-volume drivers first; stale fixes second; nice-to-haves never (demand decides).
4. **Zero-result searches** are the other input: review weekly, feed the queue. A zero-result search is a customer telling you exactly what to write, in exactly the words to title it.
5. Re-run the analysis monthly. The gap list should shrink; if it doesn't, capture (KCS step 1) is broken — coach that, don't just write more articles centrally.

## 5. Knowledge metrics (each with its attached play)

| Metric | Definition | Target | Attached play when off-target |
|--------|-----------|--------|-------------------------------|
| Link rate | % of solved tickets linked to a KB article | >60% once KCS is running | Capture coaching; check if search is failing agents |
| Participation rate | % of agents who created/edited an article this month | 100% (everyone touches knowledge) | UFFA re-training; check if tooling adds friction |
| Articles per solved case | New articles / tickets with no matching article | ~1.0 for true gaps | If <1: knowledge leaking; if >1: duplicates — merge |
| Self-service success | KB/L0 sessions with **no repeat contact within 7 days** | 30–70% by product complexity | Rewrite top failing articles; trim bot scope |
| Zero-result search rate | Searches returning nothing / all searches | Declining trend | Weekly review → writing queue |
| Ticket-per-customer | Monthly tickets ÷ active customers | Declining as KB matures | If flat while link rate rises: articles solve agents' problem, not customers' — check findability |

Success metric discipline: self-service **success**, never deflection count. "The bot answered" is not an outcome; "the user succeeded and didn't come back about it" is.

## 6. Theme coding taxonomy (shared with `--voc`)

Code every ticket/verbatim/issue into exactly one primary theme:

| Theme | Definition | Downstream owner |
|-------|-----------|------------------|
| Bug | Product behaves contrary to spec/docs | Engineering (escalation packet) |
| Friction | Works as designed but users struggle | Product/UX |
| Feature gap | Capability doesn't exist | Product (VoC report, revenue-weighted) |
| Docs gap | Capability exists, users can't find/understand it | Knowledge (writing queue) |
| Pricing | Cost, packaging, billing mechanics | Founder/finance |
| Performance | Slow, timeouts, scale limits | Engineering |

Secondary tags allowed; primary theme drives routing. Record the account and ARR when identifiable — revenue weighting depends on it.
