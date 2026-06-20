# Production-Ready Checklist (gate)
*Definition (locked): documented + tested + deployable + security/governance reviewed + named owner.*
*Every box must be checked, or carry a logged, accepted exception in `decisions.md`. An unchecked box blocks handoff.*

## Documented
- [ ] What it is and the problem it solves is written down.
- [ ] Run/use instructions are complete and accurate.
- [ ] Deploy steps + prerequisites are listed.
- [ ] Known limitations and assumptions are stated.

## Tested
- [ ] Meaningful tests/verification exist (not happy-path-only).
- [ ] Failure modes are exercised.
- [ ] Verification is reproducible by someone else.

## Deployable
- [ ] Runs from a clean state following the documented steps.
- [ ] Configuration/secrets are externalized (none hardcoded).

## Security & Governance Reviewed
- [ ] `governance/security-governance-checklist.md` completed and passed.

## Named Owner
- [ ] An owner is named in `manifest.yaml` (not UNASSIGNED).

---
**Gate result:** PASS only when all boxes are checked or exceptions are logged and accepted.
