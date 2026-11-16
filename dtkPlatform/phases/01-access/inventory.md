# Access inventory — 2026-11-15

Observed from `um690`. No Tailscale addresses. VyOS was not changed.

| Host | LabNet | Name | OS | Root filesystem | Memory |
|------|--------|------|----|-----------------|--------|
| node1 | `192.168.20.101` | n1 | Proxmox VE, `pve-manager/9.2.26`, kernel `7.0.14-28-pve` | 68G, 21G used, 44G free | 15 GiB, 1.8 GiB used |
| node2 | `192.168.20.102` | n2 | same product line | 68G, 11G used, 54G free | 15 GiB, 1.8 GiB used |
| node3 | `192.168.20.103` | n3 | same product line | 68G, 11G used, 54G free | 15 GiB, 1.8 GiB used |

n1 storage: `local` (dir, active, about 30% used) and `local-lvm` (lvm-thin, active, empty, about 141 GiB). Cluster `dtk-cloud` was quorate with 3 nodes and 0 guests.

SSH: `ssh node1`, `ssh node2`, `ssh node3` as `root` on LabNet. `ssh node1-ts`, `ssh node2-ts`, and `ssh node3-ts` as `root` over MagicDNS `n1.tail13a119.ts.net` and the matching n2 and n3 names. Each node is `tag:ops`. MagicDNS is off on the nodes. Resolver there is `1.1.1.1`.

Ollama on `um690` listened on `127.0.0.1:11434` only and reported version `0.32.6`.
