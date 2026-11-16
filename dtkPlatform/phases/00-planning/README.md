# Phase 00 — Planning

**Status:** complete (2026-11-15)

## Start

When this page was written, the notes still described node1–node3 as Ubuntu. That is stale. On 2026-11-15 the Proxmox web UI was up on all three. `um690` remains the Ubuntu desktop. Ollama was on UM690, bound to localhost. Steam and Kodi were not installed. An earlier media-server project is historical and is not part of this platform.

## What this phase decided

Recorded in [`../../PLAN.md`](../../PLAN.md).

- No Ubuntu Server reinstall. UM690 keeps the desktop it already has.
- Kodi is the only movie database.
- Nextcloud goes on node1, with a normal data directory and no home-folder symlinks.
- Weekly backups: node1 `~/Backups` (4). Monthly: `/srv/nas_a/backups/nextcloud` (3). Quarterly: an offline host named in phase 06 (3). Files are `$DATE_bak.tar.gz`.
- Minecraft on node2 is Paper + Geyser/Floodgate, with extra plugins from Hangar. Confident cap is two Paper servers at once.
- Games and the Batocera ROM library land on node3 / the NAS. The Batocera machine is wiped only after one ROM plays.
- The local model does not get root.
- Consoles outside the lab, and VyOS, stay as they are.
- Proxmox was marked paused in this planning session. That decision is superseded: the web UI was observed the same day. See the 2026-11-15 inventory.

## Exit

- [x] [`../../PLAN.md`](../../PLAN.md) matches this decision
- [x] Phase directories 01 through 11 exist
- [x] Platform docs no longer prescribe the old media server

## Handoff

Phase 00 is complete. Next session:

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/01-access
```

Say: review phase 00, and if it is complete, begin phase 01.
