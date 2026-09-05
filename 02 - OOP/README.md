# Object-Oriented Programming

**Priority:** Very High · **Prerequisite:** [[01 - Programming Logic/README|Programming Logic]] · **Next:** [[03 - Core Java/README|Core Java]]

## Class, object, and state

A class defines a type. An object is an instance with identity, state, and behavior. A field stores state; a method provides behavior; a constructor establishes a valid initial state. In CRM code, `Customer`, `Lead`, and `Activity` may be domain classes.

## Four pillars

**Encapsulation** protects invariants by controlling access. A customer’s status should not be set to an invalid value by arbitrary code; a method can validate allowed transitions. **Abstraction** exposes a useful contract while hiding implementation. **Inheritance** reuses and specializes a parent type. **Polymorphism** lets client code call a common contract while the actual object supplies behavior.

## Binding and substitution

Static or compile-time binding resolves a call before execution. Dynamic or runtime binding resolves overridden behavior based on the actual object. A subtype should be usable wherever its parent type is expected; violating this idea is a Liskov Substitution Principle problem.

## Composition versus inheritance

Inheritance expresses “is-a.” Composition expresses “has-a” and is often safer because behavior can be replaced without creating a rigid hierarchy. A `CRMService` may have a `NotificationSender`; it need not inherit from one.

## SOLID and maintainability

- **S — Single Responsibility Principle:** one reason to change.
- **O — Open/Closed Principle:** open for extension, closed for unsafe modification.
- **L — Liskov Substitution Principle:** subtypes preserve parent expectations.
- **I — Interface Segregation Principle:** prefer focused interfaces.
- **D — Dependency Inversion Principle:** high-level logic depends on abstractions, not concrete details.

High cohesion means related responsibilities stay together. Low coupling means modules depend on fewer implementation details. A code smell is a warning sign, not automatically a bug.

## Interface, abstract class, and encapsulation

An interface defines capabilities. An abstract class can share state and partial implementation. Private fields plus public methods are a common encapsulation pattern. A getter/setter is not automatically good encapsulation; it should enforce meaningful rules rather than expose everything blindly.

## Design-pattern awareness

Know the intent of common patterns. **Factory** centralizes object creation. **Singleton** restricts instance count but can harm testability. **Strategy** swaps an algorithm behind a common interface. **Observer** notifies subscribers of changes. **MVC** separates UI, request coordination, and data concerns.

## Exam traps

Overloading is not overriding. Encapsulation is not encryption. Abstraction is not deleting functionality. Inheritance does not automatically mean good reuse. Interfaces describe contracts; they do not necessarily contain all implementation.

## Checklist

- [ ] Object identity, state, behavior
- [ ] Four pillars with examples
- [ ] Static versus dynamic binding
- [ ] Composition versus inheritance
- [ ] SOLID principles
- [ ] Cohesion and coupling
- [ ] Interfaces and abstract classes
- [ ] Factory, Strategy, Observer, Singleton intent
