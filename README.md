# Systems Must Not Lie

**Engineering principles, architecture decisions and practical lessons for building systems that tell the truth.**

Software can be technically available and still be dishonest.

It can report success before work is complete, reconstruct history from convenient projections, authorize an identity without resolving its operating context, or pass a demonstration that would not survive a restart. These failures are not merely implementation defects. They are violations of the promises the system makes to people and businesses.

This repository develops a practical engineering doctrine:

> **A system must not claim more than it can prove.**

The purpose is not to prescribe one architecture or technology. It is to make important engineering decisions explicit, testable and open to challenge.

## The standard

A principle belongs here only when it can answer five questions:

1. What failure are we trying to prevent?
2. What truth must the system preserve?
3. What engineering rule follows from that truth?
4. How would the rule change an implementation?
5. What evidence would prove the system complies?

## Foundational principles

| # | Principle | Central question |
|---|---|---|
| [001](principles/001-systems-must-not-lie.md) | Systems must not lie | Can the system prove what it claims? |
| [002](principles/002-real-means-end-to-end.md) | Real means end to end | Can a stranger complete the journey without narration? |
| [003](principles/003-context-before-action.md) | Context before action | In whose authority and operating context is this action allowed? |

## How to read this repository

Each principle uses the same structure:

- **Failure** — the behaviour that creates a false or unsafe system.
- **Truth** — the invariant that must remain honest.
- **Rule** — the engineering constraint derived from that invariant.
- **Example** — how the rule affects a real design.
- **Proof** — evidence that can be executed, inspected or independently verified.
- **Challenge** — limits and trade-offs that prevent doctrine becoming dogma.

Architecture decisions can be recorded with the [ADR template](decisions/ADR-000-template.md).

## Repository map

~~~text
systems-must-not-lie/
├── principles/     # Engineering doctrine expressed as testable rules
├── decisions/      # Architecture decision records and template
├── case-studies/   # Sanitized examples connecting principles to practice
└── CONTRIBUTING.md # How to challenge or extend the work
~~~

## What this is not

This is not:

- a collection of inspirational slogans;
- a substitute for measurement, testing or operational evidence;
- a claim that one architecture fits every system;
- a publication of private product code or customer information;
- a finished body of knowledge.

The doctrine should evolve when evidence exposes a weakness.

## Author

I am [George Wiafe](https://github.com/thegeenana), a Product & Solutions Architect and engineering craftsman with nearly three decades of experience designing, building and delivering software.

My current work explores commercial runtimes, multi-tenant platforms, commerce, production certification and responsible AI-assisted engineering.

## Roadmap

The next principles will examine:

- lineage before projection;
- idempotency as a business rule;
- isolation as an invariant;
- restart-safe truth;
- proof before polish;
- observability without theatre.

Contributions and thoughtful challenges are welcome. Start with [CONTRIBUTING.md](CONTRIBUTING.md).

---

**Build no more than the truth requires, and no less than the truth demands.**
