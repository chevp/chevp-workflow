# Prompt — Lifecycle Diagram (Discover → Coordinate → Execute)

**Target:** `docs/images/chevp-workflow-lifecycle.png`

**Aspect ratio:** 16:9 or 680×320

**Purpose:** Show the 3 lifecycle steps and 4 quality gates.

---

## Prompt

Create a horizontal flow diagram with 3 step boxes and 4 gate markers.

**Flow (left to right):**

```
 [G0] → ( Discover ) → [G1] → ( Coordinate ) → [G2] → ( Execute ) → [G3]
```

**Step boxes:**
- **Discover** — violet `#8b5cf6`, subtitle "Impact map, primary owner"
- **Coordinate** — fuchsia `#d946ef`, subtitle "Workspace plan, commit sequence"
- **Execute** — emerald `#10b981`, subtitle "Orchestrated commits, pushes, PRs"

**Gate markers:**
- Small diamond shapes with labels G0, G1, G2, G3
- Each with a one-line criterion beneath (tiny text)
- G0: "workspace mode confirmed"
- G1: "impact map complete"
- G2: "plan approved"
- G3: "all repos verified"

**Style:**
- Dark slate-950 background
- Glass-panel step boxes with accent left-border
- Gate diamonds filled with the accent of the *following* step
- Inter sans-serif, thin weight
- Thin connecting lines (slate-600) with arrowheads

**Mood:** process, gated, calm authority.
