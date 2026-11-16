# Inventory snapshot — 2026-08-24

**Superseded** by [05-inventory-observed-2026-11-09.md](05-inventory-observed-2026-11-09.md). Personal and HickmaNet rows were removed from this page on 2026-11-09.

Sources: live inspection from `um690` on that date.

## Lab LAN `192.168.20.0/24`

| Address | Hostname | Function |
|---------|----------|----------|
| .1 | vyos-router | Lab-side gateway (same appliance as home gateway) |
| .100 | um690 | Control seat |
| .101 | node1 | Ubuntu fleet |
| .102 | node2 | Ubuntu fleet |
| .103 | node3 | Ubuntu fleet |
| .109 | (display) | Consumer display; not a managed node |

## Lab Tailscale (destroythekraken@)

Lab hosts on that date: `um690`, `node1`, `node2`, `node3`. Later status is in [05-inventory-observed-2026-08-29.md](05-inventory-observed-2026-08-29.md).

## How to refresh

```bash
tailscale status
# Stay on DestroyTheKraken. Do not record a personal tailnet in this repo.
```

Sanitize with [00-redaction-policy.md](00-redaction-policy.md) before committing a new dated page. Never commit raw JSON.
