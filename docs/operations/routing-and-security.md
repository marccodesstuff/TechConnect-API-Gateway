# Routing and Security

The API Gateway uses Spring Cloud Gateway's reactive routing and a custom Global Filter for JWT authentication.

## Routing Logic

Routes are defined in `src/main/resources/application.yml`. 

### Defined Routes

| ID | Path Pattern | Target URI | Description |
|---|---|---|---|
| `auth-route` | `/api/v1/auth/**` | `http://identity-service:8080/` | Routes to the Identity Service for login/registration. |
| `opportunity-route` | `/api/v1/opportunities/**` | `lb://opportunity-service` | Load-balanced route to the Opportunity Service via Eureka. |

## Security Implementation: JwtAuthFilter

The gateway implements a custom `GlobalFilter` (`JwtAuthFilter.java`) that executes for every request.

### 1. Public Paths (Exempt)
The filter allows requests to the following paths without a token:
- `/api/v1/auth/**`
- `/api/v1/auth`

### 2. Token Validation
For all other paths, the filter:
1. Checks for the `Authorization` header.
2. Verifies it starts with `Bearer `.
3. Uses the `jwt.secret` (from configuration) to parse and validate the token signature using the `RS256` or `HS256` algorithm (via `jjwt`).

### 3. Unauthorized Responses
If validation fails, the gateway returns a `401 Unauthorized` status with a JSON body:

```json
{
  "timestamp": "2024-01-01T00:00:00Z",
  "status": 401,
  "message": "Invalid or expired token",
  "data": null
}
```

## Security Configuration

The JWT secret is managed in `application.yml`:

```yaml
jwt:
  secret: ${JWT_SECRET:change-me-please-256-bit-secret-change-me-please}
```

> [!IMPORTANT]
> In production environments, always override the default secret using the `JWT_SECRET` environment variable with a strong, 256-bit key.
