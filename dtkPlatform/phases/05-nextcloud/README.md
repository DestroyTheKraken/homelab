# Phase 05 — Nextcloud on node1

**Status:** not started  
**Host:** node1 (`192.168.20.101`, user `kraken`)

## Start

Phase 04 exit checks passed. The historical media server on node1 is already stopped. node1’s disk is about 238 GB. Two 50 GB quotas fit. Four full copies of a full quota do not, which is why backups are a separate phase and leave this disk.

Do **not** use `nc-lin-cs` phase 4. That installer builds symlinks from real home folders into the Nextcloud data directory. This platform does not need that. Use one normal data directory.

## Work

1. Install Nextcloud with data in `/srv/nextcloud/data` on node1’s SSD. Docker or the distro packages are both fine. Pick the one that matches Ubuntu 26.04 docs that day. No symlinks from `/home/*/Documents`.
2. Create `joshua`, admin, quota 50 GB.
3. Create `member`, standard user, quota 50 GB.
4. Publish HTTPS with Tailscale Serve on node1.
5. Confirm family SSH and Portainer are still ops-only.
6. Do not install dashboard apps, the assistant, or backup cron in this phase.

## Exit

- [ ] `joshua` can upload a file over the tailnet URL
- [ ] `member` cannot see that file
- [ ] `member` can upload her own file
- [ ] Data is under `/srv/nextcloud/data`, and no symlink farm was created
- [ ] Both quotas report 50 GB

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/06-backups
```
