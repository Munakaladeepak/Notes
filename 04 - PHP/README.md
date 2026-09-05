# PHP

**Priority:** High · **Prerequisite:** [[02 - OOP/README|OOP]] · **Related:** [[12 - MVC and Frameworks/README|MVC and Frameworks]], [[17 - Security/README|Security]]

## Runtime model

PHP is commonly executed on a web server. A request reaches PHP, PHP runs server-side code, and the server returns HTML or an API response. The browser does not normally receive the PHP source.

## Language details

Variables begin with `$`. PHP is dynamically typed but supports type declarations and strict typing. Know scalar types, arrays, associative arrays, functions, variable scope, pass-by-value versus pass-by-reference, and return values.

`==` allows type juggling; `===` compares value and type. `isset()` returns false for null or an unset variable. `empty()` treats several values such as `0`, `"0"`, false, null, and empty strings as empty-like; this can create validation bugs.

## HTTP and forms

`$_GET` represents URL query data; `$_POST` represents request body form data; `$_SESSION` stores server-side session state; `$_COOKIE` reads browser cookies; `$_FILES` handles uploads. Validate size, MIME type, filename, and storage location for uploads. Do not trust a file extension alone.

## OOP and errors

PHP supports classes, visibility, constructors, inheritance, interfaces, traits, abstract classes, namespaces, exceptions, and autoloading. `include` may continue after a warning; `require` generally stops when loading fails. Use namespaces to avoid naming collisions.

## Security

Use prepared statements for SQL injection defense. Escape output in the correct HTML/JavaScript/URL context for XSS defense. Use `password_hash()` and `password_verify()`. Regenerate session IDs after authentication. Keep error details in logs rather than exposing stack traces.

## Laravel awareness

Laravel provides routing, middleware, controllers, Blade templates, validation, migrations, Eloquent ORM, queues, events, authentication support, and configuration. Understand the request lifecycle: route → middleware → controller → service/model → response. Know that migrations are versioned schema changes and ORM queries still need careful authorization and performance review.

## Checklist

- [ ] Dynamic typing and type declarations
- [ ] Arrays, functions, scope, references
- [ ] `==` versus `===`, `isset()` versus `empty()`
- [ ] Superglobals and sessions
- [ ] OOP, namespaces, traits, exceptions
- [ ] Include versus require
- [ ] Upload and form security
- [ ] Prepared statements and password hashing
- [ ] Laravel request lifecycle, ORM, migrations, middleware
