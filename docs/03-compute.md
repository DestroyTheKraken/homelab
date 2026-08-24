# Compute spec sheet

**Observed:** 2026-08-24

## Control seat — `um690`

| Field | Value |
|-------|--------|
| Role | Daily operator workstation, Git, docs, local Ollama, Tailscale client |
| Hardware | Minisforum UM690 (Micro Computer HK) |
| CPU | AMD Ryzen 9 6900HX (8c/16t) + Radeon 680M |
| Memory | 64 GiB |
| System disk | 1.9 TB NVMe (TEAM), Ubuntu 26.04 LTS, kernel 7.0 |
| Lab IPv4 | `192.168.20.100/24` |
| Home IPv4 | `192.168.10.150/24` |
| Users | `joshua` (operator) |
| Notable local services | OpenSSH, Tailscale, Ollama (localhost only) |

Removable USB disks attached to this seat are working media, not published inventory.

## Cluster nodes — `node1` `node2` `node3`

Identical small-form-factor desktops on the lab LAN. Used as a repeatable three-node Linux fleet (same image class, SSH + Tailscale).

| Field | Value |
|-------|--------|
| Hardware | Lenovo ThinkCentre M93p |
| CPU | Intel Core i5-4570T @ 2.90 GHz |
| Memory | 15 GiB |
| Disk | 238 GB SATA SSD |
| OS | Ubuntu 26.04 LTS |
| User | `kraken` |
| Listening (snapshot) | OpenSSH, Tailscale |
| Uptime at snapshot | ~6 days |

| Host | Lab IPv4 |
|------|----------|
| node1 | `192.168.20.101` |
| node2 | `192.168.20.102` |
| node3 | `192.168.20.103` |

These three were **not** running extra application daemons at snapshot. They are the fleet to administer, not a hidden hypervisor layer.

## Edge

Documented in [02-network.md](02-network.md). Not a compute node for workloads.

## Operator clients

Android phone (`j-phn`) and tablet (`j-tab`) on the studio tailnet. Used to practice client enrollment and remote reachability. Device identifiers beyond those hostnames are omitted.
