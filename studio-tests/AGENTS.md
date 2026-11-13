# Studio Tests

This directory validates the studio skill and role framework independently of a
game project.

Before evaluating a skill or role:

1. Read `studio-tests/catalog.yaml` for the authoritative spec path and rubric
   category.
2. Read the canonical implementation under `.claude/skills/<name>/` or
   `.claude/agents/<name>.md`, including referenced files required by the case.
3. Read the applicable root and nested `AGENTS.md` files plus the canonical
   coordination references they point to.
4. Evaluate the matching spec and `studio-tests/quality-rubric.md` section.
5. Offer to save results and update the catalog only after presenting the
   evaluation.

Specs describe intended behavior. A failure is evidence to fix the
implementation; do not weaken an assertion merely to make it pass. Use
`$skill-test` for evaluation and `$skill-improve` for the full repair loop.
