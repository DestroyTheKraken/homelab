# Inventory snapshot — 2026-08-29

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

## Home LAN `192.168.10.0/24`

| Address | Published name | Function |
|---------|----------------|----------|
| .1 | vyos-router | Home-side gateway |
| .100 / .108 | Deco APs | TP-Link Deco X20 mesh (AP mode) |
| .150 | um690 | Control seat Wi-Fi NIC |
| others | omitted | Household, guest, and IoT clients |

## Lab Tailscale (`destroythekraken@`) — observed 2026-08-29

Six devices only. Tailscale addresses and direct endpoints omitted.

| Hostname (published) | OS | Status |
|----------------------|-----|--------|
| um690 | linux | idle / reachable |
| node1 | linux | idle / reachable |
| node2 | linux | idle / reachable |
| node3 | linux | idle / reachable |
| operator-phone | android | active |
| operator-tablet | android | offline (~4 days) |

## Home Tailscale (`joshua.hickman1@`)

Not re-scanned on 2026-08-29. See [05-inventory-observed-2026-08-24.md](05-inventory-observed-2026-08-24.md) for the prior home snapshot.

## How to refresh

```bash
sudo tailscale status
sudo tailscale switch --list
# switch profile, print status, switch back
```

Sanitize with [00-redaction-policy.md](00-redaction-policy.md) before committing a new dated page. Never commit raw JSON, Tailscale IPs, or direct endpoints.
