# Prompt — Architecture Diagram

**Target:** `docs/images/chevp-workflow-architecture.png`

**Aspect ratio:** 16:9 or 1280×720

**Purpose:** Comprehensive system illustration showing workspace orchestration, delegation, and the full stack.

---

## Prompt

Create a layered architecture diagram on a dark slate background.

**Top section — Workspace layer (`chevp-workflow`):**
- Three step badges horizontally: Discover, Coordinate, Execute
- Four gate diamonds between/around them: G0, G1, G2, G3
- A small box labeled "Workspace Plan (primary-owner repo)" positioned in the Coordinate column

**Middle section — Per-repo layer (`chevp-ai-framework`):**
- Three or four repo cards, each showing their own mini-lifecycle (Context → Exploration → Production)
- Thin vertical arrows from the Workspace Plan down to each repo card labeled "delegates work item"

**Bottom section — Tooling (`chevp-setup`):**
- Small strip at the very bottom with labels: clone, pull, status
- Horizontal arrow pointing up to show it provides the repos that the middle layer operates on

**Side annotations (right edge, small text):**
- "G0: workspace mode confirmed"
- "G1: impact map complete"
- "G2: plan approved"
- "G3: all repos verified"
- "Workspace G3 passes only when every per-repo G3 passes"

**Style:**
- Dark slate-950 background
- Glass panels with colored left borders (violet for workspace, blue for per-repo, slate for tooling)
- Inter sans-serif
- Subtle grid background
- Thin arrows in slate-600 with violet glow for delegation
- No icons of people, no photorealism

**Mood:** comprehensive, authoritative, clear structure at a glance.
