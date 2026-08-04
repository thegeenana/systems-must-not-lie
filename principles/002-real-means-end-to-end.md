# 002 — Real Means End to End

## Statement

> A feature is real when a stranger can complete a meaningful journey and the system produces an authoritative result without its creator narrating over the gaps.

Real does not mean polished, feature-complete or large. It means connected.

## Failure

Teams often call work complete when:

- the user interface is connected to mock data;
- an API works only through a developer's local setup;
- the happy path requires undocumented manual intervention;
- output disappears after restart;
- the demonstration avoids real authorization, persistence or integration;
- the creator must explain which visible failures should be ignored.

These may be useful intermediate states. They are not end-to-end proof.

## Truth

A meaningful journey crosses the boundaries that determine whether the product actually works.

Depending on the system, those boundaries may include:

- identity;
- authorization;
- business rules;
- persistence;
- external dependencies;
- restart behaviour;
- evidence presented back to the user.

## Rule

Define the smallest valuable journey, then connect every boundary required to make its result true.

Do not add more scope than that journey requires. Do not omit a boundary merely because it is difficult.

## Example

For a tenant-scoped resource API, a real journey is not simply a controller returning HTTP 200.

It should demonstrate that:

1. a principal is authenticated;
2. tenant membership is resolved;
3. authorization and entitlements are evaluated;
4. the command writes to durable storage;
5. another tenant cannot read the record;
6. the authorized tenant can retrieve it after restart;
7. the audit record explains the decision.

The user interface can still be plain. The journey is nevertheless real.

## Proof

A repeatable proof should:

1. start the documented runtime;
2. create or select test actors;
3. execute the meaningful action;
4. assert the authoritative result;
5. exercise at least one denied path;
6. restart the relevant process;
7. verify that truth survives;
8. exit non-zero when any assertion fails.

A stranger should be able to run the proof from the repository instructions.

## Challenge

End-to-end tests can become slow, brittle and too broad. The answer is not to abandon them. Keep the real journey small and support it with faster tests at lower levels.

Real proof is a thin vertical slice, not an attempt to test the entire universe.
