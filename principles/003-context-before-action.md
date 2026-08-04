# 003 — Context Before Action

## Statement

> Authentication identifies a principal. It does not, by itself, establish the context in which an action is allowed.

Before executing a protected action, the system must resolve the principal's relevant operating context.

## Failure

A system becomes unsafe when it assumes:

- a valid user can act in any tenant they can name;
- a role has the same meaning everywhere;
- membership implies every entitlement;
- a route-level permission guarantees row-level isolation;
- a tenant identifier supplied by the client is authoritative;
- identity alone answers “may this action happen here?”

These shortcuts create cross-tenant leakage and unauthorized business actions.

## Truth

Authorization is contextual.

A decision may depend on:

- the authenticated principal;
- the selected tenant or organization;
- active membership;
- role and delegated authority;
- product entitlement;
- route policy;
- resource ownership;
- time, state or commercial standing;
- the database isolation boundary.

The context must be resolved from authoritative sources, not trusted merely because the client supplied matching identifiers.

## Rule

Every protected request must resolve a principal context before business execution.

A principal context should be explicit enough to answer:

- Who is acting?
- For which tenant or organization?
- Through which membership?
- With which roles and entitlements?
- Against which route policy?
- Under which data-isolation boundary?
- What evidence explains the decision?

If required context cannot be resolved, deny the action.

## Example

A request targets:

`POST /v1/tenants/acme/resources`

The server should not authorize the request solely because the token is valid and the path contains `acme`.

It should:

1. authenticate the principal;
2. resolve `acme` to an authoritative tenant;
3. find an active membership connecting the principal to that tenant;
4. evaluate the required role and entitlement;
5. establish the tenant database context;
6. execute the command;
7. record the decision and relevant identifiers.

The tenant in the path is a request parameter, not proof of authority.

## Proof

Tests should demonstrate:

- valid principal, membership, role and entitlement → allowed;
- valid principal without membership → denied;
- membership with insufficient role → denied;
- correct role without entitlement → denied;
- tenant identifier tampering → denied;
- cross-tenant record access → impossible;
- decision evidence identifies the resolved context.

The proof must exercise the database boundary, not only mock an authorization service.

## Challenge

Resolving context on every request adds complexity and may add latency. Cache carefully, but do not allow cached convenience to become unbounded authority.

Performance is a design concern. Unresolved authority is a security failure.
