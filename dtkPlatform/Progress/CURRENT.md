# Current progress

**Updated:** 2026-11-15

| Field | Value |
|-------|-------|
| Phase | 01 access is complete. Next session is `phases/02-open-webui`. |
| Blockers | Quarterly backup host is unnamed until phase 06. Patzer’s source tree was not in `~/Projects` at planning time. MiniGame3 has no name. |
| Next project step | `cd ~/Projects/HOME_LAB/dtkPlatform/phases/02-open-webui` |
| Hypervisor | Cluster `dtk-cloud` is quorate: n1, n2, n3. No guests yet. LabNet SSH works. All three are on the DTK tailnet as `tag:ops`. |
| Tailscale policy | Accepted 2026-11-15. Ops: all ports. Family: `tag:media` TCP 8096 and `tag:cloud` TCP 80/443 only. No family SSH, Proxmox UI, play, or monitor grant. Live file stays in the admin console. |

## Notes

- Portfolio scope is LabNet plus the DestroyTheKraken tailnet.
- Kodi movie files will live at `/srv/nas_a/kodi/Movies` on `um690`.
- An earlier media-server project is invalid for this platform. Phase 03 removes it after Kodi plays a file.
- `um690` and `vyos-router` stay on their current operating systems. `um690` stays a desktop.
