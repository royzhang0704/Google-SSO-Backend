# Google SSO Backend

A Spring Boot backend service for authentication and authorization, built as a foundation for implementing Google OAuth 2.0 Single Sign-On.

## Tech Stack

- **Java** 17
- **Spring Boot** 3.5.6
- **Spring Security** - Authentication and authorization framework
- **Spring Data JPA** - Database operations
- **PostgreSQL** - Relational database
- **Lombok** - Reduce boilerplate code
- **Bean Validation** - Input validation
- **Maven** - Dependency management

## Project Structure

```
src/
├── main/
│   ├── java/com/imsoft/ssobackend/
│   │   ├── config/         # Configuration classes
│   │   ├── controller/     # REST API controllers
│   │   ├── service/        # Business logic
│   │   ├── repository/     # Data access layer
│   │   ├── model/          # Entity classes
│   │   ├── dto/            # Data transfer objects
│   │   └── exception/      # Exception handling
│   └── resources/
│       └── application.yml # Application configuration
└── test/                   # Test cases
```

## Prerequisites

- Java 17 or higher
- Maven 3.8+
- PostgreSQL 14+

## Getting Started

### 1. Clone the repository

```bash
git clone git@github.com:royzhang0704/Google-SSO-Backend.git
cd Google-SSO-Backend
```

### 2. Database Setup

Create a PostgreSQL database:

```sql
CREATE DATABASE auth_db;
```

### 3. Configure Application

Create `src/main/resources/application.yml`:

```yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/auth_db
    username: your_username
    password: your_password
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
    properties:
      hibernate:
        format_sql: true

server:
  port: 8080
```

### 4. Run the Application

```bash
# Using Maven wrapper
./mvnw spring-boot:run

# Or using Maven
mvn spring-boot:run
```

The application will start at `http://localhost:8080`

## Development Roadmap

### Phase 1: Basic Authentication (Current)
- [ ] User registration
- [ ] Login with username/password
- [ ] JWT token generation and validation
- [ ] Password encryption with BCrypt
- [ ] Protected API endpoints

### Phase 2: OAuth2 Integration (Planned)
- [ ] Google OAuth2 login
- [ ] User profile synchronization
- [ ] Unified authentication flow

## Commit Message Convention

This project follows [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Build process or auxiliary tool changes

### Examples

```bash
feat(auth): implement user registration endpoint

Add POST /api/auth/register endpoint with email validation
and password encryption using BCrypt.

Closes #123
```

```bash
fix(security): correct JWT token expiration validation

The token was expiring 1 hour early due to timezone issue.
Changed to use UTC for consistent behavior.
```

## Available Scripts

```bash
# Run application
./mvnw spring-boot:run

# Run tests
./mvnw test

# Build JAR
./mvnw clean package

# Run with specific profile
./mvnw spring-boot:run -Dspring-boot.run.profiles=dev
```

## Testing

```bash
# Run all tests
./mvnw test

# Run specific test class
./mvnw test -Dtest=UserServiceTest

# Run tests with coverage
./mvnw test jacoco:report
```

Coverage report will be available at `target/site/jacoco/index.html`

## Related Repository

- Frontend: [Google-SSO-Frontend](https://github.com/royzhang0704/Google-SSO-Frontend) (Coming soon)

## License

MIT
