---
name: native-app-ui-ux-best-practices
description: "Platform-aware native mobile UI/UX design methodology for iOS/iPadOS and Android. Preserves brand-driven visual direction, design tokens, motion, component states, and anti-AI-slop guardrails while grounding navigation, controls, accessibility, typography, safe areas, system chrome, and interaction behavior in Apple HIG and Android/Material guidance. Implementation targets may include SwiftUI, UIKit, Jetpack Compose, or Android Views/XML, but this skill defines design intent and native behavior rather than framework-specific code. Use for native app design systems, visual direction, UX architecture, component specifications, motion specs, design audits, or refinement."
---

# Native App UI/UX Best Practices

Design native mobile products that feel intentional, distinctive, and at home on their platform.

This skill is a native-mobile adaptation of the OJO design methodology. It keeps the parts that improve design quality — register derivation, Convention vs Innovation tracks, anti-AI-slop guardrails, brand-driven visual direction, material metaphor, semantic tokens, motion purpose, and design audit — while removing web-specific assumptions such as Tailwind classes, DOM/ARIA requirements, browser breakpoints, hover-first interaction, fake device chrome, CSS performance rules, and web font sourcing.

The output is a **design specification**, not a framework tutorial. SwiftUI, UIKit, Jetpack Compose, and Android Views/XML are implementation targets for the same design intent; do not let a framework's API shape the design unless the platform convention genuinely requires it.

## Platform Authority

When platform behavior matters, prefer current official guidance:

- Apple Human Interface Guidelines: https://developer.apple.com/design/human-interface-guidelines/
- Android design guidance: https://developer.android.com/design/ui/mobile/
- Material 3 for Android: https://m3.material.io/
- Android accessibility guidance: https://developer.android.com/guide/topics/ui/accessibility/

If a reference app, concept shot, or old design pattern conflicts with current platform behavior, accessibility, safe areas, system navigation, or system controls, the platform constraint wins unless the deviation is deliberate, justified, and still usable.

## Framework Boundary

### iOS / iPadOS
- **SwiftUI** and **UIKit** are implementation frameworks, not separate design languages.
- The design spec should describe hierarchy, behavior, states, layout intent, typography roles, motion, accessibility, and platform semantics.
- Only add SwiftUI/UIKit notes when implementation differences are material.
- Do not produce different visual identities merely because one screen will be implemented in SwiftUI and another in UIKit.

### Android
- **Kotlin** is the language; **Jetpack Compose** and **Android Views/XML** are UI implementation systems.
- The design language should remain consistent across Compose and Views/XML.
- Prefer current Android/Material interaction and adaptive-layout conventions.
- Only add Compose/View implementation notes when a design constraint depends on them.

### Cross-platform products
- Share product identity, information architecture, content model, semantic color intent, spacing rhythm, imagery, and brand principles.
- Do **not** force pixel-identical UI across iOS and Android.
- Platform navigation, control geometry, typography behavior, iconography, sheets/dialogs, back behavior, system bars, and motion may differ.
- Preserve product identity through tokens and visual physics, not by redrawing one platform on top of the other.

## Core Design Philosophy

**Intentionality:** Nothing is arbitrary. Every color, shadow, radius, spacing value, icon choice, motion behavior, and custom control must serve the product, platform, or chosen visual direction.

**Native familiarity before custom chrome:** Familiar platform behavior reduces cognitive load. Start from native interaction expectations and customize only where brand or product value earns the deviation.

**Surprise within coherence:** A native app can be memorable without fighting the operating system. Put most brand expression into content, imagery, typography, color, composition, custom domain components, and rare high-value moments rather than rebuilding standard system behavior.

**Material honesty:** Surfaces can feel glassy, papery, metallic, soft, raw, printed, or editorial, but their visual physics must be coherent and must not interfere with legibility, touch, system contrast, or accessibility.

**Real visual assets:** When a screen needs imagery, use subject-specific photography, screenshots, product renders, maps/media thumbnails, illustrations, or generated bitmap assets that depict the actual thing. Do not substitute generic gradient blobs, fake stock smiles, or empty gray rectangles for meaningful content.

**Rhythm over density dogma:** Sparse and dense interfaces can both be excellent. Density must come from the product register and task, not from a universal "clean UI" default.

