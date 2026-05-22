# ContextGuard Versioning

ContextGuard uses `v0.minor.patch` while the app is still pre-1.0.

## Core Rule

Version bumps happen by the release pass, not by the number of commits. If one
work pass fixes 20 real things, bump the patch by 20 in that single release
pass.

Example:

```text
current: v0.1.0
20 fixes in one pass: v0.1.20
```

## Patch Bumps

Use patch bumps for normal forward work:

- bug fixes
- UI polish
- docs updates
- small workflow improvements
- detector tweaks
- helper text improvements
- small MCP or CLI additions

Patch can advance from `.1` through `.99` inside the current minor lane.

Examples:

```text
v0.1.0 -> v0.1.1
v0.1.7 -> v0.1.8
v0.1.19 -> v0.1.20
v0.1.98 -> v0.1.99
```

## Minor Bumps

Use the middle number for big changes. When the patch lane reaches `.99`, or a
release pass changes the product in a meaningful way, move to the next minor and
reset patch to `.0`.

Big changes include:

- a major new app section
- a real updater implementation
- a new model adapter family
- a new write/safety workflow
- a significant graph/search rewrite
- a large MCP tool surface expansion
- a broad packaging or CI release-system change

Examples:

```text
v0.1.99 -> v0.2.0
v0.2.14 plus a major updater feature -> v0.3.0
```

## First Release

Do not create a release tag while the worktree has uncommitted release changes.
The first public/private test release should be tagged only after:

1. `CHANGELOG.md` has real release notes.
2. `pnpm version:check` passes.
3. The relevant build/test checks pass.
4. The private release branch has the release commit.
5. The public repo remains docs/releases only.

## Commands

```powershell
pnpm version:bump 0.1.20
pnpm version:check
```

Then edit `CHANGELOG.md`, run the release checks, commit, tag, and push the tag
from the private release repository.
