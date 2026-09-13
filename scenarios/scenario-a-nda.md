### Scenario A — Agent + NDA

| Field | Value |
|---|---|
| Declared effect | `recoverable_local` |
| Consequence tier | LOW |
| Observation layer | BOUND |
| Observation age (days) | 1 |
| Staleness policy (max age) | _30_ |

### A. Agent signs an NDA

**The case.** The agent drafts and e-signs a mutual NDA. The draft can be deleted within the counterparty's cooling window.

**What the model decides, and why.** The action is reversible and low-consequence, so the gate is SUPERVISED — a human on the loop, able to step in. The model sees a deletable draft. It is right about the draft.

**What it cannot see.** An NDA is a contract. The moment it is signed it creates a legal obligation, and the party to that obligation must be a person or a legal entity — never the agent. Deleting the file does not undo the fact that a commitment was made. This is not "the draft is hard to undo"; it is "the agent cannot be the one who is bound." That question — who is bound? — is the accountability axis, and it forces HUMAN_OWNS no matter how reversible the artefact is.

**The gap in one line.** The model grades the file; the obligation is invisible.

<details>
<summary>Evidence — decision record (reversibility==1.2.0)</summary>

```json
{
  "reversibility": "REVERSIBLE",
  "consequence": "LOW",
  "required_oversight": "SUPERVISED",
  "evidence_tier": "standard",
  "binding": "BOUND",
  "mode": "declaration+observation",
  "rationale": "reversibility=reversible, consequence=low, binding=bound, oversight is the worse of the two axes",
  "declared_effect": "recoverable_local"
}

