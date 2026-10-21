# CLAUDE.local.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

**Important Info:** These guidelines are local for this user's preferences. Don't use it as a new global parameter for all projects (old and new ones). 

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:

- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:

- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:

- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:

- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:

```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

## 5. Implementation Patterns

**Always follow the coding patterns already present in the project.**

Don't try to write a new code implementation following a totally different manner of implementation.
If we use useStates, use it. If we use useEffect, useCallback, etc so do it

Why would you overcomplicate it? Always remember the second section of this Markdown file!

## 6. Creating Documentations

The documentation standard for the whole project (front-end and back-end) is the one defined in `.claude/rules/code-style.md`. Every function/method must follow this pattern:

```
    /**
     * Brief description of what the method does and where it's used on the code (references). Max: 2 lines
     *
     * @remarks Extra, in-depth information about the method, class, or property. Max: 5 lines
     *
     * @params name - type: what this parameter is doing here
     * @return type: what this method is returning
    **/
```

- List every parameter, in order, with its real TypeScript type. Mark optional ones as `type (opcional)`. For destructured React props use `props - PropsType: ...`; for the Next.js route context use `context - RouteContext: ...`.
- Always write `@return`, including `@return void` and `@return Promise<void>`.
- Omit `@remarks` when the brief is enough. If the brief would need more than 2 lines, move the rest to `@remarks`.
- Do not use `@param`, `@returns` or `@throws`. Describe error responses (thrown exceptions, HTTP status codes) in `@remarks` or in the `@return` description.
- Classes and properties use the same block with only the brief (and `@remarks` when needed).
- Write the documentation in Portuguese, the same language as the rest of the code comments.

Variables (`let` and `const`) at the top of files or inside functions get a one-line comment, as required by `code-style.md`. Say what the value is for or why it exists, without restating the code.

Avoid any unnecessary documentation and weird comment lines. Never write a TODO comment on the code.

## 7. UI Design Implementations

**Creating a new UI on a Component or Page/Screen? So this is what you need to do:**

- Always use the design.md provided as a context of colors, fonts, spacing, etc
- If the new page is a component or you're creating a new component, analyze the components folder in the project and create a new file in the most suitable folder
- Always analyze another already existing page/screen to know which components are common between them before starting a new UI implementation
- When requested to make a 3D Effect in some component, you are expected to create a 3D looking like element and use elevation and hard shadows in the styling
- If you are creating a style with a variable with Pressable, make sure you have a design made for when the button is not pressed as well
- Always prefer the Modern, Clean and Simple design when you are not given any direct instructions about how you should do it, but don't forget to ask how I would prefer it if there are not enough base files to use as a context
- Remember that for UI implementations, your ROLE is Senior Front-End Software Engineer, the CONTEXT is you were requested to implement a new UI component/screen and should focus on doing it only. Avoid doing any backend
- Look for all the already existing components on the components folder and search for all the Components Libraries that will be already installed in the project
- Be creative but don't exagerate. Use a temperature between 0.4 - 0.7
- If TailwindCSS is available in the project, use their variables

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.