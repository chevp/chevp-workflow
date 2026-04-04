---
name: Reference stub — <workspace plan title>
description: This repo is affected by a workspace plan owned elsewhere
type: reference-stub
owner-plan: <path-or-url-to-primary-owner-plan>
status: proposed | approved | in-progress | done
date: YYYY-MM-DD
---

# Reference — <Workspace Plan Title>

This repo (`<this-repo>`) participates in a workspace plan whose primary owner is:

**`<owner-repo>`** → [`context/plans/<slug>.md`](<link>)

## What changes in this repo

- <file or area that changes>

## What NOT to do

- Do not duplicate the workspace plan here.
- Do not expand scope within this repo without going back to the primary owner.
- Any change that affects the broader workspace plan must go through `<owner-repo>`.

## Commit back-reference

All commits in this repo related to this workspace plan carry:

```
Refs workspace-plan: <owner-repo>#<plan-slug>
```
