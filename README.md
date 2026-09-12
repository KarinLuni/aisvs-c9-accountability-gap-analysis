
<img width="838" height="319" alt="Снимок экрана 2026-09-12 в 21 03 26" src="https://github.com/user-attachments/assets/16485f0c-37c3-4918-b10a-8af3e3a222be" />

# Accountability Gap in AISVS C9.2.x

Empirical gap analysis of OWASP AISVS v1.0 Chapter C9 controls, 
demonstrating that the reversibility axis alone is insufficient 
for actions creating binding commitments.

## Context

This repository contains conformance test results against the 
reference model by Mayur Agnihotri (aisvs-c9-action-class-conformance), 
showing scenarios where `APPROVAL_REQUIRED` is insufficient and 
`HUMAN_OWNS` is required due to accountability constraints.

## Source

- Original paper:  DOI 10.5281/zenodo.22240230
- Reference model: https://github.com/Mayur021/aisvs-c9-action-class-conformance
- Standard: OWASP AISVS v1.0, Chapter C9 (Orchestration and Agentic Security)

## Key Finding

C9.2.x controls classify actions exclusively by reversibility. 
Actions that create legally binding commitments (NDA, chargeback, escrow) 
receive `APPROVAL_REQUIRED` despite the agent's inability to be the 
accountable subject of the commitment.

## Files

- `gap-analysis.md` — summary table with verdict comparison
- `scenarios/` — raw JSON decision records from the conformance lab
- `methodology.md` — reproduction instructions

## License

Apache-2.0


