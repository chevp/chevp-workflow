---
name: Commit Orchestration
description: Commits across repos must be ordered, cross-referenced, and verified
type: guideline
---

# Guideline: Commit Orchestration

**Rule:** Commits across repos must be ordered, cross-referenced, and verified.

**Why:** Cross-repo changes fail silently when commits land in the wrong order or without backlinks. A consumer commit pushed before its library dependency strands the consumer; a commit without a workspace-plan trailer is invisible in `git log` and untraceable later.

**How to apply:** Every workspace-scope commit follows the dependency order defined in the workspace plan. Every commit carries a `Refs workspace-plan:` trailer. Consumer commits additionally reference their upstream. Before declaring G3, verify every planned commit exists, every commit carries its trailer, and no repo is in a half-applied state.

## Commit ordering

- **Libraries before consumers.** If repo A provides an API used by B, A commits first.
- **Types/schemas before implementations.** Shared type changes propagate forward.
- **Docs can go first or last.** Reference stubs may be pushed any time if the owner plan is already shippable.
- **No circular commits.** If A needs B's change and B needs A's change in the same workspace plan, split the plan.

## No AI attribution

Commit messages must never contain AI/Claude co-authorship or attribution trailers. See [no-ai-attribution.md](no-ai-attribution.md) for the full rule and allowed trailers.

## Cross-references

Every commit in a workspace-scope change carries a trailer:

```
Refs workspace-plan: <owner-repo>#<plan-slug>
```

Consumer repos additionally reference the upstream commit/PR:

```
Refs workspace-plan: <owner-repo>#<plan-slug>
Refs upstream: <upstream-repo>@<sha-or-pr>
```

## Verification checklist (per workspace plan)

- [ ] Every planned commit exists in its repo
- [ ] Every commit carries the workspace-plan trailer
- [ ] Push order matches dependency order
- [ ] No repo is in a half-applied state
- [ ] CI passes where applicable
- [ ] Reference stubs point at the (now existing) owner plan

## PR chaining

When PRs are used:
- Open the owner-repo PR first.
- Open consumer PRs with a "depends on `<owner-repo>#<PR>`" note in the description.
- Merge in dependency order. Do not merge a consumer PR before its dependency is merged (or at least approved and stable).
