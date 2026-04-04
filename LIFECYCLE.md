# LIFECYCLE.md — chevp-workflow

The full matrix of steps, roles, gates, and deliverables for workspace-level (cross-repo) AI-assisted development.

## Step Matrix

|                         | **1. Discover**                                | **2. Coordinate**                                  | **3. Execute**                                      |
|:------------------------|:-----------------------------------------------|:---------------------------------------------------|:----------------------------------------------------|
| **Goal**                | Identify affected repos, map impact            | Write workspace plan, sequence the work            | Orchestrated commits, pushes, PRs across repos      |
| **Workspace-SDLC**      | Confirm workspace mode, assign primary owner   | Approve workspace plan, lock sequencing            | Drive G3 verification across all repos              |
| **Impact-Mapping**      | List repos, files, dependencies; build map     | Update map if coordination reveals new touches     | Verify nothing outside the map was touched          |
| **Cross-Repo-Planning** | —                                              | Produce workspace plan, commit sequence, ADR       | Hand per-repo work items to `chevp-ai-framework`    |
| **Commit-Orchestration**| —                                              | Define commit messages, order, cross-refs          | Execute commits in order, link PRs                  |
| **Repo-Ownership**      | Assign exactly one primary-owner repo          | Write reference stubs in secondary repos           | Verify stubs point at the final owner plan          |
| **Workspace-Context**   | Confirm root CLAUDE.md is loaded correctly     | Confirm per-repo CLAUDE.md files are consistent    | Update root CLAUDE.md if workspace learnings emerge |

## Quality Gates

### G0 — Entry → Discover

Triggered automatically when the AI detects an intent that writes to >1 repo.

**Criteria (all must be true):**
- AI has announced "workspace mode" and named the triggering signal
- Human has acknowledged workspace mode (explicit or implicit via continuing)
- At least 2 repos (git roots) are genuinely affected — if not, revert to per-repo

**Blocks:** any write action across repos until human acknowledges.

### G1 — Discover → Coordinate

**Criteria (all must be true):**
- Impact Map lists every affected repo with specific files/paths
- Dependencies between repos are explicit (which change requires which first)
- Primary-owner repo is assigned (exactly one)
- Human has confirmed the scope

**Blocks:** writing any workspace plan before impact is understood.

### G2 — Coordinate → Execute

**Criteria (all must be true):**
- Workspace Plan exists in the primary-owner repo, approved by human
- Commit sequence is defined (which repo first, which commit message, which cross-refs)
- Push order is defined
- Reference stubs exist in all secondary repos (or are part of the commit sequence)
- Cross-Repo ADR recorded if the change involves an architectural decision that spans repos

**Blocks:** any actual commit/push before the plan is approved and sequenced.

### G3 — Execute → Done

**Criteria (all must be true):**
- Every affected repo has the planned commits
- Push order was respected
- PRs (if any) are linked back to the primary-owner plan
- No repo is in a half-applied state (e.g., stub exists but owner plan not merged)
- Build passes in every repo that runs CI

**Blocks:** declaring the workspace task done while any repo is inconsistent.

## Workspace Modes

The AI operates in exactly one workspace mode at a time:

| Signal | Detected Mode |
|:-------|:--------------|
| "explain", "show me", "read", "analyze", single-file read, ambiguous | **Per-Repo** — Workspace framework not loaded. Delegate to sub-repo's CLAUDE.md. |
| edit/write in exactly 1 repo | **Per-Repo** — Hand off directly to chevp-ai-framework. |
| edit/commit/push affecting >1 repo, "all repos", "across", "release", "workspace" | **Workspace** — Enter Discover. Load chevp-workflow. |

Before every response where a write is anticipated, the AI:

1. **Counts** the number of distinct git roots the action would touch
2. **Chooses** Per-Repo if count ≤ 1, Workspace if count ≥ 2
3. **Announces** the mode on entry and on any change
4. **Falls back** from Execute to Coordinate if the impact map turns out to be wrong
5. **Delegates** all per-repo work down to chevp-ai-framework after G2

## Delegation Contract (chevp-workflow → chevp-ai-framework)

Once G2 is passed, the workspace plan is decomposed into per-repo work items. Each item is then executed under its own per-repo lifecycle:

```
Workspace Plan (in primary-owner repo)
    │
    ├── Work Item A (repo X) ──► chevp-ai-framework: Context → Exploration → Production
    ├── Work Item B (repo Y) ──► chevp-ai-framework: Context → Exploration → Production
    └── Work Item C (repo Z) ──► chevp-ai-framework: Context → Exploration → Production
```

Each work item carries a backlink to the workspace plan. Each per-repo CLAUDE.md is responsible for its own G1/G2/G3.

## Principles

- **Orchestration, not implementation** — chevp-workflow never writes code; it only decides which repos change in what order.
- **One owner** — Every workspace plan has exactly one primary-owner repo. Secondary repos get reference stubs.
- **Sequencing is explicit** — If repo A depends on repo B, that dependency is written down before any commit.
- **Stubs over duplicates** — Secondary repos get a one-line reference, not a copy of the plan.
- **Fall back fast** — If impact was wrong, return to Discover. Don't paper over it in Execute.