**System behavior is part of the design:** Safe areas, system bars, keyboard, back behavior, Dynamic Type/font scaling, screen readers, reduced motion, dark mode, input method, and window size are not engineering cleanup tasks. They are design constraints from the start.

---

## Style Register Derivation

Before visual exploration, derive a product **register** from evidence: subject matter, audience, brand voice, cultural context, task frequency, content density, and emotional goal.

| Dial | Poles | Observable in |
|---|---|---|
| Energy | quiet ↔ loud | saturation, contrast, collision, motion amplitude |
| Finish | raw ↔ polished | edge treatment, texture, alignment strictness |
| Density | sparse ↔ dense | whitespace, information packing, layering |
| Weight | light ↔ heavy | type weight, color-block area, depth, visual mass |
| Seriousness | playful ↔ solemn | radius, illustration language, copy, motion behavior |

Rules:
- Every dial value must be justified by product evidence.
- Vague adjectives such as premium, refined, elegant, sophisticated, restrained, epic, literary, tasteful, 高级感, 精致, 克制, 史诗 are not sufficient. Translate them into observable decisions.
- Fit before diversity: when the product clearly occupies one register region, all proposed visual directions should stay within that region and vary on other axes.
- Downstream tokens, components, motion, and layout derive from the register. Do not fall back to a house style.

## Language Rule

Match the parent session's language. If the session has a locked language, follow it exactly. Do not default to English merely because this reference is written in English.

## Required Pre-Read

Before design work, read:

- `references/anti-patterns.md`

Load these on demand:
- `references/visual-tokens.md`
- `references/component-recipe.md`
- `references/motion-system.md`
- `references/material-metaphor.md`
- `references/design-audit.md`
- `references/icon-guidelines.md`
- `references/component-libraries.md` — native platform components and system patterns
- `references/hero-enrichment.md` — native visual-enrichment patterns for high-value surfaces

---

# Workflow

## Step 0: Product + Platform Assessment

Identify:

1. **Target platform**
   - iPhone/iPad
   - Android phone/tablet/foldable
   - Both

2. **Implementation target if known**
   - iOS: SwiftUI / UIKit / mixed
   - Android: Jetpack Compose / Views/XML / mixed
   - Treat this as implementation context, not visual direction.

3. **Product value**
   - Utility/efficiency → Convention Track usually fits.
   - Brand/emotional differentiation → Innovation Track usually fits.

4. **Usage characteristics**
   - high-frequency vs occasional
   - one-handed vs two-handed
   - content-heavy vs action-heavy
   - creation vs consumption
   - novice vs expert
   - phone-only vs adaptive tablet/large-screen use

5. **Accessibility and system constraints**
   - text scaling
   - screen reader
   - reduced motion
   - localization / RTL
   - safe areas / display cutouts
   - keyboard and pointer if relevant
   - offline/loading/error states if relevant

### Convention Track

Use when product value is primarily utility:
- productivity
- settings
- personal data
- finance utility
- developer/admin tools
- record keeping
- task-oriented workflows

Adopt familiar platform patterns and learn from strong native products. "Conventional" does not mean visually generic; it means interaction behavior should be predictable.

### Innovation Track

Use when visual identity materially contributes to product value:
- lifestyle
- social
- consumer brand
- creative tools
- entertainment
- culture/media
- highly expressive content products

Keep native behavioral anchors while developing a stronger branded visual system.

If uncertain, default to Convention Track for interaction architecture, then add brand expression selectively.

---

## Step 1: Information Architecture Skeleton

Before styling, define the smallest useful navigation model.

### iOS / iPadOS
Consider:
- tab bar for a small set of peer top-level destinations
- navigation stack for drill-down hierarchy
- sheets for focused modal tasks
- popovers where context and device class make them appropriate
- sidebars / split views for iPad and larger windows
- search as part of native navigation/search patterns
- toolbar actions close to the content they affect

Respect system back/navigation expectations. Do not invent a custom back model merely for visual novelty.

### Android
Consider:
- navigation bar for 3–5 peer top-level destinations on compact widths
- navigation rail for larger widths when appropriate
- navigation drawer when the information architecture genuinely needs more destinations
- top app bar, FAB, menus, sheets, and dialogs according to task priority
- system back behavior and predictive-back expectations
- adaptive layouts rather than stretching phone layouts across large screens

