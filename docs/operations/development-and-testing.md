# Development and Testing

Guidelines for building and running the TechConnect API Gateway.

## Prerequisites

- **Java 17** (JDK)
- **Maven 3.8+**
- (Optional) **Docker**

## Building the Project

The project is managed with Maven. To compile and package the application:

```bash
mvn clean package
```

This will generate a runnable JAR file in the `target/` directory: `tp-api-gateway-0.0.1-SNAPSHOT.jar`.

## Running the Application

### 1. Locally via Maven
```bash
mvn spring-boot:run
```

### 2. Locally via JAR
```bash
java -jar target/tp-api-gateway-0.0.1-SNAPSHOT.jar
```

### 3. via Docker
```bash
docker build -t api-gateway .
docker run -p 8080:8080 api-gateway
```

## Configuration

The gateway is configured via `src/main/resources/application.yml`. Key environment variables you can override:

| Environment Variable | Default Value | Description |
|---|---|---|
| `SERVER_PORT` | `8080` | Port the gateway listens on. |
| `EUREKA_CLIENT_SERVICEURL_DEFAULTZONE` | `http://discovery-server:8761/eureka/` | URL of the Eureka Discovery Server. |
| `JWT_SECRET` | `change-me-please...` | Secret key used for signing/validating JWTs. |

## Monitoring

The gateway exposes Spring Boot Actuator endpoints for health monitoring:

- **Health Check**: `http://localhost:8080/actuator/health`
- **Info**: `http://localhost:8080/actuator/info`

## Testing

Currently, tests are not implemented in this repository. Adding integration tests using `WebTestClient` is recommended for future development.
