# 01-discover

**Step 1 — Identify affected repos, build the impact map, assign primary owner.**

## Purpose

Before any cross-repo write, the AI must know exactly which repos are touched, which files, and which dependencies exist between the repos.

## Entry

Entered from **G0** (workspace mode confirmed).

## Deliverables

- **Impact Map** — a list of `(repo, files, dependencies)` tuples
- **Primary-Owner assignment** — exactly one repo owns the workspace plan
- **Confirmed Scope** — human acknowledges the list is complete

## Exit

Passes **G1** when:

- Every affected repo is listed with specific file paths
- Dependencies between repos are explicit (A-depends-on-B → B must commit first)
- Primary owner is chosen
- Human confirms scope

## How to choose the primary owner

Ask in order:

1. **Which repo initiates the feature?** (That one usually owns.)
2. **Which repo bears the user-visible outcome?** (Prefer consumer over library.)
3. **Which repo's README/docs would a new contributor read to understand this feature?**
4. **If still ambiguous:** ask the human.

The primary-owner repo hosts the workspace plan in its own `context/plans/` directory. All other repos get a reference stub only.

## Templates

- [../templates/impact-map-template.md](../templates/impact-map-template.md)
