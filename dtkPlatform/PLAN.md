# DTK Private Platform — MVP plan

**Updated:** 2026-11-15  
**Status:** Phase 00 (planning) is written. Implementation starts in [`phases/01-access`](./phases/01-access).  
**Scope:** household platform on LabNet and the DestroyTheKraken tailnet (`tail13a119.ts.net`). Not a customer product, and not the AIDE lesson UI.

Detailed steps live in [`phases/`](./phases/README.md). One session works in one phase directory. When that phase’s exit checks pass, stop. The next session starts in the next directory.

## Roles

| Host | Role |
|------|------|
| **um690** `.100` | AI seat (Ollama + Open WebUI + Whisper), Kodi movie database, Steam Big Picture, NAS |
| **node1** `.101` | Nextcloud. Weekly backups in that account’s `~/Backups` |
| **node2** `.102` | Minecraft network: Paper + Geyser/Floodgate, plugins from Hangar |
| **node3** `.103` | Massive Decks, Bashcrawl, Patzer, RetroAssembly |
| **Other consoles** | Left alone. They are not given an address, a DNS change, or a port. |
| **vyos-router** | Unchanged. No new WAN publish, DNAT, or UPnP |

UM690 stays Ubuntu 26.04.1 desktop. It is already that release. A Server reinstall is not part of this MVP. Steam and Kodi need the graphical session.

Proxmox VE **is installed** on node1–node3 as cluster `dtk-cloud` (quorate, 0 guests, `pve-manager` 9.2.26). n1–n3 are Tailscale `tag:ops`. See [`PREP-proxmox.md`](./PREP-proxmox.md) and the 2026-11-15 inventory. Phase steps that still say “install on Ubuntu on the node” were written before that fact. Login is `root`.

## Movie database

Kodi is the only movie database. An earlier media-server project is historical and **invalid** for this platform. Do not install it, document it as a feature, or extend it. Phase 03 removes that old process after Kodi can play a file.

Movie files live on the UM690 NAS at `/srv/nas_a/kodi/Movies`. One MariaDB on UM690 is the shared Kodi library so every Kodi client sees the same database. Clients reach the files and the database over the tailnet.

DVD ingest, when Joshua asks:

1. He inserts a disc.
2. He says it is inserted and ready, and he gives the disc name.
3. The session copies the disc, remuxes to MKV without re-encoding, names the folder from the name he gave, stores it under `/srv/nas_a/kodi/Movies`, and updates the Kodi library.

## Minecraft capacity

node2 is a ThinkCentre M93p: Core i5-4570T (2 cores / 4 threads), 15 GiB RAM, 238 GB SSD.

**Two Paper servers at once** is the confident cap. That means the lobby plus one minigame, with Geyser/Floodgate and a small proxy. People should be playing in one of those worlds. A third Paper world stays installed and **stopped**. Heavy Hangar minigame packs can pull the comfortable number down to one world with players. Four worlds online will not fit this machine.

## AI boundary

| Level | When | Allowed |
|-------|------|---------|
| L0 | Phase 02 | Chat, drafts, Whisper inside Open WebUI, answers from attached files |
| L1 | Phase 07 | Nextcloud Assistant writes inside the logged-in user’s files, through Open WebUI |
| Later | Not this MVP | Read-only checks and a drafted command. Joshua runs the command |
| Never | | Root shell written by the model, VyOS edits, firewall changes, creating users, restarting services |

Ollama stays on `127.0.0.1:11434`. Open WebUI is the only tailnet door to the model.

## Backups (Nextcloud)

| Tier | Where | Keep | Name |
|------|--------|------|------|
| Weekly | node1 `~/Backups` | 4 | `$DATE_bak.tar.gz` |
| Monthly | um690 `/srv/nas_a/backups/nextcloud` | 3 | `$DATE_bak.tar.gz` |
| Quarterly | offline host named at the start of phase 06 | 3 | `$DATE_bak.tar.gz` |

No home-folder symlinks into the Nextcloud data directory. One normal data directory on node1.

## End of MVP

Every service below is installed and answers on the tailnet. Preference screens and bulk file uploads come after that, except the ROM library, which is copied before the Batocera machine is wiped.

- Open WebUI chat and a Whisper dictation
- Kodi opens the shared movie library; the DVD procedure is ready
- Steam Big Picture launches after the large Ollama model is unloaded
- Nextcloud users `joshua` (admin, 50 GB) and `member` (standard, 50 GB), isolated from each other
- Weekly, monthly, and quarterly backup paths exist; one file has been restored
- Nextcloud can draft a file for `member` through the local model
- Paper lobby is joinable on the tailnet via Java and via Geyser; only two Paper servers run
- Massive Decks, Bashcrawl, and RetroAssembly answer; Patzer is installed once its source is named
- ROM files from the live Batocera machine play in RetroAssembly
- One dashboard page links the services that are up

## Out of this MVP

- A second hypervisor install. Proxmox is already on node1–node3.
- Prometheus and Grafana until they are created in the Proxmox UI
- k3s, Ceph
- Elgg
- Changing how consoles outside the lab join a game
- Opening the VyOS firewall
- A public or customer image of this platform
- MiniGame3 content until it has a name
- Ripping discs unless Joshua prompts with the disc name
