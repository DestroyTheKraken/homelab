# Phase 08 — Minecraft network

**Status:** not started  
**Host:** node2 (`192.168.20.102`)

## Start

Phase 07 exit checks passed. node2 has SSH and Tailscale and no game server yet. Consoles outside the lab keep their own join path. Do not install a second Xbox broadcast login. Do not open VyOS. Do not publish a public port.

## Capacity

node2 is a ThinkCentre M93p: Intel Core i5-4570T, 2 cores / 4 threads, 15 GiB RAM, 238 GB SSD.

**Confident number: 2 Paper servers running at the same time.**

That pair is the lobby plus one minigame. A small proxy (Velocity) and Geyser/Floodgate sit beside them and are not extra worlds. Players should be in one world. The other minigame folders are installed and stopped. Three or four Paper processes at once are out of spec. A heavy Hangar minigame pack can make even the second world uncomfortable; if the lobby hitches while people are in the minigame, stop the lobby for that session.

## Worlds

| World | v1 state | Content |
|-------|----------|---------|
| Lobby | Running, creative | Spawn and signs that name the other worlds |
| Waterworld | Installed, stopped | All water, three small island villages, one large island village, a volcano in the middle. Building it is content work after join works. |
| Avatar | Installed, stopped | Last Airbender theme. Same rule. |
| MiniGame3 | No files | Needs a name first |

A start script stops the running minigame before it starts another, so the cap stays at two Paper processes (lobby + one).

## Work

1. Install a current Paper build for the Minecraft version chosen that day. Java clients use TCP 25565 on the tailnet only.
2. Install Geyser and Floodgate so Bedrock clients on the tailnet can join. Bedrock listen is UDP 19132 on node2, tailnet only.
3. Install Velocity as the lobby switcher if two worlds need a single address. If Velocity fights the 2-core CPU, skip it and use the start script plus signs that tell a human which port is up.
4. Extra plugins come from [Hangar](https://hangar.papermc.io/). Geyser’s own build page is the source if Hangar does not carry that build. Install the smallest set that switches worlds. Do not add a pile of minigame plugins in this phase.
5. Whitelist on. Ops SSH stays ops-only. Tailscale grant: family can reach TCP 25565 and UDP 19132 on node2.
6. Two tailnet clients join the lobby and see each other. One client may be Bedrock through Geyser.
7. Leave consoles outside the lab alone. They are not given an IP, a DNS change, or a port.

## Exit

- [ ] Two tailnet clients are in the lobby together
- [ ] `ss` or the process list shows at most two Paper servers
- [ ] Waterworld and Avatar are absent or stopped, not running beside the lobby
- [ ] Consoles outside the lab were not restarted and their join config was not edited
- [ ] VyOS was not edited

## Handoff

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/09-games
```
