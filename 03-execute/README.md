# 03-execute

**Step 3 — Orchestrated commits, pushes, and PRs across all affected repos.**

## Purpose

Execute the workspace plan exactly as sequenced: commit per repo, push in order, link PRs back to the primary-owner plan, verify consistency.

## Entry

Entered from **G2** (workspace plan approved, commit sequence locked).

## Deliverables

- **Atomic commit set** per repo, matching the planned messages
- **Orchestrated push** respecting dependency order
- **Linked PRs** — each PR references the primary-owner plan
- **Verification** — every affected repo is in the expected post-state

## Exit

Passes **G3** when:

- Every affected repo has the planned commits merged or ready to merge
- Push order was respected (no dependent repo pushed before its dependency)
- PRs cross-reference the primary-owner workspace plan
- No repo is in a half-applied state
- CI passes in every repo that runs CI
- Human approves completion

## Delegation to chevp-ai-framework

`chevp-workflow` does **not** write code. For each per-repo work item, control is handed to that repo's local `chevp-ai-framework` lifecycle:

```
Workspace Plan → Work Item (repo X) → chevp-ai-framework:
    Context → Exploration → Production → per-repo G3 → commit
```

The workspace-level G3 can only pass once every per-repo G3 has passed.

## Commit message convention

Each commit in a workspace-scope change carries a back-reference:

```
<scope>: <summary>

Refs workspace-plan: <owner-repo>#<plan-slug>
```

This allows any repo's `git log` to find the workspace plan that caused the change.

## Fall-back

If execution reveals an impact that was not in the map (new repo touched, new dependency found), **return to Discover**. Do not patch silently.
