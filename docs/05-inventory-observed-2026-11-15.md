# Inventory snapshot — 2026-11-15

Sources: Proxmox web UI on port 8006, then `ssh` from `um690` as `root` (`pvecm status`, `pveversion`, `qm list`, `pct list`). Re-checked from the shell at 21:48 local time. Personal endpoints are omitted. See [00-redaction-policy.md](00-redaction-policy.md).

## Lab LAN `192.168.20.0/24`

| Address | Lab name | Proxmox name | Role |
|---------|----------|--------------|------|
| .1 | vyos-router | — | Edge router. Not a cluster node. |
| .100 | um690 | — | Control seat. Ubuntu. Not a cluster node. |
| .101 | node1 | n1 | Proxmox node, vote 1 |
| .102 | node2 | n2 | Proxmox node, vote 1 |
| .103 | node3 | n3 | Proxmox node, vote 1 |

## Cluster `dtk-cloud`

One Proxmox datacenter. Shell and the web UI agree.

| Fact | Observed |
|------|----------|
| Product | Proxmox VE 9.2, `pve-manager/9.2.26` |
| Kernel on n1 | `7.0.14-28-pve` |
| Cluster name | `dtk-cloud` |
| Transport | corosync knet, secure authentication on |
| Nodes | 3 online, 0 offline |
| Quorum | Yes. Expected votes 3. Quorum is 2. |
| Guests | 0 virtual machines, 0 LXC containers |
| Web UI | Port 8006 on each node address. UI was opened on `.101`. |

Each node shows `local` and `local-lvm` storage in the UI. The UI resource totals at 20:39 were about 1% of 12 CPUs, 5.26 GiB of 46.52 GiB RAM, and 41.14 GiB of 626.86 GiB storage. Prometheus, Alertmanager, and Grafana were not serving on the node addresses earlier the same day and were not re-checked after the cluster joined.

## SSH

LabNet SSH works: `ssh node1`, `ssh node2`, and `ssh node3` from `um690` log in as `root` with the seat key.

Later the same day, Tailscale 1.104.7 was installed on n1, n2, and n3 and each was enrolled as `tag:ops`. MagicDNS is disabled on the nodes (`--accept-dns=false`); their resolver stays `1.1.1.1`. `um690` reaches them over the tailnet as `n1.tail13a119.ts.net`, `n2.tail13a119.ts.net`, and `n3.tail13a119.ts.net`. The cluster stayed quorate after enrollment.

## Prior snapshot

[05-inventory-observed-2026-11-09.md](05-inventory-observed-2026-11-09.md) describes the Ubuntu install. It is historical.
