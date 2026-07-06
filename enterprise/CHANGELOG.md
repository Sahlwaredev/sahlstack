# sahlstack Fork Changelog

Fork-only releases of [Sahlwaredev/sahlstack](https://github.com/Sahlwaredev/sahlstack)
(Sahlware's fork of gstack). Fork releases bump the **4th version digit** on top of the
current upstream base (`<upstream X.Y.Z>.<fork build>`), so upstream's own
`X.Y.Z.0` releases never collide. Upstream changes stay in the root `CHANGELOG.md`;
fork changes are logged here to keep upstream merges clean.

## v1.58.5.1 — 2026-07-06

- **Fork identity:** version checks and upgrades now track `Sahlwaredev/sahlstack`
  instead of upstream gstack — `bin/gstack-update-check` (remote VERSION + SHA URLs),
  `/gstack-upgrade` (fresh-clone URL), and `bin/gstack-team-init` (team onboarding
  clone instructions). Without this, an auto-upgrade would have replaced a sahlstack
  install with upstream gstack and dropped the enterprise skills.
- **AgentForce enterprise team suite** (first shipped in `5b766d4`, on the v1.58.5.0
  base): nine business-team skills (`/strategy`, `/marketing`, `/sales`, `/legal`,
  `/compliance`, `/finance`, `/people`, `/customer-success`, `/bizops`), the
  `/exec-review` board pass, the `/enterprise` front door, `/enterprise-autoplan`,
  per-team process docs, and the company-level `enterprise/PROCESS.md`.
