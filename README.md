# Homelab

Redacted spec sheets for the premises network I designed, installed, and operate in Omak, WA.

**Job search:** joshua.hickman1@gmail.com  
**Studio:** destroythekraken@gmail.com  
**GitHub:** [DestroyTheKraken](https://github.com/DestroyTheKraken)

## Who this is for

MSP and internal-IT hiring managers. I want to work **on a team**. This lab is how I practice the job I am applying for — not a k3s or “HA cloud” claim.

## What I actually run and practice

I designed and deployed the premises network: Starlink, a **VyOS** edge (ThinkCentre Tiny + USB Ethernet adapters), a lab switch, and a TP-Link Deco mesh in AP mode. Home and lab are separate. Guest and IoT SSIDs are split from household Wi-Fi. I image Linux and Windows desktops and Ubuntu/Rocky-style servers. I use VirtualBox and Multipass for disposable labs. I live in the CLI (files, packages, systemctl basics) and use default-deny firewall habits (UFW / firewalld basics).

I use **Grok Build** and **Claude Code** to research, draft, and configure **while I learn**. I type the commands, test the result, and write the notes. That is also how I would stand up a more complex stack (for example Kubernetes) if a job required it — not because a k3s cluster is what this lab is today.

## Lab at a glance (2026-08-24)

| Piece | What it is |
|-------|------------|
| WAN | Starlink (CGNAT — no inbound port-forwards) |
| Edge | VyOS rolling on a ThinkCentre M93p Tiny |
| Lab LAN | `192.168.20.0/24` wired — control seat + three Ubuntu nodes + display |
| Home WLAN | `192.168.10.0/24` — Deco APs; household, guest, and IoT SSIDs |
| Isolation | Lab hosts cannot reach home hosts; both can reach the internet |
| Control seat | `um690` — Minisforum UM690, Ryzen 9 6900HX, 64 GiB, Ubuntu 26.04 |
| Fleet | `node1`–`node3` — ThinkCentre M93p, Ubuntu 26.04, SSH + Tailscale |
| Remote access | Two Tailscale tailnets (lab identity vs home identity) |

## Two Tailscale tenancies

| Tailnet | Login | Role |
|---------|-------|------|
| Lab (Destroy the Kraken) | destroythekraken@gmail.com | Cluster + operator mobiles |
| Home (HickmaNet) | joshua.hickman1@gmail.com | Household and field clients |

Same person, two identities, two device inventories. That is the practice: users and clients as objects you administer, not one flat VPN. Addresses omitted.

## Spec sheets

| Doc | Contents |
|-----|----------|
| [docs/00-redaction-policy.md](docs/00-redaction-policy.md) | What never goes in this repo |
| [docs/01-overview.md](docs/01-overview.md) | Purpose and contact |
| [docs/02-network.md](docs/02-network.md) | Edge, segments, isolation |
| [docs/03-compute.md](docs/03-compute.md) | Hosts and PC deployments |
| [docs/04-tailscale.md](docs/04-tailscale.md) | Both tailnets (redacted) |
| [docs/05-inventory-observed-2026-08-24.md](docs/05-inventory-observed-2026-08-24.md) | Dated snapshot |
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

These pages are **observed**. If a host was only running SSH and Tailscale that day, that is what the sheet says. I do not list k3s, Ceph, or Proxmox as current production here. AI-assisted setup is how I learn; I still operate the box.

## Redaction

No WAN IPs, Tailscale addresses, MACs, keys, phone numbers, or household given names. See the [redaction policy](docs/00-redaction-policy.md).
