# API Contracts

This document defines API design standards, conventions, and contracts for this project.

---

## API Style

**Type**: [REST, GraphQL, gRPC, or combination]

**Version**: [Current API version]

**Base URL**: 
- Development: `http://localhost:[port]/api`
- Staging: `https://staging.example.com/api`
- Production: `https://api.example.com`

---

## REST API Standards

### HTTP Methods

| Method | Purpose | Idempotent | Safe |
|--------|---------|------------|------|
| GET | Retrieve resources | Yes | Yes |
| POST | Create resource | No | No |
| PUT | Update/replace resource | Yes | No |
| PATCH | Partial update | No* | No |
| DELETE | Remove resource | Yes | No |

*PATCH can be designed to be idempotent

### Endpoint Naming

**Use nouns, not verbs**:
- ✅ `GET /users`
- ❌ `GET /getUsers`

**Use plural for collections**:
- ✅ `GET /users`
- ❌ `GET /user`

**Use kebab-case for multi-word resources**:
- ✅ `GET /user-profiles`
- ❌ `GET /userProfiles`

**Nested resources** (when appropriate):
- ✅ `GET /users/{id}/orders`
- ✅ `GET /orders/{id}/items`

**Actions** (when REST doesn't fit):
- ✅ `POST /users/{id}/activate`
- ✅ `POST /orders/{id}/cancel`

---

## URL Structure

### Pattern

```
{base_url}/{version}/{resource}/{id}/{sub-resource}?{query_params}
```

### Examples

```
GET  /api/v1/users
GET  /api/v1/users/123
GET  /api/v1/users/123/orders
POST /api/v1/users
PUT  /api/v1/users/123
DELETE /api/v1/users/123
```

---

## Request Format

### Headers

**Required**:
```http
Content-Type: application/json
Accept: application/json
Authorization: Bearer {token}
```

**Optional**:
```http
X-Request-ID: {unique-id}
Accept-Language: en-US
User-Agent: {client-info}
```

### Request Body

**Format**: JSON

**Example**:
```json
{
  "email": "user@example.com",
  "name": "John Doe",
  "preferences": {
    "newsletter": true,
    "notifications": false
  }
}
```

**Conventions**:
- Use camelCase for field names
- Use ISO 8601 for dates: `"2024-01-15T10:30:00Z"`
- Use null for absent values, omit for optional fields
- Arrays should be empty `[]` not null

---

## Response Format

### Success Response

**Status Code**: 2xx

**Body Structure**:
```json
{
  "data": {
    "id": "123",
    "email": "user@example.com",
    "name": "John Doe",
    "createdAt": "2024-01-15T10:30:00Z"
  },
  "meta": {
    "requestId": "abc-123",
    "timestamp": "2024-01-15T10:30:00Z"
  }
}
```

**Collection Response**:
```json
{
  "data": [
    { "id": "1", "name": "Item 1" },
    { "id": "2", "name": "Item 2" }
  ],
  "pagination": {
    "page": 1,
    "perPage": 20,
    "total": 100,
    "totalPages": 5
  },
  "meta": {
    "requestId": "abc-123"
  }
}
```

### Error Response

**Status Code**: 4xx or 5xx

**Body Structure**:
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input provided",
    "details": [
      {
        "field": "email",
        "message": "Email format is invalid"
      }
    ]
  },
  "meta": {
    "requestId": "abc-123",
    "timestamp": "2024-01-15T10:30:00Z"
  }
}
```

---

## Status Codes

### Success (2xx)

- **200 OK**: Successful GET, PUT, PATCH, DELETE
- **201 Created**: Successful POST (resource created)
- **202 Accepted**: Request accepted, processing async
- **204 No Content**: Successful DELETE (no body)

### Client Errors (4xx)

- **400 Bad Request**: Invalid request format or data
- **401 Unauthorized**: Missing or invalid authentication
- **403 Forbidden**: Authenticated but not authorized
- **404 Not Found**: Resource doesn't exist
- **409 Conflict**: Resource conflict (e.g., duplicate)
- **422 Unprocessable Entity**: Validation errors
- **429 Too Many Requests**: Rate limit exceeded

### Server Errors (5xx)

- **500 Internal Server Error**: Unexpected server error
- **502 Bad Gateway**: Upstream service error
- **503 Service Unavailable**: Service temporarily down
- **504 Gateway Timeout**: Upstream timeout

---

## Error Codes

### Standard Error Codes

| Code | HTTP Status | Description |
|------|-------------|-------------|
| `VALIDATION_ERROR` | 422 | Input validation failed |
| `UNAUTHORIZED` | 401 | Authentication required |
| `FORBIDDEN` | 403 | Insufficient permissions |
| `NOT_FOUND` | 404 | Resource not found |
| `CONFLICT` | 409 | Resource already exists |
| `RATE_LIMIT_EXCEEDED` | 429 | Too many requests |
| `INTERNAL_ERROR` | 500 | Server error |

### Domain-Specific Error Codes

| Code | HTTP Status | Description |
|------|-------------|-------------|
| `USER_NOT_FOUND` | 404 | User doesn't exist |
| `INVALID_CREDENTIALS` | 401 | Login failed |
| `EMAIL_ALREADY_EXISTS` | 409 | Email in use |
| `INSUFFICIENT_BALANCE` | 400 | Not enough funds |

---

## Authentication

### Method

[OAuth 2.0, JWT, API Keys, or combination]

### JWT Authentication (Example)

**Obtaining token**:
```http
POST /api/v1/auth/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "securepassword"
}
```

**Response**:
```json
{
  "data": {
    "accessToken": "eyJhbGciOiJIUzI1NiIs...",
    "refreshToken": "dGhpc2lzYXJlZnJlc2h0b2tlbg...",
    "expiresIn": 3600
  }
}
```

**Using token**:
```http
GET /api/v1/users/me
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

