# REST Route Handler Rules

paths:
  - "app/api/**/*.{ts,tsx}"
---

## Route Design

- Implement APIs with Next.js Route Handlers under `app/api/`.
- Use resource-oriented paths and HTTP methods with their standard semantics.
- Do not add a parallel API convention when one already exists.
- Keep route handlers thin; move reusable business logic to the project layer already used by similar features.

## Input and Access Control

- Validate path parameters, query parameters, headers, and request bodies at the route boundary.
- Reject invalid input before business logic or persistence access.
- Authenticate and authorize before reading or modifying protected data.
- Never trust client-provided identity, role, ownership, price, permission, or state.

## Responses

- Return the resource representation directly for successful single-resource responses.
- Use a documented collection shape when pagination or metadata is needed.
- Do not add a generic `success: true` wrapper.
- Project error contract (both layers):
  - The NestJS back-end always answers errors as `{ "statusCode": 400, "message": "Texto em português.", "errors"?: ["..."] }` (`back-end/src/common/api-exception.filter.ts`; `errors` only on DTO validation).
  - Route handlers answer errors as `{ "error": "Texto em português." }`, which `lib/api-client.ts` reads. Build them with `lib/api-route.ts`: `apiError(status, message)` for checks done in the handler, `forwardApiResponse(response)` to pass the back-end response through, and `routeErrorResponse(error)` in the `catch`.
- Forward the back-end status unchanged (`201` on create, `204` without body, `4xx` errors). Never replace it with `200` or `500`.
- Handler-generated statuses: `400` for invalid input or a body that is not JSON, `401` without session, `502` when the back-end cannot be reached or returns a success body that is not JSON.
- Messages are short Portuguese sentences ending with a period that tell the user what to do (`Informe um valor válido.`, `Faça login para continuar.`). No route names, internal labels, or concatenated `error` objects.
- Never expose stack traces, internal identifiers, tokens, database details, or upstream error bodies.
Tests
- Test valid requests, invalid input, unauthenticated or unauthorized access, not-found behavior, and expected failure cases.
- Preserve backward compatibility unless the request explicitly authorizes a contract change.