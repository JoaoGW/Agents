---
name: frontend
description: Design, implement, review, or fix frontend screens, components, responsive layouts, visual states, and user flows using the project's design.md and established UI system.
when_to_use: Use for requests involving UI, frontend bugs, screens, components, forms, navigation, responsiveness, accessibility, visual polish, or end-to-end user flows.
argument-hint: "[feature, screen, component, or UI issue]"
---

# Frontend Implementation Skill

Use this skill for `$ARGUMENTS`.

## Mandatory Design Context

Before making a frontend decision, read `${CLAUDE_SKILL_DIR}/design.md` completely.

Treat it as the project's visual and interaction source of truth. Apply only the standards actually defined there; do not copy domain-specific assumptions, tokens, components, workflows, or product language from another project.

Extract the requirements relevant to the current task:

- product and safety principles;
- visual tokens and their runtime source;
- typography, spacing, radius, elevation, and responsive rules;
- navigation and layout conventions;
- reusable components and their intended usage;
- feedback, loading, empty, error, and confirmation patterns;
- localization, accessibility, motion, and platform requirements;
- confirmations and destructive-action safeguards established by the user for the current project.

If `design.md` still contains unresolved setup placeholders, collect the missing answers from the user before creating branded screens. If it is missing, incomplete, conflicts with existing code, or does not define a required decision, inspect the current project patterns. Ask for direction instead of inventing a design system.

## Discovery Before Implementation

1. Inspect the affected screen, route, component, tests, and nearby implementations.
2. Identify reusable components, tokens, primitives, hooks, localization utilities, and layout patterns.
3. Inspect the installed component library, styling configuration and local components before adding or changing UI components.
4. Define the user-visible states required by the task: default, hover or pressed, focus, disabled, loading, empty, success, error, offline, and pending states when applicable.
5. Keep the implementation scoped to frontend behavior unless the user explicitly requests API or backend work.

## Component Library Protocol

No component library is predefined by this template.

1. Inspect the actual project dependencies, local components, theme tokens and styling configuration.
2. Ask for the user's component library preference during setup if one is needed and has not been specified.
3. Consult the installed library's official documentation for the specific component or configuration detail needed.
4. Verify compatibility before changing generated components, styling configuration, aliases or build configuration.
5. Review generated source and dependencies against the project's approved tokens and accessibility requirements.

Do not replace the existing component configuration, run broad component-generation commands or introduce a second styling system without explicit user approval.

## Implementation Rules

- Reuse project primitives, existing components, tokens, and established layouts before creating new variants.
- Use runtime token sources identified by `design.md`; never scatter raw visual values through screens.
- Preserve the current Server Component and Client Component boundaries.
- Keep interactive controls understandable without color, hover, or icons alone.
- Use clear labels, visible focus, accessible names, generous touch targets, and keyboard support where applicable.
- Use localization utilities required by the project. Do not add hard-coded user-facing strings when the project uses translation dictionaries.
- Make disabled actions explain why they are unavailable.
- Do not simulate a completed action while its real operation is still pending.
- Require explicit confirmation for actions marked as destructive, irreversible, safety-critical, or externally applied by `design.md`.
- Do not create decorative metrics, placeholder product data, ambiguous CTAs, or unrelated visual changes.
- You need to understand the `ai-design-rules.md` since it has all the commom mistake patterns that AI Agents uses to build a design for web and mobile applications which need to be avoided every time possible in this project, since it can't appear to be AI Slop content.

## Shareable HTML Artifacts

When the requested deliverable is a standalone HTML artifact, use the sibling `web-artifacts-builder` skill after resolving the project's design setup. Keep ordinary application features in the existing application framework.

## Responsive and State Validation

- Preserve the primary task and information hierarchy on narrow screens.
- Use larger layouts only to improve scanning, density, or workflow clarity.
- Verify text scaling, overflow, focus order, loading behavior, empty states, and error recovery.
- Do not hide critical state, warnings, or primary actions behind decorative UI.
- Respect reduced-motion preferences when supported by the platform.

## Testing and Browser Validation

- Add or update Jest tests for changed component behavior and state transitions.
- Add or update Playwright coverage for changed user-facing flows when applicable.
- Run browser validation only against local or approved test environments.
- Do not use browser automation to access personal, production, or third-party accounts without explicit approval.
- Run the applicable project scripts: lint, typecheck, unit tests, E2E tests, and build.

## Completion Report

Report:

- the design requirements applied from `design.md`;
- reused components, tokens, and patterns;
- UI states covered;
- validation commands run and their results;
- compatibility risks, skipped checks, or decisions that still need approval.
