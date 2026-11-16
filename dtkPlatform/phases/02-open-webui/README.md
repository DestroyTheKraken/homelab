# Phase 02 — Open WebUI

**Status:** not started  
**Host:** um690

## Start

Phase 01 exit checks passed. Ollama is already installed and listening on `127.0.0.1:11434`. Models already present include `qwen3.6` and the `aide-*` names. Alpaca can stay as the local desktop chat app. It is not the tailnet door.

## Work

1. Add `open-webui-compose.yml` next to this README (copy a pointer from `dtkPlatform/Compose/` if one is written here).
2. Run Open WebUI as user `joshua`. Point it at `http://127.0.0.1:11434`.
3. Do not publish port 11434 on LabNet or the tailnet.
4. Turn authentication on. First account is Joshua. Signup is closed.
5. Publish the UI with Tailscale Serve on `um690` so the family URL is HTTPS on MagicDNS.
6. Turn on Open WebUI’s built-in Whisper. Do not add a second speech service.
7. Set Ollama’s loaded-model cap to 1 so a 22 GB model is not assumed resident beside a game. Keep-alive can stay for desktop chat. Phase 04 unloads the large model before Steam.

## Exit

- [ ] From another tailnet device, Joshua logs into Open WebUI and gets a reply from `qwen3.6`
- [ ] A short Whisper dictation returns text
- [ ] `ss` on um690 shows 11434 only on `127.0.0.1`

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/03-kodi
```
