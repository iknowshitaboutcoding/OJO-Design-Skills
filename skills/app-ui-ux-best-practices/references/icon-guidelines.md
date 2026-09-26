# Native Icon Guidelines

Icons in native apps are functional language first and visual style second.

The goal is consistency, recognizability, accessibility, and platform fit — not novelty for its own sake.

---

# 1. One Coherent Icon Language Per Platform Surface

Do not casually mix:
- SF Symbols
- Material Symbols
- Lucide
- Heroicons
- Phosphor
- emoji
- custom filled icons

inside the same product surface.

A product can use custom domain icons alongside platform symbols, but the visual system should define:
- optical size
- stroke/weight
- fill policy
- corner character
- baseline/alignment
- selected/unselected treatment

---

# 2. iOS / iPadOS

Prefer **SF Symbols** when a suitable semantic symbol exists.

Benefits:
- native optical behavior
- weight/scale integration
- accessibility/localization support for many symbols
- directional variants where appropriate
- familiar meaning

Use custom symbols for:
- domain-specific concepts
- brand-specific objects
- actions with no suitable SF Symbol

Do not replace familiar platform symbols merely to appear unique.

Examples of concepts that usually benefit from familiar symbols:
- search
- share
- add
- delete
- back/disclosure
- settings
- camera
- refresh

Brand novelty belongs more naturally in domain-specific iconography than in reinventing universal actions.

---

# 3. Android

Prefer **Material Symbols** or another coherent Android-appropriate product set for common actions when it fits the visual direction.

Use custom icons for:
- domain-specific concepts
- brand-specific objects
- concepts not represented well by standard symbols

Do not import SF Symbols into Android as a generic icon system.

---

# 4. Cross-Platform Products

Do not require the same glyph file on both platforms.

Share the **semantic icon role**:
- search
- settings
- favorite
- filter
- sort
- share
- destructive
- disclosure
- domain-specific object

Then choose the platform-appropriate representation.

The product can still feel coherent through:
- similar visual weight
- common brand/domain icons
- shared semantic roles
- consistent color and selection behavior

---

# 5. Icon Size vs Hit Target

The visible glyph may be smaller than the touch region.

Typical logic:
- glyph: visually appropriate to surrounding text/control
- hit target: large enough for reliable touch

Do not enlarge the glyph until it looks clumsy simply to meet accessibility; enlarge the tappable region.

---

# 6. Filled vs Outline

Use fill intentionally.

Common patterns:
- outline/unselected
- filled/selected
- filled for high-emphasis action
- hierarchical/multicolor only when meaningful

Do not mix filled and outline randomly across unrelated controls.

---

# 7. Weight

Icon weight should coordinate with:
- adjacent typography
- control prominence
- product register

A heavy icon beside light body type can look visually detached.

Avoid using the thinnest possible icon weight as a shortcut for "premium."

---

# 8. Color

Icons normally inherit a semantic role:
- primary
- secondary
- accent
- destructive
- disabled
- selected

Do not assign every icon a different decorative color.

Do not communicate selection or error only through color.

---

# 9. Accessibility

Interactive icons need:
- meaningful accessible label
- state/value announcement if toggleable
- sufficient hit target
- alternative text that describes action, not shape

Bad accessible label:
- "Magnifying glass"

Good:
- "Search"

Decorative icons should not create screen-reader noise.

---

# 10. Badges and Status

If an icon includes:
- unread badge
- sync state
- warning
- online/offline
- recording/live state

make sure the semantic state is available beyond the badge color/shape.

---

# 11. Emoji

Do not use emoji as ordinary control icons by default.

Problems:
- rendering differs by OS/version
- inconsistent baseline
- unpredictable color/detail
- weak control semantics

Emoji are valid as content, reactions, or a deliberate expressive feature.

---

# 12. Custom Icon Quality

Custom icons should define:
- grid/keyline
- stroke weight
- corner treatment
- optical corrections
- filled variant behavior
- selected state
- light/dark behavior
- RTL mirroring rules if directional
- accessibility label

Do not assume mathematically identical geometry looks optically aligned.

---

# 13. Quality Gate

- [ ] One coherent icon language per surface
- [ ] Platform-common actions remain recognizable
- [ ] Custom icons are used where they add product value
- [ ] Visual weight matches typography
- [ ] Selection behavior is consistent
- [ ] Touch target is larger than tiny glyphs when needed
- [ ] Interactive icons have accessible names
- [ ] Decorative icons are hidden from accessibility
- [ ] Color is not the only state cue
- [ ] iOS and Android are allowed to use different platform glyphs for the same semantic role
