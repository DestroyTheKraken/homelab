# Network spec sheet

**Observed:** 2026-11-09  
**Edge:** VyOS rolling (`2026.06.24-0045-rolling`) on a Lenovo ThinkCentre M93p Tiny, hostname `vyos-router`  
**WAN:** Starlink on `eth0` (CGNAT — address omitted; no inbound DNAT)  
**Scope:** LabNet and the DestroyTheKraken tailnet. The other premises LAN is an edge fact only.

## Logical layout

One appliance, LabNet as the documented inside network. `um690` uses the wired lab address as its working path.

| Segment | Prefix | Role |
|---------|--------|------|
| Lab LAN (wired) | `192.168.20.0/24` | Administration, workers, SSH |
| DTK tailnet | MagicDNS on `destroythekraken@gmail.com` | `um690`, plus n1–n3 as `tag:ops` |
| Other inside LAN | `192.168.10.0/24` on `eth2` | Premises separation. Clients are not inventoried in this repo. |

## Physical path

1. **Starlink** — upstream. CGNAT, so remote access is Tailscale, not port-forward.
2. **VyOS Tiny** — `eth0` WAN. Home face `eth2` = `192.168.10.1/24`. Lab face `eth3` = `192.168.20.1/24` (USB Ethernet adapter; the Tiny does not have enough onboard NICs).
3. **TP-Link USB Ethernet adapters** — extra ports so WAN, home, and lab each have a dedicated interface.
4. **Lab switch** — `um690`, `node1`–`node3`.
5. **Access points on the other inside LAN** — TP-Link Deco X20 mesh in access-point mode, DHCP off, so VyOS stays the DHCP authority. SSIDs and clients are out of scope for this repo. After a power loss the mesh can fall back to router mode; recovery is AP mode + DHCP off, then confirm leases come from `192.168.10.1`.

## Isolation (tested from the lab NIC)

| Test | Expected |
|------|----------|
| Lab host → lab gateway | pass |
| Lab host → other lab hosts | pass |
| Lab host → the other inside gateway address | pass (router SVI only) |
| Lab host → a client on the other inside LAN | fail (forward default-deny) |
| Either LAN → WAN | pass (stateful) |
| WAN → inside | fail (no DNAT) |

Forward policy: default drop; only LAN-group → WAN is accepted. SSH to the router is from the lab control seat (and the DTK tailnet).

Clients on `192.168.10.0/24` are outside this portfolio inventory.

See [06-vyos-build.md](06-vyos-build.md) and [diagrams/network.txt](../diagrams/network.txt).
