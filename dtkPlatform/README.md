# dtkPlatform

Phased **DestroyTheKraken** private platform on LabNet. Proxmox VE is installed on node1–node3. See [`PREP-proxmox.md`](./PREP-proxmox.md). The service plan is [`PLAN.md`](./PLAN.md).

**Bucket:** `HOME_LAB`. Layout rules: [`../../README.md`](../../README.md). Remotes map: [`../../REPOS.md`](../../REPOS.md).

**Separation:** This is the **platform you install**. The **AIDE_OS UI** you use to get daily guides/lessons while installing is a different MVP under `Projects/AIDE/`. See [`../../AIDE/WORKFLOW-SEPARATION.md`](../../AIDE/WORKFLOW-SEPARATION.md).

## Read first

| Doc | What it is |
|-----|------------|
| [`PLAN.md`](./PLAN.md) | MVP roles and end state. |
| [`phases/`](./phases/README.md) | One directory per session, 00 through 11. |
| [`checklist.md`](./checklist.md) | Living phase checkboxes |
| [`PREP-proxmox.md`](./PREP-proxmox.md) | Cluster is up. Monitoring guests are not. |
| [`AGENTS.md`](./AGENTS.md) | Scope rules for agents working in this folder |

## Not designed in *this* tree (on purpose)

- AIDE_OS content delivery / lesson management UI → build under **AIDE** with Grok Build  
- Homelab-wide start / stop / review procedures → separate design later  

## Layout

```text
dtkPlatform/
├── PLAN.md           # MVP roles and end state
├── phases/           # session directories 00–11
├── PREP-proxmox.md   # cluster dtk-cloud is up; monitoring guests are not
├── checklist.md
├── Compose/          # stack files for the current MVP
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
| HickMedia | Closed. Archive is `../Batocera/history-20261025-011510.tar.gz`. Do not unpack it here. |
| [`../installers/`](../installers/) | nc-lin-cs, ssh-ufw-ts → own remotes |
| `AIDE/aideTutor` | LFCS outline (study lane) |
