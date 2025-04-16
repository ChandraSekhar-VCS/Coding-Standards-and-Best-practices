# ✅ Java Code Quality & Hygiene Guidelines

A complete reference guide for professional Java developers, covering naming, formatting, logging, exceptions, and more.

---

## 📦 Naming Conventions

| Element       | Convention              | Example                   |
|---------------|--------------------------|---------------------------|
| Package       | lowercase                | `com.project.module`      |
| Class         | PascalCase               | `UserService`             |
| Interface     | PascalCase               | `Serializable`            |
| Method        | camelCase                | `getUserById()`           |
| Variable      | camelCase                | `userName`                |
| Constant      | UPPER_CASE_WITH_UNDERSCORES | `MAX_ATTEMPTS`        |
| Enum Constant | UPPER_CASE_WITH_UNDERSCORES | `CONFIRMED`            |
| Type Param    | Single uppercase letter  | `T`, `K`, `V`             |

---

## 📐 Coding Standards & Formatting

- Indentation: 4 spaces (no tabs)
- Braces on same line (K&R style)
- Max line length: 100–120 characters
- One statement per line
- Use blank lines for logical separation
- Space after keywords and around operators

---

## 📝 Commenting Guidelines

- Use `//` for short explanations
- Use block comments for complex logic
- Avoid redundant comments
- Use `@TODO`, `@FIXME`, `@NOTE`, `@HACK` tags where appropriate

---

## 🚫 Exception Handling Best Practices

- Catch specific exceptions only
- Never swallow exceptions silently
- Always log or rethrow with context
- Use custom exceptions for domain logic
- Prefer try-with-resources for closables

---

## 🪵 Logging Standards (SLF4J + Logback)

| Level | Use Case                                  |
|-------|--------------------------------------------|
| TRACE | Very detailed internal debug info          |
| DEBUG | Developer-level debug data                 |
| INFO  | Business events, lifecycle notifications   |
| WARN  | Recoverable issues, edge cases             |
| ERROR | Failures, exceptions, critical faults      |

- Use `{}` placeholders instead of string concatenation
- Never log sensitive data (passwords, tokens)
- Avoid logging in loops or deep stack methods

---

## 🔐 Immutability & `final` Usage

- Use `final` to prevent reassignment or subclassing
- Make objects immutable:
  - `final` fields
  - No setters
  - Constructor-based initialization
  - Defensive copies for mutable fields
- Prefer Java `record` types (Java 14+)

---

## ⚠️ Null Safety & Defensive Programming

- Use `Objects.requireNonNull()` for mandatory inputs
- Annotate non-null contracts (`@NonNull`, `@NotNull`)
- Return `Optional<T>` or empty collections instead of `null`
- Validate input early, fail fast with clear messages
- Never trust external data blindly

---

## 🧱 Code Organization & Layering

**Package-by-feature** is preferred over package-by-layer for scalability:

```
com.project
├── booking
│   ├── BookingController.java
│   ├── BookingService.java
│   └── BookingRepository.java
├── payment
│   ├── PaymentController.java
│   ├── PaymentService.java
│   └── PaymentRepository.java
```

**Layer Structure:**
- Controller (entry point)
- Service (business logic)
- Repository (data access)
- DTOs (API data models)
- Mappers (conversions)

---

## 🧵 Thread Safety & Concurrency Hygiene

- Avoid shared mutable state in services or beans
- Use thread-safe collections (`ConcurrentHashMap`, `CopyOnWriteArrayList`)
- Use `synchronized` carefully
- Prefer `ExecutorService`, `CompletableFuture`, `Atomic*` classes
- Stateless services are safest in Spring Boot

---

## 🔍 Static Code Analysis Tools

| Tool        | Purpose                |
|-------------|------------------------|
| Checkstyle  | Code formatting, naming, Javadoc rules |
| PMD         | Code patterns, complexity warnings     |
| SpotBugs    | Bug detection (nulls, threading, etc.) |
| SonarQube   | Centralized quality dashboard          |
| Spotless    | Auto-formatting using Google style     |

---

## 📌 Integration Tips

- Configure tools in your Maven/Gradle builds
- Set up pre-commit hooks or CI checks
- Use IntelliJ plugins: Checkstyle, PMD, SonarLint
- Gradually enforce rules to avoid legacy friction

---

> This file serves as a professional-grade reference for Java backend developers. Follow these guidelines for consistent, maintainable, production-ready code.
