# Claude Idea-to-Product

An AI system that turns business problems into valuable, evaluated solutions.

This repository contains a structured, checkpoint-driven orchestrator for Claude Code that guides the full journey from vague business idea to production-ready output. It is domain-agnostic — point it at any business problem.

## Vision

Reliably convert business problems into high-value AI solutions with clear outcomes, while maintaining human oversight at key decision points.

## Core Philosophy

- Rigorous upfront intake to prevent building the wrong thing
- Adversarial checking at critical stages (Intake, Architecture, Building, Evaluation)
- Natural checkpoints that emerge from the process
- Single-command experience with transparent progress

## Main Command

```bash
/build-solution
```

This is the primary entry point. It runs the full pipeline with built-in builder + adversarial checker loops and surfaces clean outputs at natural decision gates.

## Pipeline Overview

1. **Intake Phase** – Structured problem definition + adversarial review
2. **Architecture Phase** – Solution design + risk analysis
3. **Building Phase** – Iterative development with verification
4. **Evaluation Phase** – Functional + adversarial stress testing
5. **Final Handoff** – Documentation and deployment guidance

## Skills Included

### Discovery
- `discovery-multi-perspective`
- `discovery-adversarial-challenger`
- `discovery-synthesizer`

### Intake
- `intake-builder`
- `intake-adversarial-checker`

### Architecture
- `architecture-builder`
- `architecture-adversarial-checker`

### Building
- `build-builder`
- `build-adversarial-checker`

### Evaluation & Handoff
- `evaluation-functional`
- `evaluation-adversarial`
- `handoff-packager`

### Supporting Assets
- `templates/` — intake, architecture, evaluation rubric, manifest
- `governance/` — prod-ready & security/governance checklists
- `solutions/<slug>/` — per-run artifact store with traceability (`manifest.yaml`, `decisions.md`)

## How to Use

1. Clone or copy the `.claude/` folder into your project
2. Run `/build-solution` and describe the business problem
3. Review outputs at each natural checkpoint and provide direction

## What It Emphasizes

- Clear business value definition
- Risk management through adversarial review
- Human decision points at key stages
- Traceable reasoning

## Future Enhancements

- Packaging & deployment guidance
- Integration with external tools and data sources
- Template library for common business problem types

## License

MIT — see [LICENSE](LICENSE). Copyright (c) 2026 Leonardo Jacquez.

---

Built for Claude Code. Designed to deliver real business value reliably.