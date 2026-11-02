---
name: frontend-design-critique-audit-improve
description: Systematically audit, critique, refactor, and improve existing frontend interfaces, components, landing pages, codebases, and feature designs. Use when asked to review a layout, critique a landing page, audit a design, refactor UI, optimize a frontend, or repair visual, responsive, accessibility, or code quality issues; also trigger on /frontend-critique and /audit-design.
---

# Frontend Design Critique, Audit, and Improve

Work as a design lead and principal frontend engineer. Improve both the interface’s point of view and its implementation. Resist interchangeable AI-generated patterns: default gradients, generic font stacks, repeated rounded cards, soft shadow as decoration, and centered content walls without a clear reason.

## Workflow

### 1. Inspect before editing

- Identify the target files, framework, existing design system, and relevant project instructions. Read only the code and assets needed to understand the affected interface.
- If the user provided a screenshot or mockup, compare the implementation against it. If no implementation exists, treat the brief as a design proposal and label assumptions.
- Check existing tokens, component exports, typography, responsive conventions, and dependencies before proposing replacements. For an established system such as shadcn/ui, Tailwind v4, or Adobe Spectrum, use its canonical tokens and components.
- Do not edit files during the diagnostic pass.

### 2. Pass 1 — diagnostic audit and token map

Present a concise Markdown report before making changes. Be specific to the actual interface; avoid generic checklist findings. Include:

1. **Identity and hierarchy:** Point out where choices feel generic or conflict with the product, audience, or brand. Assess the first viewport, reading order, focal point, CTA prominence, and use of imagery/type.
2. **Severity matrix:** Score each applicable category from 0 (no material issue) to 4 (catastrophic or unusable). Add a short reason. Use `N/A` when the code or viewport cannot be assessed.

   | Category | Score | Evidence |
   |---|---:|---|
   | Visual hierarchy and identity | 0–4 | Concrete observation |
   | Spacing and composition | 0–4 | Concrete observation |
   | Responsive structure | 0–4 | Concrete observation |
   | Semantics and accessibility | 0–4 | Concrete observation |
   | Code consistency and maintainability | 0–4 | Concrete observation |

3. **Counter-plan:** Lock a small, contextual design direction before coding. Name 4–6 purposeful color values (reuse verified project colors where appropriate), a distinctive heading/body font pairing (do not default to Inter, Arial, or Roboto), and one signature compositional move. Keep the rest restrained. If adding a font would create unnecessary dependencies or harm performance, choose an available project/system font and explain the choice.
4. **Implementation priorities:** List the highest-impact fixes and the files or components likely to change. Flag uncertain items rather than presenting guesses as facts.

If the user asked only for a critique/audit, stop after Pass 1. Otherwise continue to Pass 2 in the same task; the report is an audit checkpoint, not a request for confirmation.

### 3. Pass 2 — implement the improvement

- Follow the counter-plan and project conventions. Do not introduce a new design system, dependency, or broad redesign unless the task calls for it.
- Make the smallest coherent set of changes that resolves the highest-severity issues. Preserve useful content, working interactions, brand elements, and user-provided requirements.
- Use meaningful landmarks and native elements (`header`, `nav`, `main`, `section`, `aside`, `footer`, buttons, links, forms) where appropriate. Avoid needless wrapper depth.
- Create an intentional composition with clear type scale, legible measure, deliberate alignment, and responsive shifts. Avoid defaulting to repeated three-card grids or centered text blocks; use them only when content and task justify them.
- Treat motion as a purposeful interaction. Avoid scattered scroll-triggered animation; honor `prefers-reduced-motion` and keep essential information available without animation.
- Use fluid sizing for page structure (`rem`, `em`, `%`, `clamp()`, viewport units, or grid/flex constraints). Fixed dimensions may be appropriate for small controls, icons, borders, or media ratios; do not ban `px` mechanically.
- Consolidate repeated utility patterns when this improves clarity. Use existing component abstractions and scoped styles; avoid broad selectors that could leak into unrelated views.
- Ensure visible keyboard focus, usable hit areas, associated form labels, accessible names, sensible heading order, and adequate contrast. Do not claim WCAG compliance based on visual guesswork; verify measurable contrast when feasible and state any limitation.
- Keep above-the-fold value and the primary action easy to find when the interface is conversion-oriented, without forcing every product UI into a landing-page pattern.

## Verification and handoff

- Review the final diff for unrelated changes, duplicated styles, broken semantics, and consistency with the Pass 1 tokens.
- Run only checks requested by the user or required by project instructions. If checks are not run, say so. If visual rendering is available and needed, inspect the affected responsive states rather than inferring them from source alone.
- Summarize what changed, why, and any important limitation. Link the affected files using their absolute paths. Do not claim a fix or accessibility result that was not verified.

## Triggers

`review layout`, `critique my landing page`, `audit this design`, `refactor UI`, `optimize frontend`, `repair responsive layout`, `/frontend-critique`, `/audit-design`.

Skill content license: Apache-2.0.
