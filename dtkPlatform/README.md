# dtkPlatform

Phased **DestroyTheKraken family home platform** work on LabNet (Tailscale Free · Docker/Portainer · one service at a time).

**Bucket:** `HOME_LAB`. Layout rules: [`../../README.md`](../../README.md). Remotes map: [`../../REPOS.md`](../../REPOS.md).

**Separation:** This is the **platform you install**. The **AIDE_OS UI** you use to get daily guides/lessons while installing is a different MVP under `Projects/AIDE/`. See [`../../AIDE/WORKFLOW-SEPARATION.md`](../../AIDE/WORKFLOW-SEPARATION.md).

## Read first

| Doc | What it is |
|-----|------------|
| [`PLAN.md`](./PLAN.md) | **Multiphase project only** (Phases 0–5). Not AIDE UI. Not daily ops methodology. |
| [`checklist.md`](./checklist.md) | Living phase checkboxes |
| [`AGENTS.md`](./AGENTS.md) | Scope rules for agents working in this folder |

## Not designed in *this* tree (on purpose)

- AIDE_OS content delivery / lesson management UI → build under **AIDE** with Grok Build  
- Homelab-wide start / stop / review procedures → separate design later  

## Layout

```text
dtkPlatform/
├── PLAN.md           # multiphase install plan
├── checklist.md
├── Compose/          # active stack files (origin: hickMedia templates)
├── Guides/           # optional click-path aids for a phase
├── Sessions/         # optional dated notes (not an ops system)
├── Progress/         # optional current-phase pointer
├── Prompts/          # optional; not required by PLAN.md
└── Refs/             # pointers (LFS207, official docs)
```

## Related (cross-link)

| Path | Role |
|------|------|
| [`../docs/`](../docs/) | Redacted network SoT → remote `homelab` |
| [`../hickMedia/`](../hickMedia/) | Appliance/lab tree → remote `HickMedia` |
| [`../installers/`](../installers/) | nc-lin-cs, ssh-ufw-ts → own remotes |
| `AIDE/aideTutor` | LFCS outline (study lane) |
