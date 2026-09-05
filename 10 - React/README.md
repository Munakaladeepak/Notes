# React

**Priority:** High · **Prerequisite:** [[08 - JavaScript/README|JavaScript]] · **Related:** [[11 - REST and HTTP/README|REST and HTTP]]

## Rendering model

React describes UI as a function of data. Components render based on props and state. State updates schedule a render; React compares the new element tree with the previous one and commits necessary DOM changes.

## Props, state, and ownership

Props flow from parent to child and should be treated as read-only. State belongs to the component that owns a changing value. If siblings need the same value, lift state to their closest common parent. Avoid duplicating derived data in state when it can be calculated.

## Hooks

`useState` stores local state. `useEffect` synchronizes with external systems such as network requests, timers, or subscriptions; it is not a general replacement for all calculations. Dependencies describe values used by the effect. Cleanup prevents stale subscriptions and race conditions. `useContext` shares values without passing props through every level. `useMemo` and `useCallback` are optimization tools, not defaults.

## Lists, forms, and keys

Use stable keys from data identifiers. Keys are for React’s reconciliation and are not automatically passed as component props. Controlled inputs use state as the source of truth. Handle loading, success, empty, validation-error, and server-error states explicitly.

## API and state design

Keep API concerns in a service or hook where appropriate. Handle cancellation or stale responses when a user changes search criteria quickly. Distinguish server state from local UI state. Never put secrets in frontend bundles; frontend code is delivered to users.

## Performance and accessibility

Avoid unnecessary global state and expensive work during render. Use pagination or virtualization for large CRM lists. Use semantic elements, labels, keyboard access, and visible focus. Error boundaries handle rendering failures in supported component trees but do not replace API error handling.

## Checklist

- [ ] Components, JSX, render/reconciliation
- [ ] Props, state, state ownership, lifting state
- [ ] `useState`, `useEffect`, `useContext`
- [ ] Effect dependencies and cleanup
- [ ] Lists and stable keys
- [ ] Controlled forms
- [ ] API loading/error/cancellation
- [ ] State architecture and performance
- [ ] Accessibility
