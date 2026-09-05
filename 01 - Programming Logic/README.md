# Programming Logic

**Priority:** High · **Prerequisite:** None · **Next:** [[02 - OOP/README|OOP]]

## Why this matters in technical MCQs

Complex questions often hide simple logic inside a business story. Translate the story into inputs, conditions, state changes, loops, and output. For example, “show active CRM contacts whose last interaction is within 30 days” means filter records, compare dates, and count or display matches.

## Control flow and tracing

An `if/else` chooses a branch. Nested conditions require checking the outer condition first. A loop has initialization, a condition, an update, and a body. An off-by-one error happens when a loop starts or stops one position too early or late. A dry run table with columns for variables, iteration, and output is the safest way to solve output questions.

Short-circuit evaluation matters. In `A && B`, if `A` is false, `B` may not run. In `A || B`, if `A` is true, `B` may not run. This affects both performance and whether a null-sensitive expression is evaluated.

## Functions and recursion

A function should have a clear contract: accepted inputs, assumptions, output, and side effects. A recursive function calls itself and must have a base case. Without a base case, it can cause stack overflow. Recursion uses call-stack memory; iteration often uses less stack memory.

## Data structures

Arrays provide indexed access. Linked lists connect nodes through references. A stack is LIFO and supports push/pop. A queue is FIFO and supports enqueue/dequeue. A hash map uses a hash function to locate key-value entries; collisions require handling. A tree organizes values hierarchically; a binary search tree can be efficient when balanced.

## Algorithms

Linear search checks items one by one. Binary search requires sorted data and repeatedly halves the search range. Stable sorting preserves the relative order of equal items. Know the idea behind bubble, selection, insertion, merge, and quick sort, but prioritize complexity and use cases.

| Algorithm or operation | Typical complexity | Important condition |
|---|---:|---|
| Array index access | O(1) | Known index |
| Linear search | O(n) | Works on unsorted data |
| Binary search | O(log n) | Data must be sorted |
| Hash lookup average | O(1) | Good hash distribution |
| Nested full loops | O(n²) | Each item compared with many others |
| Merge sort | O(n log n) | Uses additional memory |

## Complexity traps

Big-O describes growth, not exact seconds. Drop constants and lower-order terms: `3n² + 2n + 1` is `O(n²)`. Analyze nested loops carefully; two consecutive `O(n)` loops are still `O(n)`, while nested `O(n)` loops are commonly `O(n²)`. Space complexity includes additional memory used by the algorithm.

## Error reasoning

Syntax errors violate grammar. Compile-time errors are rejected before execution. Runtime errors occur while running. Logical errors produce incorrect results. A race condition occurs when output depends on uncontrolled timing between concurrent operations.

## Checklist

- [ ] Dry-run tables and output tracing
- [ ] Boolean short-circuiting
- [ ] Loop invariants and off-by-one errors
- [ ] Functions, side effects, and recursion
- [ ] Arrays, linked lists, stacks, queues, maps, trees
- [ ] Linear and binary search
- [ ] Sorting concepts
- [ ] Time and space complexity
- [ ] Error classification
