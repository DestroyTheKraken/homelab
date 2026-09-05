# Plan: DestroyTheKraken Home Platform (multiphase install)

> **Org:** `~/Projects/HOME_LAB/dtkPlatform/` · buckets: AIDE / DTK / HOME_LAB (`~/Projects/README.md`).  
> **This document is the multiphase project only.** Daily start/stop/review rituals, session coaching, and post-build ops UX are **out of scope** until you design them separately.

**Goal:** Shared family/friends home platform on LabNet — plug-and-play services, one phase at a time — portfolio practice for Net+ → LFCS. Not a product SKU.

**Constraints:** solo · Tailscale Free ×2 · no Google group sync · no GitHub Actions to private hosts · GUI-first for non-LFCS work (Portainer / Tailscale admin / app UIs) · CLI reserved for deliberate LFCS drills.

---

## 1. Done looks like (v1)

| Surface | Job | Implementation |
|---------|-----|----------------|
| **Home** | Launch pad | Static HTML tiles → MagicDNS URLs |
| **Watch** | Movies / TV | Jellyfin |
| **Listen** | Music / radio | Same Jellyfin |
| **Play** | Retro games | RetroArch (later phase) |
| **Settings** | Accounts / basics | Nextcloud + simple status links (not a custom settings app) |

### Non-goals

- Ubuntu Core / Frame / WPE / custom QML appliance
- Fathom / JellyEmu / Stremio stack from BraveResearch
- k3s / Longhorn / Traefik on LabNet for family services
- Customer installer / proprietary packaging
- Google Workspace sync; full GitOps CI
- Resurrecting hostname `fam-media` (chassis is **node3**)
- Designing daily ops / start-stop / review methodology (deferred)

---

## 2. Sources of truth (project)

| Priority | Path | Use |
|----------|------|-----|
| 1 | `AIDE/aideArchives/SovereignAid/ARCHITECTURE.md` | Live mesh facts |
| 1 | `HOME_LAB/docs/` | Redacted network / Tailscale inventory |
| 1 | `HOME_LAB/dtkPlatform/PLAN.md` | This phased plan |
| 2 | `HOME_LAB/hickMedia/compose/jellyfin/` | Jellyfin compose template |
| 2 | `HOME_LAB/installers/nc-lin-cs/` | Nextcloud installer option |
| 2 | `HOME_LAB/installers/ssh-ufw-ts-install/` | SSH/UFW/Tailscale bootstrap pattern |
| 3 | `Documents/BraveResearch/brave-research_mediaUI.md` | Idea scrapbook only |

Leaf GitHub remotes: see [`../../REPOS.md`](../../REPOS.md) (do not confuse local folders with remote names).

---

## 3. Ground truth (LabNet)

```
Starlink CGNAT → VyOS → LabNET 192.168.20.0/24
                         um690 .100  (joshua)  control / study seat
                         node1 .101  (kraken)  → tag:media   (Jellyfin + Portainer)
                         node2 .102  (kraken)  → tag:cloud   (Nextcloud)
                         node3 .103  (kraken)  → tag:play    (RetroArch later)
```

| Fact | Detail |
|------|--------|
| Lab tailnet | `destroythekraken@` · `tail13a119.ts.net` |
| Home tailnet | HickmaNet (`joshua.hickman1@`) — private; not family platform |
| Today | SSH + Tailscale up; no app services on workers yet |
| Nextcloud exception | Old Core appliance may sit on `taile52ad9.ts.net` — do not put mesh nodes there |

**Tenancy:** DTK tailnet = shared platform. Secrets-only-to-you stay on HickmaNet. Inside DTK: least privilege (apps yes, SSH/Portainer ops-only).

---

## 4. Tooling (how phases execute — not daily ops)

| Tool | Role in *this* project |
|------|-------------------------|
| **Docker Engine + Compose** | Required for Phase 1+ services |
| **Portainer CE** | Default GUI to deploy/manage stacks on node1 |
| **GitOps-lite** | Optional Phase 5: track compose in git; apply by hand (no Actions) |
| **Kubernetes** | Not used for family platform; optional later Multipass study only |

---

