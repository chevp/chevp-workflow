---
name: No AI Attribution in Commits
description: Commit messages and PR bodies must never include Claude/AI co-authorship or tooling references
type: guideline
---

# Guideline: No AI Attribution in Commits

**Rule:** Git commit messages, commit bodies, and PR descriptions must never include AI, Claude, or co-authorship attribution.

**Why:** Commits are the human author's work. AI assistance is a tool — not a co-author, not a contributor. Attribution trailers pollute git history, leak tooling choices into shared repos, and misrepresent authorship.

**How to apply:** Strip any AI attribution trailer before committing. When composing a commit message, include only scope, summary, body, and the `Refs workspace-plan:` trailer (where applicable). Before pushing, verify `git log --format=%B -1` contains no AI/Claude references. Applies to single-repo commits, workspace-orchestrated multi-commit sets, reference-stub commits, PR titles/bodies, and release notes.

## Forbidden

- `Co-Authored-By: Claude ...`
- `Generated with Claude Code`
- `🤖 Generated with ...`
- Any trailer, footer, or body line that references AI tooling or co-authorship

## Allowed trailers

Only workflow-meaningful trailers belong in commit messages:

```
<scope>: <summary>

<body>

Refs workspace-plan: <owner-repo>#<plan-slug>
Refs upstream: <upstream-repo>@<sha-or-pr>
```

Nothing else.
