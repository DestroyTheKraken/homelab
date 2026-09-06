# AGENTS — dtkPlatform

**Scope:** `/home/joshua/Projects/HOME_LAB/dtkPlatform` (+ read-only SoT in `HOME_LAB/docs`, `HOME_LAB/hickMedia` templates, `AIDE/aideArchives/SovereignAid`).

**Projects rules:** [`../../README.md`](../../README.md) · [`../../DESIGN.md`](../../DESIGN.md) · [`../../REPOS.md`](../../REPOS.md).

## Separation (mandatory)

This folder is the **HomeLab / DTK platform being built**.  
The **AIDE_OS UI** (tickets, daily guides, lesson management) is a **separate MVP** under `Projects/AIDE/` — built with Grok Build, then *used* while you execute phases here.

Canon: [`../../AIDE/WORKFLOW-SEPARATION.md`](../../AIDE/WORKFLOW-SEPARATION.md).

## Do

- Follow [`PLAN.md`](./PLAN.md) multiphase order (0 → 5). Prefer GUI for non-LFCS work.
- Cross-link leaf remotes correctly (`homelab` vs `HickMedia` vs `aide-os` vs `dtk`) — see `REPOS.md`.
- Document the build with Grok Build–assisted GitOps-lite (commits on the right leaf) when the operator asks.
- Keep phase evidence/notes here if useful; keep redaction rules from `HOME_LAB/docs/00-redaction-policy.md`.

## Do not

- Build or embed AIDE_OS Student/ticket UI inside this platform tree.
- Invent Homelab-wide **start / stop / review** procedures here unless the operator opens that design.
- Put platform runbooks under `DTK/` (public `site/` only).
- Replace `PLAN.md` phases with LFCS curriculum — link out to AIDE for lessons.
- Install k3s on LabNet nodes for family services.
- `git add` nested `hickMedia/` or `installers/` from the parent `HOME_LAB` repo.
