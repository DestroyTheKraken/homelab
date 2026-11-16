# Phase 09 — Games and the ROM library

**Status:** not started  
**Hosts:** node3 (`192.168.20.103`) and the UM690 NAS

## Start

Phase 08 exit checks passed. node3 is empty aside from SSH and Tailscale. Leave headroom: the machine is the same 2-core / 15 GiB chassis as node2, but it is not running Paper. Each web app should stay around 512 MiB.

ROM files go on `/srv/nas_a/roms`, not on node3’s 238 GB SSD. The closed HickMedia archive tarball under `HOME_LAB` is not the ROM source. The source is the live Batocera machine. Identify that host at the start of this phase.

## Massive Decks

Official container, Tailscale Serve HTTPS, ops-only admin. Two browsers can join a game.

## Bashcrawl

Sandbox container. The filesystem dungeon is the game. The web trainer, TermForge, tests, and git checkout are the backend and stay out of the image.

- Image: `ubuntu:22.04`
- User: `bashcrawl`
- `HOME=/home/bashcrawl`
- That home directory **is** the game entrance (the `entrance/` tree from `~/Projects/AIDE/aideGames/bashcrawl`, copied in at build time, plus the scrolls and encounters it needs)
- `cd` with no arguments returns to `/home/bashcrawl` because that is `$HOME`
- The image does not contain `web/`, `termforge/`, `src/`, or the git metadata
- Family reaches it by SSH on the tailnet as user `bashcrawl`, or by `docker exec` for ops. They do not get a login on the node3 host, and they do not get the Docker socket
- Real commands (`ls`, `cd`, `cat`) stay available. That is the game. Hiding the backend means they do not see the repo or the container build files

## Patzer

No tree for Patzer was in `~/Projects` during planning. First step in the session: ask Joshua for the source. Do not guess a GitHub repo. If he names it, install it as a small web service on node3 behind Tailscale Serve. If he does not, leave the checkbox open and continue with the other games.

## RetroAssembly and Batocera

1. Confirm the RetroAssembly project URL with Joshua before cloning. Do not guess.
2. Find the live Batocera machine and copy **only the ROM library** to `/srv/nas_a/roms`. Do not copy Batocera’s operating-system image.
3. Point RetroAssembly at that folder, read-only from node3’s point of view if the share allows it.
4. Launch one title in a tailnet browser.
5. Only after that title runs, ask Joshua to confirm the wipe of the Batocera machine. Wiping is a separate yes in that session. Do not wipe in the same unattended step as the copy.

## Exit

- [ ] Two browsers can open Massive Decks on the tailnet
- [ ] A `bashcrawl` SSH session lands in `/home/bashcrawl`, `cd` returns there, and `ls` shows the entrance rather than the git repo
- [ ] Patzer is either running or explicitly waiting on a source path
- [ ] One ROM from the Batocera library launches in RetroAssembly
- [ ] Batocera is still intact unless Joshua confirmed the wipe after that launch

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/10-dashboard
```
