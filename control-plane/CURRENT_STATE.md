# Current State

Last updated: 2026-04-19

## Objective

Create a stable control plane for development and VPS maintenance so agentic work stops depending on fragile chat context.

## Verified Facts

- The environment is split across Windows (control), WSL (staging), and VPS (runtime)
- OpenClaw agent framework is integrated for coder orchestration
- Discord bot workspace has intentional VPS-friendly deployment
- OpenClaw coder workflow is strict, contract-driven, and expects explicit plans and memory files
- A workspace-level custom agent is configured for maintenance planning

## Active Problems

- Workflow knowledge is scattered across repos, chat history, and machine-specific context
- Agent behavior is inconsistent because the first-read context is not centralized
- Planning, implementation, and runtime maintenance are too easy to blend together
- Cross-machine responsibilities are not yet codified in one place

## Immediate Direction

- Use this `control-plane` folder as the first landing zone for future agent work
- Use the `VPS Maintenance Planner` agent for topology, workflow, and maintenance planning tasks
- Require any implementation-heavy agent to receive a written handoff contract
- Use audit snapshots in `AUDITS/` as baseline verified inventory
- Run `scripts/capture-vps-audit.sh` to create fresh audits when topology needs verification

## Near-Term Milestones

1. Decide whether reserved empty paths should stay or be cleaned up
2. Start using `scripts/capture-vps-audit.sh` for repeatable read-only inventory snapshots
3. Write additional runbooks for deploy or backup recovery
4. Review and refine machine boundaries after one week of real use

## Open Questions

- Where should the long-term versioned home for this control plane live if it grows beyond the workspace root?
- Which tasks should always happen in WSL before touching the VPS?
- Which changes should require explicit approval before an agent executes them?
