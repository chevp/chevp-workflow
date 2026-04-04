# Integration — Framework Composition

How `chevp-workflow` composes with `chevp-ai-framework` and domain/project frameworks.

## Layer diagram

```
┌─────────────────────────────────────────────────────────┐
│  chevp-workflow                (workspace, cross-repo)  │
│  Steps: Discover → Coordinate → Execute                 │
│  Gates: G0 → G1 → G2 → G3                               │
└─────────────────────────────────────────────────────────┘
                         │ delegates per-repo work to
                         ▼
┌─────────────────────────────────────────────────────────┐
│  chevp-ai-framework            (per-repo lifecycle)     │
│  Steps: Context → Exploration → Production              │
│  Gates: G1 → G2 → G3                                    │
└─────────────────────────────────────────────────────────┘
                         │ extended by (optional)
                         ▼
┌─────────────────────────────────────────────────────────┐
│  domain-ai-framework           (domain-specific rules)  │
└─────────────────────────────────────────────────────────┘
                         │ used by
                         ▼
┌─────────────────────────────────────────────────────────┐
│  project frameworks            (e.g. nuna-ai-framework) │
└─────────────────────────────────────────────────────────┘
```

## Responsibility split

| Concern | Workspace | Per-Repo |
|:--------|:---------:|:--------:|
| Cross-repo impact map | ✅ | — |
| Commit sequence across repos | ✅ | — |
| Primary-owner assignment | ✅ | — |
| Reference stubs | ✅ | — |
| Single-repo context/spec/plan | — | ✅ |
| Single-repo ADRs | — | ✅ |
| Actual code changes | — | ✅ |
| Per-repo acceptance criteria | — | ✅ |
| Per-repo build/test verification | — | ✅ |

## Transition rules

- **Workspace G0** triggered → workspace mode is active, per-repo mode is suspended for orchestration concerns.
- **Workspace G2** passed → per-repo work items delegated. Each repo's chevp-ai-framework cycle now runs.
- **Workspace G3** can only pass once every per-repo G3 has passed.

## Do not

- Do not duplicate workspace-plan content into per-repo plans. Reference it.
- Do not let per-repo plans expand workspace scope. Escalate back up.
- Do not run chevp-workflow for single-repo work. It adds cost without benefit.
