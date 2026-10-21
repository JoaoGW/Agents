# [PROJECT_NAME] — Design Standards

## 1. Setup status

This is an unconfigured design template. Before creating branded screens, ask the user for the missing information below and record the answers. Reuse requirements already supplied by the user; do not ask the same question twice. Do not treat placeholders as approved values or display them in a finished interface.

| Decision | Placeholder |
| --- | --- |
| Project display name | [PROJECT_NAME] |
| Organization or brand, if applicable | [ORGANIZATION_NAME] |
| Product purpose | [PROJECT_PURPOSE] |
| Intended audience | [TARGET_AUDIENCE] |
| Target platforms | [TARGET_PLATFORMS] |
| Supported languages | [SUPPORTED_LANGUAGES] |
| Approved reference designs or assets, if any | [DESIGN_REFERENCE] |
| Brand colors and semantic feedback colors | [COLOR_TOKENS] |
| Typography and font sources | [TYPOGRAPHY] |
| Spacing, radius and elevation | [LAYOUT_TOKENS] |
| Component library preference, if any | [COMPONENT_LIBRARY] |
| Navigation and responsive conventions | [NAVIGATION_AND_RESPONSIVENESS] |

Use the same identity answers as the New Project Setup section in CLAUDE.md. Do not infer a brand, organization, domain, website, Figma file, person or business workflow from this template or another project.

## 2. Visual tokens and components

- Record the approved colors, typography, spacing, radius and elevation in the fields above.
- Identify the actual runtime source of tokens after inspecting or scaffolding the project; document its path here rather than assuming a file already exists.
- Centralize approved tokens instead of scattering raw values throughout screens.
- Inspect and reuse existing components before adding new primitives.
- No component library is predefined. Confirm any needed library choice with the user and follow the dependency approval rules in CLAUDE.md.
- Follow the approved identity consistently across screens.

## 3. Interface behavior

- Define navigation and layout from the current project's approved requirements.
- Cover normal, hover or pressed, focus, disabled, loading, empty, success and error states where applicable.
- Use clear labels and persistent feedback when the user needs to recover from an error.
- Do not simulate successful actions while the real operation is pending.
- Do not invent sample product records, metrics, testimonials or organization details for a finished interface.
- Business rules are not defined here. Ask for the new project's requirements before implementing roles, permissions, domain workflows or file restrictions.

## 4. Accessibility, localization and motion

- Use semantic controls, descriptive accessible names, visible focus and keyboard support.
- Preserve minimum AA contrast; normal text needs at least 4.5:1 contrast.
- Use generous touch targets, at least 44 × 44 px for web controls where applicable.
- Never communicate an action, status or validation error through color or an icon alone.
- Support text scaling, content overflow and reduced-motion preferences.
- Use the languages confirmed during setup; do not assume bilingual content or a particular locale.
- Provide useful alt text for informative images and appropriate treatment for decorative images.

## 5. Acceptance checks

- Is project identity confirmed and free of unresolved placeholders in the delivered UI?
- Do tokens and components follow the approved visual reference?
- Is the primary task clear at the target viewport sizes?
- Are loading, empty, disabled and error states usable where relevant?
- Can the interface be operated with a keyboard and assistive technology?
- Have all domain behaviors been established by the user for this project?
