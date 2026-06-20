# Timeline Estimate — calculated, not set
*Phase 5 supplement · Derived from architecture §7 effort sizes + the checkpoint structure · 2026-06-20*

The orchestrated pipeline has the inputs to compute a timeline rather than assert one. This is a transparent, parameterized model — every constant is an assumption you can tune; the result recomputes from them.

## Model constants (assumptions — tunable)
| Symbol | Meaning | Default |
|---|---|---|
| `b(size)` | AI-assisted active build, wall-clock hours per phase by t-shirt size | S=0.5, SM=1.0, M=1.5, L=3.0 |
| `T_cp` | Human checkpoint turnaround (review + decide) | 1.0 business day |
| `N_cp` | Checkpoints per run | 4 |
| `H_day` | Working hours per day | 8 |

## Calculation 1 — typical run (problem → handoff)
Map each phase to its architecture §7 size, then sum.

| Phase | Size | `b(size)` (h) |
|---|---|---|
| Intake | SM | 1.0 |
| Architecture | M | 1.5 |
| Building | M | 1.5 |
| Evaluation | M | 1.5 |
| Handoff | S | 0.5 |
| **Active build** | | **Σ = 6.0 h ≈ 0.75 working day** |

`Wall_clock = active_build + N_cp · T_cp = 0.75d + 4·1.0d = 4.75 business days`

> **Result: a typical run takes ≈ 0.75 day of active AI work, spread across ≈ 5 business days of calendar time.**
> **Key finding: wall-clock is dominated by human checkpoint turnaround (4 of the ~4.75 days), not build effort.** To go faster, shorten `T_cp` (e.g., same-day reviews → ~2.5 days), not the build.

## Calculation 2 — conditional → full production (close the open conditions)
Remaining work = the three evaluation conditions (F1/F3/F2).

| Item | Active build | Gated on | Critical path? |
|---|---|---|---|
| Name owner (F1) | 0 h | 1 human decision (≈1 day) | No — parallelizable |
| Pilot run on a real, non-meta problem (F3) | = Calculation 1 ≈ 4.75 d | full run | **Yes** |
| Gate-attestation line (F2) | S = 0.5 h | folds into pilot | No |

Owner-naming and the attestation tweak run in parallel with the pilot, so the critical path is the pilot run itself.

> **Result: Conditional → Production ≈ 1 business week (~5 business days)**, critical path = one real pilot run. Naming the owner during that window flips the prod-ready gate to a clean PASS.

## Sensitivity
- Same-day checkpoint reviews (`T_cp = 0.5d`): typical run ≈ **2.75 days**; conditional→prod ≈ **~3 days**.
- Slow reviews (`T_cp = 2d`): typical run ≈ **8.75 days**; conditional→prod ≈ **~9 days**.

*The estimate is review-latency-bound. The single highest-leverage timeline lever is checkpoint turnaround, not engineering effort.*
