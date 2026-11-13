# Design Directory

Apply these rules when authoring or editing files under `design/`.

## GDDs

System GDDs use this order: Overview, Player Fantasy, Detailed Rules, Formulas,
Edge Cases, Dependencies, Tuning Knobs, Acceptance Criteria. Required coverage
depends on `modes.workflow`; resolve it through
`.claude/docs/workflow-modes.md` before reporting missing sections. Accept
`Detailed Design` as an alias for `Detailed Rules`.

Name system files `design/gdd/<system-slug>.md` and update
`design/gdd/systems-index.md` when adding one. Design in this order:
Foundation, Core, Feature, Presentation, Polish. Use `$design-review` after a
GDD and `$review-all-gdds` after a related set.

## Other design records

- Put tuning and small mechanic specs under `design/quick-specs/`; use
  `$quick-design`.
- Put per-screen UX specs under `design/ux/`; use `$ux-design` and validate with
  `$ux-review` before `$team-ui`.
- Keep `design/accessibility-requirements.md` outside `design/ux/`. Workflow
  gates depend on that exact path.
