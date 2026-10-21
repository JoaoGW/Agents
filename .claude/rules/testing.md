# Testing Rules

paths:
  - "**/*.{test,spec}.{ts,tsx}"
  - "e2e/**/*.ts"
  - "jest.config.*"
  - "playwright.config.ts"
---

## General

- Test observable behavior and public contracts, not implementation details.
- Add or update tests whenever behavior changes.
- For a reproducible bug, add a failing regression test before or with the fix.
- Keep tests deterministic, independent, and readable.
- Do not weaken assertions, delete coverage, increase arbitrary timeouts, or skip tests to make a change pass.

## Layers and local entry point

- `bash scripts/test.sh unit`: docs/agents, lint/types, frontend Jest, backend Vitest and Supertest HTTP integration.
- `bash scripts/test.sh ui`: Playwright UI flows with a mocked API.
- `bash scripts/test.sh e2e`: disposable PostgreSQL, migrations, real HTTP API and browser through Next to Nest.
- `bash scripts/test.sh all`: complete local sequence. The CI uses these same scripts.
- See `docs/VALIDACAO.md` for setup, ports, evidence and agent activation. Never use a personal database or production credentials.
- Mocked HTTP/UI tests do not prove migrations, relational constraints or persistence. Cover those with the real suite when changing an integration boundary.

## Jest

- Unit-test pure logic, validation, route behavior, and isolated components.
- Mock external boundaries only: network, time, browser APIs, repositories, and third-party services.
- Do not mock the unit under test.
- Cover expected success, invalid input, failure behavior, and relevant edge cases.

## Playwright

- Add E2E coverage for changed user-facing flows.
- Prefer locators by role, label, visible text, or stable test ID.
- Do not use arbitrary sleeps; wait for observable UI or network state.
- Keep each test isolated and independent of production data.
- Verify critical validation, permission, error, and recovery flows when affected.
- UI mocks live in `front-end/e2e/`; `front-end/e2e-real/` must not intercept API routes or forge session cookies.
- Use `PLAYWRIGHT_CHANNEL=chrome` for an installed Chrome; do not create temporary Playwright configs.

## Backend and database

- Keep Vitest unit tests beside the source and HTTP integration in `back-end/test/app.e2e-spec.ts`.
- The Supertest suite mounts production guards/pipes/serialization with fake repositories; state this limitation in reports.
- Real HTTP/database tests live in `back-end/test/http.database.test.mjs` and run only through the isolated root orchestrator.
- Test migrations, actual persisted values, role denials, relational boundaries, soft delete and cascades where relevant.
- Keep cleanup scoped to resources created by the current run and fail on occupied ports rather than reuse an unknown service.

## Validation Sequence

Run the narrowest relevant test first, then run the applicable project checks:

`npm run lint`  
`npm run typecheck`  
`npm test`  
`npm run test:e2e`

If a command is unavailable, fails because of unrelated existing work, or cannot run locally, report that fact clearly for the user to see/validate and give a veridict about what to do next.
