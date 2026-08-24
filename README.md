# Homelab

Public, redacted spec sheets for the premises network I administer in Omak, WA.

This is the portfolio artifact for **Linux systems administration, networking, and IT operations**. There is no separate marketing site. `destroythekraken.com` is retired.

**Job search:** joshua.hickman1@gmail.com  
**Studio:** destroythekraken@gmail.com  
**GitHub:** [DestroyTheKraken](https://github.com/DestroyTheKraken)

## Who this is for

Hiring managers at MSPs and internal IT teams. I use this lab the way a small shop uses a bench: keep hosts reachable, keep the edge honest, write down what is running, and get back in remotely without opening inbound WAN ports.

## Lab at a glance (2026-08-24)

| Piece | What it is |
|-------|------------|
| Edge | One VyOS rolling router, two inside networks |
| Lab LAN | `192.168.20.0/24` wired — control seat + three Ubuntu nodes |
| Home WLAN | `192.168.10.0/24` — mesh + household clients, separate from the cluster |
| Control seat | `um690` — Minisforum UM690, Ryzen 9 6900HX, 64 GiB, Ubuntu 26.04, dual-homed |
| Fleet | `node1`–`node3` — Lenovo ThinkCentre M93p, Ubuntu 26.04, SSH + Tailscale |
| Remote access | Two Tailscale tailnets (career identity vs studio identity) |

## Tailscale practice

Two accounts, on purpose:

- **Career** — `joshua.hickman1@gmail.com`
- **Studio** — `destroythekraken@gmail.com`

Studio tailnet (live, redacted): `um690`, `node1`–`node3`, operator phone `j-phn`, operator tablet `j-tab`. Career tailnet is a separate tenancy; the VyOS edge has a Tailscale interface that is **not** in the studio peer list. Full career inventory needs a profile switch on a machine with operator rights and will be published as another dated table.

That split is the skill on display: **users and clients as inventory**, not a single flat VPN.

## Spec sheets

| Doc | Contents |
|-----|----------|
| [docs/00-redaction-policy.md](docs/00-redaction-policy.md) | What never goes in this repo |
| [docs/01-overview.md](docs/01-overview.md) | Purpose and contact |
| [docs/02-network.md](docs/02-network.md) | Edge and segments |
| [docs/03-compute.md](docs/03-compute.md) | Host hardware and roles |
| [docs/04-tailscale.md](docs/04-tailscale.md) | Dual-tailnet practice |
| [docs/05-inventory-observed-2026-08-24.md](docs/05-inventory-observed-2026-08-24.md) | Dated live snapshot |
| [diagrams/network.txt](diagrams/network.txt) | ASCII topology |

## Related public repos

- [nc-lin-cs](https://github.com/DestroyTheKraken/nc-lin-cs) — Nextcloud hub installer
- [ssh-ufw-ts-install](https://github.com/DestroyTheKraken/ssh-ufw-ts-install) — SSH / UFW / Tailscale bootstrap
- [aide-os](https://github.com/DestroyTheKraken/aide-os) — lab / study notes
- [SovereignAid](https://github.com/DestroyTheKraken/SovereignAid) — platform ops experiments

## Honesty note

Pages here are **observed**, not aspirational. If a host was only running SSH and Tailscale that day, that is what the sheet says.

## Redaction

No WAN IPs, Tailscale addresses, MACs, keys, phone numbers, or household names. See the [redaction policy](docs/00-redaction-policy.md).
