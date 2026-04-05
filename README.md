# chevp-workflow

**A workspace-level meta-lifecycle for AI-assisted development across multiple repositories.**

> One feature often touches many repos. When that happens, single-repo processes break down.
> This framework owns the space *above* the single repo: impact, coordination, orchestration.

![chevp-workflow — workspace orchestration across multiple repositories](docs/Workflow-Diagram%20mit%20Repository-Karten.png)

---

## Why a separate layer?

| Concern | Per-Repo (`chevp-ai-framework`) | Workspace (`chevp-workflow`) |
|:--------|:---|:---|
| One repo, one lifecycle | ✅ | — |
| Context / Exploration / Production gates (G1/G2/G3) | ✅ | — |
| Which repos does this feature touch? | — | ✅ |
| Cross-repo commit sequencing | — | ✅ |
| Orchestrated push / PR chaining | — | ✅ |
| Primary-owner rule per workspace plan | — | ✅ |
| Release trains across repos | — | ✅ |

`chevp-workflow` does **not** replace `chevp-ai-framework` — it sits one layer above and delegates single-repo work back to it.

---

## Lifecycle

```
1. Discover → 2. Coordinate → 3. Execute
```

| Step | Purpose | Mandatory Deliverables |
|:-----|:--------|:------------------------|
| **[Discover](01-discover/)** | Identify all affected repos, map dependencies | Impact Map, Primary-Owner assignment, Scope |
| **[Coordinate](02-coordinate/)** | Write the workspace plan, sequence the work | Workspace Plan, Commit/Push Sequence, Cross-Repo ADR |
| **[Execute](03-execute/)** | Orchestrated commits, pushes, PRs across repos | Atomic commit set, linked PRs, verified state |

Quality gates **G0**, **G1**, **G2**, **G3** enforce human approval at every transition.

| Gate | Transition | Key Rule |
|:-----|:-----------|:---------|
| **G0** | Triggered → Discover | Workspace mode confirmed: action writes to >1 repo |
| **G1** | Discover → Coordinate | Impact map complete, primary owner assigned, scope confirmed |
| **G2** | Coordinate → Execute | Workspace plan approved, commit sequence defined |
| **G3** | Execute → Done | All affected repos committed/pushed/verified |

See [LIFECYCLE.md](LIFECYCLE.md) for the full matrix.

---

## Roles

Six workspace-level roles operate within each step:

| Role | Scope |
|:-----|:------|
| **Workspace-SDLC** | Workspace process governance, G0–G3 gates |
| **Impact-Mapping** | Which repos, which files, which dependencies |
| **Cross-Repo-Planning** | Workspace plan, commit sequence, primary-owner rule |
| **Commit-Orchestration** | Atomic commit sets, push order, PR chaining |
| **Repo-Ownership** | Single-owner per plan, stubs in secondary repos |
| **Workspace-Context** | Root CLAUDE.md, when to load workspace vs. per-repo |

---

## The "Trivial Read" Principle

Reading must stay lightweight. `chevp-workflow` is only activated when the AI is about to **write to more than one repo**.

```
Intent: "explain", "show me", "what does X do"
 → stay in the sub-repo's CLAUDE.md. Do NOT load chevp-workflow.

Intent: "edit X in A and B", "commit all", "push all", "release"
 → enter Workspace Mode. Load chevp-workflow. Pass G0.
```

---

## Quick Start

Add this block to your **workspace root** `CLAUDE.md` (e.g. `c:/chevp/CLAUDE.md`):

```markdown
## Workspace Mode — when to load chevp-workflow

This directory is a multi-repo workspace (not a single project).

Read / explain / ask → stay in the sub-repo's CLAUDE.md. Do NOT load chevp-workflow.

Any action that writes to >1 repo (edit, commit, push, PR, release) →
load the chevp-workflow index BEFORE the first write, then follow
links to the files you actually need:
@url https://chevp.github.io/chevp-workflow/index.md

Signals that trigger workspace mode:
- plan touches files across >1 sub-repo
- user says "commit all", "push all", "release", "across repos"
- a single feature spans multiple git roots
```

Single-repo work continues to use `chevp-ai-framework` as before.

See [integration/](integration/) for details.

---

## Repository Structure

```
index.md          Entry point — links to every file in this repo
01-discover/      Step 1 — Identify affected repos, build impact map
02-coordinate/    Step 2 — Workspace plan, commit sequence, primary owner
03-execute/       Step 3 — Orchestrated commits, pushes, PRs
templates/        Workspace plan, impact map, cross-repo ADR, multi-commit
guidelines/       Trivial-read, primary-owner, write-requires-plan, cross-platform
integration/      Root CLAUDE.md snippet, interplay with chevp-ai-framework
prompts/          Source prompts for images, diagrams, and copy
docs/             Overview page (HTML) + images
```

There is **no compiled bundle**. Load `index.md` first, then follow links to individual files on demand.

---

## Principles

| Principle | Why |
|:----------|:----|
| **Read is trivial** | Workspace framework never loads for read-only intent |
| **Write needs a plan** | Any cross-repo write requires a workspace plan first |
| **One owner per plan** | Every workspace plan lives in exactly one primary repo |
| **Secondary repos get stubs** | Other touched repos reference the owner, they don't duplicate |
| **Gates are blockers** | No forward movement without all criteria satisfied |
| **Delegates down, never up** | Per-repo work delegates to chevp-ai-framework |
| **Cross-platform** | All examples and paths work on Windows, macOS, and Linux |

---

## Relation to other frameworks

```
chevp-workflow           ← this repo (workspace meta-lifecycle)
     │
     ▼  delegates per-repo work to
chevp-ai-framework       ← per-repo lifecycle (Context/Exploration/Production)
     │
     ▼  extended by
domain-ai-framework      ← domain-specific layer (optional)
     │
     ▼  used by
project frameworks       ← e.g. nuna-ai-framework
```

Tooling (repo cloning, status, pull) stays in [chevp-setup](https://github.com/chevp/chevp-setup).

---

## License

This project is licensed under the MIT License.
