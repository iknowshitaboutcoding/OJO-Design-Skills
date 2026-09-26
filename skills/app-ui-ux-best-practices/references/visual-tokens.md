# Native Visual Design Tokens Reference

Use tokens to describe **design intent**, not framework syntax.

The same product may be implemented with SwiftUI, UIKit, Jetpack Compose, or Android Views/XML. Tokens should survive that choice. Define shared semantic intent first, then resolve values per platform where platform conventions differ.

---

## 1. Token Layers

Use three layers:

### A. Product semantics
Stable across platforms.

Examples:
- `color.action.primary`
- `color.text.primary`
- `color.status.destructive`
- `space.group.small`
- `radius.control`
- `motion.feedback.quick`

### B. Platform mapping
Resolve product semantics into iOS or Android behavior.

Examples:
- iOS semantic/system color or asset color
- Android Material color role or theme token
- iOS text style
- Android Material typography role
- iOS point spacing
- Android dp spacing

### C. Component alias
Optional component-specific aliases.

Examples:
- `button.primary.background`
- `tab.selected.foreground`
- `card.border`

Do not jump straight to component literals if multiple components share the same semantic intent.

---

# 2. Color System

## Required semantic roles

At minimum define:

### Content
- `text.primary`
- `text.secondary`
- `text.tertiary`
- `icon.primary`
- `icon.secondary`

### Surfaces
- `background.primary`
- `background.secondary`
- `surface.primary`
- `surface.secondary`
- `surface.elevated`
- `separator`

### Actions
- `action.primary`
- `action.primary.onColor`
- `action.secondary`
- `selection`
- `focus`

### Semantic status
- `destructive`
- `warning`
- `success`
- `informational`
- `disabled`

### Optional brand roles
- `brand.primary`
- `brand.secondary`
- `brand.accent`

Brand color does not automatically equal every interactive control color.

## Light / Dark / Increased Contrast

Define appearance behavior rather than only two hex palettes.

A token should answer:
- What is this color's semantic purpose?
- How does it change in dark appearance?
- Does it need a higher-contrast alternative?
- Is it content color, control color, or decorative color?

Avoid hardcoding one literal color where the platform can provide an adaptive semantic role.

## iOS mapping principles

Prefer platform-semantic behavior for ordinary chrome and content where possible.

Examples of design intent:
- primary label
- secondary label
- system background
- grouped background
- separator
- tint/accent
- destructive

Custom asset colors are appropriate for brand/content colors, but verify:
- light appearance
- dark appearance
- increased contrast where applicable
- legibility over translucent/material backgrounds

Do not flood standard controls with brand color. Brand can live strongly in content while system controls remain familiar.

## Android mapping principles

Map semantics to Material color roles where appropriate:
- primary / onPrimary
- secondary / onSecondary
- tertiary / onTertiary
- surface / surfaceVariant-equivalent roles in the active system
- onSurface
- outline
- error / onError

Dynamic color can be supported when it fits the product, but it is not mandatory for every brand.

If the brand requires a stable identity, define how brand colors coexist with user/system dynamic color rather than mixing uncontrolled palettes.

## Contrast and meaning

- Do not rely on color alone for status or action.
- Text and icons must remain legible in all supported appearances.
- Test semantic status colors against every surface they can appear on.
- Preserve contrast when content scrolls under translucent system materials.

---

# 3. Typography System

Typography must preserve platform scaling behavior.

## Product roles

Define product-level roles such as:
- Display
- Large Title
- Title
- Headline
- Body
- Callout
- Label
- Caption
- Data / Numeric
- Code / Monospaced

Do not define 12 near-identical roles just because a type scale generator can.

## System typography is a valid default

Never reject system typography merely because it is common.

For dense UI and body text, system typography often gives:
- best platform familiarity
- correct language fallback
- Dynamic Type / font scaling behavior
- optical sizing and rendering tuned for the OS
- predictable component metrics

## Custom fonts

Use custom fonts when the brand genuinely benefits.

Good native pattern:
- display/title moments use a brand face
- body/UI text remains system or highly legible
- all custom text scales with accessibility settings

A custom font must:
- support the required writing systems
- include required weights
- survive large accessibility sizes
- handle punctuation and numerals correctly
- not clip in controls
- remain readable at small sizes

Do not force Google Fonts, emfont, Adobe Fonts, or any specific provider. Font licensing and delivery are implementation/product decisions.

## iOS

Prefer semantic text styles as the baseline:
- Large Title
- Title 1/2/3
- Headline
- Body
- Callout
- Subheadline
- Footnote
- Caption

The final implementation may use SwiftUI or UIKit; the design spec should name semantic roles and scaling behavior first.

Do not freeze body/UI text at one point size if Dynamic Type is expected.

## Android

Map product roles to current Material typography roles or a coherent custom type scale.

Text must respect font scaling. Avoid layouts that depend on a label remaining on exactly one line at the default scale.

## Numeric data

Use tabular numerals when vertical alignment of changing numeric values matters:
- timers
- prices
- statistics
- tables
- scoreboards

Do not use monospaced type for all numbers unless the product language calls for it.

---

# 4. Spacing System

Use a small compositional scale, typically built around 4-unit increments, but do not force every distance to be mathematically identical.

Example semantic spacing:

