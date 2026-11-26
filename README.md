# 🛒 E-Commerce Backend Application

<p align="center">
  <b>A REST API-based E-Commerce Backend using Java, Spring Boot and MySQL</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=openjdk" />
  <img src="https://img.shields.io/badge/Spring%20Boot-3.5.x-brightgreen?style=for-the-badge&logo=springboot" />
  <img src="https://img.shields.io/badge/MySQL-8-blue?style=for-the-badge&logo=mysql" />
  <img src="https://img.shields.io/badge/Maven-Build-red?style=for-the-badge&logo=apachemaven" />
</p>

## 📌 About the Project

The E-Commerce Backend Application is a REST API-based project developed using Java, Spring Boot, Spring Security and MySQL.

The application provides backend functionality for an online shopping platform, including product management, category management, user registration, secure login, JWT authentication and order processing.

It uses Spring Data JPA for database operations and Spring Security for authentication and authorization. Postman is used to test the REST API endpoints.

## ✨ Implemented Features

### Phase 1 – Spring Boot Setup
- Created a Spring Boot application.
- Configured REST API endpoints.
- Tested backend connectivity.

### Phase 2 – Database Integration
- Integrated MySQL with Spring Boot.
- Implemented Spring Data JPA.
- Created Product and Category entities.
- Developed repository and service layers.
- Implemented product and category APIs.
- Added initial product and category data.

### Phase 3 – User Authentication and Security
- Implemented user registration and login.
- Integrated Spring Security.
- Implemented JWT-based authentication.
- Added BCrypt password hashing.
- Configured protected API endpoints.
- Added request validation and exception handling.

### Phase 4 – Order Management
- Implemented Order and OrderItem entities.
- Established database relationships between users, orders and products.
- Implemented order placement functionality.
- Added product stock validation.
- Implemented automatic order total calculation.
- Updated product stock after successful orders.
- Used database transactions with `@Transactional`.
- Implemented user-specific order history.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Java 17 | Backend programming |
| Spring Boot 3.5.x | Backend framework |
| Spring Web | REST API development |
| Spring Data JPA | Database operations |
| Hibernate | ORM |
| Spring Security | Authentication and authorization |
| JWT | Token-based authentication |
| BCrypt | Password hashing |
| MySQL 8 | Database |
| Maven | Dependency management |
| Postman | API testing |

## 🏗️ Backend Architecture

```text
             CLIENT
                |
                ▼
          REST API
                |
                ▼
          CONTROLLER
                |
                ▼
            SERVICE
                |
                ▼
           REPOSITORY
                |
                ▼
             MySQL
```

## 📁 Project Structure

```text
ecommerce/
│
├── src/main/java/com/shop/ecommerce/
│   │
│   ├── config/
│   │   ├── WebConfig.java
│   │   ├── SecurityConfig.java
│   │   └── DataSeeder.java
│   │
│   ├── controller/
│   │   ├── HelloController.java
│   │   ├── CategoryController.java
│   │   ├── ProductController.java
│   │   ├── UserController.java
│   │   └── OrderController.java
│   │
│   ├── dto/
│   │
│   ├── exception/
│   │
│   ├── model/
│   │   ├── Category.java
│   │   ├── Product.java
│   │   ├── User.java
│   │   ├── Order.java
│   │   └── OrderItem.java
│   │
│   ├── repository/
│   │
│   ├── security/
│   │   ├── JwtUtil.java
│   │   ├── JwtAuthFilter.java
│   │   └── CustomUserDetailsService.java
│   │
│   ├── service/
│   │
│   └── EcommerceApplication.java
│
├── src/main/resources/
│   └── application.properties
│
└── pom.xml
```

## ⚙️ Installation and Setup

### 1. Prerequisites

- Java JDK 17 or later
- Spring Tool Suite (STS)
- MySQL Server 8
- MySQL Workbench
- Maven
- Postman

### 2. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

### 3. Database Configuration

Open MySQL Workbench and create the database:

```sql
CREATE DATABASE ecommerce_db;
```

### 4. Configure application.properties

Update your database credentials:

```properties
spring.application.name=ecommerce
server.port=8080

spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
spring.datasource.username=root
spring.datasource.password=YOUR_MYSQL_PASSWORD

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

Also configure the JWT secret using the property expected by the application.

**Note:** Do not upload actual database passwords or JWT secrets to GitHub.

### 5. Run the Application

Open the project in Spring Tool Suite.

Run the main application:

`EcommerceApplication.java`

Or use the terminal:

```bash
mvn spring-boot:run
```

Backend runs at:

```text
http://localhost:8080
```

## 🔗 REST API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/hello` | Check backend connection |
| GET | `/api/products` | Get all products |
| GET | `/api/products/{id}` | Get product by ID |
| GET | `/api/categories` | Get all categories |
| POST | `/api/users/register` | Register a new user |
| POST | `/api/users/login` | User login |
| POST | `/api/orders` | Place an order |
| GET | `/api/orders/my` | Get logged-in user's orders |

**Authentication:**
- Public endpoints: Products, categories, registration and login.
- Protected endpoints: Order placement and order history.
- Protected requests require a valid JWT Bearer token.

## 🔐 JWT Authentication Flow

1. User registers with name, email and password.
2. Password is stored as a BCrypt hash.
3. User logs in using email and password.
4. Backend verifies the credentials.
5. A JWT token is generated.
6. Client sends the token in the Authorization header.
7. JWT filter validates the token before allowing access to protected endpoints.

## 📦 Order Processing

1. Authenticated user sends product IDs and quantities.
2. Backend verifies the user and requested products.
3. Checks available product stock.
4. Calculates the total using actual database prices.
5. Updates product stock.
6. Saves order and order items in MySQL.
7. Returns the created order.
8. User can retrieve their order history.

All order operations are handled within a database transaction to ensure consistency.

## 🧪 API Testing

The REST APIs are tested using Postman.

Test scenarios include:

- Product and category retrieval.
- User registration.
- Duplicate email validation.
- User login with correct and incorrect passwords.
- JWT token generation and validation.
- Access to protected endpoints.
- Successful order placement.
- Insufficient stock validation.
- Order history retrieval.
- Database verification using MySQL Workbench.

## 📚 Learning Outcomes

- Understanding Spring Boot architecture.
- Building RESTful APIs.
- Integrating Spring Boot with MySQL.
- Performing CRUD operations using Spring Data JPA.
- Implementing Spring Security and JWT.
- Securing passwords using BCrypt.
- Managing entity relationships.
- Implementing transactional order processing.
- Testing APIs using Postman.

## 🚀 Future Enhancements

- React.js frontend integration.
- Shopping cart interface.
- Checkout and payment integration.
- Admin dashboard.
- Product management interface.
- Order tracking.

## 👨‍💻 Author

**Baskar J**

Computer Science and Engineering

Saveetha Engineering College

---

<p align="center">
  <b>Built with Java, Spring Boot and MySQL ❤️</b>
</p>