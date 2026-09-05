# JavaScript

**Priority:** Very High · **Prerequisite:** [[07 - Web Technologies/README|Web Technologies]] · **Next:** [[10 - React/README|React]]

## Types and coercion

JavaScript has primitive values such as string, number, bigint, Boolean, undefined, symbol, and null, plus objects. `typeof null` is a historic quirk that returns `"object"`. `NaN` means not-a-number and is not equal to itself; `Number.isNaN()` is safer for checking it.

`==` performs coercion; `===` checks value and type. Know truthy/falsy values, `null` versus `undefined`, optional chaining `?.`, and nullish coalescing `??`.

## Scope and closures

`var` is function-scoped; `let` and `const` are block-scoped. A closure is a function retaining access to variables from its lexical outer scope. Closures are useful for callbacks and modules but can retain memory if long-lived references are not cleaned up.

## Objects and prototypes

Objects hold properties and methods. JavaScript inheritance is prototype-based. `class` syntax provides a clearer form over prototypes but still uses the prototype system. Know shallow copying with spread syntax and that nested objects remain shared unless deeply copied.

## Async model

JavaScript runs synchronous code on a call stack. The event loop coordinates tasks and microtasks. Promise callbacks run as microtasks and can run before later timer tasks. A Promise can be pending, fulfilled, or rejected. `async` functions return Promises; `await` pauses that function until settlement, not the entire runtime.

## DOM and fetch

Use selectors, event listeners, event delegation, and `preventDefault()` for custom form flows. For `fetch`, check `response.ok` because HTTP 404/500 do not automatically reject the Promise. Parse JSON only when appropriate and handle aborts and errors.

## Common technical traps

`map()` transforms and returns a new array; `filter()` keeps matching values; `reduce()` accumulates. `forEach()` does not await asynchronous callbacks in the way many beginners expect. Mutating shared objects can create state bugs. Hoisting differs for function declarations, `var`, `let`, and `const`.

## Checklist

- [ ] Primitive/reference values and coercion
- [ ] `==`, `===`, truthy/falsy, nullish operators
- [ ] Scope, hoisting, closures
- [ ] Objects, prototypes, shallow copies
- [ ] `map`, `filter`, `reduce`, `forEach`
- [ ] Event propagation and delegation
- [ ] Promises, microtasks, async/await
- [ ] Fetch status/error handling
