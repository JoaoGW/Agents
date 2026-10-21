# How to identify whether a Web/Mobile design was made by AI

The items below must be avoided when generating any design in this project.

## 1. Color signals

- Purple-blue gradient (“vibecode purple”), especially as an accent unrelated to the brand.
- Recurrent default indigo/violet, such as `#4F46E5` or `#5E6AD2`, without visual-identity justification.
- A timid palette with no dominant color, contrast, or clear hierarchy.
- A 3–4 px colored card side strip (_left-border strip_).
- “Rainbow status list”: each list or table row has a different-colored badge, including neutral states.
- Automatic dark mode with neon cyan or violet card borders.
- In image-composed pages: excessive glassmorphism, 3D orbs, plastic illustrations, and faceless 3D people.

## 2. Typography signals

- Nearly automatic use of Inter, Poppins, Space Grotesk, Geist, or Roboto, without the choice seeming to belong to the brand.
- An italic serif word in the middle of a sans-serif heading as a recurring decorative accent.
- Text too small on large screens, or an enormous centered heading with a ✨ badge above it.
- Weak hierarchy: heading, subheading, and body use very similar weights.
- UPPERCASE labels above every section (_overlines_) without a real informational function.

## 3. Icons and illustrations

- An icon in a rounded pastel chip repeated in every feature card.
- Generic Lucide or Heroicons icons without adaptation to the product’s visual language.
- Emojis as interface icons, introducing colors and styles outside the palette.
- Generated imagery with inconsistent stroke weights, odd proportions, or colors apparently bleeding between elements.
- Abstract 3D illustrations of faceless people in implausible poses, holding geometric shapes or orbs.

## 4. Repetitive layout and structure

This is usually the strongest signal, because it is structural rather than merely decorative:

- Centered hero with a small badge, gradient heading, subtitle, and gradient CTA.
- Exactly three feature cards in a row, each with a top icon and centered text.
- Exactly three pricing plans, with the middle plan highlighted.
- A “trusted by” logo strip after the hero and an accordion FAQ near the footer.
- _Cardocalypse_: cards within cards, all with their own shadow, border, and padding.
- Numbered steps “1 · 2 · 3” or indexes “01 · 02 · 03” replacing icons unnecessarily.
- Hero with text left, image right, and two pill-shaped CTAs.
- The hero → cards → logos → pricing → FAQ → footer sequence, with no business-specific content.

## 5. Copy and microcopy

- Words such as “empower,” “unlock,” “seamless,” “elevate,” “supercharge,” “game-changer,” “unleash,” and “revolutionize.”
- Generic phrases such as “Built for modern teams” or “Empower your team to unlock productivity.”
- Excessive em dashes and the “it’s not just X, it’s Y” structure.
- Implausible examples such as “Lorem ipsum,” “User Name,” or “Item 1” on a screen presented as final.
- Testimonials with generic names, photos, or claims and no real context.

## 6. Signals specific to mobile apps

- Mixing iOS and Android conventions, such as an iOS tab bar alongside an Android FAB.
- A back button placed or behaving incompatibly with the platform.
- Touch targets smaller than 44 × 44 pt on iOS or 48 × 48 dp on Android.
- Invented gestures with no correspondence to known _swipe_ or _long press_ patterns.
- Important actions at the top, ignoring thumb-reach zones.
- No empty, loading, error, or permission-denied states: only the happy path exists.
- Generic three-to-five-screen onboarding with the same structure, illustration, heading, and short paragraph.

## 7. Signals specific to websites and web apps

- A textbook responsive grid, with no content-adapted breakpoints or behavior.
- Purposeless microinteractions: identical _fade-ins_, wobbling icons, or animated gradient text used only for attention.
- Hover states that do not communicate action or hide critical information.
- Inconsistency between separately generated screens: the primary color, font, or style changes without reason in one product.

## 8. When the “design” is a generated image, not a real interface

On platforms such as Pinterest and Dribbble, many pieces presented as UI are static images made by Midjourney, DALL·E, or Stable Diffusion. Look for:

