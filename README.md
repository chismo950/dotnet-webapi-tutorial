# C# Web API Learning Project

This repository contains a learning project based on the tutorial series: **[ASP.NET Core Web API Tutorial](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWunQnm3WnZxJrseIw2zSAk)**

## Overview

A simple Todo API built with ASP.NET Core 8.0 that demonstrates fundamental web API concepts including CRUD operations, middleware, dependency injection, and endpoint filtering.

## Features

- **RESTful Todo API** with full CRUD operations
- **In-memory data storage** using a singleton service
- **Custom middleware** for request/response logging
- **URL rewriting** (`/tasks/*` redirects to `/todos/*`)
- **Endpoint filtering** with validation for business rules
- **Typed results** for better API responses
- **HTTP test files** for API testing

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/todos` | Get all todos |
| `GET` | `/todos/{id}` | Get a specific todo by ID |
| `POST` | `/todos` | Create a new todo |
| `DELETE` | `/todos/{id}` | Delete a todo by ID |
| `GET` | `/version` | Get API version |

## Project Structure

```
├── Program.cs              # Main application entry point
├── MyRequests.http         # HTTP test requests
├── web_api.csproj         # Project configuration
├── appsettings.json       # Application settings
└── Properties/
    └── launchSettings.json # Launch configuration
```

## Key Learning Concepts

### 1. Minimal APIs
The project uses ASP.NET Core's minimal API approach, defining endpoints directly in `Program.cs` without controllers.

### 2. Dependency Injection
- `ITaskService` interface with `InMemoryTaskService` implementation
- Registered as a singleton service

### 3. Middleware Pipeline
- Custom logging middleware that tracks request start/finish times
- URL rewriting middleware for backward compatibility

### 4. Endpoint Filters
- Validation filter that prevents:
  - Creating todos with past due dates
  - Creating already completed todos

### 5. Typed Results
Using `Results<Ok<Todo>, NotFound>` for better type safety and API documentation.

## Running the Application

1. **Prerequisites**: .NET 8.0 SDK
2. **Run the application**:
   ```bash
   dotnet run
   ```
3. **Test the API**: Use the requests in `MyRequests.http` or access endpoints at `http://localhost:5045`

## Sample Usage

### Create a Todo
```http
POST http://localhost:5045/todos
Content-Type: application/json

{
  "id": 1,
  "name": "Learn ASP.NET Core",
  "dueDate": "2026-01-01",
  "isCompleted": false
}
```

### Get All Todos
```http
GET http://localhost:5045/todos
```

## Technologies Used

- **ASP.NET Core 8.0** - Web framework
- **C# 12** - Programming language
- **Minimal APIs** - Lightweight API approach
- **In-memory storage** - Simple data persistence

## Learning Resources

This project follows the comprehensive tutorial series by Nick Chapsas:
🎥 **[ASP.NET Core Web API Tutorial Playlist](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWunQnm3WnZxJrseIw2zSAk)**

The tutorial covers essential web API concepts from basics to advanced topics, making it perfect for learning modern ASP.NET Core development.