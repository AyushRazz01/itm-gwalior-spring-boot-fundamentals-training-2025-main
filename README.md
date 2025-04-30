# Spring Boot Fundamentals Training - ITM Gwalior

## **Duration**: 4 hours per day x 6 days (24 hours total)

![Spring Boot - Fundamentals - Code with DBC.png](Spring%20Boot%20-%20Fundamentals%20-%20Code%20with%20DBC.png)

### [Day 1 : Introduction & Java Refresher](./notes/day-1/README.md)

#### Session 1 (2 hours) : Welcome, environment setup, OOP concepts review

* **Welcome & Overview** (30 minutes)
  * Training objectives and schedule
  * Pre-requisite knowledge assessment
  * Setting up the development environment (JDK, IntelliJ IDEA, Git)

* **Java Refresher: OOP Concepts** (90 minutes)
  * Classes and Objects review
  * Inheritance and polymorphism in practice
  * Interfaces and abstract classes
  * Annotations in Java (built-in annotations and their purpose)

#### Session 2 (2 hours) : Modern Java features, Introduction to Spring Framework

* **Java Refresher: Modern Java Features** (60 minutes)
    * Lambda expressions and functional interfaces
    * Stream API basics
    * Optional class for null handling
    * Method references

* **Introduction to Spring Framework** (60 minutes)
    * Spring Core concepts
    * Dependency Injection and Inversion of Control
    * Spring vs Spring Boot
    * Spring Boot advantages and features


### [Day 2 : Spring Boot Fundamentals](./notes/day-2/README.md)

#### Session 1 (2 hours) : Project setup, application properties, auto-configuration

* **Spring Boot Project Setup** (60 minutes)
  * Spring Initializr (start.spring.io)
  * Maven project structure
  * POM configuration and dependencies
  * application.properties/YAML configuration

* **Spring Boot Core Concepts** (60 mintues)
  * @SpringBootApplication anatomy
  * Component scanning
  * Auto-configuration
  * Profiles for environment specific configuration

#### Session 2 (2 hours) : Dependency Injection, component scanning, bean lifecycle

* **Dependency Injection in Spring Boot** (90 minutes)
  * Bean lifecycle
  * @Component, @Service, @Repository annotations
  * @Autowired and constructor injection
  * Scopes of Spring beans (Singleton vs Prototype)
  * Building a simple service layer

* **Practical Exercise** (30 minutes)
  * Create a Spring Boot application with multiple components
  * Configure beans with different injection methods
  * Test bean initialization and dependency injection


### [Day 3 : REST API Development with Spring Boot](./notes/day-3/README.md)

#### Session 1 (2 hours) : REST principles, Spring MVC, controller implementation

* **REST Principles** (45 minutes)
  * HTTP methods and their semantics
  * Resource naming conventions
  * Status codes
  * Richardson Maturity Model

* **Spring MVC & REST Controllers** (75 minutes)
  * @RestController vs @Controller
  * Request Mapping (@GetMapping, @PostMapping, etc.)
  * Path variables and request parameters
  * RequestBody and ResponseEntity

#### Session 2 (2 hours) : Advanced REST features, request/response handling, validation

* **Building RESTful APIs** (90 minutes)
  * API versioning strategies
  * Request/Response DTOs
  * Validation (@Valid, custom validators)
  * Content negotiation (JSON, XML)

* **Practical Exercise** (30 minutes)
  * Implement a CRUD REST API for a simple entity
  * Test endpoints using Postman
  * Implement validation and error handling


### [Day 4 : Data Persistence with Spring Data JPA](./notes/day-4/README.md)

#### Session 1 (2 hours) : Spring Data JPA introduction, entity mapping repositories

* **Introduction to Spring Data JPA with PostgreSQL** (60 minutes)
  * ORM concepts and JPA overview
  * Entity-relationship fundamentals
  * @Entity, @Table, @Column annotations
  * Primary keys and @Id

* **Repository Pattern** (60 minutes)
  * JpaRepository interface
  * CRUD operations
  * Query methods
  * @Query annotation for custom query methods

#### Session 2 () : Relationships, transactions, query methods

* **Advanced JPA concepts** (90 minutes)
  * Relationships (@OneToMany, @ManyToOne etc)
  * Lazy vs Eager loading
  * Transaction management (@Transactional)
  * Auditing with @CreatedDate


* **Practical Exercise** (30 minutes)
  * Design and implement entities with relationships
  * Create repositories with custom query methods
  * Test data access layer


### [Day 5 : Exception Handling & Testing](./notes/day-5/README.md)

#### Session 1 (2 hours) : Global exception handling, custom exceptions, logging

* **Global Exception Handling** (90 minutes)
  * @ControllerAdvice and @ExceptionHandler
  * Creating custom exceptions
  * Standardized error responses
  * Handling validation errors

* **Logging in Spring Boot** (30 minutes)
  * SLF4J and Logback configurations
  * Log levels and best practices
  * Structured logging

#### Session 2 (2 hours) : Unit and integration testing with JUnit and Mockito

* **Testing Spring Boot Applications** (90 minutes)
  * Unit testing with JUnit 5
  * Mock objects with Mockito
  * @SpringBootTest and TestRestTemplate
  * Testing slices with @WebMvcTest and @DataJpaTest

* **Practical Exercise** (30 minutes)
  * Implement global exception handling for a REST API
  * Write unit and integration tests for controllers and services


### [Day 6 : API Documentation & Mini Project](./notes/day-6/README.md)

#### Session 1 (2 hours) : OpenAPI/Swagger documentation, Spring Boot Actuator

* **API Documentation with OpenAPI** (60 minutes)
  * Springdoc-openapi setup
  * Swagger UI integration
  * Documenting endpoints with annotations
  * Enhancing documentation with examples

* **Spring Boot Actuator** (60 minutes)
  * Health checks and metrics
  * Custom endpoints
  * Security considerations

#### Session 2 (2 hours) : Guided mini-project implementation and review

* **Mini Project: Building a complete API** (120 minutes)
  * Requirements analysis
  * Designing the data model
  * Implementing repositories, services, and controllers
  * Adding validation and exception handling
  * Documenting with OpenAPI
  * Testing the complete application