- Illegible text or pseudo-text in buttons and navigation bars.
- Functionally meaningless elements: duplicated buttons, icons that do not match labels, or charts unrelated to data.
- Shadows and depth without a coherent light source.
- Slightly misaligned columns, margins, and alignments, without a real grid.
- Components with no state variation: everything is a frozen image.

## 9. Clichés change over time

These signals are not a fixed checklist. As clichés such as indigo, icon chips, and rainbow lists become obvious, models reproduce others, including identical KPI cards, index numbers, and pill CTAs. It is more useful to observe repeated cross-product patterns and the absence of contextual decisions than to memorize styles.

---

## 10. Design system: the strongest indicator of human authorship

AI-only interfaces tend to be inconsistent between screens: button heights, padding, shadows, borders, and spacing vary without a clear pattern. Mature projects use _design tokens_, reusable components, and consistent typography, spacing, elevation, and border-radius scales.

## 11. Component states

AI-generated designs often show only the perfect state. Check for:

- Hover, focus, pressed, and disabled;
- Loading and skeleton;
- Empty and error states;
- Offline and timeout;
- Permission denied.

## 12. Navigation flow

AI can generate isolated screens. A designer creates complete journeys, considering continuity, error prevention and recovery, confirmation, return, and the ability to undo actions.

## 13. Information architecture

Look for redundant categories, inconsistent naming, excessive menus, and unintuitive groupings. They reveal insufficient understanding of the domain and user task.

## 14. Consistency between screens

Compare several screens in the same product: input heights, spacing, icons, typography, and reused components should remain coherent. Repeated small differences are a strong signal of generation without a single source of truth.

## 15. Information density

AI may produce overly empty screens with little useful data. Real products balance productivity, scanability, and density according to context and frequency of use.

## 16. Unrealistic data

Extremely generic data indicates low curation. Prefer plausible, contextualized examples, with names, values, dates, and states that make sense for the product.

## 17. Accessibility

Check contrast, visible focus, touch-target size, WCAG compliance, keyboard navigation, and semantics. Accessibility treated as part of the system is a strong signal of human refinement.

## 18. Microinteractions

Animations should communicate state change, continuity, and causality — not merely decorate the interface. Ask what each movement tells the user.

## 19. Brand personality

Key question: **if I replace the logo, does this product still look the same?** The stronger its own visual identity, the less it relies on generic patterns.

---

## Applying the current project's component system

The complementary implementation document is [design.md](design.md). During setup, ask the user to resolve its identity and visual placeholders before creating branded screens.

- No component library is predefined. Inspect the actual dependencies and existing components, and confirm any needed library choice with the user.
- Reuse existing components and apply the approved tokens from the runtime sources identified by the project.
- Consult the chosen library's official documentation for the component being changed.
- Adapt generated components to the approved identity, accessibility, responsive behavior and required UI states.
- Do not replace the project's styling setup, icon set or token architecture as a side effect of adding a component.
- Choose navigation and information density according to the current product and target platforms.
- Follow the dependency restrictions in CLAUDE.md.

## Quick checklist

1. Does this layout appear in products across many different niches?
2. Does the palette have a clear brand color or merely “safe indigo”?
3. Do icons, typography, spacing, and components follow one system?
4. Does the language of headings and buttons seem written for this product or generic?
5. Are empty, error, loading, permission, and offline states present?
6. On mobile, does navigation respect iOS or Android instead of forming a hybrid?
7. Do visual identity, data, and interaction rules remain coherent across screens?
8. Do microinteractions and information density help the user’s real task?
9. Does the interface meet basic accessibility requirements?
10. Is there evidence of research, testing, and refinement after the initial generation?

## Possible criteria for a future evaluation

- Use of _design tokens_;
- component and typography consistency;
- state coverage;
- accessibility;
- repetition of generic patterns;
- visual identity;
- information density;
- navigation coherence;
- plausibility and contextualization of data.
