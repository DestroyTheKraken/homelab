# Network spec sheet

**Observed:** 2026-08-24  
**Edge:** single VyOS rolling router (`2026.06.24-0045-rolling`), hostname `vyos-router`  
**WAN address:** omitted (redaction policy)

## Logical layout

One appliance, two inside networks. The control seat (`um690`) is dual-homed; default route prefers the wired lab LAN.

| Segment | Prefix | Role |
|---------|--------|------|
| Lab LAN (wired) | `192.168.20.0/24` | Administration, cluster nodes, SSH |
| Home WLAN | `192.168.10.0/24` | Operator Wi-Fi, vendor mesh, IoT |
| Studio tailnet | MagicDNS `*.tail13a119.ts.net` | Remote access for studio identity |
| Career tailnet | not published | Remote access for job-search identity |

## Edge interfaces (roles only)

| Interface | Role | Addressing published |
|-----------|------|----------------------|
| WAN / upstream | Internet edge | no |
| Lab LAN | `192.168.20.1/24` | yes (gateway) |
| Home WLAN | `192.168.10.1/24` | yes (gateway) |
| Wireless radio on the router | present, down at snapshot | n/a |
| Tailscale on the edge | present; **not** a member of the studio tailnet | address omitted |

SSH to the edge is reachable from the lab LAN. SSH from the home WLAN to the home-side gateway address timed out at snapshot (management stays on the lab LAN).

## Home WLAN (summarized)

Consumer mesh access points and a typical household IoT mix live on `192.168.10.0/24`. Individual MACs, SSIDs, and guest names are omitted. The point for a hiring manager: **user / IoT traffic is not on the same L2 segment as the cluster.**

## Routing note

`um690` has two default routes. Wired lab metric wins over DHCP Wi-Fi. Dual-homing is intentional so the control seat can see both segments without bridging them.

See [diagrams/network.txt](../diagrams/network.txt).
