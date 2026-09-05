# Guide — Portainer CE on node1 (Phase 1)

**Lane:** Platform (GUI after one-time install)  
**Official docs:** [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/) · [Portainer CE install](https://docs.portainer.io/start/install-ce/server/docker/linux)

## Goal

Ops-only Docker GUI on `node1` (`tag:media`) so you deploy Jellyfin as a stack without living in the CLI.

## Preconditions

- Phase 0 tags/ACL drafted (`tag:media` on node1; port `9000` ops-only in grants).
- You can SSH as `kraken@node1` from um690 (ops).

## Click-path / steps

### A. One-time host prep (minimal CLI — then leave CLI)

On **node1** (via SSH from um690 only if Docker is not installed yet):

1. Follow Docker’s Ubuntu install page (apt repo → `docker-ce`).
2. Add `kraken` to the `docker` group; re-login.
3. Create Portainer data volume and run the official Portainer CE container (see Portainer docs — publish `9000:9000` or use `9443` HTTPS as you prefer).
4. Open UFW for Tailscale / allow `9000` only as needed; family must **not** get `9000` in ACL.

### B. Day-to-day (GUI)

1. On um690 browser: `https://node1.tail13a119.ts.net:9443` (or `:9000` if you chose HTTP).
2. Create the admin user (once).
3. Select the local Docker environment.
4. **Stacks** → **Add stack** → paste/`upload` from `Compose/jellyfin-compose.yml` when ready for Jellyfin.
5. Use Portainer for start/stop/logs/volumes afterward.

## Optional YouTube query

`Portainer CE Docker stacks tutorial 2024` — one video max.

## Stop conditions

- Installing Portainer on um690 “just because” when node1 is the media host → don’t (keep roles clear).
- Exposing Portainer to `group:family` → never.
- Diving into k8s inside Portainer → out of scope.

## Rollback

In Portainer: stop/remove the Portainer container only if you still have SSH+Docker CLI access; or `docker stop`/`rm` the portainer container from SSH.

## LFCS explain-later (max 3)

```bash
docker ps
ss -tlnp | grep -E '9000|9443|8096'
systemctl status docker --no-pager
```
