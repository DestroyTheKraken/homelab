# Phase 10 — Service dashboard

**Status:** not started  
**Host:** node1, or a tiny static page on um690 if node1 is too full

## Start

Phases 02 through 09 have their exit checks passed or an explicit skip note in that phase’s README (Patzer may be the only skip).

Nextcloud is a door, not the game launcher. This phase is a link board. It does not single-sign-on Kodi, Steam, Paper, or Nextcloud.

## Work

1. One HTTPS page on the tailnet (Homepage, or a static page). Family can open it. They cannot SSH through it.
2. Tiles, each opening in a new tab:
   - Open WebUI
   - Kodi note: Kodi is an app, so the tile points at a short page that states the tailnet library address and how to add it in Kodi. There is no browser player.
   - Nextcloud
   - Minecraft lobby address (tailnet host and ports)
   - Massive Decks
   - Bashcrawl connection hint
   - RetroAssembly
   - Patzer, only if phase 09 installed it
3. Optional: a Nextcloud External sites entry that links to this same page.
4. Do not embed the AIDE lesson UI.

## Exit

- [ ] One MagicDNS URL opens
- [ ] Each live service tile reaches that service
- [ ] Family accounts still cannot SSH or open Portainer

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/11-mvp
```
