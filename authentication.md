---
layout: default
title: Authentication
---

# Authentication

## Overview

The BarunCorp Public API uses token-based authentication. To access any endpoint, you first need to generate an authentication token using your existing BMS credentials.

## Endpoint: /auth/signin

**Method:** POST  
**URL:** `https://api-public.baruncorp.com/prod/auth/signin`

This endpoint is used to generate your token for further requests.

### Request Body

Provide your BMS email and password in JSON format:

```json
{
  "email": "you@example.com",
  "password": "your-password"
}
```

### Example Response

If your credentials are valid, you'll receive a JSON response with an `accessToken` and a `refreshToken`:

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImIwZDYxMjk1LWI3ZTgtNGY4NC05YWIzLWI2MjRjZDUyYmNhZCIsImlhdCI6MTc0MzY5NjM3MiwiZXhwIjoxNzQzNzgyNzcyfQ.gz67AZaUYaxmm6zWZWaYXu5b1XS8naJMZmwEN4yq2yg",
  "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImIwZDYxMjk1LWI3ZTgtNGY4NC05YWIzLWI2MjRjZDUyYmNhZCIsImlhdCI6MTc0MzY5NjM3MiwiZXhwIjoxNzQ0MzAxMTcyfQ.to9QaPj6C_FRlHLq6FNqkrY-7D2n8gZgDrhywUgH2-g"
}
```

## Using the Token

Include the token in the `Authorization` header of all subsequent requests. For example:

```
Authorization: Bearer YOUR_JWT_TOKEN
```

This token verifies your identity and authorizes your access to your organization's data within our BMS system.

## Security Note

- **Keep your token secure:** Do not expose your token publicly.
- **Token Expiration:** The `accessToken` will expire. Use the `refreshToken` to obtain a new access token when necessary.

If you encounter any issues or have questions about authentication, please contact [support@baruncorp.com](mailto:support@baruncorp.com).