| Token | Typical role |
|---|---|
| `space.1` | micro separation |
| `space.2` | icon-label gap |
| `space.3` | compact internal padding |
| `space.4` | standard internal padding |
| `space.6` | related-group separation |
| `space.8` | section separation |
| `space.12+` | major visual breathing room |

Resolve to:
- pt on iOS
- dp on Android

## Register mapping

### Sparse
- wider group separation
- fewer simultaneous controls
- larger content breathing room

### Standard
- familiar native rhythm
- balanced grouping
- moderate information density

### Dense
- tighter grouping
- more information visible
- **touch targets do not shrink**
- use hierarchy, separators, alignment, and typography rather than simply removing space

Do not make text or controls touch container edges accidentally.

---

# 5. Corner Geometry

Avoid a single universal radius applied to everything.

Define roles:
- `radius.control`
- `radius.container`
- `radius.sheetOrPanel`
- `radius.media`
- `radius.pill`
- `radius.none`

Geometry should follow:
- product register
- component type
- platform behavior
- material metaphor where relevant

Do not use giant rounded rectangles as the default container for every section.

On Android, component geometry may follow the Material shape language or a deliberate brand override.

On iOS, respect system component geometry when using system components; custom content surfaces may use brand geometry.

---

# 6. Stroke, Separator, and Containment

Define:
- separator color/opacity
- border thickness
- selected/focused stroke
- destructive/error stroke
- grouped-surface containment

Do not add borders to every element just to make hierarchy visible.

Containment hierarchy can come from:
- spacing
- background role
- material
- edge
- typography
- divider
- elevation

Use the lightest mechanism that still makes grouping clear.

---

# 7. Depth and Elevation

Do not copy CSS shadow recipes into native specs.

Define perceived depth:

- Flat
- Raised
- Floating
- Modal
- Transient overlay

For each level describe:
- separation from background
- shadow softness/hardness
- tonal contrast
- blur/translucency if relevant
- whether elevation changes during interaction

## iOS
System materials, translucency, and platform-provided presentations often already communicate depth. Avoid stacking extra shadows over every system material.

## Android
Use Material elevation/tonal roles where they fit. Do not mix arbitrary iOS-style blur, heavy shadows, and Material elevation without a coherent reason.

## Brand/raw registers
Hard offset shadows, printed edges, heavy strokes, or no shadows at all are valid when intentionally derived from the register.

---

# 8. Materials, Blur, and Texture

Texture is optional, not a polish requirement.

Possible roles:
- `material.base`
- `material.elevated`
- `material.overlay`
- `texture.content`
- `texture.brandMoment`

Rules:
- Texture must not harm text legibility.
- Blur must preserve foreground contrast.
- Do not place blur everywhere simply because the platform supports it.
- Avoid stacking multiple translucent layers until hierarchy becomes muddy.
- A raw visual register may use grain, halftone, torn edges, hard strokes, or photographic texture.
- A polished register may use restrained translucency, soft tonal separation, or precise highlights.
- Keep standard navigation/control chrome more restrained than branded content unless there is a strong product reason.

---

# 9. Icon Tokens

Define:
- base icon scale
- compact icon scale
- prominent/action icon scale
- stroke/weight treatment
- selected/unselected treatment
- filled vs outline policy

Do not mix SF Symbols, Material Symbols, and a third icon family inside one platform surface without a deliberate reason.

See `icon-guidelines.md`.

---

# 10. Motion Tokens

Define **perceived behavior**, not framework syntax.

Example:

| Token | Perceived behavior | Typical use |
|---|---|---|
| `motion.feedback.instant` | immediate, minimal travel | press/state confirmation |
| `motion.transition.standard` | controlled, short | local state change |
| `motion.presentation` | spatially clear | sheet/panel presentation |
| `motion.brand.emphasis` | expressive, rare | onboarding/celebration |
| `motion.none` | instant | reduced-motion substitution |

A motion token can later map to:
- SwiftUI animation / transaction
- UIKit animator / transition coordinator
- Compose animation spec
- Android Animator / Motion system

The design layer should not prescribe one spring API.

---

# 11. Haptic Roles

If the product uses haptics, define semantic roles:
- selection
- light confirmation
- success
- warning
- error
- impact/emphasis

Do not attach haptics to every tap. System controls may already provide feedback.

---

# 12. Adaptivity Tokens

Do not define web-style breakpoints as the primary model.

Instead define:
- compact layout
- medium layout
- expanded layout
- single-pane
- multi-pane
- constrained reading width
- modal presentation transformation

Examples:
- bottom navigation → navigation rail
- sheet → side sheet / popover
- list → list-detail
- single-column form → centered constrained form

Platform window classes and size environments map these behaviors at implementation time.

---

# Non-Negotiable Rules

1. Semantic roles before literals.
2. Platform mappings may differ while product meaning stays the same.
3. Text must scale.
4. Touch targets must not shrink with dense spacing.
5. Light/dark appearance is not a simple color inversion.
6. Brand color is not a license to repaint all system chrome.
7. System typography is allowed and often preferred.
8. No provider-specific font mandate.
9. No CSS/Tailwind values as the canonical token source.
10. No token exists merely because a design-tool template includes it.
11. If a token cannot be explained by product hierarchy, platform behavior, or brand direction, remove it.
