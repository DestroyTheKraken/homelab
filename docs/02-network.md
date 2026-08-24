# Network spec sheet

**Observed:** 2026-08-24  
**Edge:** VyOS rolling (`2026.06.24-0045-rolling`) on a Lenovo ThinkCentre M93p Tiny, hostname `vyos-router`  
**WAN:** Starlink on `eth0` (CGNAT — address omitted; no inbound DNAT)

## Logical layout

One appliance, two inside networks. The control seat (`um690`) is dual-homed; the wired lab default route wins.

| Segment | Prefix | Role |
|---------|--------|------|
| Lab LAN (wired) | `192.168.20.0/24` | Administration, cluster, SSH, display |
| Home LAN / WLAN | `192.168.10.0/24` | Household, guest SSID, IoT SSID |
| Lab tailnet | MagicDNS on the studio identity | Remote access for lab hosts |
| Home tailnet | MagicDNS on the job-search identity | Household and field clients |

## Physical path

1. **Starlink** — upstream. CGNAT, so remote access is Tailscale, not port-forward.
2. **VyOS Tiny** — `eth0` WAN. Home face `eth2` = `192.168.10.1/24`. Lab face `eth3` = `192.168.20.1/24` (USB Ethernet adapter; the Tiny does not have enough onboard NICs).
3. **TP-Link USB Ethernet adapters** — extra ports so WAN, home, and lab each have a dedicated interface.
4. **Lab switch** — `um690`, `node1`–`node3`, display.
5. **TP-Link Deco X20 (×2)** — mesh in **access-point** mode, DHCP off. VyOS is the only DHCP/DNS edge for Home. SSIDs: household, guest, and IoT (same home prefix; client classes isolated at the mesh). After a power loss the mesh can fall back to router mode on a private prefix; recovery is: AP mode + DHCP off, then confirm leases come from `192.168.10.1`.

## Isolation (tested from the lab NIC)

| Test | Expected |
|------|----------|
| Lab host → lab gateway | pass |
| Lab host → other lab hosts | pass |
| Lab host → home gateway address | pass (router SVI only) |
| Lab host → a home/Deco client | fail (forward default-deny) |
| Either LAN → WAN | pass (stateful) |
| WAN → inside | fail (no DNAT) |

Forward policy: default drop; only LAN-group → WAN is accepted. SSH to the router is from the lab control seat (and Tailscale), not from the home WLAN.

## Home WLAN (summarized)

Household phones, laptops, displays, and IoT sit on `192.168.10.0/24` behind the Deco APs. Guest and IoT use separate SSIDs. Individual MACs, PSKs, and given names are omitted.

See [06-vyos-build.md](06-vyos-build.md) and [diagrams/network.txt](../diagrams/network.txt).