### Shared rules
- A navigation control is for **destinations**, not arbitrary actions.
- Do not create a bottom tab for every feature.
- Do not hide frequent core actions inside overflow menus.
- Do not use gesture-only discovery for critical actions.
- Keep primary actions reachable and close to the content they affect.
- On larger screens, reorganize into panes/sidebars/rails when appropriate; do not simply scale everything up.

This step defines structure only. Do not lock visual styling yet.

---

## Step 2: Inspiration Research — Mandatory for substantial design work

Research 3–5 high-quality references.

Priority:
1. User-provided screenshots, Figma, existing product, or URL
2. Current Apple/Android platform guidance for behavior
3. Real shipped native apps in the same task family
4. App Store / Google Play screenshots and official product media
5. Curated UI sources such as Mobbin / UI Notes
6. Dribbble / Behance concepts only as visual inspiration, never as proof of usable native behavior

Research questions:
- What navigation model is common, and why?
- Which controls are platform-standard vs custom?
- Where is brand identity expressed?
- What information hierarchy survives across text sizes and devices?
- How are loading, empty, error, offline, permissions, and destructive actions handled?
- Which patterns are current vs merely fashionable?
- What should **not** be copied?

Do not clone a competitor pixel-for-pixel.

When the user provides a visual reference, analyze it first:
- palette and color roles
- type character
- density and rhythm
- surface/depth model
- icon treatment
- image strategy
- navigation shell
- component geometry
- motion character
- which parts are brand identity vs platform behavior

Use whatever research tools are available. No paid MCP or scraping service is required by this skill.

---

## Step 3: Style Direction Confirmation

For exploratory design, present 2–3 genuinely distinct directions **within the derived register**.

Each direction should cover:
- Feel
- Color identity
- Typography strategy
- Surface/material treatment
- Density and spacing rhythm
- Imagery/illustration strategy
- Icon character
- Navigation-shell treatment
- Motion character
- Platform fit: how it remains native on iOS and/or Android

Directions must differ in design logic, not just hue.

Bad:
- A = blue
- B = green
- C = purple

Good:
- Direction A: quiet editorial, type-led, restrained surfaces, content-first
- Direction B: tactile object-like, stronger depth, compact controls, physical motion
- Direction C: graphic/poster-led, bold image cropping, hard edges, abrupt motion

If the caller asks for one decisive direction, provide one. The confirmation menu is methodology scaffolding, not an inflexible output contract.

---

## Step 4: Brand Methodology — Innovation Track only

Choose the method that best explains the brand:
- Material Metaphor
- archetype-driven
- narrative-driven
- cultural-semiotic
- another research-grounded method

If using Material Metaphor, read `references/material-metaphor.md`.

Do not turn metaphor into decoration. A "paper" metaphor does not require fake paper cards everywhere; it may instead influence edge treatment, layering, transition behavior, imagery, and tactile feedback.

---

## Step 5: Design Tokens

Read `references/visual-tokens.md`.

Define **semantic design intent first**, then map it to each platform.

Required token domains:
- semantic color roles
- typography roles
- spacing rhythm
- corner geometry
- stroke/separator treatment
- depth/elevation
- opacity
- imagery treatment
- motion roles
- optional material/texture roles

### Native typography rule
System typography is the default baseline, especially for body/UI text.

Custom fonts are allowed when brand value justifies them, but they must:
- remain legible at small sizes
- support required scripts/weights
- scale with accessibility text settings
- not break truncation or layout
- not turn every UI label into branding

A strong pattern is often:
- brand/custom type for selected display/title moments
- system/platform type for dense UI and body text

Never ban SF Pro, San Francisco system typography, Roboto, or platform defaults merely for being common. Familiarity and legibility are strengths in native UI.

### Color rule
Use semantic roles rather than hardcoded color names:
- accent/action
- primary/secondary text
- background/surface
- separator
- destructive
- warning
- success
- informational
- selection
- disabled

Support light/dark appearance and increased-contrast needs. Do not rely on color alone to communicate state.

---

## Step 6: Native Component Recipes

Read `references/component-recipe.md`.

For every important interactive component, specify:

1. **Role and purpose**
2. **Platform primitive**
   - iOS: standard control/pattern when suitable
   - Android: Material/system control/pattern when suitable
