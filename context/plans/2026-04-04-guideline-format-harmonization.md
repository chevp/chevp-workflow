---
name: Harmonize guideline format across chevp-workflow and chevp-ai-framework
description: Adopt memory-style frontmatter (name/description/type + Rule/Why/How to apply) for all guidelines in both frameworks, with chevp-workflow as the canonical source
type: workspace-plan
status: approved
date: 2026-04-04
primary-owner: misc/chevp-workflow
affected-repos: [misc/chevp-workflow, misc/chevp-ai-framework]
workspace-framework: misc/chevp-workflow
---

# Workspace Plan — Guideline Format Harmonization

## Goal

Make `misc/chevp-ai-framework/guidelines/*` follow the same memory-style format that `misc/chevp-workflow/guidelines/*` already uses: frontmatter (name, description, type) + `Rule / Why / How to apply` header, then additional sections as needed. The format is defined canonically by chevp-workflow; chevp-ai-framework adopts it.

## Impact map

| # | Repo | Role | Files touched | Depends on |
|:--|:-----|:-----|:--------------|:-----------|
| 1 | `misc/chevp-workflow` | primary-owner (library: defines format) | `guidelines/README.md` (note downstream adopters) | — |
| 2 | `misc/chevp-ai-framework` | consumer (adopts format) | `guidelines/ai-collaboration.md`, `guidelines/context-management.md`, `guidelines/plan-granularity.md`, `guidelines/README.md` (new) | 1 |

## Primary owner

**`misc/chevp-workflow`** — reason: the format is canonically defined in this repo's guidelines. chevp-ai-framework is the consumer that adopts it. Library before consumer.

## Scope

### In scope
- Add frontmatter (name, description, type: guideline) to all 3 chevp-ai-framework guideline files
- Add `**Rule:** / **Why:** / **How to apply:**` block near the top of each
- Preserve all existing content and sections
- Create new `guidelines/README.md` in chevp-ai-framework referencing the canonical format
- Add a short "Shared with" note in chevp-workflow's `guidelines/README.md`

### Out of scope
- Content rewrites of the 3 guidelines (only restructuring)
- Changes to `templates/`, `integration/`, `01-context/`, `02-exploration/`, `03-production/`
- Renaming files

## Commit sequence

| # | Repo | Branch | Commit message | Depends on |
|:--|:-----|:-------|:---------------|:-----------|
| 1 | `misc/chevp-workflow` | `feat/guideline-format-shared` | `docs(guidelines): note format shared with chevp-ai-framework` | — |
| 2 | `misc/chevp-ai-framework` | `feat/guideline-format-harmonization` | `refactor(guidelines): adopt memory-style format from chevp-workflow` | 1 |

## Push order

1. `misc/chevp-workflow` → remote (after G2)
2. `misc/chevp-ai-framework` → remote (after 1)

## Commit back-references

Both commits carry:

```
Refs workspace-plan: misc/chevp-workflow#2026-04-04-guideline-format-harmonization
```

Commit 2 additionally carries:

```
Refs upstream: misc/chevp-workflow@<sha-of-commit-1>
```

## Per-repo work items (delegated to chevp-ai-framework lifecycle)

### Work item A — `misc/chevp-workflow` (library)
- File: `guidelines/README.md`
- Change: add short paragraph noting the format is adopted by chevp-ai-framework
- Size: trivial (~5 lines)

### Work item B — `misc/chevp-ai-framework` (consumer)
- Files: 3 existing guideline files + 1 new README
- Change per existing file:
  - Add frontmatter block
  - Add `**Rule:** / **Why:** / **How to apply:**` at top of body
  - Preserve all existing content below
- New `guidelines/README.md`: explains format, references canonical chevp-workflow definition

## Acceptance criteria

- [ ] chevp-workflow guidelines/README.md mentions chevp-ai-framework as adopter
- [ ] Every chevp-ai-framework guideline file has frontmatter with name/description/type
- [ ] Every chevp-ai-framework guideline file has Rule/Why/How-to-apply block
- [ ] All existing content in chevp-ai-framework guidelines preserved
- [ ] chevp-ai-framework/guidelines/README.md exists and points at canonical format
- [ ] Both commits carry workspace-plan trailer
- [ ] Commit 2 references commit 1

## Workspace gates

- **G0** (workspace mode confirmed): ✅ 2 repos touched
- **G1** (impact map complete, primary owner assigned): ✅
- **G2** (plan approved, commit sequence locked): ✅ (user requested dogfood; proceeding)
- **G3** (all repos verified): pending execution
