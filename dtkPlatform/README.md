# dtkPlatform

Phased **DestroyTheKraken family home platform** work on LabNet (Tailscale Free · Docker/Portainer · one service at a time).

**Bucket:** `HOME_LAB`. Layout rules: [`../../README.md`](../../README.md). Remotes map: [`../../REPOS.md`](../../REPOS.md).

## Read first

| Doc | What it is |
|-----|------------|
| [`PLAN.md`](./PLAN.md) | **Multiphase project only** (Phases 0–5). Not daily ops. |
| [`checklist.md`](./checklist.md) | Living phase checkboxes |
| [`AGENTS.md`](./AGENTS.md) | Scope rules for agents working in this folder |

## Not designed yet (on purpose)

Homelab-wide **start / stop / review** procedures and any daily session coach after the phased build completes are **out of scope**. Do not invent them here. Design that in a separate pass when you want it.

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
