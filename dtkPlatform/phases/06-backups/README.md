# Phase 06 — Nextcloud backups

**Status:** not started  
**Hosts:** node1 and um690

## Start

Phase 05 exit checks passed. Nextcloud data is `/srv/nextcloud/data` on node1. At the start of this phase, ask Joshua for the quarterly offline host. If he does not have a name yet, write the quarterly script so the destination is a variable, leave it unset, and still finish weekly and monthly.

## Layout

| Tier | Where | Keep | Filename |
|------|--------|------|----------|
| Weekly | node1 `~/Backups` (the `kraken` account: `/home/kraken/Backups`) | 4 | `$DATE_bak.tar.gz` |
| Monthly | um690 `/srv/nas_a/backups/nextcloud` | 3 | `$DATE_bak.tar.gz` |
| Quarterly | the host he names | 3 | `$DATE_bak.tar.gz` |

`$DATE` is `YYYYMMDD`.

## Work

1. Dump the Nextcloud database and archive `/srv/nextcloud/data` plus that dump into one `$DATE_bak.tar.gz`.
2. Weekly cron on node1 writes the archive to `~/Backups` and deletes archives older than the newest 4.
3. Refuse to write a weekly archive if it would leave less than 20 GB free on node1.
4. Monthly cron copies the newest weekly archive to `/srv/nas_a/backups/nextcloud` and keeps 3 monthly files. Run it once by hand in this phase so the directory is not empty.
5. Quarterly: a script that copies the newest monthly archive to the named host and keeps 3. If the host is unnamed, the script exists and exits with a clear “destination not set” message.
6. Restore drill: pick one file from `member`, restore it from the weekly archive into a temporary directory, and compare it to the live file. Do not overwrite the live file unless the compare fails and that user wants the restore.

## Exit

- [ ] `/home/kraken/Backups` contains a `$DATE_bak.tar.gz`
- [ ] `/srv/nas_a/backups/nextcloud` contains that monthly copy
- [ ] A restored file matches the live file
- [ ] Retention is 4 weekly and 3 monthly
- [ ] Quarterly script is present, either pointed at the named host or explicitly waiting for a name

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/07-assistant
```
