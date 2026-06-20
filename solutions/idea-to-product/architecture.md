# Solution Architecture — Idea-to-Product Pipeline
*Phase 2 artifact · Gate: PASSED (0 open must-fix) · Checkpoint 2 approved 2026-06-20*

## 1. High-Level Approach
A **file-based, checkpoint-gated pipeline** living entirely inside Claude Code. One orchestrator command (`/build-solution`) drives five phases. Each phase runs a **Builder → Adversarial Checker → Gate** micro-loop, persists a versioned artifact to `solutions/<slug>/`, and stops at a human checkpoint. The same machinery is dogfooded to build the reference solution (this pipeline itself).

## 2. Key Components
| # | Component | Purpose |
|---|-----------|---------|
| C1 | Orchestrator (`/build-solution`) | Drives phases, enforces gates, wires artifacts, maintains traceability. |
| C2 | Phase skill pairs (Builder + Adversarial Checker) | Intake, Architecture, Build, Evaluation. |
| C3 | Artifact store `solutions/<slug>/` | Versioned markdown artifacts + `manifest.yaml`; git = traceability. |
| C4 | Rubrics & templates library | Section templates + scored rubrics (functional, adversarial, security/governance, prod-ready checklist). |
| C5 | Governance layer | Named-owner field, security checklist, `decisions.md` log. |
| C6 | Reference solution | The pipeline itself, evaluated through its own Phase 4 (dogfood). |

## 3. Technology Recommendations
Claude Code skills (markdown) + slash command orchestrator; Claude Opus 4.8 for builder/checker reasoning; Agent/subagents for independent builder vs checker perspectives; git for persistence + traceability; Task tool for progress.

## 4. Scope & Phasing
In scope (v1): pipeline core, four builder/checker pairs, rubrics/templates, governance, one reference solution.
Out of scope (v1): runtime monitoring/alerting, multiple live domain solutions, internal-data integrations.
Build sequence: **3a** core+artifact store → **3b** skill pairs+rubrics → **3c** governance+prod-ready gate → **3d** dogfood reference (designed now, run in Phase 4).

## 5. Success / Loss Functions
**Success:** each artifact passes its adversarial gate with zero open must-fix, conforms to template, is logged in `decisions.md`; reference reaches prod-ready bar; traceability chain intact.
**Loss:** checkpoint skipped, must-fix waived without logged rationale, missing owner, no tests, or absent security review.

## 6. Risks & Mitigations
Adoption (behavioral) → frictionless one-command UX + reference proof + templates. "Production-ready" vague → hard prod-ready checklist gate. Scope creep → one reference only. Meta-risk → dogfood via Phase 4. Checker not independent → separate subagent + refute-by-default. No live monitoring → accepted at medium bar; future enhancement.

## 7. Estimated Effort & Dependencies
3a small/med · 3b medium (bulk) · 3c small · 3d medium (depends on 3a–3c). No external dependencies. Decision dependencies resolved: reference = dogfood; owner/timeline carried as open assumptions.

---
### Adversarial review summary
Strengths: constraints honored, quality bar codified, traceability free via git, dogfooding credible. Key risk: checker independence + rubric quality are the linchpins (mitigated in 3b). Recommendation: **proceed to build.**
