# Spring Boot Demo Application

A simple Spring Boot application demonstrating REST API development with H2 database.

## Features

- **Demo REST Controller** - Simple "Hello" endpoint at `/`
- **Book Store REST API** - Complete CRUD operations for managing books

## Book Store API

The Book Store REST API provides a complete set of CRUD operations for managing books in a bookstore.

### Quick Start

1. **Build the application**:
   ```bash
   mvn clean compile
   ```

2. **Run the application**:
   ```bash
   mvn spring-boot:run
   ```

3. **Access the application**:
   - Application: http://localhost:8080
   - H2 Console: http://localhost:8080/h2-console
   - Book API: http://localhost:8080/api/books

### API Endpoints

| Method | Endpoint              | Description          |
|--------|-----------------------|----------------------|
| POST   | /api/books            | Create a new book    |
| GET    | /api/books            | Get all books        |
| GET    | /api/books/{id}       | Get book by ID       |
| PUT    | /api/books/{id}       | Update a book        |
| DELETE | /api/books/{id}       | Delete a book        |

### Example Usage

**Create a book**:
```bash
curl -X POST http://localhost:8080/api/books \
  -H "Content-Type: application/json" \
  -d '{"title":"The Great Gatsby","author":"F. Scott Fitzgerald","isbn":"978-0743273565","price":15.99}'
```

**Get all books**:
```bash
curl http://localhost:8080/api/books
```

For complete API documentation, see [API_DOCUMENTATION.md](API_DOCUMENTATION.md)

## Technology Stack

- **Framework**: Spring Boot 3.1.2
- **Java**: 17
- **Build Tool**: Maven
- **Database**: H2 (In-Memory)
- **ORM**: Spring Data JPA

## Project Structure

```
src/main/java/com/example/demo/
├── DemoApplication.java       # Main application class
├── DemoController.java        # Demo REST controller
├── Book.java                  # Book entity
├── BookController.java        # Book REST controller
├── BookService.java           # Book service layer
└── BookRepository.java        # Book repository layer
```

## Architecture

The application follows a three-layered architecture:

1. **Controller Layer** - Handles HTTP requests and responses
2. **Service Layer** - Contains business logic
3. **Repository Layer** - Handles database operations

## Building & Running

### Build
```bash
mvn clean package
```

### Run
```bash
java -jar target/demo-0.0.1-SNAPSHOT.jar
```

## Database

The application uses H2 in-memory database:
- **URL**: `jdbc:h2:mem:bookstore`
- **Username**: `sa`
- **Password**: (empty)
- **Console**: http://localhost:8080/h2-console

## License

This is a demo project for learning purposes.