3. **Visual anatomy**
4. **State model**
5. **Touch target**
6. **Content behavior**
7. **Accessibility semantics**
8. **Motion/haptics**
9. **Platform differences**
10. **Custom treatment justification**, if deviating from a native primitive

### Core state model

Account for relevant states:
- Default
- Pressed / active
- Focused — when keyboard/pointer focus exists
- Selected / checked
- Disabled
- Loading / progress
- Error
- Success / completion

Optional input-specific states:
- Hover — iPad pointer, Android pointer/desktop contexts only
- Long-press / context-menu affordance
- Dragging / swiping / reordering
- Expanded / collapsed

Do not make Hover a mandatory mobile state.

### Touch targets
- iOS/iPadOS: design ordinary touch controls around the platform-recommended 44×44 pt hit region; smaller visible glyphs can sit inside a larger hit target.
- Android: target at least 48×48 dp for touch interactions.
- Do not shrink hit targets to satisfy a visual grid.

### Native controls first
Prefer system/native components for common behavior:
- buttons
- text fields
- toggles/switches
- menus
- lists
- navigation
- sheets/dialogs
- pickers
- date/time selection
- search
- progress
- share/activity surfaces

Custom controls are justified when the domain interaction itself is custom or when brand value outweighs the loss of familiar behavior. When custom, reproduce accessibility, state, and input behavior — not just appearance.

---

## Step 7: Layout + Adaptivity

### Units
- iOS design specs: use points (pt)
- Android design specs: use density-independent pixels (dp); text follows scalable typography conventions
- Product-level token names may be platform-neutral, but final platform specs must resolve to platform units.

### Safe areas and system UI
Never draw fake OS chrome into the product UI.

Design around:
- status bars
- Dynamic Island / camera cutouts
- home indicator / gesture navigation
- Android system bars
- display cutouts
- software keyboard / IME
- iPad multitasking and resizable windows
- Android window size classes, foldables, multi-window, desktop windowing where relevant

Use edge-to-edge intentionally. Content may extend beneath system bars while interactive content respects safe/inset regions.

### Adaptivity
Do not treat "responsive" as web breakpoints.

Instead specify behavior changes:
- one column → list/detail
- bottom navigation → navigation rail
- modal sheet → side sheet / popover
- compact toolbar → expanded toolbar
- single pane → multi-pane
- edge-to-edge media → constrained readable content

Set sensible maximum widths for reading/forms on large screens. Do not stretch phone controls to fill tablet width.

### Density tiers
Derive from the register:

| Tier | Character | Native interpretation |
|---|---|---|
| Sparse | calm, editorial | larger grouping gaps, strong focus, fewer simultaneous actions |
| Standard | balanced utility | familiar platform rhythm, comfortable grouping |
| Dense | workbench/feed/poster | tighter grouping and more information, but touch targets and reading order remain clear |

Dense does not mean cramped; sparse does not mean empty.

---

## Step 8: Motion + Feedback

Read `references/motion-system.md`.

Motion must serve one or more purposes:
- Feedback
- Guidance
- Continuity
- Brand expression

Native rules:
- Prefer system transitions for standard navigation and presentation.
- Custom motion should not fight the directional logic of the platform.
- High-frequency actions need brief, precise feedback.
- Rare brand moments can be more expressive.
- Haptics may reinforce meaningful feedback but must not become decorative noise.
- Motion must remain interruptible where practical.
- Respect iOS Reduce Motion and Android accessibility/user motion preferences where applicable.
- Never make an animation the only carrier of important information.

Do not impose one universal spring constant across SwiftUI, UIKit, Compose, and Views. Specify perceived behavior first — snappy, damped, heavy, elastic, abrupt — then map to the framework.

---

## Step 9: Accessibility + Internationalization

Accessibility is part of the design spec.

### iOS / iPadOS
Account for:
- Dynamic Type
- VoiceOver
- Bold Text / contrast preferences where relevant
- Reduce Motion
- Differentiate Without Color
- Switch Control / alternative input
- sufficiently sized controls
- standard gestures with alternatives
- localization and RTL

### Android
Account for:
- font scaling
- TalkBack
- semantic roles / labels / state
- Switch Access / Voice Access
- minimum touch targets
- color contrast
- gesture alternatives
- window/inset changes
- localization and RTL

