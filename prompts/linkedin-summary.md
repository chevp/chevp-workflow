# Prompt — LinkedIn Summary Post

**Target:** short LinkedIn post introducing `chevp-workflow`.

**Length:** 4–6 short paragraphs, under 1200 characters total.

**Tone:** confident, practical, slightly opinionated. No hype. No emojis unless explicitly requested.

---

## Prompt

Write a LinkedIn post introducing `chevp-workflow`, a workspace-level meta-lifecycle for AI-assisted development across multiple repositories.

Cover:

1. **The problem:** single-repo AI frameworks break down when a feature touches several repos at once. Commits strand, scope drifts, no one owns the cross-repo plan.
2. **The approach:** a thin orchestration layer above the per-repo lifecycle. Three steps — Discover, Coordinate, Execute — gated by G0–G3. One primary-owner repo per workspace plan; others get reference stubs.
3. **The delegation contract:** `chevp-workflow` never writes code; it hands per-repo work down to `chevp-ai-framework` after the workspace plan is approved.
4. **The trivial-read principle:** reads stay cheap. The framework only activates when the AI is about to *write* across repos.
5. **Call to read more:** link to `https://chevp.github.io/chevp-workflow/`.

Constraints:
- No marketing adjectives ("revolutionary", "game-changing", etc.)
- No emoji
- Plain sentences, one idea per sentence where possible
- End with the link, no sign-off
