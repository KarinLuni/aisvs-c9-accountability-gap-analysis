## Scenario A — Agent signs an NDA

The honest classification of signing an NDA is `recoverable_local` (the draft can be
deleted) + `LOW` (no financial exposure). The obligation it creates — a party bound to
a contract — is on neither axis.

Walking only the consequence tier on the same reversible action, binding BOUND:

| Consequence | required_oversight |
|---|---|
| LOW | SUPERVISED |
| MEDIUM | SUPERVISED |
| HIGH | APPROVAL_REQUIRED |
| CRITICAL | HUMAN_OWNS |

`HUMAN_OWNS` appears only at `CRITICAL`. An NDA signature is not a catastrophe, so the
only way to make the gate return `HUMAN_OWNS` is to misdeclare its blast radius. The
gate reaches the right answer through a wrong input.

<details><summary>Evidence — LOW (honest classification)</summary>

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
```
</details>

<details><summary>Evidence — MEDIUM</summary>

```json
{
  "reversibility": "REVERSIBLE",
  "consequence": "MEDIUM",
  "required_oversight": "SUPERVISED",
  "evidence_tier": "standard",
  "binding": "BOUND",
  "mode": "declaration+observation",
  "rationale": "reversibility=reversible, consequence=medium, binding=bound, oversight is the worse of the two axes",
  "declared_effect": "recoverable_local"
}
```
</details>

<details><summary>Evidence — HIGH</summary>

```json
{
  "reversibility": "REVERSIBLE",
  "consequence": "HIGH",
  "required_oversight": "APPROVAL_REQUIRED",
  "evidence_tier": "enhanced",
  "binding": "BOUND",
  "mode": "declaration+observation",
  "rationale": "reversibility=reversible, consequence=high, binding=bound, oversight is the worse of the two axes",
  "declared_effect": "recoverable_local"
}
```
</details>

<details><summary>Evidence — CRITICAL (only path to HUMAN_OWNS; false about the action)</summary>

```json
{
  "reversibility": "REVERSIBLE",
  "consequence": "CRITICAL",
  "required_oversight": "HUMAN_OWNS",
  "evidence_tier": "highest",
  "binding": "BOUND",
  "mode": "declaration+observation",
  "rationale": "reversibility=reversible, consequence=critical, binding=bound, oversight is the worse of the two axes",
  "declared_effect": "recoverable_local"
}
```
</details>

The accountability verdict for the honest LOW row is `HUMAN_OWNS`: an agent cannot be a
party to a contract. The gate's honest-input verdict is `SUPERVISED`. They diverge — and
the only input that closes the divergence is a false one.
