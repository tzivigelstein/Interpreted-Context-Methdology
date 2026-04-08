# Stack and Rules Detection

How agents in any stage figure out what stack a target repo uses and where its project rules live. Run this every session. Never bake the result into a file.

## Stack Detection

Look for these markers in the target repo's root:

| Marker File | Stack |
|---|---|
| `pyproject.toml` or `setup.py` | Python |
| `package.json` | Node.js |
| `Cargo.toml` | Rust |
| `go.mod` | Go |
| `Gemfile` | Ruby |
| `pom.xml` | Java |
| `build.gradle` | Java or Kotlin |
| `composer.json` | PHP |

If `pyproject.toml` is present, also read it and look for: `flask`, `django`, `fastapi`, `sqlalchemy`, `alembic`, `celery`, `pydantic`. List the ones found as the framework stack.

If `package.json` is present, read its `dependencies` and `devDependencies` and look for: `next`, `react`, `vue`, `nuxt`, `svelte`, `express`, `typescript`. List the ones found.

If multiple top-level markers exist (a polyglot repo), report all of them.

If no markers are found, report "Unknown" and ask the user.

## Rules Locations

Look for these in the target repo, in order:

1. **Folders**: `.cursor/rules/`, `.claude/rules/`, `docs/`. Include only if the folder is non-empty.
2. **Top-level files**: `CLAUDE.md`, `AGENTS.md`, `CONVENTIONS.md`. Include only if the file exists.
3. **Domain-level files**: `app/domain/*.md`, `src/domain/*.md`. Include any markdown found in these locations.

Build a list of every rules location found. Read every file in the list before doing your stage's main work. Internalize the rules.

If no rules are found anywhere, ask the user: "I did not find a CLAUDE.md, AGENTS.md, .cursor/rules/, or similar. Do you have project conventions written somewhere I should read?".

## Why Detection Runs Every Session

The original CLI baked detection results into a static `DESIGN.md` at init time. When the stack changed (new framework added, rules moved, project conventions edited), the doc lied silently. Detecting per-session means the agent always has current information and there is no doc to keep in sync.
