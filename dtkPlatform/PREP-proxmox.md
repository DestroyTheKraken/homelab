# Prep — Proxmox VE on node1–node3

**Written:** 2026-11-09  
**Status:** installed and clustered. Observed 2026-11-15. `dtk-cloud` is quorate. n1–n3 are `tag:ops` on the DTK tailnet.  
**Inventory:** [../docs/05-inventory-observed-2026-11-15.md](../docs/05-inventory-observed-2026-11-15.md)

LabNet is the learning and portfolio network. This prep stays on the DestroyTheKraken tailnet.

## Observed 2026-11-15

| Host | State |
|------|--------|
| node1 `192.168.20.101` | Proxmox VE. UI title `n1`. pve-manager asset `9.2.26`. |
| node2 `192.168.20.102` | Proxmox VE. UI title `n2`. pve-manager asset `9.2.26`. |
| node3 `192.168.20.103` | Proxmox VE. UI title `n3`. pve-manager asset `9.2.26`. |
| um690 `192.168.20.100` | Operator workstation. Stays Ubuntu. |
| vyos-router `192.168.20.1` | Edge. Stays VyOS. |

Prometheus and Grafana are the first monitoring guests, created in the Proxmox UI after a node is up. Other services (media, files, play) are also created there later. They are not part of the bare-metal install.

## Already true

- All three workers and the router are ThinkCentre M93p Tiny, type 10AB0016US.
- BIOS on each is `FBKTE0AUS`, 2021-12-23, release 1.224. That matches the latest public Lenovo package for this model. No further firmware step is required before install media is chosen.
- LabNet addresses above answer ping from `um690`.
- The Proxmox web UI answers on all three LabNet addresses.
- `pveversion` on n1 is `pve-manager/9.2.26`, kernel `7.0.14-28-pve`.
- Guest list is empty.
- LabNet SSH and MagicDNS SSH work as `root`.
- Each node is Tailscale `tag:ops`. MagicDNS is off on the hypervisors.
- Prometheus port 9090 and Grafana port 3000 did not answer on the node addresses.

## Still open

1. Prometheus and Grafana guests, created in the Proxmox UI.
2. `um690` and `vyos-router` stay on their current operating systems.
