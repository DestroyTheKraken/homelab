# 04-steam — Steam Big Picture

This directory is one session of the DTK Platform build on um690. Host for this phase: um690.

When Joshua says **Begin this phase**, do the following and nothing else first.

## Read

1. `../../AGENTS.md`
2. `../../PLAN.md`
3. `../../checklist.md`
4. `../../Progress/CURRENT.md`
5. `README.md` in this directory
6. `../03-kodi/README.md`

## Say where the work stands

In a short brief, state:

- This phase's status line from `README.md`
- Which exit checks are already true, and which are open
- What the previous phase handed off, if there was one
- Any blocker in `Progress/CURRENT.md` that changes this phase

Do not invent a machine fact. If a check needs a command on a host, say so and wait. Joshua runs commands on the machines.

## If this phase is already complete

Do not redo it. Give Joshua this command and stop:

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/05-nextcloud
grok
```

The next phrase is again: Begin this phase

## If this phase is open

Continue from the first unchecked item in this README. One step, then wait.

Split that step:

- **Joshua runs** the command or the click on the host.
- **Grok writes** only files in this tree: compose, notes, and a checklist tick after the exit line is true.

Do not start the next phase in this session. Do not install k3s, edit VyOS, reinstall node1–node3, or bring back the old media server. Do not build the AIDE lesson UI here. The platform rules in `../../AGENTS.md` still apply.
