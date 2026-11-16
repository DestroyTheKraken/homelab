# Inventory snapshot — 2026-11-09

**Superseded** for the workers by [05-inventory-observed-2026-11-15.md](05-inventory-observed-2026-11-15.md). On 2026-11-15 the Proxmox web UI was up on node1–node3. This page is the last Ubuntu read.

Sources: ping and SSH from `um690` on LabNet, plus `tailscale status` while logged into DestroyTheKraken. Personal endpoints and HickmaNet are omitted on purpose. See [00-redaction-policy.md](00-redaction-policy.md).

On this date Proxmox was not installed. That is no longer true.

A media server from an earlier project was still on node1 on this date. That project is historical and invalid for the DTK Private Platform. It is not a service to keep.

## Lab LAN `192.168.20.0/24`

Sweep of the /24 on this date answered only these addresses.

| Address | Hostname | Function | OS observed |
|---------|----------|----------|-------------|
| .1 | vyos-router | Edge router, LabNet gateway | VyOS `2026.06.24-0045-rolling` |
| .100 | um690 | Control seat | Ubuntu 26.04.1 LTS, kernel `7.0.0-38-generic` |
| .101 | node1 | Worker, current service host | Ubuntu 26.04.1 LTS |
| .102 | node2 | Worker | Ubuntu 26.04.1 LTS |
| .103 | node3 | Worker | Ubuntu 26.04.1 LTS |

The former display address `.109` did not answer. It is not a managed node.

## M93p firmware

`node1`, `node2`, `node3`, and `vyos-router` are ThinkCentre M93p Tiny, type 10AB0016US. Each reported BIOS `FBKTE0AUS`, date 2021-12-23, release 1.224. That is the latest public Lenovo package found for this model. `um690` is a Minisforum UM690 on AMI `1.16` (2023-02-15) and is not part of the M93p firmware set.

## DTK tailnet

Lab hosts only. Detail in [04-tailscale.md](04-tailscale.md).

| Hostname | Status |
|----------|--------|
| um690 | reachable, user `destroythekraken@` |
| node1 | reachable, tagged device |
| node2 | reachable, tagged device |
| node3 | reachable, tagged device |

## Services worth knowing before a reinstall

These are Ubuntu facts, observed 2026-11-07 and still the layout the Proxmox prep replaces. They are not the target platform.

| Host | Observed |
|------|----------|
| node1 | Docker 29.8.0. `docker ps` as `kraken` reported 0 containers, while Portainer and a historical media-server process were still running under containerd. Host listened on 9443, 25567, and 19132. The historical media server listened on 8096 inside its container namespace only. From `um690` and from `vyos-router`, TCP 8096, 9443, 25567, and 19132 did not accept. `minecraft-proxy.service` active. `minecraft-lobby.service` inactive. |
| node2, node3 | SSH and Tailscale. No Docker, no k3s. |
| um690 | SSH, Tailscale, Ollama on localhost, NFS export of `/srv/nas_a/mediahub/media` (~100 GB on a 1.9 TB USB disk). LabNet and the other premises prefix are read-only clients in the export. Multipass is installed with no VMs. |
| vyos-router | SSH open on the LabNet address. DHCP pool `LABNET` had 2 leases of 101. |

No k3s, Ceph, or Proxmox process was observed on these hosts.

## How to refresh

```bash
tailscale status
# stay on DestroyTheKraken; do not switch to a personal tailnet for this repo
```

Sanitize with [00-redaction-policy.md](00-redaction-policy.md). Never commit raw JSON, Tailscale IPs, or direct endpoints.
