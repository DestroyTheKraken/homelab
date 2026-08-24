# Inventory snapshot — 2026-08-24

Sources: live inspection from `um690`, plus operator-provided `sudo tailscale status` for both profiles.

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

## Lab Tailscale (destroythekraken@)

`um690`, `node1`, `node2`, `node3`, `j-phn`, `j-tab` — all online.

## Home Tailscale (joshua.hickman1@)

Online: `um690`, `a-lap`, `pookie`.  
Offline: `hickles`, `a-phn`, `j-phn`, `j-tab`, `dtk-field`.

## How to refresh

```bash
tailscale status
sudo tailscale switch --list
# switch profile, print status, switch back
```

Sanitize with [00-redaction-policy.md](00-redaction-policy.md) before committing a new dated page. Never commit raw JSON.
