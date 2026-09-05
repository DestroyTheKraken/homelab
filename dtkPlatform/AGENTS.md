# AGENTS — dtkPlatform

**Scope:** `/home/joshua/Projects/HOME_LAB/dtkPlatform` (+ read-only SoT in `HOME_LAB/docs`, `HOME_LAB/hickMedia` templates, `AIDE/aideArchives/SovereignAid`).

**Projects rules:** [`../../README.md`](../../README.md) · [`../../DESIGN.md`](../../DESIGN.md) · [`../../REPOS.md`](../../REPOS.md).

## Do

- Follow [`PLAN.md`](./PLAN.md) multiphase order (0 → 5). Prefer GUI for non-LFCS work.
- Cross-link leaf remotes correctly (`homelab` vs `HickMedia` vs `aide-os` vs `dtk`) — see `REPOS.md`.
- Keep phase evidence/notes here if useful; keep redaction rules from `HOME_LAB/docs/00-redaction-policy.md`.

## Do not

- Invent Homelab-wide **start / stop / review** procedures or a daily ops methodology — the operator has not designed that yet.
- Put platform runbooks under `DTK/` (public `site/` only).
- Mix LFCS `aide-day` curriculum into this folder’s project plan.
- Install k3s on LabNet nodes for family services.
- `git add` nested `hickMedia/` or `installers/` from the parent `HOME_LAB` repo.
