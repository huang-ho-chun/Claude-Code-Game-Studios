# Codex Compatibility Layer

This repository originated as Claude Code Game Studios. The Codex conversion is
an additive compatibility layer so upstream framework updates can still be
merged without maintaining two divergent copies of every workflow.

## What Codex loads

- `AGENTS.md` at the repository root and scoped `AGENTS.md` files in working
  directories.
- Repository skills discovered under `.agents/skills/<name>/SKILL.md`.
- The canonical workflow, references, templates, scripts, and studio-role
  prompts under `.claude/` when an instruction or wrapper points to them.

Each Codex skill wrapper contains discovery metadata and tells Codex to read the
canonical implementation. Edit workflow behavior in `.claude/skills/`, then run
`.agents/scripts/sync-skill-wrappers.ps1 -Check` to detect wrapper drift. Run it
without `-Check` to regenerate wrappers after adding, removing, renaming, or
redescribing a canonical skill.

## Compatibility boundary

Codex does not automatically activate this repository's Claude Code
`settings.json`, status line, hooks, permission matchers, or `.claude/rules/`
files. The root `AGENTS.md` carries the always-needed behavioral contract;
skills load workflow-specific rules and run their existing scripts explicitly.

Treat `.claude/hooks/` as reference implementations unless hooks have been
separately packaged, reviewed, and trusted through a supported Codex plugin
installation. In particular, do not claim that commit, push, write, or asset
guards ran merely because their Claude hook files exist.

## Skill vocabulary

Canonical skills may say `/prototype`, `Skill`, `Task`, `AskUserQuestion`,
`Read`, `Glob`, `Grep`, or `Bash`. The root `AGENTS.md` defines their Codex
equivalents. Claude-only frontmatter remains in canonical files because Claude
Code still consumes it and because it records the original permission intent.

## Maintaining both runtimes

1. Make skill behavior changes only in `.claude/skills/`.
2. Regenerate or check `.agents/skills/` wrappers.
3. Keep `CLAUDE.md` and `AGENTS.md` aligned when project-wide policy changes.
4. Keep nested `CLAUDE.md` and `AGENTS.md` pairs aligned for scoped policy.
5. Test deterministic helpers directly; test runtime-specific hooks only in the
   runtime that actually loads them.
