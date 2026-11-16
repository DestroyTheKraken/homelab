# Homelab

Redacted LabNet spec sheets: **VyOS** edge, **Proxmox VE** on `node1`–`node3`, DestroyTheKraken tailnet for portfolio remote access.

**Projects layout:** [`../README.md`](../README.md) (naming/ownership) · [`../DESIGN.md`](../DESIGN.md) (migration decisions) · [`AGENTS.md`](./AGENTS.md).  
This bucket owns premises infra and the **DTK family platform daily workspace** (`dtkPlatform/`). The HickMedia appliance is closed. Its files are in `../Batocera/history-20261025-011510.tar.gz`. There is no `hickMedia/` folder here.
**What this is not:** a Kubernetes / HA private-cloud résumé. It is a working premises network plus dated, redacted notes.

**Job search:** joshua.hickman1@gmail.com · **Lab identity (Tailscale):** destroythekraken@gmail.com · **GitHub:** [DestroyTheKraken](https://github.com/DestroyTheKraken)

## Who this is for

MSP and internal-IT hiring managers. I want to work **on a team**. This lab is how I practice the job I am applying for.

**Read in order:** [docs/00-redaction-policy.md](docs/00-redaction-policy.md) first, then `01` → `06`.

## What I actually run and practice

I designed and deployed the premises edge: Starlink, a **VyOS** router (ThinkCentre Tiny + USB Ethernet adapters), and a lab switch. LabNet is the network this portfolio documents. I image Linux servers, use Multipass for disposable labs, live in the CLI, and use default-deny firewall habits.

I use **Grok Build** and **Claude Code** to research, draft, and configure **while I learn**. I type the commands, test the result, and write the notes. That is also how I would stand up a more complex stack (for example Kubernetes) if a job required it — not because a k3s cluster is what this lab is today.

## Lab at a glance

| Piece | What it is |
|-------|------------|
| WAN | Starlink (CGNAT — no inbound port-forwards) |
| Edge | VyOS rolling on a ThinkCentre M93p Tiny |
| Lab LAN | `192.168.20.0/24` wired — control seat + three workers |
| Isolation | LabNet is the documented segment. The other inside LAN is not inventoried here. |
| Control seat | `um690` — Minisforum UM690, Ryzen 9 6900HX, 64 GiB, Ubuntu 26.04.1. Not a Proxmox target. |
| Fleet | Cluster `dtk-cloud`: n1–n3, Proxmox VE 9.2.26, quorate, 0 guests. Prometheus and Grafana are not installed. |
| Remote access | DestroyTheKraken tailnet. `um690` plus n1–n3 as `tag:ops`. |

## Tailnet

| Tailnet | Login | What this repo lists |
|---------|-------|----------------------|
| DestroyTheKraken | destroythekraken@gmail.com | `um690`, `n1`, `n2`, `n3` |

**Membership (2026-11-15):** those four lab hosts are online. n1–n3 are `tag:ops`. Details in [docs/04-tailscale.md](docs/04-tailscale.md). Other devices on that tailnet are omitted.

## Platform daily workspace

| Path | Role |
|------|------|
| [dtkPlatform/](./dtkPlatform/) | Sessions, Portainer/Tailscale guides, active Compose, Phase checklist (Grok Build cwd) |

## Spec sheets

| Doc | Contents |
|-----|----------|
| [docs/00-redaction-policy.md](docs/00-redaction-policy.md) | What never goes in this repo |
| [docs/01-overview.md](docs/01-overview.md) | Purpose and contact |
| [docs/02-network.md](docs/02-network.md) | Edge, segments, isolation |
| [docs/03-compute.md](docs/03-compute.md) | Hosts and PC deployments |
| [docs/04-tailscale.md](docs/04-tailscale.md) | DTK tailnet, lab hosts only |
| [docs/05-inventory-observed-2026-11-15.md](docs/05-inventory-observed-2026-11-15.md) | Current snapshot: cluster `dtk-cloud`, LabNet SSH, `tag:ops` |
| [docs/05-inventory-observed-2026-11-09.md](docs/05-inventory-observed-2026-11-09.md) | Prior snapshot (Ubuntu workers) |
| [docs/05-inventory-observed-2026-08-29.md](docs/05-inventory-observed-2026-08-29.md) | Prior snapshot |
| [docs/05-inventory-observed-2026-08-24.md](docs/05-inventory-observed-2026-08-24.md) | Prior snapshot |
| [docs/06-vyos-build.md](docs/06-vyos-build.md) | How the router was built |
| [diagrams/network.txt](diagrams/network.txt) | ASCII topology |

## Related repos

| Repo | Role |
|------|------|
| [aide-os](https://github.com/DestroyTheKraken/aide-os) | Current lab / study platform |
| [SovereignAid](https://github.com/DestroyTheKraken/SovereignAid) | Historical predecessor of aide-os |
| [nc-lin-cs](https://github.com/DestroyTheKraken/nc-lin-cs) | Nextcloud hub installer |
| [ssh-ufw-ts-install](https://github.com/DestroyTheKraken/ssh-ufw-ts-install) | SSH / UFW / Tailscale bootstrap |
| [dtk](https://github.com/DestroyTheKraken/dtk) | Archived mock-business / AI-tooling experiment |

## Honesty note

These pages are **observed**. Proxmox is listed because the web UI answered on node1–node3 on 2026-11-15. k3s and Ceph are not listed. AI-assisted setup is how I learn; I still operate the box.

## Redaction

No WAN IPs, Tailscale addresses, MACs, keys, phone numbers, or household given names. See the [redaction policy](docs/00-redaction-policy.md).
