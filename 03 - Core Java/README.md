# Core Java

**Priority:** Very High · **Prerequisite:** [[02 - OOP/README|OOP]] · **Related:** [[13 - Testing and Debugging/README|Testing]]

## Execution model

The JDK provides tools such as `javac`. The compiler converts `.java` source into bytecode. The JRE supplies runtime libraries and the JVM. The JVM loads, verifies, and executes bytecode. Java’s portability comes from compiling to bytecode for a compatible JVM, not from source code being magically identical on every operating system.

## Types and conversions

Java is statically typed. Primitive types hold simple values; reference variables point to objects. Widening conversion such as `int` to `long` is generally safe. Narrowing conversion such as `double` to `int` may lose information and requires casting.

Wrapper classes such as `Integer` represent primitive values as objects. **Autoboxing** converts a primitive to a wrapper; **unboxing** converts back. Beware of null wrappers during unboxing and of `Integer` reference comparison with `==`.

## Keywords and access

`this` identifies the current object. `super` accesses parent behavior or constructors. `static` belongs to the class. `final` prevents reassignment of a variable, overriding of a method, or extension of a class. `private`, default, `protected`, and `public` progressively control visibility.

## Constructors and initialization

A constructor has the class name and no return type. If no constructor is declared, the compiler may provide a no-argument default constructor. If any constructor is declared, that automatic constructor is not supplied. Initialization order includes static initialization, instance field initialization, and constructor execution according to class hierarchy.

## Strings and equality

`String` is immutable. String literals may use the string pool. `.equals()` tests content; `==` tests reference identity. `StringBuilder` is mutable and efficient for repeated concatenation in one thread; `StringBuffer` provides synchronized operations with extra overhead.

## Collections and generics

`List` preserves order and allows duplicates. `Set` models uniqueness. `Map` maps keys to values. `Queue` represents pending work. Generics provide compile-time type safety, such as `List<String>`. Know average lookup behavior of `HashMap`, sorted behavior of `TreeMap`, and that `HashSet` uses hashing for uniqueness.

`equals()` and `hashCode()` must be consistent: equal objects must have equal hash codes. Mutable keys are dangerous if their fields used in hashing change after insertion.

## Exceptions

Checked exceptions are compiler-checked. Unchecked exceptions derive from `RuntimeException`. `try` contains risky code, `catch` handles, `finally` cleans up, `throw` raises, and `throws` declares. Use try-with-resources for closeable resources. Do not catch overly broad exceptions and silently ignore them.

## Memory and concurrency

The stack stores call frames and local references; the heap stores objects. Garbage collection reclaims unreachable objects. A thread is a path of execution within a process. A race condition occurs when unsynchronized shared state produces timing-dependent results. `synchronized`, locks, atomic classes, and immutable data help coordinate access. Deadlock requires conditions such as circular waiting; prevention includes consistent lock ordering.

## Common technical questions

Know `ArrayList` versus `LinkedList`, `HashMap` versus `Hashtable`, interface versus abstract class, `final` versus `finally` versus `finalize`, compile-time versus runtime polymorphism, and `throw` versus `throws`.

## Checklist

- [ ] JDK/JRE/JVM and bytecode flow
- [ ] Primitive/reference types and casting
- [ ] Autoboxing and unboxing
- [ ] Constructors and initialization order
- [ ] Modifiers and keywords
- [ ] String pool, immutability, equality
- [ ] Collections, generics, equals/hashCode
- [ ] Checked/unchecked exceptions and resources
- [ ] Heap, stack, garbage collection
- [ ] Threads, synchronization, race conditions, deadlock