### Token Refresh

```http
POST /api/v1/auth/refresh
Content-Type: application/json

{
  "refreshToken": "dGhpc2lzYXJlZnJlc2h0b2tlbg..."
}
```

---

## Authorization

### Permission Model

[RBAC, ABAC, or custom model]

**Roles** (example):
- `admin` - Full access
- `user` - Standard user access
- `guest` - Limited read access

### Checking Permissions

Authorization checked on every request:
1. Verify authentication (valid token)
2. Extract user identity and roles
3. Check permission for requested resource/action
4. Return 403 if unauthorized

---

## Pagination

### Query Parameters

```
GET /api/v1/users?page=2&perPage=20
```

**Parameters**:
- `page`: Page number (starts at 1)
- `perPage`: Items per page (default: 20, max: 100)

### Response

```json
{
  "data": [...],
  "pagination": {
    "page": 2,
    "perPage": 20,
    "total": 157,
    "totalPages": 8,
    "hasNext": true,
    "hasPrevious": true
  },
  "links": {
    "first": "/api/v1/users?page=1&perPage=20",
    "prev": "/api/v1/users?page=1&perPage=20",
    "next": "/api/v1/users?page=3&perPage=20",
    "last": "/api/v1/users?page=8&perPage=20"
  }
}
```

### Cursor-Based Pagination (Alternative)

For high-performance or real-time data:

```
GET /api/v1/posts?cursor=eyJpZCI6MTIzfQ&limit=20
```

**Response**:
```json
{
  "data": [...],
  "pagination": {
    "nextCursor": "eyJpZCI6MTQzfQ",
    "hasMore": true
  }
}
```

---

## Filtering

### Query Parameters

```
GET /api/v1/users?status=active&role=admin
```

**Comparison operators** (if supported):
```
GET /api/v1/orders?total[gte]=100&createdAt[lt]=2024-01-01
```

Operators: `eq`, `ne`, `gt`, `gte`, `lt`, `lte`, `in`, `nin`

---

## Sorting

### Query Parameter

```
GET /api/v1/users?sort=createdAt:desc,name:asc
```

**Format**: `{field}:{direction}`

**Directions**: `asc` (ascending), `desc` (descending)

**Default**: [Specify default sort]

---

## Field Selection

### Sparse Fieldsets

Request only needed fields:

```
GET /api/v1/users?fields=id,name,email
```

**Response**:
```json
{
  "data": [
    { "id": "1", "name": "John", "email": "john@example.com" },
    { "id": "2", "name": "Jane", "email": "jane@example.com" }
  ]
}
```

---

## Versioning

### Strategy

**URL Versioning** (recommended for this project):
```
/api/v1/users
/api/v2/users
```

**Alternatives** (not used):
- Header versioning: `Accept: application/vnd.api.v1+json`
- Query parameter: `/api/users?version=1`

### Deprecation Policy

1. Announce deprecation with 6 months notice
2. Add `Deprecation` header to responses
3. Update documentation
4. Provide migration guide
5. Sunset old version after notice period

**Example header**:
```http
Deprecation: Sun, 11 Jul 2024 00:00:00 GMT
Link: </api/v2/users>; rel="successor-version"
```

