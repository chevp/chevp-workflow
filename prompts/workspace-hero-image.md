# Prompt — Workspace Hero Image (chevp-ai-framework style)

**Target:** `docs/images/chevp-workflow-hero.png`

**Aspect ratio:** 16:9 (1920×1080 recommended, usable down to 680×380)

**Purpose:** Hero diagram for the chevp-workflow landing page, matching the visual language of https://chevp.github.io/chevp-ai-framework/ so both frameworks read as a single family.

---

## Prompt

Create a minimal, dark-themed technical illustration that depicts a **workspace-level orchestration layer sitting above multiple independent git repositories**, rendered in the same visual language as the chevp-ai-framework hero: arctic palette, glassmorphism panels, thin Inter typography, subtle blue grid background, gated horizontal flow.

### Composition (two stacked bands)

**Top band — Workspace orchestration layer:**
- A single wide glass-panel rectangle spanning the full width
- Label inside: **"chevp-workflow · workspace orchestration"** (thin Inter, tracking-wide)
- Left-border accent stripe in violet-to-fuchsia gradient
- Subtle inner glow

**Middle band — Lifecycle flow (left → right):**
- Three step-boxes connected by thin arrowed lines, interleaved with four small diamond gate markers:

```
 [G0] ◇ → ( 1. Discover ) → ◇ [G1] → ( 2. Coordinate ) → ◇ [G2] → ( 3. Execute ) → ◇ [G3]
```

- **Discover** — icon: magnifier over stacked repos; accent violet `#8b5cf6`; subtitle "Impact map · Primary owner"
- **Coordinate** — icon: nodes on a timeline; accent fuchsia `#d946ef`; subtitle "Workspace plan · Commit sequence"
- **Execute** — icon: orchestrated arrows pushing to repos; accent emerald `#10b981`; subtitle "Atomic commits · Linked PRs"
- Gate diamonds are small, filled with the accent colour of the *following* step, outlined slate-400

**Bottom band — Target repositories:**
- Row of 4–5 small slate-800 repo-card icons (rounded squares with a `git` glyph), labeled `repo-a`, `repo-b`, `repo-c`, `repo-d`
- Thin vertical dotted lines connect each repo up to the Execute step, suggesting orchestrated delivery
- One repo card highlighted with a thicker violet-500 border and a small "primary owner" tag

### Color palette (arctic + workflow accents)

- Background: slate-950 `#020617` with a 20px blue grid `#1e3a8a` at ~8% opacity
- Glass panels: `rgba(15,23,42,0.6)` with 12px backdrop blur, slate-700 1px border
- Primary gradient (workspace band): violet `#a78bfa` → fuchsia `#d946ef`
- Step accents: violet `#8b5cf6`, fuchsia `#d946ef`, emerald `#10b981`
- Connecting lines: slate-600 `#475569`, 1.5px, with arrowheads
- Text: slate-300 `#cbd5e1` for labels, slate-500 `#64748b` for subtitles

### Typography

- Inter (or similar geometric sans), thin/regular weights only
- Labels uppercase tracking-wide for band titles
- Mixed-case regular for step names and subtitles

### Mood

Structural, calm, governed, orchestration-first. Reads as a sibling to chevp-ai-framework's hero — same arctic family, distinguishable by the violet/fuchsia workflow accent.

### Constraints

- No photorealism, no people, no code snippets in the image
- No 3D perspective — flat, diagrammatic, 2D
- No decorative flourishes that obscure the flow
