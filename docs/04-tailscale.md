# Tailscale practice

Tailscale is how this lab practices **identity, client inventory, and remote access** — not a substitute for the LAN.

Two Google-backed tailnets are intentional:

| Tailnet identity | Role in the exercise |
|------------------|----------------------|
| `joshua.hickman1@gmail.com` | Career / job-search identity. Separate user and device set. |
| `destroythekraken@gmail.com` | Studio identity. Lab compute and operator mobile clients. |

That split is the portfolio point: users and clients are administered as two tenancies, the way an MSP keeps customer environments apart.

## Studio tailnet (live dump, redacted)

**Owner login:** destroythekraken@gmail.com  
**MagicDNS suffix:** `tail13a119.ts.net`  
**Snapshot:** 2026-08-24 from `um690`  
**Addresses:** omitted (CGNAT / IPv6)

| Hostname | OS | Role | Online |
|----------|-----|------|--------|
| um690 | linux | Control seat | yes |
| node1 | linux | Cluster node | yes |
| node2 | linux | Cluster node | yes |
| node3 | linux | Cluster node | yes |
| j-phn | android | Operator phone | yes |
| j-tab | android | Operator tablet | yes |

All six devices were owned by the single studio user. No ACL tags and no advertised subnet routes were set at snapshot. MagicDNS is on. SSH to the Linux nodes is also possible via `*.tail13a119.ts.net` (see local `~/.ssh/config` host aliases `um690-ts`, `node1-ts`, …).

## Career tailnet (partial)

`um690` is logged into the **studio** profile. Listing the other profile requires `sudo tailscale switch` and this seat does not have passwordless operator rights.

Observed evidence that a second tailnet is in use:

- The VyOS edge has a Tailscale interface.
- That interface is **not** one of the six studio-tailnet peers above.

A redacted career-tailnet table belongs in [05-inventory](05-inventory-observed-2026-08-24.md) once a switchable dump is available. Template: [examples/tailscale-status.example.md](examples/tailscale-status.example.md).

## What this demonstrates

1. Enroll Linux servers and Android clients under a named user
2. Keep a second identity’s devices off the first tailnet
3. Reach the lab without inbound WAN port-forwards
4. Document the inventory so another operator could reconstruct who owns what
