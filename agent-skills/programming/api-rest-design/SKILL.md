---
name: api-rest-design
description: Design practical REST/JSON APIs with consistent errors, versioning, and auth boundaries. Use when adding backend endpoints or reviewing API shapes.
---

# REST API Design

## Defaults
- Nouns for resources: `/projects`, `/projects/{id}`
- Plural names; nest only one level deep when possible
- JSON camelCase or snake_case — pick one repo-wide
- Explicit error body: `{ "error": { "code", "message" } }`

## Status codes
| Code | When |
|------|------|
| 200/201 | success |
| 400 | validation |
| 401/403 | authz |
| 404 | missing |
| 409 | conflict |
| 429 | rate limit |
| 5xx | server fault |

## Workflow
1. List use cases, not tables.
2. Define request/response examples first.
3. Authn/authz matrix per route.
4. Idempotency for payments/webhooks.
5. OpenAPI or equivalent living doc.

## Pitfalls
- Returning 200 for all errors
- Leaking stack traces
- Breaking clients without version strategy

## Acceptance
- Happy path + 2 failure examples per endpoint documented
