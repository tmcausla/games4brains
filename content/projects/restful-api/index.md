# RESTful API & React Client

[< Back Home](/)

I built this project to give myself hands-on experience designing and consuming a REST API from both sides of the application.

The backend provides CRUD operations for a simple pet-management service, while a React client consumes the API and manages the resulting application state.

## Tech Stack

- JavaScript
- Node.js
- Express
- React
- Git / GitHub
- Supertest
- OpenAPI / Swagger

## How It Works

The backend is organized into a series of layers, with each one being responsible for a specific job within the application.

```
React Client
    |
    v
REST API
    |
    v
Routes
    |
    v
Controllers
    |
    v
Data Access
```

The Express application exposes endpoints for creating, reading, updating, and deleting pets' profiles.  

1. Routes determine endpoint has been requested
2. Controllers handle the HTTP request and response
3. Data access layer handles the underlying pet data

This separation keeps the individual pieces small and makes the application easier to understand and modify.

## REST API

The API provides the standard CRUD operations:

- **GET /pets** - retrieve all pet data
- **GET /pets/:id** - retrieve data for a specific pet
- **POST /pets** - create data for a new pet profile
- **PUT /pets/:id** - update data for an existing pet
- **DELETE /pets/:id** - delete all profile data for a specific pet

The API is also documented using OpenAPI/Swagger, so the available endpoints and request formats can be explored without having to dig through the source code.

## React Client

The project also includes a React client that consumes the API.

This gave me an opportunity to work with the API as an actual client rather than treating the backend as an isolated exercise.  The client is responsible for making requests to the API and managing the resulting application state.  

Building both sides of the application also made the relationship between an API's interface and the software consuming it much more apparent.

## Testing

I used Supertest to write integration tests against the Express application.

The tests exercise the API through its HTTP endpoints rather than testing each function in isolation.  This allowed me to verify both the returned HTTP status codes and the data returned by the API.

The CRUD workflow is tested as a complete sequence, including creating and modifying records and then verifying that they can subsequently be removed.  

## API Documentation

The project includes an interactive Swagger interface generated from the API's OpenAPI's specification.  

![Swagger documentation showing five CRUD endpoints](/images/api-overview.png) 

![GET /pets JSON response](/images/api-get-endpoint.png)

[< Back Home](/)
