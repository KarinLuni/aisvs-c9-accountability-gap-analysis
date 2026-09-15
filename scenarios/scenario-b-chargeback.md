### Scenario B — Agent + Chargeback

| Field | Value |
|---|---|
| Declared effect | `externally_recoverable` |
| Consequence tier | HIGH |
| Observation layer | BOUND |
| Observation age (days) | 1 |
| Staleness policy (max age) | _30_ |

### B. Agent files a chargeback
**The case.** The agent files a chargeback representment — a formal statement to the bank disputing a transaction, committing the institution to a position.

**What the model decides, and why.** The payment can be reversed through the card network (externally reversible) and the stakes are high, so the gate is APPROVAL_REQUIRED — a human clicks "yes," then the agent files. The model is right that the transaction can be walked back.

**What it cannot see.** APPROVAL_REQUIRED answers "may this be done?" It does not answer "who is the declarant?" The representment binds the institution to a factual and legal claim. A human approving the send does not make the agent the author of a legal declaration — someone must be accountable for its content, and that someone cannot be the agent. Approval settles authorization; it leaves delegability untouched.

**The gap in one line.** A human pressed yes, but the declaration still has no accountable subject.

<details>
<summary>Evidence — decision record (aisvs-c9-action-class-conformance v1.2.0)</summary>

```json
{
  "reversibility": "EXTERNALLY_REVERSIBLE",
  "consequence": "HIGH",
  "required_oversight": "APPROVAL_REQUIRED",
  "evidence_tier": "enhanced",
  "binding": "BOUND",
  "mode": "declaration+observation",
  "rationale": "reversibility=externally_reversible, consequence=high, binding=bound, oversight is the worse of the two axes",
  "declared_effect": "externally_recoverable"
}
