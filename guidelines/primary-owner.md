---
name: One Primary Owner Per Plan
description: Every workspace plan lives in exactly one primary-owner repo; secondary repos get reference stubs only
type: guideline
---

# Guideline: One Primary Owner Per Plan

**Rule:** Every workspace plan lives in exactly one primary-owner repo. Secondary repos get reference stubs only.

**Why:** Duplicating plans across repos causes drift, contradictory updates, and confusion about who owns scope. A single owner means one source of truth, one place to evolve the plan, one backlink target for all commits.

**How to apply:** When writing a workspace plan, choose one primary-owner repo. Place the plan under `<owner>/context/plans/YYYY-MM-DD-<slug>.md`. In every other affected repo, add a one-page reference stub using the reference-stub template. Commits in secondary repos carry `Refs workspace-plan: <owner-repo>#<slug>`.

## Choosing the owner

Pick, in order:
1. The repo that initiates the feature.
2. The repo that delivers the user-visible outcome.
3. The repo whose README a new contributor would read first.
4. If still ambiguous — ask the human.

## What a stub must contain

- Pointer to owner plan
- List of files that change in this repo
- Explicit "do not duplicate" note
- Commit back-reference format

## What a stub must NOT contain

- A copy of the owner plan's scope, acceptance criteria, or commit sequence
- Any decision that could contradict the owner plan
