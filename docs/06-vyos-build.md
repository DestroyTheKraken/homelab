# VyOS edge — how it was built

**Hardware:** Lenovo ThinkCentre M93p Tiny  
**Software:** VyOS rolling, image dated 2026-06-24  
**WAN:** Starlink on `eth0`  
**Inside:** Home `eth2` (`192.168.10.1/24`), lab `eth3` (`192.168.20.1/24`)

## Why this box

The Tiny does not have three useful Ethernet ports. I added **TP-Link USB Ethernet adapters** so WAN, home, and lab each have a dedicated NIC. A small switch fans the lab ports out to the PCs.

I installed the image, wrote the interface, DHCP, firewall, and SSH config, and brought the box into daily use myself. Grok (CLI and web) was a research and debug partner: I asked why a commit failed, compared `show` output, and searched docs. **I typed every command and accepted every commit.**

## Design choices a hiring manager can check

| Choice | Why |
|--------|-----|
| VyOS instead of a consumer all-in-one | Practice real edge config: interfaces, firewall, DHCP, change discipline |
| Starlink + no WAN DNAT | CGNAT means inbound port-forwards are the wrong tool; Tailscale is the remote path |
| Two inside SVIs, default-deny forward | Home and lab share an internet edge without sharing L2 |
| Deco in AP mode, DHCP off | One DHCP authority (VyOS). Mesh is radio, not a second router |
| SSH only from the lab control seat | Management stays on the admin LAN |
| Rolling image, manual upgrades | Weekly config snapshot; image installs are never cron'd |

## Operations I actually run

- Config snapshots (commands + boot config) on a weekly cadence
- Image-age checks; upgrades only with a console or second session and a keep-old-image fallback
- After power loss: confirm Deco is still in AP mode (it has come back as a router on a private prefix)
- DHCP static maps for the lab core (`um690`, `node1`–`node3`, display)

Exact `config.boot` is **not** in this public repo.

## What I am claiming

I can install an edge OS, give it three interfaces, write a default-deny forward policy, hand out addresses, keep home and lab apart, and recover when the mesh or a NIC falls over. I use an assistant the way I would use a senior on the bench: questions and second opinions, then I own the result.