### Shared
- Never use color alone for status.
- Decorative imagery should not receive noisy accessibility labels.
- Useful imagery needs meaningful descriptions.
- Destructive actions need clear consequences and appropriate confirmation/undo strategy.
- Text layouts must survive localization expansion.
- Do not clip essential content at larger text sizes.
- Gesture-only actions need another discoverable route.

---

## Step 10: Design Specification Output

A complete native design spec should include:

### 1. Product register
- five dial values with evidence

### 2. Platform scope
- iOS / Android / both
- SwiftUI/UIKit/Compose/Views notes only where material

### 3. Information architecture
- destinations
- hierarchy
- modal flows
- search
- major actions
- adaptive behavior

### 4. Confirmed visual direction
- visual thesis
- color
- typography
- surfaces
- imagery
- icons
- density
- motion

### 5. Semantic tokens
- shared intent
- iOS mapping
- Android mapping when applicable

### 6. Component specs
For each important component:
- anatomy
- dimensions/rhythm
- states
- hit area
- content rules
- accessibility
- motion/haptics
- platform-specific differences

### 7. Screen / layout specs
- hierarchy
- safe-area/inset behavior
- scrolling
- keyboard behavior
- empty/loading/error/offline
- compact vs expanded layout if relevant

### 8. Motion spec
- purpose
- trigger
- perceived physics
- duration range if useful
- reduced-motion behavior
- platform mapping notes

### 9. Accessibility verification
- text scaling
- screen reader semantics
- contrast
- touch size
- gesture alternatives
- localization/RTL

### 10. Audit
Read `references/design-audit.md` and run the native quality gate.

---

# Global Guardrails

## Hard bans

- No Tailwind/CSS class output as the primary design specification.
- No DOM/ARIA rules used as substitutes for native accessibility semantics.
- No mandatory hover states on touch-only flows.
- No fake iOS/Android status bars, home indicators, gesture bars, Dynamic Island, phone bezels, or keyboards inside product UI.
- No web breakpoint logic used as the native adaptive model.
- No custom recreation of system sheets/dialogs/navigation solely to look "more designed."
- No forced custom font merely to avoid system typography.
- No one-to-one pixel cloning across iOS and Android.
- No gesture-only critical actions.
- No color-only state communication.
- No decorative animation that blocks high-frequency work.
- No automatic "modern app = purple/blue gradient + glass cards + giant rounded rectangles."
- No arbitrary 3D/WebGL requirement for native app polish.
- No hardcoded current-year assumptions in research queries; use the actual session date.

## Soft guidelines

- System components are a starting point, not a creativity ceiling.
- Express brand more strongly in content and domain-specific components than in generic navigation chrome.
- Custom components should inherit native behavior even when their visuals are distinctive.
- Use haptics sparingly and intentionally.
- Keep icon language coherent.
- Preserve readable hierarchy under large text and localization.
- Test both appearance modes where the product supports them.
- Design empty, loading, permission, error, destructive, and offline states before calling a flow complete.

---

# Platform Mapping Principle

The design spec should be understandable before any code is chosen.

Example:

**Design intent**
- A compact secondary action appears inline with a card.
- It has a 44/48-sized hit region, subtle press feedback, no independent container unless needed for contrast, an accessible label, and a contextual menu on long press where useful.

**iOS**
- Map to an appropriate SwiftUI `Button` / `Menu` or UIKit `UIButton` / `UIAction` / context-menu pattern.
- Use SF Symbols when a suitable semantic symbol exists.
- Preserve Dynamic Type and VoiceOver semantics.

**Android**
- Map to an appropriate Compose Material control or Views/Material Components equivalent.
- Use Material Symbols or product icons consistent with the app.
- Preserve TalkBack semantics and 48dp touch target.

The implementation differs; the interaction intent does not.

---

# Quality Gate

Before finalizing:

- Does the app feel native without becoming generic?
- Is brand expression strongest where it adds product value?
- Does navigation follow platform mental models?
- Are iOS and Android allowed to differ where they should?
- Do custom controls preserve standard behavior and accessibility?
- Do text scaling and localization survive the layout?
- Are safe areas and system bars treated as real system constraints?
- Are loading, empty, error, destructive, and offline states designed?
- Does motion communicate rather than decorate?
- Is the interface free of obvious AI-template signatures?
- Could a developer implement the spec in SwiftUI, UIKit, Compose, or Views without reverse-engineering the intended behavior?

If the last answer is no, the design spec is not complete.
