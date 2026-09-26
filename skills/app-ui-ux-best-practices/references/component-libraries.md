# Native Platform Components Reference

This file replaces the old web/React component-library catalog.

The native design skill does not choose third-party UI kits by default. It starts from platform components and behaviors, then adds custom product components only where they create real value.

---

# 1. Principle: Platform Components Are Behavioral Contracts

A native component is more than appearance. It often includes:
- touch behavior
- focus behavior
- accessibility semantics
- text scaling
- keyboard/pointer support
- animation
- selection behavior
- platform conventions
- localization behavior

Therefore, a visually similar custom control is not automatically equivalent.

Use native/system components when the task is standard. Customize appearance when useful. Replace behavior only when the product interaction genuinely differs.

---

# 2. iOS / iPadOS Component Families

The implementation may be SwiftUI or UIKit. The design decision is the same.

## Navigation
- Navigation stack / hierarchical drill-down
- Tab bar for peer top-level destinations
- Sidebar / split view on iPad and larger layouts
- Search integrated into navigation where appropriate
- Toolbars for contextual actions
- Popovers for contextual presentation on larger devices

## Presentation
- Sheet
- Full-screen modal
- Alert
- Confirmation dialog
- Popover
- Context menu
- Activity/share sheet

## Actions and selection
- Button
- Menu
- Toggle / Switch
- Segmented control
- Picker
- Date/time picker
- Stepper
- Slider

## Input
- Text field
- Secure field
- Text view / multiline input
- Search field

## Content
- List
- Table/collection-style grids
- Scroll view
- Disclosure groups / expandable content
- Progress indicators
- Badges
- SF Symbols / custom symbols

## Media
- Image
- Video/player surfaces
- Photo/media pickers
- Map

### iOS design rule
Do not redraw system controls simply to prove that the app has a custom visual identity. Express brand more strongly through content surfaces, imagery, type, color, and domain-specific components.

---

# 3. Android Component Families

The implementation may be Jetpack Compose or Android Views/XML.

## Navigation
- Navigation bar
- Navigation rail
- Navigation drawer
- Top app bar
- Tabs as secondary navigation
- System back / predictive back

## Presentation
- Modal bottom sheet
- Side sheet where appropriate
- Dialog
- Snackbar
- Menu
- Tooltip

## Actions and selection
- Button variants
- Icon button
- Floating action button
- Switch
- Checkbox
- Radio button
- Segmented/button groups where appropriate
- Slider

## Input
- Text field
- Search
- Date/time picker

## Content
- List item
- Card
- Lazy/recycler list/grid
- Progress indicator
- Badge/chip

## Media
- Image
- Video/player surfaces
- Photo/media picker
- Map

### Android design rule
Material 3 provides a strong default behavior model, but the app does not have to visually look like an untouched sample app. Customize color, typography, shape, imagery, composition, and product-specific components while retaining predictable behavior.

---

# 4. SwiftUI vs UIKit

Do not design separate UI systems for SwiftUI and UIKit.

They may differ in:
- available APIs
- transition capabilities
- hosting/migration constraints
- exact implementation of custom drawing
- version availability

But the design spec should remain shared:
- same semantic roles
- same hierarchy
- same touch targets
- same accessibility behavior
- same motion intent
- same navigation model

If a visual effect is dramatically harder in one framework, flag implementation risk rather than silently weakening the design.

---

# 5. Compose vs Views/XML

Likewise, do not design separate products for Compose and Views.

They may differ in:
- layout APIs
- animation APIs
- accessibility semantics APIs
- component implementations
- migration constraints

The design system should remain the same.

If an effect is only practical in one stack, document the constraint explicitly before changing the product behavior.

---

# 6. Third-Party Component Libraries

Do not introduce a third-party UI library merely because it is fashionable.

A third-party component is justified when it provides:
- a complex domain control
- mature accessibility
- large implementation savings
- behavior not readily available from the platform

Before recommending one, verify:
- active maintenance
- platform/version compatibility
- accessibility behavior
- customization limits
- licensing
- performance
- dependency cost

The design skill should not hardcode a library choice without current project context.

---

# 7. Platform-Specific Icon Sources

## iOS
Prefer SF Symbols when:
- a suitable semantic symbol exists
- the symbol matches the intended action
- localization/direction variants help
- system consistency matters

Custom product symbols are appropriate for:
- domain concepts
- brand-specific actions
- concepts missing from SF Symbols

## Android
Prefer Material Symbols or a coherent product icon set when:
- they match standard Android semantics
- the chosen visual weight fits the product

Custom icons are appropriate for domain-specific concepts.

Do not mix multiple icon languages casually.

See `icon-guidelines.md`.

---

# 8. Component Selection Heuristics

Ask in order:

1. Is this a standard platform task?
2. Is there a native component/pattern that already communicates it?
3. Can the native component be styled sufficiently?
4. If not, what exact product value is gained by custom behavior?
5. Can the custom version preserve accessibility and system expectations?

If questions 4–5 do not have strong answers, stay native.

---

# 9. Examples

## Settings toggle

Correct design logic:
- This is an immediate boolean preference.
- Use a switch/toggle pattern.
- Keep label readable at large text sizes.
- Announce state to screen readers.
- Whole-row tapping may be acceptable if it does not conflict with nested controls.

Do not invent:
- swipe-to-toggle cards
- hold-to-confirm
- animated knobs with nonstandard meanings

## Destructive action

Correct design logic:
- clear destructive label
- appropriate red/destructive semantic role
- confirmation only when needed
- undo when practical

Do not use an unlabeled trash icon as the only path when the consequence is significant.

## Item detail

Correct design logic:
- hierarchical navigation if the item is part of a collection
- sheet only when the task is temporary/contextual

Do not use a bottom sheet solely because bottom sheets look modern.

---

# 10. Quality Gate

A component choice is sound when:
- the user recognizes the interaction
- the platform handles ordinary behavior naturally
- custom styling supports the brand
- accessibility survives customization
- large text/localization survive
- iOS and Android differences are intentional
- the choice can be implemented in SwiftUI/UIKit or Compose/Views without changing product meaning
