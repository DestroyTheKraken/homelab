# Guide — Tailscale ACL grants (Phase 0)

**Lane:** Platform (GUI)  
**Official docs:** [Policy file syntax](https://tailscale.com/docs/reference/syntax/policy-file) · [Grants](https://tailscale.com/docs/features/access-control/grants)

## Goal

Replace open “everyone can talk” defaults with grants: family → Jellyfin only; ops → servers; Portainer ops-only.

## Click-path

1. Browser → [Tailscale admin](https://login.tailscale.com/admin) → sign in as `destroythekraken@…`.
2. Confirm MagicDNS domain is **`tail13a119.ts.net`** (lab). Do not edit HickmaNet here.
3. **Access controls** → open the policy editor.
4. Paste the grants draft from `PLAN.md` §6.1 (start with `group:ops` = you only; leave `group:family` empty or commented until invites exist).
5. **Save**. Fix any syntax errors the UI reports.
6. **Machines** → for `node1`, set tag `tag:media` (re-authenticate with tags if the UI requires it). Repeat later for `tag:cloud` / `tag:play` / `tag:ops` as those hosts get roles.
7. From a second device (or after a family invite): confirm you can still reach your own devices; SSH to node1 only works for ops.

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
# From um690: ssh kraken@node1   # should work for ops only after tags/SSH rules
```
