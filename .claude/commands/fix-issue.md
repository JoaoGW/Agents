---
description: Investigate and fix a described defect with scoped implementation and verification.
argument-hint: "<issue description or local reproduction>"
---

# Fix Issue Workflow

Treat `$ARGUMENTS` as the issue scope.

## Process

1. Use the supplied defect description and reproduction steps. If required details are missing, ask the user for them. No external issue tracker is configured by this template.
2. Read the issue, relevant code, local documentation, existing tests, and related API contracts.
3. Define observable success criteria before editing.
4. Reproduce the problem with a focused test when practical.
5. Explain the smallest implementation plan if the change spans multiple files or layers.
6. Implement only the requested correction.
7. Run applicable lint, typecheck, unit, E2E, and build validation.
8. Report the result and unresolved limitations.

## Constraints

- Do not add dependencies, migrations, integrations, or unrelated refactors without approval.
- Do not update external services, create a pull request, commit, or push without explicit approval.
- Stop and ask for direction when the issue requires a product, API, security, data-model, or component configuration decision not already established.
