# OpenCode AI Instructions - Court Booking API

You are an expert backend software engineer working on a Spring Boot (Java 25) project (`court-booking-api`). Adhere strictly to the architectural rules, design patterns, and engineering constraints defined below.

## 🏛️ Architecture & Design Patterns

1. **MVC & Layered Architecture:**
    - **Controller Layer:** Handle HTTP requests, input validation (`@Valid`), and return standard responses. Do not put business logic here.
    - **Service Layer:** Contain all business logic, transaction management (`@Transactional`), and core rules.
    - **Repository Layer:** Spring Data JPA interfaces for database interaction. Keep them clean and decoupled from business logic.
    - **Model / Entity Layer:** JPA entities mapped cleanly to PostgreSQL tables.

2. **Object-Oriented Programming (OOP):**
    - Encapsulate behavior inside domain models where appropriate.
    - Favor composition over inheritance.
    - Keep classes small, cohesive, and focused on a single responsibility.

3. **GRASP Patterns:**
    - Apply core GRASP principles: *Controller* (handle system events via API endpoints), *Creator*, *Information Expert* (assign responsibilities to the class that has the required data), and *Low Coupling / High Cohesion*.

4. **SOLID Principles:**
    - **S:** Single Responsibility Principle per class and method.
    - **O:** Open/Closed Principle (open for extension, closed for modification).
    - **L:** Liskov Substitution Principle.
    - **I:** Interface Segregation Principle (keep service and repository interfaces concise).
    - **D:** Dependency Inversion Principle (inject dependencies via constructors using Spring's dependency injection; avoid field injection).

---

## 🌐 RESTful API Standards
- Use proper HTTP methods (`GET`, `POST`, `PUT`, `DELETE`).
- Return correct HTTP status codes (`200 OK`, `201 Created`, `400 Bad Request`, `404 Not Found`, `409 Conflict`).
- Use plural nouns for endpoints (e.g., `/api/pitches`, `/api/reservations`).
- Keep request/response payloads clean using DTOs (Data Transfer Objects). Never expose raw JPA entities directly in controllers.

---

## 🗄️ Database & SQL Best Practices (PostgreSQL)
- Rely primarily on Spring Data JPA derived queries or JPQL/Criteria API for standard operations.
- If native queries or complex JPQL are used, ensure they are optimized, avoid N+1 query problems (use `@EntityGraph` or `JOIN FETCH` when necessary), and include proper indexing awareness.
- Ensure proper constraints (foreign keys, unique constraints on overlapping reservation checks) at the database level where applicable.

---

## 🛑 Anti-Overengineering & Testing Policy

1. **Anti-Overengineering (YAGNI / KISS):**
    - **Do not add unnecessary abstractions**, generic wrapper layers, or enterprise design patterns (like heavy CQRS or Event Sourcing) unless explicitly requested.
    - Keep the codebase lean, readable, and straightforward. A trainee-level professional project shines through its clarity, correctness, and clean execution, not through complex boilerplate.

2. **Testing Constraints:**
    - **Do not write excessive or redundant unit/integration tests.**
    - Focus tests strictly on critical business logic (e.g., the overlap validation engine for court reservations and automatic price calculation).
    - Avoid mocking everything just for the sake of 100% code coverage. Write meaningful tests only where regression risks are high.