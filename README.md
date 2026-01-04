# TechConnect API Gateway

The central entry point and security layer for the TechConnect microservices ecosystem. Built with Spring Cloud Gateway and Java 17.

## 📖 Documentation

A comprehensive guide to the operation, routing, and security of this repository can be found in the **[docs/ folder](./docs/README.md)**.

### Quick Links
- **[System Context](./docs/operations/system-context.md)** – Role in the ecosystem.
- **[Routing & Security](./docs/operations/routing-and-security.md)** – How requests are processed.
- **[Development Guide](./docs/operations/development-and-testing.md)** – Build and run instructions.

## Quick Start (Docker)

If you have the TechConnect ecosystem set up, you can run the gateway via Docker:

```bash
docker build -t techconnect-api-gateway .
docker run -p 8080:8080 techconnect-api-gateway
```

For more ways to run the project, see the [Development Guide](./docs/operations/development-and-testing.md).
