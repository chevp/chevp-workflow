---
name: Write Requires Plan
description: No cross-repo write may begin before a workspace plan has been approved (G2)
type: guideline
---

# Guideline: Write Requires Plan

**Rule:** No write across >1 repo may begin before a workspace plan has been approved (G2).

**Why:** Cross-repo writes are high-blast-radius. Commits in one repo can strand commits in another if the sequence is wrong. A workspace plan locks the sequence before any commit happens.

**How to apply:** When the AI detects that an action touches ≥2 repos, it enters Discover, builds an impact map (G1), then writes the workspace plan with commit sequence (G2). Only after G2 passes may per-repo work items be handed off to `chevp-ai-framework`. No amending one repo to match another without updating the workspace plan first.

## Forbidden shortcuts

- No "quick fix across two repos" without a plan.
- No amending one repo to match another without updating the workspace plan first.
- No `git push` in a secondary repo before its dependency has been pushed (or explicitly sequenced otherwise).

## When the plan turns out wrong

If Execute reveals the impact map was incomplete:
1. Stop.
2. Return to Discover.
3. Update the impact map.
4. Update or supersede the workspace plan.
5. Re-pass G1, G2.
6. Resume Execute.

Do not patch silently in Execute.
