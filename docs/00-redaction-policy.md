# Redaction policy

This repository is public. Inventory is written for hiring managers, not for an attacker recon dump.

## Always omit

- Passwords, tokens, API keys, Tailscale auth keys, SSH private keys
- WAN / public IP addresses
- Tailscale CGNAT (`100.64.0.0/10`) and Tailscale IPv6 addresses
- MAC addresses, serial numbers, machine-ids, disk serials
- Street address, phone numbers, family names
- Google account photo URLs and Tailscale numeric user IDs
- Guest / IoT hostnames that identify household members
- Exact Wi-Fi SSIDs and any PSK material

## Allowed

- RFC1918 lab and home prefixes, described by role (lab LAN vs home WLAN)
- Hostnames that are already operational names (`um690`, `node1`–`node3`, `vyos-router`)
- Hardware model names and CPU / RAM / disk class
- OS names and versions
- Service roles (SSH, Tailscale, edge routing)
- The two operator identities used for the dual-tailnet exercise:
  - Job / career: `joshua.hickman1@gmail.com`
  - Studio: `destroythekraken@gmail.com`

## Snapshot rule

Every inventory page is dated. If a fact was not observed on that date, it is marked **not enumerated** rather than guessed.

Raw `tailscale status --json` is never committed. Publish a redacted table instead.
