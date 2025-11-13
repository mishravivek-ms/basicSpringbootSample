# Book Store REST API Documentation

## Overview
This is a Spring Boot application that provides a RESTful API for managing books in a book store. The application uses an H2 in-memory database for data persistence.

## Technology Stack
- **Framework**: Spring Boot 3.1.2
- **Java Version**: 17
- **Build Tool**: Maven
- **Database**: H2 (In-Memory)
- **ORM**: Spring Data JPA / Hibernate

## Architecture
The application follows a three-layered architecture:

1. **Controller Layer** (`BookController.java`)
   - Handles HTTP requests and responses
   - Maps REST endpoints to service methods
   - Returns appropriate HTTP status codes

2. **Service Layer** (`BookService.java`)
   - Contains business logic
   - Manages transactions
   - Handles exceptions

3. **Repository Layer** (`BookRepository.java`)
   - Extends JpaRepository
   - Handles database operations
   - Provides CRUD functionality

4. **Entity Layer** (`Book.java`)
   - Represents the Book entity
   - Maps to the `books` table in the database

## Database Configuration
- **Database URL**: `jdbc:h2:mem:bookstore`
- **H2 Console**: Accessible at `http://localhost:8080/h2-console`
- **Username**: `sa`
- **Password**: (empty)

## API Endpoints

### Base URL
```
http://localhost:8080/api/books
```

### 1. Create a Book
**Endpoint**: `POST /api/books`

**Request Body**:
```json
{
  "title": "The Great Gatsby",
  "author": "F. Scott Fitzgerald",
  "isbn": "978-0743273565",
  "price": 15.99
}
```

**Response**: `201 Created`
```json
{
  "id": 1,
  "title": "The Great Gatsby",
  "author": "F. Scott Fitzgerald",
  "isbn": "978-0743273565",
  "price": 15.99
}
```

### 2. Get All Books
**Endpoint**: `GET /api/books`

**Response**: `200 OK`
```json
[
  {
    "id": 1,
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "isbn": "978-0743273565",
    "price": 15.99
  },
  {
    "id": 2,
    "title": "To Kill a Mockingbird",
    "author": "Harper Lee",
    "isbn": "978-0061120084",
    "price": 18.99
  }
]
```

### 3. Get Book by ID
**Endpoint**: `GET /api/books/{id}`

**Response**: `200 OK` (if found) or `404 Not Found`
```json
{
  "id": 1,
  "title": "The Great Gatsby",
  "author": "F. Scott Fitzgerald",
  "isbn": "978-0743273565",
  "price": 15.99
}
```

### 4. Update a Book
**Endpoint**: `PUT /api/books/{id}`

**Request Body**:
```json
{
  "title": "The Great Gatsby - Updated",
  "author": "F. Scott Fitzgerald",
  "isbn": "978-0743273565",
  "price": 19.99
}
```

**Response**: `200 OK` (if found) or `404 Not Found`
```json
{
  "id": 1,
  "title": "The Great Gatsby - Updated",
  "author": "F. Scott Fitzgerald",
  "isbn": "978-0743273565",
  "price": 19.99
}
```

### 5. Delete a Book
**Endpoint**: `DELETE /api/books/{id}`

**Response**: `204 No Content` (if deleted) or `404 Not Found`

## Running the Application

### Build the Application
```bash
mvn clean compile
```

### Run the Application
```bash
mvn spring-boot:run
```

The application will start on `http://localhost:8080`

### Package the Application
```bash
mvn clean package
```

### Run the JAR
```bash
java -jar target/demo-0.0.1-SNAPSHOT.jar
```

## Testing the API

### Using cURL

#### Create a Book
```bash
curl -X POST http://localhost:8080/api/books \
  -H "Content-Type: application/json" \
  -d '{"title":"The Great Gatsby","author":"F. Scott Fitzgerald","isbn":"978-0743273565","price":15.99}'
```

#### Get All Books
```bash
curl -X GET http://localhost:8080/api/books
```

#### Get Book by ID
```bash
curl -X GET http://localhost:8080/api/books/1
```

#### Update a Book
```bash
curl -X PUT http://localhost:8080/api/books/1 \
  -H "Content-Type: application/json" \
  -d '{"title":"The Great Gatsby - Updated","author":"F. Scott Fitzgerald","isbn":"978-0743273565","price":19.99}'
```

#### Delete a Book
```bash
curl -X DELETE http://localhost:8080/api/books/1
```

## Book Entity Structure

| Field  | Type   | Description                    |
|--------|--------|--------------------------------|
| id     | Long   | Primary key (auto-generated)   |
| title  | String | Title of the book              |
| author | String | Author of the book             |
| isbn   | String | ISBN number                    |
| price  | Double | Price of the book              |

## Error Handling
The API returns appropriate HTTP status codes:
- `200 OK` - Successful GET/PUT request
- `201 Created` - Successful POST request
- `204 No Content` - Successful DELETE request
- `404 Not Found` - Resource not found

## Features
- ✅ Complete CRUD operations
- ✅ RESTful API design
- ✅ In-memory H2 database
- ✅ Spring Data JPA for database operations
- ✅ Proper HTTP status codes
- ✅ Constructor-based dependency injection
- ✅ Clean architecture (Controller-Service-Repository pattern)

## Future Enhancements
- Add input validation using Bean Validation (@Valid, @NotNull, etc.)
- Implement pagination for GET all books endpoint
- Add exception handling with @ControllerAdvice
- Add unit and integration tests
- Add API documentation with Swagger/OpenAPI
- Implement search and filter capabilities
- Add authentication and authorization
