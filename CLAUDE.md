# CLAUDE.md — chevp-workflow

This is a **workspace-level** process framework for AI-assisted development across multiple repositories.
It defines the meta-lifecycle that Claude must follow whenever an action touches more than one repo.

## Core Principle

The human writes naturally. The AI detects whether a request is single-repo or workspace-scope.

Workspace mode is **opt-in by intent**: reads stay trivial, writes across repos require the full workspace lifecycle. The human never declares "workspace mode" — the AI infers it from the intended blast radius.

This framework is **orchestration-driven**: single-repo work is delegated to `chevp-ai-framework`. `chevp-workflow` owns only what lives between repos (impact, sequencing, orchestration).

## Core Rules

1. **Trivial reads stay trivial** — Never load this framework for read-only intent
2. **Any cross-repo write enters workspace mode** — Even one commit across two repos counts
3. **One primary owner per plan** — Every workspace plan lives in exactly one repo; others get reference stubs
4. **Delegation is mandatory** — Per-repo work is handed down to `chevp-ai-framework`, not duplicated here
5. **Gates are blockers** — G0 through G3 must be satisfied before forward movement
6. **Secondary repos never own scope** — Only the primary owner's plan can drive scope changes
7. **Cross-platform by default** — All paths, commands, and examples must work on Windows, macOS, and Linux (see [guidelines/cross-platform.md](guidelines/cross-platform.md))
8. **No AI attribution in commits** — Never add Claude/AI co-authorship or tooling references to commit messages or PR bodies (see [guidelines/no-ai-attribution.md](guidelines/no-ai-attribution.md))

## Lifecycle: 3 Steps × 6 Roles × 4 Gates

```
1. Discover → 2. Coordinate → 3. Execute
```

The AI infers workspace mode from intent. Before every write-action response the AI:

1. **Detects** whether the action affects >1 repo (git root)
2. **Enters** workspace mode if yes; stays in per-repo mode if no
3. **Announces** the workspace step it is currently in
4. **Checks** gate prerequisites — blocks if unmet, explains what is missing
5. **Acts** within the boundaries of the current workspace step
6. **Delegates** per-repo execution to `chevp-ai-framework` once the workspace plan is approved

| Intent Signal | Workspace Mode? |
|:--------------|:----------------|
| "explain", "show me", "what does", "read", ambiguous | **No** — stay in per-repo |
| edit in a single repo | **No** — stay in per-repo |
| edit across >1 repo, "commit all", "push all", "release", "across repos" | **Yes** — enter Discover |
| single feature whose plan names files in >1 repo | **Yes** — enter Discover |

### Mandatory Deliverables

| Step | Deliverables |
|:-----|:-------------|
| **Discover** | Impact Map (which repos, which files, which dependencies), Primary-Owner assignment, Confirmed Scope |
| **Coordinate** | Workspace Plan (lives in primary-owner repo), Commit/Push Sequence, Cross-Repo ADR (if applicable), Reference Stubs in secondary repos |
| **Execute** | Atomic commit set per repo, Orchestrated push order, Linked PRs, Verified state across all affected repos |

### Quality Gates

| Gate | Transition | Key Rule |
|:-----|:-----------|:---------|
| **G0** | (entry) → Discover | AI confirms workspace mode: action writes to >1 repo; human acknowledges |
| **G1** | Discover → Coordinate | Impact map complete, primary owner assigned, scope confirmed by human |
| **G2** | Coordinate → Execute | Workspace plan approved, commit sequence and push order defined, cross-repo ADR recorded (if relevant) |
| **G3** | Execute → Done | All affected repos committed/pushed/verified; no repo left in a half-applied state |

Within each step, 6 cross-cutting workspace roles operate:
**Workspace-SDLC** · **Impact-Mapping** · **Cross-Repo-Planning** · **Commit-Orchestration** · **Repo-Ownership** · **Workspace-Context**

## Relation to chevp-ai-framework

Once G2 is passed, the workspace plan is broken down into per-repo work items. Each per-repo work item is then executed under `chevp-ai-framework`'s own lifecycle (Context → Exploration → Production) inside its own repo's CLAUDE.md.

**chevp-workflow never writes code directly.** It only orchestrates which repos change, in what order, under which commit strategy. The actual per-repo code changes are driven by `chevp-ai-framework`.

## Documentation

| Folder | Content |
|:-------|:--------|
| [01-discover/](01-discover/) | Step 1: Identify affected repos, build impact map, assign primary owner |
| [02-coordinate/](02-coordinate/) | Step 2: Workspace plan, commit/push sequence, cross-repo ADRs |
| [03-execute/](03-execute/) | Step 3: Atomic commits, orchestrated pushes, linked PRs |
| [templates/](templates/) | Workspace plan, impact map, cross-repo ADR, multi-commit templates |
| [guidelines/](guidelines/) | Trivial-read, primary-owner, write-requires-plan, ownership-per-repo |
| [integration/](integration/) | Root CLAUDE.md snippet, interplay with chevp-ai-framework |
