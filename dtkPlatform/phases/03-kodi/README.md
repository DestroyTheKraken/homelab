# Phase 03 — Kodi movie database

**Status:** not started  
**Host:** um690

## Start

Phase 02 exit checks passed. Kodi is not installed. Movie files for this platform do not exist yet at `/srv/nas_a/kodi/Movies`. The NAS is `/srv/nas_a` (about 1.7 TB free at planning time).

Kodi is the only movie database. A media server from an earlier project may still be running on node1. It is invalid. This phase removes it only after Kodi has played one file.

## Work

1. Install Kodi on the UM690 desktop session.
2. Install MariaDB on um690. Bind it to localhost and the tailnet address, not the whole LAN, and allow Kodi’s video database from tailnet clients.
3. Create `/srv/nas_a/kodi/Movies` owned by `joshua`.
4. Point Kodi at that folder and at the MariaDB video library (`advancedsettings.xml`).
5. Share that folder to tailnet clients (Samba or NFS limited to `100.64.0.0/10`). LabNet may read it. Do not publish it through VyOS.
6. Put one short test video in the movie folder, scan the library, and play it in Kodi on um690.
7. Install `dvdbackup` and `mkvmerge` or `ffmpeg` so a later rip can remux without re-encoding. Do not rip a disc in this phase unless Joshua prompts with the procedure below.
8. After the test file plays, stop and disable the historical media-server container on node1 (the container named for that old project, published on TCP 8096). Do not delete movie files on the NAS while doing that. Live-TV playlist files under the old tree are not imported.

### When Joshua asks to rip a disc

He will insert the DVD, say it is ready, and give the disc name. Then:

1. Confirm the mounted disc volume matches that name.
2. Copy the disc with `dvdbackup` into a work directory.
3. Remux MPEG-2 to MKV with stream copy. Do not re-encode.
4. Store it as `/srv/nas_a/kodi/Movies/<name he gave>/<name he gave>.mkv`. If he included a year, keep it in the name: `Title (Year)`.
5. Remove the work copy after the MKV plays.
6. Update the Kodi library and confirm the title appears.

An Avatar disc happened to be mounted during planning. It is not ripped until he sends that prompt.

## Exit

- [ ] Kodi on um690 plays the test file from `/srv/nas_a/kodi/Movies`
- [ ] A second Kodi client on the tailnet can see the same library entry (files + MariaDB)
- [ ] The old media-server process on node1 is stopped and disabled
- [ ] Port 8096 is not part of the platform docs or firewall allows added in this phase

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/04-steam
```
