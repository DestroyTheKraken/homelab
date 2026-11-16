# Phase 04 — Steam Big Picture

**Status:** not started  
**Host:** um690 desktop session

## Start

Phase 03 exit checks passed. Steam is not installed. The session is GNOME on Wayland. This phase does not add a second autologin gamescope seat.

The Radeon 680M can run light and medium games. It is not a discrete GPU. `qwen3.6` is about 22 GB and will hitch the game if it stays loaded.

## Work

1. Install Steam from Ubuntu’s current docs or Valve’s apt repository. Pick the one Ubuntu documents for 26.04 on that day.
2. Add a launcher that unloads Ollama models (`ollama ps`, then unload or `ollama stop` the large model) and then starts Big Picture.
3. Launch Big Picture from the UM690 keyboard and open the library. A game launch is the exit if an account with a game is available. If the library is empty, Big Picture itself reaching the library screen is enough, and say so.
4. Leaving Steam does not have to reload the model.

## Exit

- [ ] Big Picture is on screen from the local keyboard
- [ ] `ollama ps` does not show `qwen3.6` while Big Picture is open

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/05-nextcloud
```
