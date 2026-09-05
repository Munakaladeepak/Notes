# MVC and Frameworks

**Priority:** Medium · **Prerequisite:** [[02 - OOP/README|OOP]] · **Related:** [[04 - PHP/README|PHP]], [[03 - Core Java/README|Core Java]]

## MVC and layered architecture

The Model represents data and domain rules. The View presents UI. The Controller accepts a request and coordinates. In larger applications, services hold business use cases and repositories/data-access objects isolate persistence. This is a layered architecture, not a requirement that every project use identical folders.

## Laravel

Laravel is a PHP framework. Know routing, middleware, controllers, request validation, authorization policies, Blade, migrations, seeders, Eloquent ORM, relationships, queues, events, configuration, and environment files. ORM convenience does not eliminate N+1 query problems or authorization checks.

## Spring

Spring is a Java ecosystem. Spring Boot provides auto-configuration and conventions. Know controllers, services, repositories, dependency injection, configuration, validation, exception handling, and REST endpoints. `@RestController`, `@Service`, and `@Repository` commonly communicate roles, while annotations should not replace understanding the underlying flow.

## Dependency Injection and IoC

Dependency Injection supplies collaborators from outside a class. Inversion of Control means framework/container code manages creation and lifecycle. Constructor injection makes dependencies explicit and improves testing. Avoid service locators and hidden global state when possible.

## ORM and migrations

An ORM maps objects to database records. It improves developer productivity but can hide SQL, cause inefficient queries, and complicate transactions. Migrations version schema changes so environments can reproduce structure. Treat migrations as deployment-sensitive code.

## Checklist

- [ ] MVC responsibilities and request flow
- [ ] Layered architecture and service/repository roles
- [ ] Laravel routes, middleware, validation, ORM, migrations
- [ ] Spring Boot, controllers, services, repositories
- [ ] Dependency Injection and IoC
- [ ] ORM trade-offs and N+1 awareness
