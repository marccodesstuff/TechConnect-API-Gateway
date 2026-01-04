# TechConnect API Gateway Documentation

Welcome! This documentation provides a technical and operational guide for the TechConnect API Gateway.

## ⚙️ Operations

Critical information for running and understanding the gateway's role.

- **[System Context](./operations/system-context.md)** – How the gateway connects the frontend to backend services.
- **[Routing & Security](./operations/routing-and-security.md)** – Deep dive into route definitions and JWT validation logic.
- **[Development & Testing](./operations/development-and-testing.md)** – How to build, run, and test the gateway.

## 🛠️ Technical Details

- **Runtime**: Java 17
- **Framework**: Spring Boot 3.4.1 + Spring Cloud Gateway
- **Security**: JWT (via `jjwt`)
- **Service Discovery**: Eureka

---

**Quick Links:**
[Main Project README](../README.md) • [Maven Config](../pom.xml) • [Application Config](../src/main/resources/application.yml)
