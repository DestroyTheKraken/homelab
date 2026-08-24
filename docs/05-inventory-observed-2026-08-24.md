# Inventory snapshot — 2026-08-24

Source: live inspection from `um690` (lab LAN + home WLAN + studio Tailscale). Career tailnet not fully listed (see [04-tailscale.md](04-tailscale.md)).

## Layer 3 — lab LAN `192.168.20.0/24`

| Address | Hostname | Function |
|---------|----------|----------|
| .1 | vyos-router | Lab-side gateway (same appliance as home gateway) |
| .100 | um690 | Control seat |
| .101 | node1 | Ubuntu fleet node |
| .102 | node2 | Ubuntu fleet node |
| .103 | node3 | Ubuntu fleet node |
| .109 | (unnamed) | Consumer device on lab LAN; not a managed node |

ICMP sweep also used to confirm liveness. Other addresses did not answer.

## Layer 3 — home WLAN `192.168.10.0/24`

| Address | Published name | Function |
|---------|----------------|----------|
| .1 | vyos-router | Home-side gateway |
| .100 / .108 | mesh APs | Vendor mesh management / AP interfaces |
| .150 | um690 | Control seat (Wi-Fi NIC) |
| others | omitted | Operator and IoT clients (randomized MACs, smart-home, displays) |

Household hostnames and MACs are omitted on purpose.

## Studio Tailscale

Six devices, all online. See [04-tailscale.md](04-tailscale.md).

## Career Tailscale

Not enumerated from this seat. Edge Tailscale interface exists and is not in the studio peer list.

## Software on managed Linux (snapshot)

| Host | OS | Extra running services beyond SSH / Tailscale / base OS |
|------|-----|--------------------------------------------------------|
| um690 | Ubuntu 26.04 | Desktop stack, Ollama (localhost), xrdp, KDE Connect |
| node1–3 | Ubuntu 26.04 | none observed |
| vyos-router | VyOS 2026.06 rolling | edge routing |

## How to refresh (operator)

On a machine with Tailscale operator rights:

```bash
# redacted table only — do not commit JSON
tailscale status
sudo tailscale switch --list
# switch, print status, switch back
```

Sanitize with [00-redaction-policy.md](00-redaction-policy.md) before committing a new dated inventory page.
