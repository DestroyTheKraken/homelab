# Guide — Tailscale ACL grants (Phase 0)

**Lane:** Platform (GUI)  
**Official docs:** [Policy file syntax](https://tailscale.com/docs/reference/syntax/policy-file) · [Grants](https://tailscale.com/docs/features/access-control/grants)

## Goal

Ops (`group:ops`) may reach every device. Family (`group:family`) may reach only future service tags: `tag:media` TCP 8096, and `tag:cloud` TCP 80 and 443. Family is not granted SSH (22), the Proxmox UI (8006), `tag:play`, or `tag:monitor`. There is no open member-to-everything grant. Accepted 2026-11-15.

## Click-path

1. Browser → [Tailscale admin](https://login.tailscale.com/admin) → sign in as `destroythekraken@…`.
2. Confirm MagicDNS domain is **`tail13a119.ts.net`** (DestroyTheKraken). This guide does not cover any other tailnet.
3. **Access controls** → open the policy editor.
4. Paste the policy from the operator session. Do not commit the live file: it names a family login, and this repo does not store that address.
5. **Save**. Fix any syntax errors the UI reports.
6. n1–n3 are already `tag:ops`. Do not add `tag:media` or `tag:cloud` to the hypervisors. Those tags are for guests, later.
7. From `um690`, `ssh node1` and `ssh node1-ts` should both log in as `root`.

## Optional YouTube query

`Tailscale ACL grants tags tutorial` — watch **one** recent overview; prefer official docs for JSON details.

## Stop conditions

- Wrong tailnet selected → abort and switch account.
- Save fails → do not half-apply; fix JSON first.
- You feel tempted to add Google sync or GitOps Actions → stop (out of scope).

## Rollback

Restore previous policy from Access controls version history / your last known-good paste in this session note.

## LFCS explain-later (max 3)

```bash
tailscale status
tailscale status --json | less
# From um690: ssh node1 && ssh node1-ts
```
