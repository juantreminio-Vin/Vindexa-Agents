# Vindexa-Agents

A small team of AI agents that helps Vindexa test, investigate and explain the product, with knowledge kept in version-controlled files instead of in people's heads.

**Owner (v1):** Juan Treminio. Every change goes through a pull request that he reviews. To hand a domain over, add its owner to `.github/CODEOWNERS`.

## What is in here

| Path | What it is | Changes |
|---|---|---|
| `CLAUDE.md` | The lead agent's protocol. Short on purpose. | Rarely |
| `rules/` | Shared rules every agent follows (approvals, verdicts, live-first, writing). | Rarely |
| `domains/<name>/` | One folder per product domain: `agent.md`, `flows/`, `memory.md`. | Often |
| `.claude/agents/` | One specialist subagent per domain. | Rarely |
| `.claude/skills/` | Repeatable procedures (bug triage, UI check, ticket draft, ...). | Sometimes |
| `benchmarks/` | How we score the product against consultant output. Method only. | Sometimes |
| `templates/project/` | Empty fact sheet, source manifest and findings log for a new project. | Rarely |
| `docs/` | Format specs (freshness stamps, memory entries). | Rarely |
| `local/` | Your own index of project folders. **Gitignored, never pushed.** | You |

## What is NOT in here

Project data, customer documents, Drive links to project evidence, passwords, consultant files. Those stay where they live (Drive, Linear). At the start of a task you say "Project: X" and point at its evidence folder, and the agent reads it live.

## Three kinds of knowledge, kept apart

- **Flows** (`domains/*/flows/`): how things work. Slow-changing intent.
- **Memory** (`domains/*/memory.md`): dated, sourced corrections the agents got wrong. A staging buffer, promoted into flows once stable.
- **Skills** (`.claude/skills/`): procedures.

One owner per fact. If two files describe the same behavior, one is wrong. Reference, never copy.

## Live first

The product changes constantly. A written flow is a starting point, never proof. Before any verdict or ticket, agents check merged code, open PRs and Linear for the area, and re-verify against the live UI when behavior matters. See `rules/live-first.md`.

## Start here

1. Open this repo in Claude Code.
2. Say what you want: a question, a finding to investigate, a ticket to draft.
3. Name the project if there is one, and give its evidence location.
4. Review the draft. Nothing outward-facing happens without your approval.
