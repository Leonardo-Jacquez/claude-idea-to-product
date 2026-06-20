# Evaluation Rubric

Score each dimension 0–3. **Any dimension scoring 0 is a must-fix and blocks PASS.**

| Dimension | 0 (blocking) | 1 (weak) | 2 (adequate) | 3 (strong) |
|-----------|--------------|----------|--------------|------------|
| **Functional correctness** | Does not do the core job | Works only on narrow happy path | Handles main cases | Handles main + edge cases, verified |
| **Requirements coverage** | Misses primary outcome | Meets some success metrics | Meets all primary metrics | Meets all + measurable evidence |
| **Robustness** | Breaks on normal-ish input | Fragile to edge cases | Degrades gracefully | Resilient to hostile/edge input |
| **Security & governance** | Exposes secrets/data or no owner | Gaps in review | Reviewed, owner named | Reviewed + least-privilege + owner |
| **Tests / verification** | No tests | Happy-path only, no assertions | Meaningful tests for main paths | Tests incl. failure modes, reproducible |
| **Documentation** | None | Sparse | Run/deploy steps present | Complete: run, deploy, own, limits |
| **Traceability** | No link to intake | Partial | Artifact chain present | Full chain + decision log |
| **Maintainability** | Opaque / hidden coupling | Hard to change | Reasonably clear | Clear, conventions-matched, low coupling |

## Verdict rule
- **PASS:** no dimension at 0, security & tests both ≥ 2.
- **CONDITIONAL:** no 0s but one or more dimensions at 1 — list remediation.
- **FAIL:** any dimension at 0.
