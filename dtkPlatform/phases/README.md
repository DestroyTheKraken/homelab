# Phase sessions

Each directory is one session. Finish it before opening the next.

**Start here:** [`02-open-webui`](./02-open-webui). Phase 01 access is complete.

## How a session starts

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/02-open-webui
```

Then tell Grok: review the last completed phase, and if it is complete, begin this phase.

Grok reads the previous phase README, checks the exit items against the machines, and only then does the work in the current README.

## How a session ends

Grok states that the phase is complete and gives the next `cd` command. Do not start the next phase in the same session.

## Order

| Dir | Phase | Host | Exit in one line |
|-----|--------|------|------------------|
| [00-planning](./00-planning) | Planning | docs | This plan and the platform docs agree |
| [01-access](./01-access) | Reach the nodes | LabNet | SSH and MagicDNS work |
| [02-open-webui](./02-open-webui) | Local AI on the tailnet | um690 | Chat and Whisper work; Ollama stays on localhost |
| [03-kodi](./03-kodi) | Kodi movie database | um690 | Kodi plays a file from `/srv/nas_a/kodi/Movies` |
| [04-steam](./04-steam) | Steam Big Picture | um690 | Big Picture launches with the large model unloaded |
| [05-nextcloud](./05-nextcloud) | Files | node1 | `joshua` and `member` each have 50 GB and cannot see each other’s files |
| [06-backups](./06-backups) | Backup tiers | node1 + NAS | One restored file matches |
| [07-assistant](./07-assistant) | File assistant | node1 → um690 | A note lands in `member`’s files |
| [08-minecraft](./08-minecraft) | Paper network | node2 | Two tailnet clients join the lobby; only two Paper servers run |
| [09-games](./09-games) | Other games and ROMs | node3 + NAS | Decks, Bashcrawl, and one ROM work |
| [10-dashboard](./10-dashboard) | Service board | node1 | One page opens every live service |
| [11-mvp](./11-mvp) | Acceptance | all | MVP checklist is true |

Phase 01 is complete. Current cluster state is in [00-planning](./00-planning) and [`../../docs/05-inventory-observed-2026-11-15.md`](../../docs/05-inventory-observed-2026-11-15.md).
