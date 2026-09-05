# Node.js and Express

**Priority:** High · **Prerequisite:** [[08 - JavaScript/README|JavaScript]] · **Related:** [[11 - REST and HTTP/README|REST and HTTP]]

## Node runtime

Node.js executes JavaScript outside the browser using a runtime built around an event loop and asynchronous I/O. It is strong for I/O-heavy workloads, but CPU-heavy synchronous work blocks the event loop and delays all requests on that process.

## Modules and npm

Modules isolate functionality. npm manages dependencies and scripts. `package.json` describes metadata and scripts; lockfiles pin dependency versions. Distinguish production dependencies from development dependencies. Avoid unreviewed packages and audit supply-chain risk.

## Express request lifecycle

A request passes through middleware in registration order, then route handlers, services, data access, and a response. Middleware can parse JSON, authenticate, validate, log, add context, or handle errors. A route should not become the entire business layer.

## Error handling

Centralized error middleware converts known failures to safe status codes and messages. Do not leak stack traces or secrets. Distinguish validation errors, authentication errors, authorization errors, missing resources, conflicts, and unexpected server errors.

## Architecture

A maintainable API often separates routes, controllers, services, repositories/data access, validation schemas, configuration, and error handling. Keep secrets in environment variables. Use connection pooling and close resources appropriately.

## Performance and security

Avoid synchronous filesystem or CPU-heavy operations on request paths. Apply body-size limits, rate limiting, input validation, secure headers, CORS restrictions, authentication, authorization, and structured logging. Prevent duplicate submissions with idempotency strategies where required.

## Checklist

- [ ] Event loop and blocking operations
- [ ] Modules, npm, package.json, lockfiles
- [ ] Express routes and middleware order
- [ ] Central error handling
- [ ] Controller/service/repository separation
- [ ] Environment configuration
- [ ] Validation, rate limiting, CORS, secure headers
- [ ] Database pooling and performance
