# AGENTS — dtkPlatform

**Scope:** `/home/joshua/Projects/HOME_LAB/dtkPlatform` (+ read-only SoT in `HOME_LAB/docs`, `AIDE/aideArchives/SovereignAid`). LabNet and the DestroyTheKraken tailnet only.

**Projects rules:** [`../../README.md`](../../README.md) · [`../../DESIGN.md`](../../DESIGN.md) · [`../../REPOS.md`](../../REPOS.md).

## Separation (mandatory)

This folder is the **HomeLab / DTK platform being built**.  
The **AIDE_OS UI** (tickets, daily guides, lesson management) is a **separate MVP** under `Projects/AIDE/` — built with Grok Build, then *used* while you execute phases here.

Canon: [`../../AIDE/WORKFLOW-SEPARATION.md`](../../AIDE/WORKFLOW-SEPARATION.md).

## Do

- Treat Proxmox VE on node1–node3 as installed. The 2026-11-15 inventory observed the web UI. Follow [`PLAN.md`](./PLAN.md) for services, and do not describe those nodes as Ubuntu.
- Cross-link leaf remotes correctly (`homelab` vs `HickMedia` vs `aide-os` vs `dtk`) — see `REPOS.md`.
- Document the build with Grok Build–assisted GitOps-lite (commits on the right leaf) when the operator asks.
- Keep phase evidence/notes here if useful; keep redaction rules from `HOME_LAB/docs/00-redaction-policy.md`.

## Do not

- Build or embed AIDE_OS Student/ticket UI inside this platform tree.
- Invent Homelab-wide **start / stop / review** procedures here unless the operator opens that design.
- Put platform runbooks under `DTK/` (public `site/` only).
- Replace `PLAN.md` phases with LFCS curriculum — link out to AIDE for lessons.
- Install k3s on LabNet nodes for portfolio services.
- Claim the nodes are still Ubuntu, or that Proxmox is not installed.
- Install or document the historical media server. Kodi is the only movie database.
- Reinstall or wipe node1–node3. Proxmox is already there.
- Document phones, tablets, laptops, or HickmaNet in this tree.
- `git add` nested `hickMedia/` or `installers/` from the parent `HOME_LAB` repo.

## Phase sessions

Each directory under `phases/` has its own `AGENTS.md`. Grok loads rules from the directory where the session starts, so a session must be started inside the phase.

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/02-open-webui
grok
```

Joshua says: Begin this phase

That file tells Grok to read the plan, the checklist, and this phase, then give one guided step. Joshua runs host commands. Grok writes files in this tree. The next phase is a new session.
