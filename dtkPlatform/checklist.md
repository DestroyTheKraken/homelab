# Phase checklist — DTK home platform

Multiphase project only. Not an ops runbook.

## Phase 0 — Access foundation

- [ ] Confirm lab tailnet `tail13a119.ts.net` on um690 + node1–3
- [ ] Apply ACL grants + tags (`PLAN.md` §5) via Tailscale admin GUI
- [ ] UFW baseline on workers
- [ ] Exit: ops SSH yes · family-like SSH no · Portainer not for family

## Phase 1 — Watch + Listen (Jellyfin)

- [ ] Docker Engine on node1
- [ ] Portainer CE (ops-only)
- [ ] Deploy `Compose/jellyfin-compose.yml` via Portainer
- [ ] Tiny media test library
- [ ] Family Jellyfin users
- [ ] Phone streams over MagicDNS

## Phase 2 — Home portal

- [ ] Static five-tile page
- [ ] Reachable over Tailscale

## Phase 3 — Nextcloud

- [ ] Choose Option A (existing Core) or B (node2)
- [ ] Family accounts + photo test

## Phase 4 — Play (RetroArch)

- [ ] Deferred until Phases 0–3 exit

## Phase 5 — Portfolio polish (optional)

- [ ] Short per-service notes + compose in git (manual apply)
- [ ] No GitHub Actions required

## Deferred (separate design later)

- [ ] Homelab-wide start / stop / review procedures after all phases complete
