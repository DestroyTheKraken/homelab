# Tailscale practice

Tailscale is how this lab practices **identity, client inventory, and remote access**. It is not a substitute for the LAN, and it is not a WAN port-forward.

Two Google-backed tailnets, on purpose:

| Name I use | Login | Attached to |
|------------|-------|-------------|
| Destroy the Kraken (lab) | destroythekraken@gmail.com | Lab LAN / cluster |
| HickmaNet (home) | joshua.hickman1@gmail.com | Home LAN / household clients |

Same operator, two tenancies. That is the skill: enroll, name, and review clients the way a shop keeps customer environments apart.

Addresses, relays, and numeric user IDs are omitted.

## Lab tailnet — 2026-08-24

Captured on `um690` (`sudo tailscale status`). All six were online.

| Hostname | OS | Role |
|----------|-----|------|
| um690 | linux | Control seat |
| node1 | linux | Lab fleet |
| node2 | linux | Lab fleet |
| node3 | linux | Lab fleet |
| j-phn | android | Operator phone |
| j-tab | android | Operator tablet |

No ACL tags and no advertised subnet routes at snapshot. SSH to the Linux nodes also works via MagicDNS host aliases.

## Home tailnet — 2026-08-24

Captured on `um690` after switching profiles. IPs omitted.

| Hostname | OS | Role | Status |
|----------|-----|------|--------|
| um690 | linux | Control seat (also on lab tailnet) | online |
| a-lap | linux | Household laptop | online |
| pookie | linux | Household Linux seat | online |
| hickles | linux | Household Linux seat | offline (~3 days) |
| a-phn | android | Household phone | offline (~16 hours) |
| j-phn | android | Operator phone (home enrollment) | offline (~10 days) |
| j-tab | android | Operator tablet (home enrollment) | offline (~8 days) |
| dtk-field | android | Field client | offline (~50 days) |

`um690` appears on **both** tailnets. That is intentional: the control seat is the operator workstation for each identity. The stale field client is left on the list so inventory review stays honest.

## What this demonstrates

1. Enroll Linux servers and Android clients under a named user
2. Keep home devices off the lab tailnet and lab nodes off the home tailnet (except the dual-homed control seat)
3. Reach the lab without inbound WAN ports under Starlink CGNAT
4. Read a status table and know who owns what, including offline clients
