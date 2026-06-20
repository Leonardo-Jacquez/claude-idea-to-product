# Build Solution Orchestrator

The main entry point for turning a business problem into an evaluated, production-ready solution.

## Operating Principles
- **One command, human at the gates.** Run internal builder/checker loops automatically; stop only at the four natural checkpoints for human direction.
- **Defensible from the outset.** Every phase output passes an adversarial gate before it is presented.
- **Everything is traceable.** Each run lives in `solutions/<slug>/` with a `manifest.yaml`, the phase artifacts, and an append-only `decisions.md`.

## Artifact Store (per run)
```
solutions/<slug>/
  manifest.yaml     # status, owner, decisions, artifact chain, checkpoints
  intake.md         # Phase 1 artifact
  architecture.md   # Phase 2 artifact
  build/            # Phase 3 outputs
  evaluation.md     # Phase 4 artifact
  handoff.md        # Phase 5 artifact
  decisions.md      # append-only decision log (audit trail)
```
Templates live in `templates/`; governance gates in `governance/`.

## The Builder → Checker → Gate Loop (every phase)
1. **Build** with the phase's builder skill, conforming to the phase template.
2. **Check** with the phase's adversarial-checker skill — run as an *independent* perspective (separate subagent), refute-by-default, classifying findings as **must-fix / should-fix / consider**.
3. **Gate:** revise until **zero open must-fix**. Only then present the artifact at the checkpoint.
4. **Log** the checkpoint decision + rationale in `decisions.md`; update `manifest.yaml`.

## Phases
1. **Intake** — `intake-builder` + `intake-adversarial-checker` → **Checkpoint 1**.
2. **Architecture** — `architecture-builder` + `architecture-adversarial-checker` → **Checkpoint 2**.
3. **Building** — break into components; per component run `build-builder` + `build-adversarial-checker`; progress updates → **Checkpoint 3**.
4. **Evaluation** — `evaluation-functional` + `evaluation-adversarial` against the rubric → **Checkpoint 4**.
5. **Final Handoff** — `handoff-packager`: package docs, run the **prod-ready checklist** + **security/governance checklist**, confirm named owner, deliver deployment guidance.

## Gates that block handoff (prod-ready = medium bar)
Documented · tested · deployable · security/governance reviewed · **named owner**. Any unchecked box blocks handoff (or requires a logged, accepted exception).

## Start
Ask the user to describe the business problem, then begin Phase 1.
