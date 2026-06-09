# Usage examples — OntoRamp Decision Intelligence

Once connected (see [`../llms-install.md`](../llms-install.md)), an agent can call these tools. Inputs are realistic; outputs are described conceptually (your organization's real authority graph determines the response).

## `find_decision_precedent` *(Free)*

Before making a call, look up what's been decided before.

```jsonc
{ "name": "find_decision_precedent", "arguments": {
  "topic": "Choosing a vendor for customer-data storage"
}}
```

Returns prior decisions relevant to the topic — what was decided, by whom, and the context — so an agent doesn't re-litigate settled matters.

## `log_decision` *(Developer — write, auth required)*

Record a consequential decision so it becomes part of the auditable trail.

```jsonc
{ "name": "log_decision", "arguments": {
  "decision": "Adopt Postgres (not DynamoDB) for the billing service",
  "rationale": "Relational integrity + existing ops expertise",
  "authority": "Platform architecture review"
}}
```

Returns a confirmation with the logged decision's identity. Each logged decision pre-seeds your governance graph.

## `evaluate_decision` *(Developer)*

Check a proposed decision against authority and precedent before committing.

```jsonc
{ "name": "evaluate_decision", "arguments": {
  "decision": "Grant the data-science team write access to production"
}}
```

Returns an evaluation: authority gaps, precedent conflicts, and governance-alignment signals — so the agent knows whether to proceed, adjust, or escalate.

## `request_assessment` *(all tiers, rate-limit exempt)*

```jsonc
{ "name": "request_assessment", "arguments": {
  "context": "Assessing decision governance for our platform org"
}}
```

Returns a confirmation; the OntoRamp team follows up.

---

**Tiers at a glance:** Free → `find_decision_precedent` (read) + `request_assessment`, 20/mo. Developer → `log_decision` + `evaluate_decision` (write-path, auth). Get a free key at [ontoramp.com/mcp](https://ontoramp.com/mcp).
