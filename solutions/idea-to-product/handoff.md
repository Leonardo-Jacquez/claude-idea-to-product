# Handoff — Idea-to-Product Pipeline
*Phase 5 artifact · Status: CONDITIONAL / pilot-ready · 2026-06-20*

## 1. What This Is
A checkpoint-driven Claude Code system that turns a business problem into an evaluated, production-ready AI solution. One command (`/build-solution`) drives five phases — Intake → Architecture → Building → Evaluation → Handoff — each running an internal Builder → Adversarial Checker → Gate loop and stopping at a human checkpoint. It was built and proven by dogfooding: this system was created through its own pipeline.

## 2. How to Run / Deploy
**Prerequisites:** Claude Code with this repo's `.claude/` folder present. No external infra.
**To use on a new problem:**
1. Run `/build-solution`.
2. Describe the business problem when prompted.
3. Review and give direction at each of the 4 checkpoints.
4. The run is persisted under `solutions/<slug>/` (artifacts + `manifest.yaml` + `decisions.md`).
**To deploy the system to another project:** copy the `.claude/`, `templates/`, and `governance/` folders into the target repo. Start a fresh `solutions/<slug>/` per problem from `templates/manifest-template.yaml`.

## 3. Prod-Ready Checklist Result (gate)
| Item | Status |
|---|---|
| Documented | ✅ README, orchestrator, 11 skills, templates |
| Tested / verified | ✅ End-to-end dogfood run + structural verification (failure-mode tests: deferred, see F2/F4) |
| Deployable | ✅ Copy 3 folders; runs from clean state |
| Security & governance reviewed | ✅ Checklist passed (markdown system; no secrets/unsafe capability) |
| **Named owner** | ❌ **UNASSIGNED — accepted exception (D6)** |

**Gate result: CONDITIONAL PASS** — all boxes green except a named owner, which is a logged, user-accepted exception (D6). Naming an owner flips this to a full PASS.

## 4. Ownership & Support
- **Owner:** UNASSIGNED (deferred per D6). **Resolve before company-wide scale.**
- **Artifacts live in:** this repo — `.claude/` (logic), `templates/` + `governance/` (gates), `solutions/<slug>/` (runs).
- **Report issues:** via the repo; every decision is traceable in `decisions.md`.
- **Known limitations:** gate enforcement is advisory not mechanical (F2); consistency proven by one self-referential run (F3); AI-specific risks of *built* solutions untested (F4).

## 5. Traceability Index
Problem → [intake.md](intake.md) → [architecture.md](architecture.md) → build (`.claude/` + `templates/` + `governance/`) → [evaluation.md](evaluation.md) → handoff (this file). Decisions: [decisions.md](decisions.md) (D1–D6). State: [manifest.yaml](manifest.yaml).

## 6. Future Enhancements (recommended order)
1. **Name the owner** (resolves F1 → clean prod-ready PASS).
2. **Run the pipeline on one real, non-meta problem** (resolves F3 — second proof before scale).
3. **Add per-checkpoint gate-attestation** line to `decisions.md` (mitigates F2).
4. Set a target timeline/milestone (open assumption).
5. Later (enterprise bar): runtime monitoring, template library for common problem types, internal-data integrations.

**Recommended next step:** assign an owner and run one real-domain problem through `/build-solution` as the pilot.
