# Compute spec sheet

**Observed:** 2026-11-15  
**Scope:** LabNet machines.  
**Workers:** Proxmox VE is installed on `node1`–`node3`. Prometheus and Grafana were not reachable on the host addresses. See [05-inventory-observed-2026-11-15.md](05-inventory-observed-2026-11-15.md).

## Control seat — `um690`

| Field | Value |
| --- | --- |
| Role | Operator workstation for LabNet and the DTK tailnet: Git, docs, local models |
| Hardware | Minisforum UM690 |
| CPU | AMD Ryzen 9 6900HX (8c/16t) + Radeon 680M |
| Memory | 64 GiB |
| System disk | 1.9 TB NVMe, Ubuntu 26.04 LTS |
| Lab IPv4 | `192.168.20.100/24` |
| User | `joshua` |
| Role in the transition | Stays the operator workstation. Not a Proxmox target. |

Removable USB disks on this seat are working media, not published inventory.

## Lab fleet — `node1` `node2` `node3`

Three matching small-form-factor PCs. Proxmox VE is installed on the bare metal.

| Field | Value |
| --- | --- |
| Hardware | Lenovo ThinkCentre M93p |
| CPU | Intel Core i5-4570T @ 2.90 GHz |
| Memory | 15 GiB |
| Disk | 238 GB SATA SSD |
| OS today | Proxmox VE 9.2. Cluster `dtk-cloud`, quorate. `pve-manager/9.2.26`, kernel `7.0.14-28-pve` on n1. |
| BIOS | `FBKTE0AUS` (2021-12-23), release 1.224. Last read 2026-11-09, before this install. Not re-read after the reinstall. |
| Web UI names | n1, n2, n3 |
| SSH | `root` from `um690` on LabNet and on `n1.tail13a119.ts.net` (n2 and n3 match). Tailscale tag `tag:ops`. |
| Guests | 0 virtual machines, 0 LXC containers. |

| Host | Lab IPv4 | Note |
| --- | --- | --- |
| node1 | `192.168.20.101` | Proxmox UI title `n1`. Port 8006 open. |
| node2 | `192.168.20.102` | Proxmox UI title `n2`. Port 8006 open. |
| node3 | `192.168.20.103` | Proxmox UI title `n3`. Port 8006 open. |

## Edge

VyOS on a fourth ThinkCentre M93p Tiny, same BIOS string as the workers. Not a workload node and not a Proxmox target. See [06-vyos-build.md](06-vyos-build.md).

## Software (2026-11-15)

| Host | Observed |
| --- | --- |
| um690 | Desktop stack. Not re-scanned in full on this date. |
| node1–node3 | Proxmox VE cluster `dtk-cloud`. Web UI on port 8006. Tailscale `tag:ops` with MagicDNS off. No guests. Prometheus and Grafana are not installed. |
| vyos-router | Ping only. Edge role unchanged in the docs. OS not re-read. |
