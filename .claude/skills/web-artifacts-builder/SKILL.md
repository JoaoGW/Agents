---
name: web-artifacts-builder
description: Create interactive, multi-component web artifacts and package a compatible browser frontend as one self-contained HTML file. Use for shareable prototypes, demos, and complex HTML artifacts; keep ordinary application work in its existing framework.
license: Complete terms in LICENSE.txt
---

# Web Artifacts Builder

Create a browser artifact, then deliver a self-contained HTML file. For a simple single-file HTML task, write the file directly instead of scaffolding an application.

This is a local adaptation of [Anthropic's skill](https://github.com/anthropics/skills/tree/main/skills/web-artifacts-builder). See [SOURCE.md](SOURCE.md) for provenance and changes.

## Project setup and scope

- Read the repository's CLAUDE.md, dependency restrictions, and frontend design template before choosing tools or visual identity.
- During a new project's setup, ask for the missing display name, package slug, audience, target platforms, languages, and visual references. Reuse answers already supplied; do not invent brand or business details.
- Use the confirmed identity and design tokens. No component library, external service, or domain workflow is predefined by this skill.
- Do not introduce or recommend Prisma or Zustand.
- Reuse the application's existing framework for production features. The starter below is an optional, isolated React/TypeScript/Vite workspace for a browser artifact; it does not replace a Next.js application or make Vite mandatory for other projects.
- A standalone HTML artifact cannot contain a server runtime. Do not represent backend-dependent behavior as working offline.

## Create an isolated artifact

Resolve the skill's directory before running its scripts; do not assume the current working directory is the skill folder.

After confirming the artifact's identity and destination, run:

```text
node <skill-directory>/scripts/init-artifact.mjs <new-directory> --name <confirmed-package-slug> --title <confirmed-display-name> --lang <confirmed-language-tag>
```

The script creates an empty, typed React entry point, plain CSS, Vite configuration and package.json. It refuses existing directories, performs no network access, installs no dependencies, and installs no global tooling. The starter's dependency versions are scoped to this optional workspace, not a repository-wide stack requirement.

Review package.json with the user before installing its dependencies unless the current request already authorizes them. From the artifact directory, use the project's approved package manager; with npm:

```text
npm install
npm run dev
```

Implement the requested artifact with the actual local components and approved styling system. Add only dependencies needed for the task and permitted by the repository. Confirm the current toolchain's Node requirements when changing the starter's pinned versions.

## Bundle a compatible frontend

The bundler requires a Vite 8 browser project with installed local dependencies and index.html at its root. For other frameworks, use their existing static export process or create an isolated compatible workspace; do not run the helper blindly against a server-rendered application.

```text
npm run typecheck
node <skill-directory>/scripts/bundle-artifact.mjs <artifact-directory> --output bundle.html
```

The helper uses the project's local Vite, builds in memory, and inlines JavaScript, CSS and imported assets. It does not install packages, change package.json or build configuration, remove a dist directory, or overwrite an existing output file. Choose a new output filename when needed. Both helpers support --help.

Keep assets in the import graph so they can be embedded. Remote assets, unresolved public paths, web workers and separately emitted chunks/assets require adaptation; the helper fails rather than claiming a file is self-contained. API requests and other runtime network behavior still require explicit review and cannot become offline just by bundling.

## Verify and deliver

- Validate the main interaction and relevant loading, empty and error states. Check the target viewports and accessible keyboard behavior when applicable.
- Open the generated HTML directly in a browser to verify the artifact works without a development server. Check console errors and unexpected network requests before claiming offline operation.
- Deliver the generated HTML with a usable local link or preview. Report the checks actually performed and any remaining runtime network requirements.

For interface work inside the application, use the frontend skill and its design context. Use this skill specifically when a shareable HTML artifact is the requested output.