---

## Rate Limiting

### Limits

**Authenticated requests**: [e.g., 1000 requests per hour]

**Unauthenticated requests**: [e.g., 100 requests per hour]

### Headers

**Response includes**:
```http
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 998
X-RateLimit-Reset: 1609459200
```

### Rate Limit Exceeded

**Status**: 429 Too Many Requests

**Response**:
```json
{
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "Too many requests. Please try again later.",
    "retryAfter": 3600
  }
}
```

**Header**:
```http
Retry-After: 3600
```

---

## CORS

### Allowed Origins

- Development: `http://localhost:*`
- Staging: `https://staging.example.com`
- Production: `https://example.com`, `https://www.example.com`

### Headers

```http
Access-Control-Allow-Origin: https://example.com
Access-Control-Allow-Methods: GET, POST, PUT, PATCH, DELETE, OPTIONS
Access-Control-Allow-Headers: Content-Type, Authorization
Access-Control-Max-Age: 86400
```

---

## Webhooks

### Registering Webhooks

```http
POST /api/v1/webhooks
Content-Type: application/json

{
  "url": "https://your-app.com/webhook",
  "events": ["user.created", "order.completed"],
  "secret": "your-webhook-secret"
}
```

### Webhook Payload

```json
{
  "id": "evt_123",
  "type": "user.created",
  "createdAt": "2024-01-15T10:30:00Z",
  "data": {
    "user": {
      "id": "123",
      "email": "user@example.com"
    }
  }
}
```

### Security

**Signature Header**:
```http
X-Webhook-Signature: sha256=5f9c4ab08cac7457e9111a6d4cbc...
```

**Verification**:
```
HMAC-SHA256(payload, secret) == signature
```

---

## Idempotency

### Idempotent Requests

For POST requests that should be idempotent:

```http
POST /api/v1/payments
Idempotency-Key: unique-key-123
Content-Type: application/json

{
  "amount": 100,
  "currency": "USD"
}
```

**Behavior**: Same key within 24 hours returns original response

---

## Caching

### Cache Headers

**Immutable resources**:
```http
Cache-Control: public, max-age=31536000, immutable
```

**Frequently changing**:
```http
Cache-Control: public, max-age=300
ETag: "33a64df551425fcc55e4d42a148795d9f25f89d4"
```

**No cache**:
```http
Cache-Control: no-cache, no-store, must-revalidate
```

### Conditional Requests

**Using ETag**:
```http
GET /api/v1/users/123
If-None-Match: "33a64df551425fcc55e4d42a148795d9f25f89d4"
```

**Response**: 304 Not Modified (if unchanged)

---

## API Documentation

### OpenAPI/Swagger

**Specification**: [Link to OpenAPI spec]

**Interactive Docs**: [Link to Swagger UI or similar]

### Example Requests

All endpoints documented with:
- Description
- Parameters
- Request example
- Response example
- Error cases

---

## API Endpoints Reference

### Authentication

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/auth/login` | User login |
| POST | `/auth/register` | User registration |
| POST | `/auth/refresh` | Refresh token |
| POST | `/auth/logout` | User logout |

### Users

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/users` | List users |
| GET | `/users/{id}` | Get user details |
| POST | `/users` | Create user |
| PUT | `/users/{id}` | Update user |
| DELETE | `/users/{id}` | Delete user |

### [Other Resources]

[Add more resource tables as needed]

---

## Testing

### Testing APIs

**Tool**: [e.g., Postman, Insomnia, curl, httpie]

**Collection**: [Link to Postman collection or similar]

### Example Requests

**Create user**:
```bash
curl -X POST https://api.example.com/v1/users \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer {token}" \
  -d '{
    "email": "user@example.com",
    "name": "John Doe"
  }'
```

---

## Changelog

### v1 (Current)

- Initial API release
- User management endpoints
- Authentication with JWT
- [Other features]

### Future Versions

**v2** (planned):
- [Planned breaking changes]
- [New features]

---

## Best Practices Summary

1. **Use standard HTTP methods correctly**
2. **Return appropriate status codes**
3. **Provide clear error messages**
4. **Version your API**
5. **Use consistent naming conventions**
6. **Include pagination for collections**
7. **Implement rate limiting**
8. **Validate all input**
9. **Log requests for debugging**
10. **Document everything**

---

**Last Updated**: [YYYY-MM-DD]

**API Version**: v1

**Support**: [Contact info or link]
