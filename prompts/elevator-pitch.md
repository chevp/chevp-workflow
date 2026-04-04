# Prompt — 60-Second Elevator Pitch

**Target:** spoken or written pitch, ~150 words.

**Audience:** technical lead or staff engineer who already uses per-repo AI frameworks.

---

## Prompt

Write a 60-second elevator pitch for `chevp-workflow`.

The listener already knows about single-repo AI frameworks (like `chevp-ai-framework`) that enforce a Context → Exploration → Production lifecycle. Your job: explain why a separate *workspace* layer is needed and what it does.

Structure:

1. **Hook** (1 sentence): the pain point — "One feature, three repos, no owner."
2. **Claim** (1 sentence): `chevp-workflow` is the missing layer above per-repo frameworks.
3. **What it does** (3 sentences): Discover (impact map), Coordinate (workspace plan, commit sequence), Execute (orchestrated commits/pushes/PRs).
4. **Boundary** (1 sentence): it never writes code — it delegates to `chevp-ai-framework`.
5. **Principle** (1 sentence): reads stay trivial; only cross-repo writes trigger it.
6. **Close** (1 sentence): call to read the docs.

Tone: direct, practical. No jargon the listener doesn't already own. No buzzwords.
