# Inventory snapshot — 2026-08-29

**Superseded** by [05-inventory-observed-2026-11-09.md](05-inventory-observed-2026-11-09.md). Personal endpoints were removed from this page on 2026-11-09 so they are not read as current DTK inventory.

Sources: operator-provided lab `sudo tailscale status` from `um690` (2026-08-29 ~19:27). LAN rows unchanged from the 2026-08-24 premises inspection unless noted.

## Lab LAN `192.168.20.0/24`

| Address | Hostname | Function |
|---------|----------|----------|
| .1 | vyos-router | Lab-side gateway (same appliance as home gateway) |
| .100 | um690 | Control seat |
| .101 | node1 | Ubuntu fleet |
| .102 | node2 | Ubuntu fleet |
| .103 | node3 | Ubuntu fleet |
| .109 | (display) | Consumer display; not a managed node |

## Lab Tailscale (`destroythekraken@`) — lab hosts observed 2026-08-29

Tailscale addresses and direct endpoints omitted. Non-lab devices from that capture are not kept in this repo.

| Hostname (published) | OS | Status |
|----------------------|-----|--------|
| um690 | linux | idle / reachable |
| node1 | linux | idle / reachable |
| node2 | linux | idle / reachable |
| node3 | linux | idle / reachable |

## How to refresh

```bash
tailscale status
# Stay on DestroyTheKraken. Do not record a personal tailnet in this repo.
```

Sanitize with [00-redaction-policy.md](00-redaction-policy.md) before committing a new dated page. Never commit raw JSON, Tailscale IPs, or direct endpoints.
