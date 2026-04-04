# Prompt — Impact Map Visual Example

**Target:** `docs/images/chevp-workflow-impact-map.png`

**Aspect ratio:** 4:3 or 680×520

**Purpose:** Example impact map showing a realistic cross-repo change (library + consumer + stub).

---

## Prompt

Create a node-graph diagram showing 4 repositories affected by a single workspace change.

**Nodes (each a labeled rounded rectangle):**
1. `lib-core` — role "library", files "src/api/*.ts"
2. `app-consumer-a` — role "consumer", files "src/integrations/*.ts"
3. `app-consumer-b` — role "consumer", files "src/integrations/*.ts"
4. `docs-site` — role "reference-stub", files "context/plans/*.md"

**Edges (directed arrows):**
- `lib-core → app-consumer-a` (depends-on, solid)
- `lib-core → app-consumer-b` (depends-on, solid)
- `lib-core → docs-site` (referenced-by, dashed)

**Primary-owner highlight:**
- `lib-core` has a thicker violet border (`#8b5cf6`) and a small crown/star badge
- Label: "primary-owner"

**Role color coding:**
- library: violet accent
- consumer: blue accent
- reference-stub: slate-500 accent

**Style:**
- Dark slate-950 background with subtle grid
- Nodes are glass panels with colored left border
- Edge labels in tiny Inter
- Dependency arrows slightly thicker than reference arrows
- No photorealism

**Mood:** clear, structural, one-glance understanding.
