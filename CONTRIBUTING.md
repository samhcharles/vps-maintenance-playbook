# Contributing to the VPS Maintenance Playbook

This notebook exists to capture real operational knowledge so it survives beyond any single session. If you ran a maintenance task and the docs didn't match reality, fix them.

---

## What belongs here

- **Runbook corrections** — a step that's wrong, a command that's changed, or a missing step that caused problems
- **New runbooks** — a task you had to figure out manually that will come up again
- **State updates** — `control-plane/CURRENT_STATE.md` and `control-plane/TOPOLOGY.md` should always reflect what's actually running
- **Audit snapshots** — after an inspection pass, add a new file in `control-plane/AUDITS/`
- **Handoffs** — if you're handing a session to another agent or operator, write a `control-plane/HANDOFFS/YYYY-MM-DD.md`

**Do not** add application code, secrets, credentials, or bot feature work here. That belongs in [madebymadhouse/chopsticks-lean](https://github.com/madebymadhouse/chopsticks-lean).

---

## How to contribute

1. Fork the repo
2. Branch: `docs/runbook-name` or `fix/short-description`
3. Make your change — keep it scoped to one runbook or one state update
4. Open a PR using the PR template
5. The Librarian runs a unification pass on any changes to standards or patterns

Default workflow for Mad House repos:

https://github.com/madebymadhouse/bot-dev-playbook/blob/main/AGENTIC_GIT_WORKFLOW.md

---

## Commit format

All commits must follow [Conventional Commits](https://www.conventionalcommits.org/):

```
docs(runbooks): add redis flush runbook
fix(topology): update postgres version to 16
chore(state): update current state after April 20 maintenance
```

---

## What gets rejected

- Changes to audit snapshots in `control-plane/AUDITS/` — those are historical records, not living docs
- Application code or bot-specific config
- Speculative runbooks for tasks that haven't actually been run on this server
- PRs without a description of what changed and why
