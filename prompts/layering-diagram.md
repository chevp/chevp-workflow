# Prompt — Layering Diagram

**Target:** `docs/images/chevp-workflow-layering.png`

**Aspect ratio:** 4:3 or 680×540

**Purpose:** Show the 4-layer framework stack: workspace → per-repo → domain → project.

---

## Prompt

Create a vertical layer-stack diagram with 4 horizontal bands, each labeled.

**Layers (top to bottom):**
1. **chevp-workflow** (workspace, cross-repo) — violet `#8b5cf6`
2. **chevp-ai-framework** (per-repo lifecycle) — blue `#3b82f6`
3. **domain-ai-framework** (domain-specific) — teal `#14b8a6`
4. **Project frameworks** (e.g. nuna-ai-framework) — emerald `#10b981`

**Elements per layer:**
- Layer name in bold
- One-line subtitle describing its scope
- Downward arrow between layers labeled "delegates to" (between workspace and per-repo) or "extended by"/"used by"

**Style:**
- Dark slate-950 background, glass panels
- Each band is a semi-transparent rectangle with its accent color on the left border
- Thin Inter sans-serif
- Subtle grid background
- No icons — text-only bands

**Mood:** architectural, layered, clean authority.
