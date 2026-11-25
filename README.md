# First Two Spring Framework Apps (Exercise 16)

Laboratory project for **Vistula University** (`Akademia Finansów i Biznesu Vistula`) covering the fundamentals of building web applications and REST APIs with **Spring Boot**, **Spring MVC**, **Spring Data JPA**, **H2**, and **Swagger / OpenAPI**[cite: 2, 3, 14, 29, 56].

## Overview

The assignment is divided into two main parts[cite: 3, 14]:

1. **Task 1 — First Spring Boot Web App & MVC View**
   - Bootstrapping a Maven project via Spring Initializr with **Spring Web**, **Lombok**, and **Thymeleaf**[cite: 4, 5].
   - Creating `HelloController` with a basic `@GetMapping("/")` endpoint returning plain text[cite: 8, 9].
   - Expanding the controller to `@Controller` with `@GetMapping("/greeting")`, `@RequestParam`, and `Model` to render `greeting.html` with a static image (`vistula.png`)[cite: 11, 12].

2. **Task 2 — REST API (`Products API for Vistula`)**
   - Layered architecture under `pl.edu.vistula.firstrestapispring.product` (`api`, `api.request`, `api.response`, `domain`, `repository`, `service`, `support`, `support.exception`) plus shared response DTOs in `shared.api.response`[cite: 15, 16, 17, 18, 39, 42].
   - **CRUD Endpoints (`/api/v1/products`)**:
     - `POST /api/v1/products` — create a product (`201 Created`)[cite: 24, 25, 29].
     - `GET /api/v1/products/{id}` — retrieve a product by ID (`200 OK`)[cite: 34, 38].
     - `GET /api/v1/products` — list all products (`200 OK`)[cite: 50, 52].
     - `PUT /api/v1/products/{id}` — update an existing product (`200 OK`)[cite: 44, 46].
     - `DELETE /api/v1/products/{id}` — delete a product by ID (`204 No Content`)[cite: 53].
   - **Exception Handling**: `ProductNotFoundException`, `ProductExceptionSupplier`, `@ControllerAdvice` (`ProductExceptionAdvisor`), and `ErrorMessageResponse` returning `404 Not Found` instead of an unhandled `500` error[cite: 39, 40, 41, 42].
   - **Swagger UI / OpenAPI**: documented via `springdoc-openapi-starter-webmvc-ui` and `@OpenAPIDefinition`[cite: 29, 30, 31].
   - **Persistence with Spring Data JPA & H2**: `Product` mapped as a JPA `@Entity(name = "products")` with `@Id` and `@GeneratedValue`, `ProductRepository` extending `JpaRepository<Product, Long>`, and in-memory H2 console enabled[cite: 56, 57, 60, 63, 64].

## Tech Stack

- **Java** & **Spring Boot** (Maven)[cite: 4, 5]
- **Spring Web** (Spring MVC / REST)[cite: 5]
- **Thymeleaf** & **Lombok**[cite: 5]
- **Spring Data JPA** & **Hibernate**[cite: 56]
- **H2 Database** (in-memory)[cite: 15, 56]
- **springdoc-openapi** (Swagger UI)[cite: 29]

## Configuration (`src/main/resources/application.properties`)

properties
spring.h2.console.enabled=true
spring.h2.console.path=/console/
spring.datasource.url=jdbc:h2:mem:testdb
logging.level.org.hibernate.SQL=DEBUG
[cite: 57, 61]

## Running the Application

1. Clone the repository and open it in your IDE (e.g., IntelliJ IDEA)[cite: 4, 15, 66].
2. Reload Maven dependencies (`pom.xml`)[cite: 6].
3. Run the main Spring Boot application class[cite: 6, 7, 15].

## Useful URLs (when running on `localhost:8080`)

- **Greeting page:** `http://localhost:8080/greeting?name=Vistula`[cite: 11, 13]
- **Swagger UI:** `http://localhost:8080/swagger-ui/index.html`[cite: 32]
- **OpenAPI JSON:** `http://localhost:8080/v3/api-docs`[cite: 33]
- **H2 Console:** `http://localhost:8080/console` (JDBC URL: `jdbc:h2:mem:testdb`)[cite: 57, 58]
- **Products API:** `http://localhost:8080/api/v1/products`[cite: 25, 36]
