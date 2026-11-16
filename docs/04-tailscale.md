# Tailscale — DestroyTheKraken

Tailscale is how this lab reaches LabNet without an inbound WAN port-forward. It is not a substitute for the LAN.

This repo records one tailnet: **DestroyTheKraken (DTK)**, login `destroythekraken@gmail.com`. Other tailnets are private and are not documented here. Non-lab devices on DTK are omitted on purpose.

Addresses, relays, direct endpoints, and numeric user IDs are omitted.

## DTK tailnet — lab hosts observed 2026-11-15

Captured on `um690` with `tailscale status`, then checked on the cluster over LabNet SSH. Only lab machines are listed.

| Hostname | OS | Status |
|----------|-----|--------|
| um690 | linux | Logged into `destroythekraken@gmail.com`. MagicDNS suffix `tail13a119.ts.net`. |
| n1, n2, n3 | linux | Enrolled the same day. Each is `tag:ops` and online. MagicDNS is off on the nodes so Proxmox keeps its own resolver (`1.1.1.1`). |

LabNet SSH works as `ssh node1`, `ssh node2`, and `ssh node3`. Tailnet SSH works as `ssh node1-ts`, `ssh node2-ts`, and `ssh node3-ts`, which resolve to `n1.tail13a119.ts.net` and the matching names for n2 and n3.

The 2026-11-09 read showed `node1`–`node3` as tagged devices on the Ubuntu install. Those enrollments were replaced by this Proxmox enrollment.

`vyos-router` was not in the 2026-11-15 status output.

## What this demonstrates

1. Keep the portfolio tailnet limited to lab machines
2. Use device tags on the workers and a user identity on the control seat
3. Reach the lab without inbound WAN ports under Starlink CGNAT
