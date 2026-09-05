# REST and HTTP

**Priority:** Very High · **Prerequisite:** [[08 - JavaScript/README|JavaScript]] · **Related:** [[09 - Node and Express/README|Node and Express]]

## HTTP request/response

A request has a method, target URL, headers, and optional body. A response has a status code, headers, and optional body. HTTP is stateless at the protocol level; applications add state through cookies, sessions, or tokens.

## REST design

Model nouns as resources: `/customers`, `/customers/{id}`, and `/customers/{id}/activities`. Use methods consistently. Keep representations predictable, validate payloads, and return useful status codes. Idempotency matters: repeating an idempotent operation should have the same intended result; GET, PUT, and DELETE are generally treated as idempotent, while POST usually is not.

## Methods and status codes

GET reads, POST creates or triggers non-idempotent processing, PUT replaces, PATCH partially updates, and DELETE removes. Know 200, 201, 202, 204, 400, 401, 403, 404, 409, 415, 422, 429, 500, and 503.

- **401:** missing/invalid authentication.
- **403:** identity known but permission denied.
- **409:** state conflict, such as duplicate unique data.
- **429:** rate limit exceeded.

## Parameters and headers

Path parameters identify a resource. Query parameters filter, sort, search, or paginate. Headers carry metadata such as `Content-Type`, `Accept`, caching directives, correlation IDs, and authorization. Never put sensitive tokens into URLs where they can leak through logs and history.

## Authentication and authorization

Authentication verifies identity. Authorization checks permissions. A JWT is a signed token format, not automatically encryption or a complete security solution. Sessions store server-side state and use a session identifier in a cookie. Protect tokens, expiration, refresh, revocation, and CSRF concerns according to the architecture.

## API quality

Use versioning when contracts change, consistent error shapes, validation schemas, pagination, filtering limits, rate limiting, logging with correlation IDs, and OpenAPI-style documentation. CORS is not authentication; it is a browser access-control mechanism.

## Checklist

- [ ] Request/response anatomy
- [ ] REST resources and statelessness
- [ ] HTTP methods and idempotency
- [ ] Status codes 2xx/4xx/5xx
- [ ] Headers and parameter types
- [ ] JSON and content negotiation
- [ ] Authentication versus authorization
- [ ] Sessions versus JWT awareness
- [ ] Pagination, validation, errors, rate limiting, CORS
