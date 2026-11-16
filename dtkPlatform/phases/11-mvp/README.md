# Phase 11 — MVP acceptance

**Status:** not started  
**Hosts:** the whole platform

## Start

Phase 10’s page is up. This phase installs nothing new unless a check fails and the fix is inside a service that was already in scope. A failure goes back to that phase’s directory, gets fixed, and this checklist is run again.

## End state

The platform is ready for preference screens and for Joshua to upload files. Bulk DVD ripping is not this phase. He starts a rip later by inserting a disc and giving its name (phase 03 procedure).

## Checklist

- [ ] Open WebUI: login, one reply from the local model, one Whisper dictation
- [ ] Ollama still bound to `127.0.0.1:11434` only
- [ ] Kodi on um690 plays a file from `/srv/nas_a/kodi/Movies`
- [ ] A second tailnet Kodi sees that same library entry
- [ ] Steam Big Picture opens with `qwen3.6` unloaded
- [ ] Nextcloud: `joshua` (admin, 50 GB) and `member` (standard, 50 GB) cannot read each other’s files
- [ ] No symlink farm under the Nextcloud data directory
- [ ] Weekly archive in node1 `~/Backups`, monthly copy on `/srv/nas_a/backups/nextcloud`, restore of one file matched
- [ ] Quarterly script exists. Destination is either the named host or still marked unset
- [ ] `member` can create a note through the assistant, and the assistant has no SSH key
- [ ] Two tailnet clients join the Paper lobby. At most two Paper servers are running
- [ ] Consoles outside the lab were not changed. VyOS was not changed
- [ ] Massive Decks accepts two browsers
- [ ] Bashcrawl user lands in `/home/bashcrawl` and `cd` returns to the entrance
- [ ] One Batocera ROM plays in RetroAssembly
- [ ] Dashboard tiles match the services that are actually up
- [ ] The historical media server is not running and is not in the current platform docs

Write `acceptance.md` in this directory with the date and a pass or fail on each line.

## Handoff

When every required line passes, say the MVP is up. There is no phase 12. Later work is preference configuration, DVD rips when he prompts, MiniGame3 when it has a name, and the quarterly host if it is still unset.
