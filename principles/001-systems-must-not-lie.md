# 001 — Systems Must Not Lie

## Statement

> A system must not claim more than it can prove.

A system lies when its external claim is stronger than its authoritative state. The lie may be accidental, temporary or convenient, but the effect is the same: a person or another system makes a decision using information that is not true.

## Failure

Common examples include:

- returning success before durable work has completed;
- displaying a payment as settled when it is only initiated;
- rebuilding authoritative history from a lossy projection;
- reporting an action as authorized without recording the decision context;
- calling a mocked or narrated journey production-ready;
- hiding uncertainty behind a single confident status.

The problem is not imperfect software. All systems fail. The problem is representing uncertainty, partial completion or failure as something stronger.

## Truth

Every meaningful external claim must be traceable to authoritative evidence.

That evidence must be appropriate to the strength of the claim. A health endpoint can prove that a process responds; it cannot prove that a customer journey works. A unit test can prove a rule in isolation; it cannot prove that production dependencies are correctly connected.

## Rule

For every business-significant claim:

1. Define the authoritative source.
2. Define the transition that makes the claim true.
3. Persist enough lineage to explain the transition.
4. Represent intermediate and uncertain states explicitly.
5. Provide evidence at the same level as the claim.

## Example

A billing system receives a usage event.

A dishonest implementation may return `BILLED` after placing the event on a queue.

An honest implementation distinguishes:

- `ACCEPTED` — the event passed admission and was durably recorded;
- `RATED` — a pricing decision produced an amount;
- `INVOICED` — the rated amount was assigned to an invoice;
- `SETTLED` — payment reached the defined settlement state.

Each state is supported by its own authoritative record and lineage to the previous state.

## Proof

Evidence should include:

- a real request and response;
- the durable authoritative record;
- identifiers connecting the request, decision and outcome;
- duplicate replay behaviour;
- failure behaviour;
- verification after process restart.

A screenshot alone is not proof of system truth.

## Challenge

Absolute certainty is rarely possible in distributed systems. This principle does not require pretending otherwise. It requires the system to model what it knows, what it does not know and what remains in progress.

Honesty includes explicit uncertainty.
