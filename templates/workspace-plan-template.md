---
name: <Workspace plan title>
description: Cross-repo plan — owner repo, affected repos, commit sequence
type: workspace-plan
status: proposed | approved | in-progress | done
date: YYYY-MM-DD
primary-owner: <repo-name>
affected-repos: [<repo-a>, <repo-b>, ...]
---

# <Workspace Plan Title>

## Goal

<What does this workspace-scope change accomplish?>

## Scope

### Primary owner
**`<repo-a>`** — this plan lives here; all secondary repos reference it.

### Affected repos (from impact map)
- `<repo-a>` (primary-owner): <what changes>
- `<repo-b>` (consumer): <what changes>
- `<repo-c>` (reference-stub): link only

### Out of scope
- <things explicitly excluded>

## Commit sequence

| # | Repo | Branch | Commit message | Depends on | Notes |
|:--|:-----|:-------|:---------------|:-----------|:------|
| 1 | `<repo-a>` | `feat/<slug>` | `<scope>: <summary>` | — | lib change first |
| 2 | `<repo-b>` | `feat/<slug>` | `<scope>: <summary>` | 1 | consumes new API |
| 3 | `<repo-c>` | `docs/<slug>` | `docs: reference workspace plan <slug>` | 1 | stub only |

## Push order

1. `<repo-a>` → remote
2. `<repo-b>` → remote (after 1 merged or at least pushed)
3. `<repo-c>` → remote (any time after 1)

## Per-repo work items

Each work item is executed under that repo's own `chevp-ai-framework` lifecycle.

### Work item A — `<repo-a>`
- Context: <which files, which CLAUDE.md>
- Exploration: <plan/spec ref>
- Production: <acceptance criteria>

### Work item B — `<repo-b>`
- Context: <...>
- Exploration: <...>
- Production: <...>

### Work item C — `<repo-c>` (stub)
- Add `context/plans/<slug>-stub.md` referencing this plan

## Acceptance criteria

- [ ] All commits landed per sequence
- [ ] All pushes respect order
- [ ] PRs link back to this plan
- [ ] No repo in half-applied state
- [ ] Build passes in every repo with CI

## Risks / open questions

1. <risk or question>
