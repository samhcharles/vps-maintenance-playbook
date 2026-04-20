# Current State

Last updated: 2026-04-20

## Purpose

This repo exists so VPS maintenance does not depend on chat memory.

## Verified Facts

- The VPS is the live runtime
- The main live workload is a Discord bot stack deployed with Docker Compose
- Stack path: `/home/samhcharles/srv/bots/chopsticks-lean`
- Control script: `scripts/ops/chopsticksctl.sh` — one entrypoint for all stack operations
- Audit snapshots exist in `AUDITS/` and should be treated as the baseline verified inventory
- A read-only audit script exists at `scripts/capture-vps-audit.sh`
- Fresh operators should start with the docs in this folder before touching the server

## Container State (last verified 2026-04-20)

| Container | Status | Notes |
|---|---|---|
| `chopsticks-lean-bot` | healthy | Up, healthz on `0.0.0.0:9100` |
| `chopsticks-lean-postgres` | healthy | Internal port 5432 only |
| `chopsticks-lean-redis` | healthy | Internal port 6379 only |

Health endpoint: `curl http://127.0.0.1:9100/healthz` returns `{"ok":true}` when bot is running.

## Bug Fixed in This Session

`chopsticksctl.sh` `bot_exec()` and `health_check()` were hardcoded to `chopsticks-bot` (wrong container name) and `8080/health` (wrong endpoint). Fixed:
- `bot_exec()` now uses `docker compose exec bot`
- `health_check()` now uses `curl http://127.0.0.1:9100/healthz` (matching docker-compose healthcheck)
- Fix committed to `samhcharles/chopsticks-lean`

## What Is Working

- The repo now has a clear first-read path for a fresh AI or human
- Topology and runtime inventory have been documented from real audit passes
- The maintenance workflow distinguishes inspection from code changes
- All four main runbooks are verified against real scripts
- `chopsticksctl.sh doctor` passes cleanly

## What Still Needs Work

- Reverse proxy and scheduled maintenance are still only partially verified
- Some reserved directories and ownership boundaries are still undocumented

## Current Operating Direction

- Use this repo as the first stop for VPS maintenance work
- Audit first when the live state is uncertain
- Write down anything the next operator would otherwise have to rediscover
- Keep repo-specific code changes in the relevant application repo, not here
