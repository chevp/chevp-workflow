---
name: Read Is Trivial
description: The workspace framework must never load for read-only intent
type: guideline
---

# Guideline: Read Is Trivial

**Rule:** The workspace framework must never be loaded for read-only intent.

**Why:** If every "explain" or "show me" query pulled in workspace orchestration machinery, exploration would become slow and expensive. The workspace framework exists to constrain *writes*, not to narrate reads.

**How to apply:** Only load `chevp-workflow` when the intended action writes to more than one repo. For reads, single-file edits, single-repo plans, or grep/explain queries, stay in the sub-repo's own CLAUDE.md and do not load this framework.

## Do NOT load chevp-workflow when

- "explain", "what does", "show me", "describe", "why", "how does"
- reading a file, grepping a codebase, answering a factual question
- a single-file edit in a single repo
- planning within one repo (that's `chevp-ai-framework`'s job)

## DO load chevp-workflow when

- writing to files across >1 repo in one action
- committing, pushing, or releasing across >1 repo
- creating PRs that span repos
- a feature plan whose file list touches >1 repo

## Edge cases

- **"explain this cross-repo plan"** → still a read. Do not load workspace framework; just read the plan.
- **"plan a feature that spans A and B"** → this is a write (the plan itself is a write, and the feature will be). Load workspace framework.
- **"rename X in every repo"** → write, enters workspace mode.
