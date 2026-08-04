# ADR-NNN — Decision title

- **Status:** Proposed
- **Date:** YYYY-MM-DD
- **Decision owners:** Names or roles
- **Related principles:** Links to applicable principles
- **Related issues:** Links

## Context

Describe the situation that requires a decision.

Include:

- the business or user outcome;
- relevant constraints;
- authoritative sources and boundaries;
- current behaviour;
- the failure or risk being addressed;
- what must remain true after the decision.

Avoid presenting a preferred solution as though it were context.

## Decision drivers

List the forces that materially affect the choice.

Examples:

- correctness;
- security and privacy;
- operability;
- latency;
- recoverability;
- delivery cost;
- reversibility;
- regulatory or contractual obligations.

## Considered options

### Option A — Name

Explain the approach, strengths, weaknesses and evidence.

### Option B — Name

Explain the approach, strengths, weaknesses and evidence.

### Option C — Name

Explain the approach, strengths, weaknesses and evidence.

## Decision

State the selected option and why it best satisfies the decision drivers.

Be explicit about what is in scope and out of scope.

## Truth preserved

State the invariant or external promise this decision protects.

> After this decision, the system must always...

## Consequences

### Positive

- Consequence.

### Negative

- Consequence.

### Risks

- Risk and mitigation.

## Proof obligations

Define evidence required before this decision can be considered implemented.

- [ ] Automated tests cover the invariant.
- [ ] A meaningful allowed journey passes.
- [ ] Relevant denied or failure journeys pass.
- [ ] Authoritative state can be inspected.
- [ ] Restart or recovery behaviour is verified where applicable.
- [ ] Documentation matches runtime behaviour.

## Reversal and review

Explain how the decision could be reversed and what evidence would trigger reconsideration.

## Notes

Record later clarifications without rewriting the historical decision.