## 5. Phase 0 — Access foundation

**Deliverable:** DestroyTheKraken ACL grants + tags; workers firewalled sensibly.

- Confirm devices on `tail13a119.ts.net`
- Grants (conceptual): `group:family` → `tag:media:8096` and cloud HTTP(S); `group:ops` → tagged servers `*`; Portainer `:9000`/`:9443` **ops-only**; SSH check-mode for ops only
- Tags: node1 `tag:media`, node2 `tag:cloud`, node3 `tag:play`, um690 `tag:ops` (as roles land)
- UFW: default deny; SSH; Tailscale; open service ports when installed

**Exit:** Ops can SSH; family-like identity cannot SSH and cannot open Portainer.

**Guide stub:** `Guides/tailscale-acl-grants.md` (click-path aid, not an ops system).

---

## 6. Phase 1 — Watch + Listen (Jellyfin on node1)

**Deliverable:** Jellyfin reachable at `http://node1.tail13a119.ts.net:8096` via Portainer stack.

- Docker Engine on node1
- Portainer CE (ops-only)
- Stack from `Compose/jellyfin-compose.yml` (origin: `hickMedia/compose/jellyfin`)
- Small `/srv/mediahub/media/{movies,tv,music}` test library
- Per-user Jellyfin accounts (not shared admin)

**Exit:** Phone on DTK streams a test video and plays a music folder.

**Guide stub:** `Guides/portainer-on-node1.md`.

---

## 7. Phase 2 — Home portal

**Deliverable:** One static page with five tiles (Home destinations for Watch / Listen / Play / Settings / status).

- Caddy/nginx or Tailscale Serve
- No gamepad shell / starfield / Bridge product UI

**Exit:** Family opens one Home URL and reaches Jellyfin.

---

## 8. Phase 3 — Settings / files (Nextcloud)

Pick **one**:

| Option | When |
|--------|------|
| **A** Keep existing Nextcloud Core on `taile52ad9` | Already healthy |
| **B** Fresh on node2 (`nc-lin-cs` or Docker/Portainer) on `tail13a119` | Prefer one tailnet |

- Tailscale Serve HTTPS
- Family accounts; Docs / Photos
- Defer AI helpers until stable

**Exit:** Photo upload on phone visible on another DTK device.

---

## 9. Phase 4 — Play (RetroArch)

- Seat: node3 HDMI or household PC on DTK
- Flatpak/Ubuntu RetroArch; legal ROMs only
- Link Play tile on Home

**Exit:** One controller, one core, one game, documented once (a short note — not a full ops program).

---

## 10. Phase 5 — Portfolio polish (optional)

- Short per-service runbook snippets (start/stop/backup/invite) suitable for a résumé appendix
- Commit compose + redacted notes; apply by hand (GitOps-lite)
- Refresh `HOME_LAB/docs` inventory when roles change
- Still no GitHub Actions required

**Not included:** a Homelab-wide start/stop/review console, daily session system, or post-project ops methodology — design that later if you want it.

---

## 11. Open forks

| Fork | Default | Alternative |
|------|---------|-------------|
| Jellyfin host | node1 | um690 |
| Docker GUI | Portainer CE | CLI-only (LFCS drill days) |
| Nextcloud | node2 or keep Core appliance | um690 |
| Play seat | defer; node3 later | household PC |
| Media store | local `/srv/mediahub/media` first | NAS first |

---

## 12. Implementation order

1. Phase 0 — ACL + tags + UFW  
2. Phase 1 — Docker + Portainer + Jellyfin  
3. Phase 2 — Home portal  
4. Phase 3 — Nextcloud  
5. Phase 4 — RetroArch  
6. Phase 5 — Polish / GitOps-lite (optional)  

**Parallel (separate from this plan):** LFCS via `AIDE/aideTutor` + `aideOs`; k8s only in Multipass if/when you choose.

---

## 13. Explicitly deferred (do not invent here)

- Daily session coach / PlasmaLLM ritual  
- Homelab-wide start · stop · review procedures after all phases complete  
- Unified “ops dashboard” for every service  

Those need their own design pass when you are ready. This plan stops at **building the phased platform**.
