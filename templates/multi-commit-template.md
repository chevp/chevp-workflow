---
name: <Multi-commit title>
description: Orchestrated commit set across several repos
type: multi-commit
workspace-plan: <path-or-url-to-workspace-plan>
---

# Multi-Commit — <title>

Each commit below corresponds to exactly one entry in the workspace plan's commit sequence.

## Commits

### Commit 1 — `<repo-a>`

**Branch:** `feat/<slug>`

**Message:**
```
<scope>: <summary>

<body — what changed and why>

Refs workspace-plan: <owner-repo>#<plan-slug>
```

**Files:**
- `path/to/file`
- `path/to/other`

**Depends on:** —

---

### Commit 2 — `<repo-b>`

**Branch:** `feat/<slug>`

**Message:**
```
<scope>: <summary>

<body>

Refs workspace-plan: <owner-repo>#<plan-slug>
Refs upstream: <repo-a>@<sha-or-pr>
```

**Files:**
- `path/to/file`

**Depends on:** Commit 1 pushed/merged

---

### Commit 3 — `<repo-c>` (stub)

**Branch:** `docs/<slug>`

**Message:**
```
docs: reference workspace plan <slug>

Refs workspace-plan: <owner-repo>#<plan-slug>
```

**Files:**
- `context/plans/<slug>-stub.md`

**Depends on:** —

## Verification

- [ ] Each commit applied in order
- [ ] Each commit carries the `Refs workspace-plan:` trailer
- [ ] Dependent commits only pushed after their dependency
