# 02-coordinate

**Step 2 — Write the workspace plan, sequence the work, record cross-repo decisions.**

## Purpose

Translate the impact map into an executable workspace plan: which repo commits first, in which order, with which commit messages and cross-references.

## Entry

Entered from **G1** (impact map complete, primary owner assigned).

## Deliverables

- **Workspace Plan** — stored in the primary-owner repo under `context/plans/YYYY-MM-DD-<slug>.md`
- **Commit Sequence** — ordered list of `(repo, branch, commit-message, depends-on)`
- **Push Order** — which remote branches push in which order
- **Reference Stubs** — one per secondary repo, pointing at the owner plan
- **Cross-Repo ADR** (if applicable) — architectural decision that spans repos

## Exit

Passes **G2** when:

- Workspace plan is approved by the human
- Commit sequence is defined for every affected repo
- Push order respects dependencies
- Reference stubs are written (or are part of the commit sequence itself)
- Human confirms readiness to execute

## Sequencing rules

1. **Libraries before consumers** — If A provides an API used by B, A commits first.
2. **Types/schemas before implementations** — Shared types propagate forward.
3. **Stubs can go first OR last** — Depending on whether the owner plan is already shippable.
4. **No circular commits** — If A needs B and B needs A, split the feature.

## Templates

- [../templates/workspace-plan-template.md](../templates/workspace-plan-template.md)
- [../templates/multi-commit-template.md](../templates/multi-commit-template.md)
- [../templates/cross-repo-adr-template.md](../templates/cross-repo-adr-template.md)
