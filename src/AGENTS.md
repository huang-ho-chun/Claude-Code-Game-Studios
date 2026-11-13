# Source Directory

Apply these rules when writing or editing game code under `src/`.

- Read the selected engine's pinned reference under `docs/engine-reference/`
  before using engine APIs.
- Give public APIs doc comments.
- Keep gameplay values in external configuration instead of hardcoding them.
- Prefer dependency injection over global singletons.
- Put architecture decisions in `docs/architecture/`; required ADR depth comes
  from `modes.workflow`.
- Route engine-specific work using `specialists` in `project.yaml`. When
  uncertain, use `specialists.code`.
- Put tests under `tests/`, not `src/`. Use `$test-setup` when the framework is
  absent.
- For gameplay systems, write tests first for formulas and edge cases. For UI,
  verify with screenshots and compare expected with observed behavior.
