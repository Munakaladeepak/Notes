# Web Technologies

**Priority:** High · **Prerequisite:** [[01 - Programming Logic/README|Programming Logic]] · **Related:** [[08 - JavaScript/README|JavaScript]], [[11 - REST and HTTP/README|REST and HTTP]]

## Browser pipeline

The browser parses HTML into the DOM, parses CSS into style rules, calculates layout, paints pixels, and responds to events. JavaScript can alter the DOM and trigger new layout or paint work. Excessive synchronous work blocks the main thread and harms responsiveness.

## HTML

HTML provides structure and semantics. Know forms, labels, input types, validation attributes, links, images, tables, lists, and semantic elements. A `<label>` associated with an input improves accessibility. Client-side form constraints improve experience but are not security boundaries.

## CSS

Know the cascade, inheritance, specificity, box model, positioning, display modes, Flexbox, Grid, media queries, and responsive units. Specificity conflicts are resolved by importance, origin, specificity, and source order. `box-sizing: border-box` makes declared dimensions include padding and border.

## AJAX and browser communication

AJAX describes asynchronous requests from the browser. `fetch()` returns a Promise. Handle network failure, non-2xx status, JSON parsing errors, loading state, timeout/cancellation, and empty results. CORS is a browser security policy controlling cross-origin requests; it is configured by server response headers.

## Accessibility and performance

Use semantic elements, keyboard access, focus visibility, alt text where appropriate, labels, sufficient contrast, and meaningful error messages. Optimize images, avoid unnecessary reflows, reduce JavaScript work, and paginate large CRM tables.

## Checklist

- [ ] DOM/rendering pipeline
- [ ] Semantic HTML, forms, labels
- [ ] CSS cascade and specificity
- [ ] Box model and `box-sizing`
- [ ] Flexbox, Grid, positioning, responsive units
- [ ] AJAX/fetch failure handling
- [ ] CORS awareness
- [ ] Accessibility and frontend performance
