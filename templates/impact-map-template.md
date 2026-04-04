---
name: <Impact map title>
description: Which repos, files, and dependencies are affected by this workspace change
type: impact-map
date: YYYY-MM-DD
status: draft | confirmed
---

# Impact Map — <title>

## Trigger

<One-line description of the change that triggered workspace mode.>

## Affected repos

| # | Repo | Role | Files touched | Depends on |
|:--|:-----|:-----|:--------------|:-----------|
| 1 | `<repo-a>` | primary-owner | `path/to/file`, `path/to/other` | — |
| 2 | `<repo-b>` | consumer | `path/to/file` | 1 |
| 3 | `<repo-c>` | reference-stub | `context/plans/<stub>.md` | 1 |

**Role values:** `primary-owner` | `library` | `consumer` | `reference-stub` | `docs`

## Dependency graph

```
<repo-a>  ──►  <repo-b>
   │
   └────────►  <repo-c> (stub)
```

## Primary owner

**`<repo-a>`** — reason: <why this repo owns the plan>

## Scope boundary

**In scope:**
- <repo/file>

**Out of scope:**
- <repo/file that looked relevant but is not>

## Confirmation

- [ ] All affected repos listed
- [ ] Dependencies explicit
- [ ] Primary owner assigned
- [ ] Human confirmed scope
