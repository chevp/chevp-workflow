# Integration — Root CLAUDE.md Snippet

Place this block in the **workspace root** `CLAUDE.md` (e.g. `c:/chevp/CLAUDE.md`) so Claude knows when to switch from per-repo mode to workspace mode.

## Snippet

```markdown
## Workspace Mode — when to load chevp-workflow

This directory is a multi-repo workspace (not a single project).
Top-level folders are categories (sites/, misc/, frameworks/, nuna/, ...),
each containing independent git repos with their own CLAUDE.md.

### Read / explain / ask
Stay in the sub-repo's own CLAUDE.md. Do NOT load chevp-workflow.
Reads are trivial — never pay for workspace orchestration on a read.

### Write to exactly 1 repo
Stay in per-repo mode. Use chevp-ai-framework inside that repo.
Do NOT load chevp-workflow.

### Write to >1 repo (edit, commit, push, PR, release)
Load the chevp-workflow index BEFORE the first write,
then follow links on demand (no compiled bundle):

    @url https://chevp.github.io/chevp-workflow/index.md

From there, load CLAUDE.md for rules, the step README when entering
a step, and templates/guidelines as needed.

Lifecycle: Discover → Coordinate → Execute, gated by G0 → G1 → G2 → G3.

### Signals that trigger workspace mode
- plan touches files across >1 sub-repo
- user says "commit all", "push all", "release", "across repos", "workspace"
- a single feature spans multiple git roots
- coordinating changes between a library and its consumers

### Delegation
chevp-workflow orchestrates; it never writes code directly.
Per-repo work items are delegated to chevp-ai-framework once G2 is passed.
```

## Where to place it

Put the snippet near the top of the root `CLAUDE.md`, before any per-repo or per-category instructions. It establishes the mode-selection rule that governs everything else.

## Interplay with chevp-ai-framework

- `chevp-workflow` — activated only for cross-repo writes
- `chevp-ai-framework` — activated for per-repo writes, or per-repo execution of a workspace plan

They compose: a workspace plan (G2-approved under chevp-workflow) breaks down into per-repo work items, each executed under chevp-ai-framework's Context → Exploration → Production lifecycle.
