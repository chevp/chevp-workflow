# guidelines/

Framework-level rules for `chevp-workflow`. Each file is a single, focused guideline.

## File format

Every guideline uses memory-style frontmatter plus a **Rule / Why / How to apply** header, mirroring the conventions used by Claude's own memory system:

```markdown
---
name: <Guideline name>
description: <one-line description>
type: guideline
---

# Guideline: <Title>

**Rule:** <the rule stated plainly>

**Why:** <reason>

**How to apply:** <concrete application — when/where this kicks in>

## <Additional sections as needed>
```

The **Rule / Why / How to apply** block is the minimum. Add sections only where they pay for themselves (tables, forbidden lists, edge cases, verification checklists).

## Relation to Claude memory

Guidelines in this folder are **framework rules** shipped with the repo — public, shared across anyone who adopts chevp-workflow.

Claude's personal memory (`~/.claude/.../memory/`) is a separate, per-user store. Users may mirror individual guidelines into their own memory if they want Claude to apply them across all projects, not just under chevp-workflow. The two systems use similar syntax on purpose, but they are not auto-synchronised.

## Current guidelines

| File | Rule |
|:-----|:-----|
| [read-is-trivial.md](read-is-trivial.md) | Never load this framework for read-only intent |
| [write-requires-plan.md](write-requires-plan.md) | No cross-repo write before G2 |
| [primary-owner.md](primary-owner.md) | One primary-owner repo per workspace plan |
| [commit-orchestration.md](commit-orchestration.md) | Commits must be ordered, cross-referenced, verified |
| [no-ai-attribution.md](no-ai-attribution.md) | Commit messages must never reference AI/Claude |
| [cross-platform.md](cross-platform.md) | All paths and commands work on Windows, macOS, Linux |
