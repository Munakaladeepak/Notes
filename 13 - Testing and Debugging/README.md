# Testing and Debugging

**Priority:** High · **Prerequisite:** [[01 - Programming Logic/README|Programming Logic]] · **Related:** [[14 - Git/README|Git]], [[17 - Security/README|Security]]

## SDLC and quality

Requirements become design, implementation, tests, deployment, and maintenance. Agile delivers increments, but it does not mean “no documentation” or “no planning.” Quality includes correctness, security, performance, usability, reliability, and maintainability.

## Test levels

Unit tests isolate a function/class. Integration tests connect modules such as an API and database. System/end-to-end tests exercise complete flows. Regression tests protect existing behavior. Smoke tests quickly determine whether a build is usable. Acceptance tests confirm business expectations.

## Test design

Equivalence partitioning divides inputs into representative valid and invalid groups. Boundary-value analysis tests edges and just-inside/outside values. Decision tables test combinations of conditions. Property-based tests verify general rules over many generated inputs.

## Defects

A defect report contains title, environment, prerequisites, exact steps, input, expected result, actual result, evidence, severity, priority, and reproducibility. Severity is impact; priority is order of fixing. Root-cause analysis asks why the defect occurred, not merely where it surfaced.

## Debugging

Reproduce the problem, capture logs and stack traces, isolate the smallest failing unit, inspect inputs and state, form a hypothesis, change one thing, test the fix, and run regression tests. Use breakpoints, watch expressions, request traces, database query logs, and controlled test data. Avoid logging passwords, tokens, or personal data unnecessarily.

## Performance and reliability

Measure before optimizing. Look for slow queries, missing indexes, N+1 requests, blocking Node operations, large payloads, excessive React renders, memory leaks, and repeated network calls. Caching improves speed but creates invalidation and consistency concerns.

## Code review

Review behavior, security, tests, error handling, API compatibility, data integrity, performance, readability, and maintainability. Automated linting and tests support but do not replace human review.

## Checklist

- [ ] SDLC and Agile
- [ ] Unit, integration, system, E2E, regression, smoke, acceptance
- [ ] Equivalence partitions, boundaries, decision tables
- [ ] Defect severity, priority, reproducibility
- [ ] Debugging tools and root cause
- [ ] Performance bottlenecks and measurement
- [ ] Reliability and safe logging
- [ ] Code review criteria
