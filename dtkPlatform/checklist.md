# Phase checklist — DTK private platform

MVP sessions live in [`phases/`](./phases/README.md). Proxmox VE is installed on node1–node3 (observed 2026-11-15).

## 00 — Planning

- [x] Roles and end state in `PLAN.md` (2026-11-15)
- [x] Phase directories 01–11 written
- [x] Old media server removed from current platform docs

## 01 — Access

- [x] SSH from um690 to node1, node2, node3 (LabNet and DTK MagicDNS, as `root`)
- [x] `phases/01-access/inventory.md` written (2026-11-15)
- [x] Ollama still localhost-only (`127.0.0.1:11434`)
- [x] VyOS untouched

## 02 — Open WebUI

- [ ] Tailnet login, one model reply, one Whisper dictation
- [ ] Port 11434 still on localhost only

## 03 — Kodi

- [ ] Kodi plays a file from `/srv/nas_a/kodi/Movies`
- [ ] A second tailnet Kodi sees the same library entry
- [ ] Historical media server on node1 stopped and disabled

## 04 — Steam

- [ ] Big Picture opens from the UM690 keyboard
- [ ] Large Ollama model unloaded during that session

## 05 — Nextcloud

- [ ] `joshua` admin, 50 GB
- [ ] `member` standard, 50 GB
- [ ] They cannot see each other’s files
- [ ] Data directory only. No home-folder symlinks

## 06 — Backups

- [ ] Weekly `$DATE_bak.tar.gz` in node1 `~/Backups` (keep 4)
- [ ] Monthly copy in `/srv/nas_a/backups/nextcloud` (keep 3)
- [ ] One restored file matches
- [ ] Quarterly script present

## 07 — Assistant

- [ ] `member` gets a drafted note in her files
- [ ] Assistant has no SSH key

## 08 — Minecraft

- [ ] Two tailnet clients join the Paper lobby
- [ ] At most two Paper servers running
- [ ] Consoles outside the lab, and VyOS, untouched

## 09 — Games

- [ ] Massive Decks, two browsers
- [ ] Bashcrawl login lands in `/home/bashcrawl`
- [ ] One Batocera ROM plays in RetroAssembly
- [ ] Patzer installed, or source still unnamed

## 10 — Dashboard

- [ ] One tailnet page links the live services

## 11 — MVP

- [ ] `phases/11-mvp/acceptance.md` all required lines pass
