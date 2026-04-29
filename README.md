# Employee REST API – Exception Handling & Validation

## Overview

This project is a **Spring Boot RESTful application** that demonstrates:

*  REST API development
*  Bean Validation using `jakarta.validation`
*  Global Exception Handling using `@RestControllerAdvice`
*  Integration with SQL Server Express
*  Meaningful JSON error responses

---

##  What is a RESTful Application?

A RESTful application is a web service that:

* Uses HTTP methods (GET, POST, PUT, DELETE)
* Works with resources (like Employee data)
* Returns data in JSON format
* Is stateless
* Uses proper HTTP status codes

---

##  HTTP Methods Used

| Method | Operation | Description         |
| ------ | --------- | ------------------- |
| GET    | Read      | Fetch employee data |
| POST   | Create    | Add new employee    |
| PUT    | Update    | Modify employee     |
| DELETE | Delete    | Remove employee     |

---

##  Application Flow

Client (Postman / Browser)
⬇
Controller
⬇
Service
⬇
Repository (JPA)
⬇
SQL Server Database

---

##  Aim

* Implement input validation using annotations
* Handle exceptions globally
* Return meaningful error responses in JSON format
* Connect Spring Boot with SQL Server database

---

##  Technologies Used

* Java 17
* Spring Boot
* Spring Data JPA
* SQL Server Express
* Hibernate
* Maven
* Postman

---

##  Database Setup (SQL Server)

```sql
CREATE DATABASE employee;
GO

USE employee;

CREATE TABLE employees (
    id BIGINT IDENTITY(1,1) PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    salary DECIMAL(10,2) NOT NULL,
    department VARCHAR(100) NOT NULL
);
```

---

##  Project Setup

### 1. Clone Repository

```bash
git clone https://github.com/Aishwarya12112005/-exception-handling-and-validation-to-the-RESTful-application..git
```

### 2. Open in Spring Tools Suite (STS)

* File → Import → Existing Maven Project
* Select project folder

---

##  Dependencies (pom.xml)

* Spring Web
* Spring Data JPA
* SQL Server JDBC Driver
* Spring Boot Validation

---

##  Configuration (application.properties)

```properties
spring.datasource.url=jdbc:sqlserver://localhost\\SQLEXPRESS;databaseName=employee;encrypt=false
spring.datasource.username=studentuser
spring.datasource.password=yourpassword

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.SQLServerDialect
```

---

##  Validation Example

```java
@NotBlank(message = "Name cannot be empty")
private String name;

@Email(message = "Invalid email format")
private String email;
```

---

##  Global Exception Handling

Implemented using:

```java
@RestControllerAdvice
```

Handles:

* Validation errors
* Resource not found
* General exceptions

---

##  Sample API Endpoints

| Method | Endpoint        | Description       |
| ------ | --------------- | ----------------- |
| GET    | /employees      | Get all employees |
| POST   | /employees      | Create employee   |
| PUT    | /employees/{id} | Update employee   |
| DELETE | /employees/{id} | Delete employee   |

---

##  Testing

Use **Postman** to test APIs:

* Send JSON requests
* Validate responses
* Check error handling

---

##  Features

* Clean architecture (Controller → Service → Repository)
* Validation using annotations
* Centralized exception handling
* SQL Server integration
* JSON-based responses

---

