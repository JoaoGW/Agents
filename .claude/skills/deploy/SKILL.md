# Deployment Readiness Workflow

Read `deploy-config.md` before doing anything else.

Description: Verify deployment readiness. Publishing is disabled until a provider and release process are explicitly approved.

- disable-model-invocation: true

## Current State

When `status` is `disabled`:

- Do not run a provider CLI.
- Do not create environments, projects, tokens, secrets, release tags, or external resources.
- Do not publish packages, deploy previews, or deploy production.
- Run only local readiness checks that exist in `package.json`.

## Readiness Checks

Run applicable commands in this order:

1. `npm run lint`
2. `npm run typecheck`
3. `npm test`
4. `npm run test:e2e`
5. `npm run build`

Stop at a failure only when later checks cannot provide useful information.

## Output Contract

Report:

- each command and its result;
- skipped commands and why;
- release blockers;
- whether the application is locally build-ready;
- the explicit statement: `Publishing remains disabled by deploy-config.md.`

Never bypass a disabled deployment configuration.