## Test Results: Mayur's Reference Model vs Accountability Axis

| ID | Scenario | Input (Declared effect + Consequence + Binding) | AISVS C9 Verdict | Accountability Verdict | Match | Rationale |
|---|---|---|---|---|---|---|
| A | Agent signs NDA | recoverable_local + LOW + BOUND | SUPERVISED | **HUMAN_OWNS** | ❌ | NDA creates legally binding commitment; agent cannot be contractual party |
| B | Chargeback request | externally_recoverable + HIGH + BOUND | APPROVAL_REQUIRED | **HUMAN_OWNS** | ❌ | Chargeback is a legal declaration; agent cannot bear liability for its content |
| D | Stale API (read_only) | read_only + LOW + STALE | HUMAN_OWNS | **HUMAN_OWNS** | ✅ | Same verdict, different rationale: Mayur (fail closed), Accountability (unknown capability requires human verification) |
| E | Escrow creation | externally_recoverable + HIGH + BOUND | APPROVAL_REQUIRED | **HUMAN_OWNS** | ❌ | Escrow creates fiduciary obligation; agent cannot be escrow agent |
| C | Chain: balance → validation → payment | mixed chain + HIGH | APPROVAL_REQUIRED | **HUMAN_OWNS** | ❌ | Chain culminates in commitment; worst-case rule only folds reversibility, not accountability |

## Chain-Level Impact

Under C9.2.10, the worst-case rule folds the chain at the highest reversibility class. 
If a chain step creates a binding commitment (accountability class = human_only), 
the oversight level should escalate to `HUMAN_OWNS` regardless of reversibility.

## Proposed Addition

Introduce accountability classification (`α`) orthogonal to reversibility (`κ`):

- `α = delegable` — agent may execute after approval
- `α = human_only` — agent cannot be the accountable subject; human must own the action

This maps to the plan-time framing proposed in Lunina, K. (2026). Authorization Is the Boundary. Zenodo. https://doi.org/10.5281/zenodo.22240230.
