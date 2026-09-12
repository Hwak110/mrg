# Repository instructions for GitHub Copilot

## How to work in this repository

- Before changing code, inspect the existing structure, naming, dependencies, tests, and build commands.
- Read `ARCHITECTURE.md` before changing workflow boundaries, agent responsibilities, state transitions, or quality gates. Update it in the same change when those contracts change.
- Prefer the smallest coherent change that solves the request. Preserve existing public APIs unless the task explicitly requires a breaking change.
- Explain the plan briefly before implementing a non-trivial change, then implement it and run the most relevant checks.
- Do not claim a check passed unless it was actually run. Report skipped checks and the reason.

## Design and maintainability

- Keep business rules in focused domain/application services; keep controllers, handlers, and adapters thin.
- Use guard clauses and small private helpers to reduce nesting. Target a maximum nesting depth of two levels.
- Keep methods focused. When a method grows beyond roughly 25 lines of meaningful logic, split it around a clear responsibility instead of splitting mechanically.
- Avoid long `switch` statements and chains of four or more conditional branches in core business flows. Use a Strategy plus a registry or factory when behavior varies by type, channel, or state.
- Introduce an interface at a real substitution boundary (for example, an external provider, persistence adapter, or policy), not for every class by default.
- Do not add speculative abstractions, frameworks, or dependencies.
- Replace magic values with named constants, enums, value objects, or configuration. Keep secrets and environment-specific values out of source control.

## Correctness, security, and concurrency

- Validate untrusted input at the boundary and return actionable errors without exposing secrets or internal stack traces.
- For state changes involving money, inventory, quotas, redemption, or other concurrent resources, identify the transaction boundary and enforce atomicity with the project’s database transaction/locking facilities. Do not rely on an in-memory check alone.
- Make retry behavior and idempotency explicit for operations that can be delivered more than once.
- Use parameterized queries and established authentication/authorization middleware. Never log credentials, tokens, or personal data unnecessarily.

## Tests and documentation

- Add or update focused tests for changed behavior, especially boundary cases and failure paths.
- Follow the repository’s existing test style and naming conventions.
- Update documentation and examples when behavior, configuration, or public interfaces change.

## Response format

- Summarize what changed and why.
- List validation commands and their results.
- Call out assumptions, limitations, and any follow-up work that remains.
