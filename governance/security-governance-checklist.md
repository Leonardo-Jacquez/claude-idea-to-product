# Security & Governance Checklist
*Completed during Phase 4 (Evaluation) and confirmed at Handoff.*

## Data & Secrets
- [ ] No secrets/credentials/API keys committed or hardcoded.
- [ ] Sensitive data handling is identified and appropriate.
- [ ] Outputs do not leak internal/confidential data unintentionally.

## Input / Output Safety
- [ ] Untrusted input is validated/sanitized.
- [ ] For AI components: prompt-injection and unsafe-output risks considered and mitigated.

## Access & Permissions
- [ ] Least-privilege: the solution can only access what it needs.
- [ ] No unintended write/delete/external-publish capability.

## Accountability
- [ ] Named owner assigned.
- [ ] Decision log (`decisions.md`) is complete and traceable.
- [ ] Compliance/legal/risk constraints from intake are satisfied.

## Result
- [ ] **PASS** — all items satisfied or exceptions logged & accepted.
