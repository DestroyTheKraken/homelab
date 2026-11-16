# Phase 07 — Nextcloud file assistant

**Status:** not started  
**Hosts:** node1 (Nextcloud) and um690 (Open WebUI)

## Start

Phase 06’s restore drill passed. Open WebUI from phase 02 is up on the tailnet. Ollama is still localhost-only on um690.

## Work

1. Point Nextcloud Assistant at Open WebUI’s OpenAI-compatible API.
2. Store the API key on node1, not in git and not in a Modelfile.
3. The assistant may summarize, draft, and create files in the logged-in user’s Nextcloud.
4. Do not give it an SSH key, `occ` upgrade rights, or any route to VyOS or the firewall.

## Exit

- [ ] Logged in as `member`, a prompt creates a note in her files
- [ ] The same prompt cannot read `/etc` on node1
- [ ] `joshua` does not see her new note unless it was placed in a share

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/08-minecraft
```
