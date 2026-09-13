### Scenario D — Read-only call with a stale declaration (control case)

| Field | Value |
|---|---|
| Declared effect | `read_only` |
| Consequence tier | LOW |
| Observation layer | STALE |
| Observation age (days) |  |
| Staleness policy (max age) |  |

### D. Read-only call with a stale declaration — control case

**The case.** The agent makes a read-only API call, but the effect declaration is stale — classified against an older version of the endpoint.

**What the model decides, and why.** Binding is STALE, so the model fails closed: it treats the action as irreversible and gates it HUMAN_OWNS. Correct behaviour — when you cannot trust the label, assume the worst.

**Why this case is here.** The verdict matches the accountability verdict — both say HUMAN_OWNS — but for a completely different reason. The model escalates because it doesn't know (staleness). The accountability axis is not even engaged here; this is a fourth concern, currency — whether the justification is still true at the moment of action. This case is the control that proves the method honest: matching verdicts do not mean the dimension is covered. If we counted D as support for the accountability axis, we would be overclaiming.

**The gap in one line.** Right answer, wrong reason — which is why it proves nothing about accountability, and says so.

<details>
<summary>Evidence — decision record (reversibility==1.2.0)</summary>

```json
{
  "reversibility": "IRREVERSIBLE",
  "consequence": "LOW",
  "required_oversight": "HUMAN_OWNS",
  "evidence_tier": "highest",
  "binding": "STALE",
  "mode": "declaration+observation",
  "rationale": "declaration not usable: binding=stale, failed closed to irreversible",
  "declared_effect": "read_only"
}
```

</details>
