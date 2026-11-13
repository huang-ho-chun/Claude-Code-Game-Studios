# Codex Game Studio Instructions

This repository is a game-development studio harness. `project.yaml` is the
primary configuration source. The existing `.claude/` directory remains the
canonical store for framework scripts, templates, role definitions, and the
full skill implementations; `.agents/skills/` exposes those workflows to Codex.

## Start here

- For a game request or playable prototype, use `$prototype`.
- For first-time orientation, use `$start`.
- For the next recommended workflow step, use `$next-step`.
- Before using an engine API, read the matching pinned reference under
  `docs/engine-reference/<engine>/`.
- Read `production/session-state/active.md` after compaction, recovery, or when
  resuming an interrupted studio workflow.

## Repository map

- `project.yaml`: engine, specialists, modes, platform, and performance config.
- `design/`: briefs, GDDs, UX specifications, and design registries.
- `docs/`: architecture records, workflow guides, and engine references.
- `src/`: game source after an engine is configured.
- `production/`: plans, stories, evidence, and session state.
- `.claude/skills/`: canonical workflow instructions and references.
- `.claude/agents/`: canonical studio-role prompts used as delegation context.
- `.claude/scripts/`: deterministic framework helpers.
- `.agents/skills/`: Codex discovery wrappers; do not duplicate workflow logic
  there.

## Claude-to-Codex compatibility

When a canonical skill uses Claude Code vocabulary, translate it by intent:

| Canonical instruction | Codex behavior |
|---|---|
| `/skill-name` or the `Skill` tool | Invoke the matching `$skill-name` repository skill. |
| `Task` with `subagent_type: role` | Delegate only when the skill explicitly calls for it; give the subagent `.claude/agents/<role>.md` as its role contract. |
| `AskUserQuestion` | Use the available user-input UI; otherwise ask one concise plain-text question and wait. |
| `Read`, `Glob`, `Grep` | Use filesystem reads and `rg`/`rg --files`. |
| `Bash(...)` | Run the named command in the project shell, preserving its arguments and approval boundary. |
| `$ARGUMENTS` | Use the arguments supplied with the skill invocation. |

Claude-only skill frontmatter such as `allowed-tools`, `model`,
`argument-hint`, and `user-invocable` is compatibility metadata. Follow the
workflow body and the current Codex tool/permission policy.

## Collaboration and writes

The studio's design workflow is user-driven: question, options, decision,
draft, approval. When a studio skill requires approval before writing, show the
proposed artifact or concise changeset and ask for approval. A direct user
request to implement a clearly scoped repository change supplies that approval
for the requested scope. Never commit or push unless the user asks.

## Verification

- Use `.claude/scripts/` helpers for deterministic checks; they report
  observations, while the agent makes contextual judgments.
- Run the narrowest relevant tests after changes and report commands plus
  results.
- For UI changes, verify with screenshots when the relevant runtime is
  available.
- Preserve unrelated user changes in a dirty worktree.

## Scoped instructions

Read the nearest nested `AGENTS.md` before working under `design/`, `docs/`,
`src/`, or `studio-tests/`. Read `.claude/docs/coordination-rules.md` when a
workflow delegates studio roles, `.claude/docs/coding-standards.md` for code
changes, and `.claude/docs/context-management.md` for long-running work.

## Codex limitations

`.claude/settings.json`, `.claude/hooks/`, `.claude/rules/`, and
`.claude/statusline.sh` are not automatically loaded by Codex. Their important
behavior must come from this instruction hierarchy, an invoked skill, explicit
verification, or a separately reviewed Codex/plugin hook installation. See
`docs/CODEX-MIGRATION.md` for the compatibility boundary.
