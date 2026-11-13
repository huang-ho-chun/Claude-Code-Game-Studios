# Documentation Directory

Apply these rules when authoring or editing files under `docs/`.

## Architecture decisions

Use `.claude/docs/templates/architecture-decision-record.md`. ADRs include:
Title, Status, Context, Decision, Consequences, ADR Dependencies, Engine
Compatibility, and GDD Requirements Addressed.

The lifecycle is `Proposed` -> `Accepted` -> `Superseded`; a story cannot depend
on a proposed ADR. Use `$architecture-decision` to create ADRs and
`$architecture-review` after a related set.

`docs/architecture/tr-registry.yaml` owns stable requirement IDs. Append IDs;
never renumber existing ones. Keep the control manifest's dated version in sync
with story references.

## Engine references

Before using an engine API, read `docs/engine-reference/<engine>/VERSION.md` and
the relevant pinned module/plugin notes. Treat these references as newer and
more authoritative than model memory.
