# Decision Log — Idea-to-Product Pipeline
*Append-only. Every checkpoint choice + rationale lands here. This is the audit trail.*

| # | Date | Checkpoint | Decision | Rationale | Decided by |
|---|------|-----------|----------|-----------|-----------|
| D1 | 2026-06-20 | CP1 Intake | **Success bar = consistent, defensible, business-aligned value with traceability**; adoption is a byproduct. | Builder+adversarial loops should make outputs defensible from the outset rather than relying on iterative v1 fixes. | User |
| D2 | 2026-06-20 | CP1 Intake | **"Production-ready" = documented + tested + deployable + security/governance reviewed + named owner** (medium bar). | Balances fast value delivery with baseline security/compliance/accountability without full enterprise monitoring. | User |
| D3 | 2026-06-20 | CP2 Arch | **Scope = full pipeline + ONE reference solution.** | Proves the method in practice while staying bounded; avoids abstract-only or autonomous-multi-solution extremes. | User |
| D4 | 2026-06-20 | CP2 Arch | **Approve architecture; design reference now, build it last.** | Locking the reference (dogfood) design early lets it shape the rubrics. | User |
| D5 | 2026-06-20 | CP2 Arch | **Reference solution = the pipeline dogfoods itself**, evaluated through its own Phase 4. | Maximum meta-proof, zero extra domain scope. | User |

| D6 | 2026-06-20 | CP3 Build | **Defer naming the owner** — carry as accepted open assumption. | User chose "decide later." Makes handoff CONDITIONAL with a logged exception rather than blocked. | User |
| D7 | 2026-06-20 | Handoff | **Owner may remain UNASSIGNED** (accepted exception, not just deferred). | User confirmed the conditional handoff is acceptable as-is. | User |
| D8 | 2026-06-20 | Handoff | **Timeline is CALCULATED, not set** — see `timeline-estimate.md`. | User: the orchestrated system should derive the timeline from its own effort/checkpoint model rather than asserting a date. | User |

## Resolved at handoff
- **Target timeline** — CALCULATED (D8): typical run ≈5 business days; conditional→production ≈1 business week. Review-latency-bound; tunable via `T_cp`.
- **Long-term owner** — UNASSIGNED, accepted exception (D6/D7).
