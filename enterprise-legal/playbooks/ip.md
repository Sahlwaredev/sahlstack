# IP Playbook — chain of title, OSS licenses, trademark clearance

Reference for `/legal --ip`. Three audits, each producing its own artifact.

## 1. Chain-of-title audit

The question: **does the company actually own everything in the product?** Founders'
pre-formation work, contractors, employees, and AI-generated content are the four leak paths.
A broken chain is the killer finding in financing and acquisition diligence.

### Procedure

1. **Enumerate contributors** from reality, not memory:
   ```bash
   git shortlog -sne --all
   git log --format='%an <%ae>' --all | sort -u
   ```
   Run across every repo that ships product code. Add non-code contributors the user
   identifies: designers, logo/brand creators, copywriters, ML-data labelers.
2. **Classify each contributor:** founder / employee / contractor / open-source drive-by /
   unknown. Note first-commit date vs incorporation date and vs hire date.
3. **Match to signed agreements.** Required paper per class:
   - **Employees:** PIIA signed at hire, dated **before day one** of work.
   - **Contractors:** agreement with work-made-for-hire designation PLUS present-tense
     assignment backup (WFH alone fails for most software — software rarely fits the nine
     statutory WFH categories).
   - **Founders:** pre-incorporation IP assigned in the stock purchase agreement (or a
     standalone technology assignment agreement).
   - **Drive-by OSS contributors:** inbound license via the repo's LICENSE, or CLA/DCO.
4. **Verbatim language test.** Open each agreement and verify the operative words:
   **"hereby assigns"** (present tense, self-executing). "Agrees to assign" is a promise,
   not a transfer — the Stanford v. Roche trap — and is a gap even with a signature on file.
5. **AI-generated code provenance.** Note the company's policy (or absence) on AI codegen:
   tool, terms governing output ownership, and whether any dependency-scale code was
   generated under terms the company hasn't reviewed.

### Output — gap matrix

| Contributor | Class | First commit | Agreement on file? | "Hereby assigns"? | Gap | Cure |
|---|---|---|---|---|---|---|

**Cure = confirmatory assignment:** a short agreement in which the contributor confirms and
presently assigns all right, title, and interest in the identified contributions, with
consideration recited (nominal payment or continued engagement). Draft one per gap, name the
specific work. Unlocatable or hostile ex-contributors → escalate to human counsel.

## 2. Open-source license compliance

### Policy (default — adopt or adjust via foundation)

| Tier | Licenses | Rule |
|---|---|---|
| Allowlist | MIT, BSD-2/3, Apache-2.0, ISC | Use freely; preserve notices |
| Review | LGPL, MPL-2.0, EPL | Allowed with dynamic linking / file-level isolation; counsel review for static linking or modification |
| Prohibited without approval | GPL-2.0/3.0, AGPL-3.0, SSPL, custom "source-available" | GPL: viral on distribution. **AGPL: viral on network use — the SaaS killer.** Any hit = Critical finding |
| Unknown/none | Unlicensed code, "TODO: license" | Treat as all-rights-reserved: prohibited |

### Scan the actual dependency tree — never guess

Detect the ecosystem, then run the real scan:

```bash
# Node
npx license-checker --summary && npx license-checker --csv --out licenses.csv
# Python
pip-licenses --format=markdown --with-urls
# Rust
cargo license
# Go
go-licenses report ./...
```

If tooling is unavailable, fall back to reading lockfiles + each package's declared license
field, and say so in the report. Include transitive dependencies — direct-only scans miss
most copyleft. For vendored/copied code (files with foreign headers), Grep for
`SPDX-License-Identifier`, `GNU`, `AGPL`, `GPL` across the source tree.

### Output — OSS inventory report

1. Summary counts by license tier.
2. Violations table: package, version, license, tier, where used, remediation
   (**replace** with an allowlist alternative / **isolate** behind a network boundary or
   separate process / **seek approval + comply** with obligations). AGPL anywhere in a SaaS
   product = Critical, remediate before next release.
3. NOTICE file draft — attribution for licenses that require it (Apache-2.0 NOTICE
   pass-through, BSD/MIT copyright lines).
4. Inbound-contribution policy recommendation: DCO (lightweight, sign-off trailer) for most
   startups; CLA if relicensing flexibility matters.
5. AI-codegen provenance note: policy for AI-generated code entering the tree.

## 3. Trademark clearance

### Search protocol (WebSearch — do the research, then rate the risk)

1. **USPTO** — search the exact mark and close variants (sound-alikes, spelling variants,
   translations) in Classes 9 (downloadable software) and 42 (SaaS). Note live
   registrations and pending applications, their goods/services, and status.
2. **Common law** — general web search for the mark + product category; competitors using
   the name unregistered still have priority rights in their territory.
3. **Domains and app stores** — exact and close-variant .com/.io/.ai availability; App
   Store/Google Play listings under the name.
4. **Company registries** — obvious same-name software companies.

### Risk analysis — likelihood of confusion factors (DuPont / Sleekcraft)

Weigh: similarity of the marks (sight/sound/meaning); relatedness of goods/services;
strength of the senior mark (fanciful > arbitrary > suggestive > descriptive — a descriptive
mark is also hard to register at all); marketing channels overlap; buyer sophistication;
evidence of actual confusion; the senior user's likelihood of expansion.

### Output — clearance memo

```
MARK: <name>  ·  CLASSES: 9, 42  ·  AS OF: <date>
VERDICT: CLEARABLE / RISKY (proceed with named mitigations) / BLOCKED (rebrand before traction)
CONFLICTS FOUND: <each: mark, owner, reg/app number or common-law cite, goods, why it does or doesn't matter>
STRENGTH: <fanciful/arbitrary/suggestive/descriptive — registrability note>
RECOMMENDATION: <file intent-to-use now | file use-based | rebrand | search deeper with counsel>
```

### Filing strategy (drafted; filing itself is human/counsel-executed)

- File **intent-to-use** (1(b)) before launch or **use-based** (1(a)) after; Classes 9 + 42
  core, add others only with real use planned.
- Specimens: screenshots showing the mark used with the software/service.
- Maintenance calendar: office-action responses (tight statutory windows); Section 8 & 15
  declarations at years 5–6; renewal at year 10. Madrid Protocol for international once the
  US base is filed.
- Note: responding to substantive office actions and any opposition/dispute = licensed
  attorney work. Patent questions (patentability, provisionals, prosecution) = registered
  patent attorney/agent only; this team drafts landscape notes, never applications.
