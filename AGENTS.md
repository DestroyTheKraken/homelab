# AGENTS — HOME_LAB bucket

- **Bucket:** `/home/joshua/Projects/HOME_LAB`
- **Projects rules:** [`../README.md`](../README.md), [`../DESIGN.md`](../DESIGN.md)

## Ownership

| Path | Role |
|------|------|
| `docs/`, `diagrams/` | Redacted premises network / Tailscale inventory (public-safe) |
| `hickMedia/` | Living-room / media appliance lab tree (canonical) |
| `installers/` | Lab installers (nc-lin-cs, ssh-ufw-ts, …) |
| **`dtkPlatform/`** | Daily Platform Agent workspace: sessions, GUI guides, active Compose, family-platform checklist |

## Do

- Put new **family platform / LabNet service** session work under `dtkPlatform/`.
- Put new appliance experiments under `hickMedia/` (or link from `dtkPlatform/Compose`).
- Keep redaction rules in `docs/00-redaction-policy.md`.
- Cross-link to `AIDE/` for LFCS study — do not fork curricula here.

## Do not

- Put public website pages here (those belong in `DTK/site/` only).
- Put LFCS lesson product work here (those belong in `AIDE/`).
- Claim k3s/Ceph/Proxmox as current production in inventory docs unless observed.
- Duplicate HickMedia trees under DTK.
