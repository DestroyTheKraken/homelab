# AGENTS — HOME_LAB bucket

- **Bucket:** `/home/joshua/Projects/HOME_LAB`
- **Projects rules:** [`../README.md`](../README.md), [`../DESIGN.md`](../DESIGN.md)

## Ownership

| Path | Role |
|------|------|
| `docs/`, `diagrams/` | Redacted premises network / Tailscale inventory (public-safe) |
| `hickMedia/` | Removed. The closed tree is the archive `../Batocera/history-20261025-011510.tar.gz`. Do not unpack it here or start new HickMedia work. |
| `installers/` | Lab installers (nc-lin-cs, ssh-ufw-ts, …) |
| **`dtkPlatform/`** | HomeLab / DTK **platform build** (phases, Compose, guides). Not the AIDE_OS lesson UI. |

## Do

- Put new **family platform / LabNet service** session work under `dtkPlatform/`.
- Do not add appliance experiments under `hickMedia/`. That product is closed. The console work is `../Batocera`.
- Keep redaction rules in `docs/00-redaction-policy.md`.
- Document **LabNet** and the **DestroyTheKraken** tailnet only. Leave phones, tablets, laptops, and HickmaNet out of this bucket.
- Proxmox VE on `node1`–`node3` was observed on 2026-11-15 (web UI). `um690` and `vyos-router` are not Proxmox hosts. Do not claim k3s or Ceph unless observed.
- Cross-link to `AIDE/` for LFCS study — do not fork curricula here.

## Separation

HomeLab services ≠ AIDE_OS content delivery UI. See [`../AIDE/WORKFLOW-SEPARATION.md`](../AIDE/WORKFLOW-SEPARATION.md).

## Do not

- Put public website pages here (those belong in `DTK/site/` only).
- Put LFCS lesson product / Student ticket UI here (those belong in `AIDE/`).
- Claim k3s/Ceph/Proxmox as current production in inventory docs unless observed.
- Duplicate HickMedia trees under DTK.
