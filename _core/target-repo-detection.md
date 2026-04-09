# Target Repo Detection

How any workspace that operates on external repos identifies the target repo. Run this when the agent enters a workspace stage that needs to read or write artifacts about a specific repo.

## Detection Logic

1. Run `git rev-parse --show-toplevel` from the current working directory.
2. If the result is the icm repo itself (the root that contains this `_core/` folder), the cwd is icm. The agent does NOT yet know the target. Ask the user: "which repo is this for?" and accept either a repo name or an absolute path.
3. Otherwise, the result is the target repo. The basename of that path is `<repo>` for all output paths in the workspace. Example: `/home/tzivigelstein/codes/ac-hub` -> `<repo>` is `ac-hub`.
4. If the cwd is not inside any git repo, ask the user explicitly. Do not guess.

The `<repo>` value is used as a subfolder in the workspace's `output/` so that artifacts from different repos do not collide.

## When to Re-Run

Run detection at the start of each session. The cwd may have changed since the last invocation. Never bake the result into a file.
