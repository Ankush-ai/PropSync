
# PropSync - Property Management Application

PropSync is a property management application built using Spring Boot. It provides a backend API for managing properties with features such as user authentication, and CRUD operations for properties.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
  - [Authentication](#authentication)
  - [Property Operations](#property-operations)
- [Endpoints](#endpoints)
- [Development](#development)
- [Contributing](#contributing)
- [License](#license)

## Features

- User authentication (Login/Logout)
- CRUD operations for properties (View, Create, Update, Delete)

## Technologies Used

- Spring Boot
- Spring Data JPA
- Hibernate
- MySQL (or H2 for development)
- Lombok
- Spring DevTools

## Getting Started

### Prerequisites

- Java 8 or higher
- Maven
- MySQL (for production) or H2 (for development)

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/prop-sync.git
   ```

2. Navigate to the project directory:

   ```bash
   cd prop-sync
   ```

3. Build the project:

   ```bash
   mvn clean install
   ```

4. Run the application:

   ```bash
   mvn spring-boot:run
   ```

## Configuration

Configure the application properties in `src/main/resources/application.properties` or `src/main/resources/application.yml` according to your database and application requirements.

```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/propsync
spring.datasource.username=root
spring.datasource.password=password
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update

# Development Configuration
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
```

## Usage

### Authentication

- **Login:** Use the `/login` endpoint with valid credentials to authenticate and receive a token.

  ```http
  POST /login
  Content-Type: application/json

  {
    "username": "your-username",
    "password": "your-password"
  }
  ```

  Response:

  ```json
  {
    "token": "your-access-token"
  }
  ```

- **Logout:** Use the `/logout` endpoint to logout and invalidate the token.

  ```http
  POST /logout
  Authorization: Bearer your-access-token
  ```

### Property Operations

- **Create Property:** Use the `/api/v1/properties` endpoint with a POST request to create a new property.

  ```http
  POST /api/v1/properties
  Content-Type: application/json
  Authorization: Bearer your-access-token

  {
    "name": "Property Name",
    "description": "Property Description",
    "price": 100000
  }
  ```

- **Update Property:** Use the `/api/v1/properties/{propertyId}` endpoint with a PUT request to update an existing property.

  ```http
  PUT /api/v1/properties/{propertyId}
  Content-Type: application/json
  Authorization: Bearer your-access-token

  {
    "name": "Updated Property Name",
    "description": "Updated Property Description",
    "price": 120000
  }
  ```

- **Delete Property:** Use the `/api/v1/properties/{propertyId}` endpoint with a DELETE request to delete a property.

  ```http
  DELETE /api/v1/properties/{propertyId}
  Authorization: Bearer your-access-token
  ```

- **View Properties:** Use the `/api/v1/properties` endpoint with a GET request to retrieve a list of all properties.

  ```http
  GET /api/v1/properties
  Authorization: Bearer your-access-token
  ```

## Endpoints

- **Authentication:**
  - `POST /login`: Authenticate and receive an access token.
  - `POST /logout`: Logout and invalidate the access token.

- **Property Management:**
  - `POST /api/v1/properties`: Create a new property.
  - `PUT /api/v1/properties/{propertyId}`: Update an existing property.
  - `DELETE /api/v1/properties/{propertyId}`: Delete a property.
  - `GET /api/v1/properties`: Retrieve a list of all properties.

## Development

For development, H2 database is used by default. Access the H2 console at `http://localhost:8080/h2-console` with JDBC URL `jdbc:h2:mem:testdb`, username `sa`, and an empty password.

## Contributing

If you'd like to contribute, please fork the repository and create a pull request. We appreciate your contributions!

## License

This project is licensed under the [MIT License](LICENSE).

---

Feel free to customize this `README.md` according to your specific requirements and add more details as needed.
