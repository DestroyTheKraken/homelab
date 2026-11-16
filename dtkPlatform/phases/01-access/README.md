# Phase 01 — Reach the nodes

**Status:** complete (2026-11-15)  
**Host:** um690, talking to LabNet and the DTK tailnet

## Start

Phase 00 is complete. This phase does not install services. VyOS is not edited. The tailnet is `destroythekraken@` / `tail13a119.ts.net`.

The workers are Proxmox nodes `n1`, `n2`, and `n3` in cluster `dtk-cloud`, not Ubuntu hosts. Login is `root`, not `kraken`.

## Observed

1. `um690`, `n1`, `n2`, and `n3` are on `tail13a119.ts.net`. The nodes are `tag:ops`.
2. LabNet SSH and MagicDNS SSH work. Facts are in [`inventory.md`](./inventory.md).
3. Ollama on um690 listens only on `127.0.0.1:11434`.
4. VyOS was not changed. No WAN ports were added.
5. Guest count on the cluster was 0. There is no Docker install to clean up in this phase.

## Exit

- [x] SSH to node1, node2, and node3 works from um690
- [x] `inventory.md` in this directory lists OS, disk free, and memory for each worker
- [x] Ollama is still localhost-only
- [x] VyOS config was not changed

## Handoff

When those boxes are checked, say phase 01 is complete and tell Joshua to run:

```bash
cd ~/Projects/HOME_LAB/dtkPlatform/phases/02-open-webui
```
