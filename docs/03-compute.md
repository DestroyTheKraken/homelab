# Compute spec sheet

**Observed:** 2026-08-24

## Control seat — `um690`

| Field | Value |
|-------|--------|
| Role | Daily operator workstation, Git, docs, local models, Tailscale (both identities over time) |
| Hardware | Minisforum UM690 |
| CPU | AMD Ryzen 9 6900HX (8c/16t) + Radeon 680M |
| Memory | 64 GiB |
| System disk | 1.9 TB NVMe, Ubuntu 26.04 LTS |
| Lab IPv4 | `192.168.20.100/24` |
| Home IPv4 | `192.168.10.150/24` |
| User | `joshua` |

Removable USB disks on this seat are working media, not published inventory.

## Lab fleet — `node1` `node2` `node3`

Three matching small-form-factor PCs I imaged and keep as a repeatable Ubuntu fleet.

| Field | Value |
|-------|--------|
| Hardware | Lenovo ThinkCentre M93p |
| CPU | Intel Core i5-4570T @ 2.90 GHz |
| Memory | 15 GiB |
| Disk | 238 GB SATA SSD |
| OS | Ubuntu 26.04 LTS |
| User | `kraken` |
| Listening (snapshot) | OpenSSH, Tailscale |

| Host | Lab IPv4 | Note |
|------|----------|------|
| node1 | `192.168.20.101` | Worker |
| node2 | `192.168.20.102` | Worker |
| node3 | `192.168.20.103` | Worker (this chassis previously had another role; rebuilt into the fleet) |

## Edge

VyOS on a fourth ThinkCentre Tiny. Not a workload node. See [06-vyos-build.md](06-vyos-build.md).

## Other on-site deployments

| Class | Where | Notes |
|-------|--------|--------|
| Lab display | Lab LAN | Consumer display; not managed as a server |
| Household Linux seats | Home tailnet | Laptops / extra PCs enrolled as clients |
| Operator mobiles | Both tailnets at different times | Phone and tablet |
| Field Android | Home tailnet | Stale enrollment (practice in leaving inventory visible) |
| IoT / guest | Home SSIDs | Not listed by hostname |

## Software on managed Linux (snapshot)

| Host | Extra services beyond SSH / Tailscale / base OS |
|------|--------------------------------------------------|
| um690 | Desktop stack, Ollama on localhost |
| node1–3 | none observed |
| vyos-router | Edge routing, DHCP, firewall |
