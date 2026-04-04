# chevp-workflow — Index

Workspace-level meta-lifecycle for AI-assisted development across multiple repositories.

This is the entry point. Follow the links below to load individual files as needed — nothing is bundled.

---

## Core

- [README.md](README.md) — Overview, layering, quick start
- [CLAUDE.md](CLAUDE.md) — Rules for AI: when to enter workspace mode, core lifecycle
- [LIFECYCLE.md](LIFECYCLE.md) — Full step × role × gate matrix

## Lifecycle Steps

- [01-discover/README.md](01-discover/README.md) — Identify affected repos, build impact map
- [02-coordinate/README.md](02-coordinate/README.md) — Workspace plan, commit sequence, ADRs
- [03-execute/README.md](03-execute/README.md) — Orchestrated commits, pushes, PRs

## Templates

- [templates/impact-map-template.md](templates/impact-map-template.md)
- [templates/workspace-plan-template.md](templates/workspace-plan-template.md)
- [templates/multi-commit-template.md](templates/multi-commit-template.md)
- [templates/cross-repo-adr-template.md](templates/cross-repo-adr-template.md)
- [templates/reference-stub-template.md](templates/reference-stub-template.md)

## Guidelines

- [guidelines/README.md](guidelines/README.md) — Format and relation to Claude memory
- [guidelines/read-is-trivial.md](guidelines/read-is-trivial.md) — Never load this for reads
- [guidelines/primary-owner.md](guidelines/primary-owner.md) — One owner per plan
- [guidelines/write-requires-plan.md](guidelines/write-requires-plan.md) — No cross-repo write before G2
- [guidelines/commit-orchestration.md](guidelines/commit-orchestration.md) — Order, cross-refs, PR chaining
- [guidelines/no-ai-attribution.md](guidelines/no-ai-attribution.md) — No Claude/AI references in commit messages
- [guidelines/cross-platform.md](guidelines/cross-platform.md) — Windows, macOS, Linux

## Integration

- [integration/root-claude-md-snippet.md](integration/root-claude-md-snippet.md) — Snippet for workspace root CLAUDE.md
- [integration/framework-composition.md](integration/framework-composition.md) — Interplay with chevp-ai-framework

## Prompts

- [prompts/README.md](prompts/README.md) — Source prompts for images, diagrams, and copy
- [prompts/framework-image.md](prompts/framework-image.md)
- [prompts/layering-diagram.md](prompts/layering-diagram.md)
- [prompts/lifecycle-diagram.md](prompts/lifecycle-diagram.md)
- [prompts/impact-map-diagram.md](prompts/impact-map-diagram.md)
- [prompts/architecture-diagram.md](prompts/architecture-diagram.md)
- [prompts/linkedin-summary.md](prompts/linkedin-summary.md)
- [prompts/elevator-pitch.md](prompts/elevator-pitch.md)

---

## Loading strategy

Load files on demand, not eagerly:

1. **Always load first:** this `index.md`
2. **Load for rule enforcement:** `CLAUDE.md`
3. **Load when entering a step:** that step's `README.md`
4. **Load when writing an artifact:** the matching template
5. **Load on disputes:** the relevant guideline

Never load the entire framework. Follow the links that are relevant to the current step.
