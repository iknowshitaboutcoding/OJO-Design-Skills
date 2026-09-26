# Native Component Recipe Reference

This reference defines how to specify native mobile components without collapsing design intent into framework syntax.

A component recipe should be implementable in:
- SwiftUI
- UIKit
- Jetpack Compose
- Android Views/XML

The design spec describes role, anatomy, behavior, states, accessibility, motion, and platform mapping. Code-level APIs are secondary.

---

# 1. Native State Model

The old web-oriented 8-state model is replaced with a touch-first native state model.

## Core states

Every interactive component should account for the states that actually apply:

1. **Default**
2. **Pressed / Active**
3. **Focused** — keyboard/pointer/accessibility focus where relevant
4. **Selected / Checked**
5. **Disabled**
6. **Loading / In progress**
7. **Error**
8. **Success / Completed**

Optional states:
- Hover — pointer environments only
- Long-press / context menu
- Dragging / reordering
- Expanded / collapsed
- Indeterminate
- Read-only
- Offline / unavailable

Do not manufacture every state for every control. A static label does not need loading/selected states; a button does not need an error state if errors are presented at the task level.

---

# 2. Press Feedback Is Mandatory for Custom Controls

A custom tappable control must feel responsive.

Possible feedback:
- subtle scale or shape response
- tint/opacity change
- tonal change
- elevation/depth change
- highlight/state layer
- haptic when meaningful

Rules:
- feedback begins immediately with touch-down where practical
- feedback must not shift layout
- the control returns cleanly when the gesture cancels
- do not make every press bounce
- preserve the platform's normal behavior when using standard controls

iOS system buttons and Android Material controls already provide useful behavior; do not layer gratuitous effects over them.

---

# 3. Touch Targets

## iOS / iPadOS
Ordinary touch controls should generally provide a hit region around 44×44 pt even when the visible glyph is smaller.

## Android
Interactive touch targets should be at least 48×48 dp.

The hit region can exceed the visible bounds.

Never reduce touch targets because:
- the layout is dense
- the icon is visually small
- the reference screenshot looks tighter
- the card grid needs to fit one more item

Spacing and grouping should adapt around accessible targets.

---

# 4. Platform Primitive First

Before inventing a custom component, identify the closest native primitive.

## iOS examples
- Button
- Toggle/Switch
- Text Field
- Search Field
- Picker
- Menu
- Context Menu
- List
- Navigation Stack
- Tab Bar
- Toolbar
- Sheet
- Alert
- Confirmation Dialog
- Progress
- Date/Time Picker
- Share/Activity surface

Implementation may be SwiftUI or UIKit.

## Android examples
- Button / Icon Button
- Switch / Checkbox / Radio
- Text Field
- Search
- Menu
- List item
- Navigation bar / rail / drawer
- Top app bar
- FAB
- Bottom sheet
- Dialog
- Snackbar
- Progress
- Date/Time picker

Implementation may be Compose or Views/XML.

### Customization rule

Customize the native primitive if you need visual identity but its behavior is already correct.

Create a custom control when:
- the domain interaction has no suitable native primitive
- the control's behavior is genuinely product-specific
- brand expression materially benefits from a custom form

When custom, you inherit responsibility for:
- touch behavior
- accessibility semantics
- focus
- text scaling
- disabled state
- selected state
- gestures
- keyboard/pointer support where relevant
- reduced motion
- localization

---

# 5. Component Specification Format

For every major component, document:

## [Component name]

**Purpose**
- What task does it support?
- Is it primary, secondary, or contextual?

**Platform primitive**
- iOS:
- Android:

**Anatomy**
- container
- leading content
- primary label
- secondary label
- accessory
- status
- affordance

**Geometry**
- visible size
- minimum hit region
- internal spacing
- alignment
- radius/shape
- separator/stroke

**Content rules**
- label length
- truncation/wrapping
- optional vs required elements
- localization expansion
- empty/null behavior

**States**
- default
- pressed
- focused
- selected
- disabled
- loading
- error
- success
- optional pointer/gesture states

**Accessibility**
- semantic role
- accessible label
- value/state announcement
- order/grouping
- custom actions
- gesture alternative
- large-text behavior

**Motion + haptics**
- feedback purpose
- perceived motion
- reduced-motion behavior
- haptic role if any

**Platform differences**
- iOS behavior
- Android behavior

**Custom-treatment justification**
- why the standard primitive is insufficient, if custom

---

# 6. Buttons

## Primary action

Use for the most important action in the current view or task.

Rules:
- one visually dominant primary action per decision cluster
- label the outcome clearly
- preserve enough hit area
- pressed feedback is immediate
- loading state prevents accidental duplicate submission when appropriate
- destructive primary actions must be unmistakable

Avoid:
- giant full-width buttons for every minor action
- multiple equal "primary" buttons competing in one group
- icon-only primary actions when the meaning is not obvious

## Secondary action

Secondary does not mean low contrast to the point of invisibility.

Possible treatments:
- text button
- bordered/tonal button
- toolbar action
- inline action

Use platform hierarchy rather than forcing the same button family on both systems.

## Icon button

Requirements:
- accessible name
- adequate hit target
- clear selected state if toggleable
- badge/state not communicated only by color

A 20–24 pt/dp glyph can live inside a 44/48 hit region.

---

# 7. Inputs

## Text field

Specify:
- label strategy
- placeholder role
- keyboard/input type
- clear action if needed
- validation timing
- error presentation
- helper text
- secure-entry behavior if relevant
- multiline behavior
- text scaling
- keyboard avoidance

Do not use placeholder text as the only persistent label for important forms.

Validation:
- avoid showing an error before the user has had a meaningful chance to complete input
- error messages explain what happened and how to fix it
- do not communicate error with red outline alone

## Search

Search is navigation/content retrieval, not merely a styled text field.

Specify:
- where search lives
- when it becomes active
- cancellation/dismissal
- recent/suggested queries
- empty results
- loading
- keyboard behavior
- scope/filter behavior

Use platform search conventions where possible.

---

# 8. Selection Controls

Use familiar controls for familiar choices.

- Switch: immediate on/off setting
- Checkbox: independent selection, common on Android and multi-select contexts
- Radio/single-choice list: one of several options
- Segmented control / tabs: a small set of peer modes, not arbitrary navigation
- Picker/menu: compact selection when scanning all choices is not essential

Do not use a switch for an action that happens once.
Do not use a checkbox for navigation.

---

# 9. Lists and Rows

Rows should make hierarchy clear through alignment, typography, and accessories.

Possible anatomy:
- leading icon/image/avatar
- title
- subtitle
- metadata
- status
- trailing value
- disclosure/chevron
- toggle/action

Rules:
- the whole row may be tappable if it opens one destination
- avoid placing several competing hit targets in a cramped row
- destructive swipe actions need discoverable alternatives when important
- reorder affordances should be clear
- support large text without clipped essential information

Do not put every row inside an individual floating card by default.

---

# 10. Cards and Containers

A card is not a universal grouping primitive.

Use a container when it provides:
- semantic grouping
- action boundary
- media object
- selectable object
- meaningful depth/containment

Avoid:
- card inside card inside card
- every section as a rounded rectangle
- shadows used only to make a flat hierarchy look "designed"

A native list, grouped section, plain spacing, or divider may be better.

---

# 11. Navigation Components

## Bottom navigation / Tab bar
Use for peer top-level destinations.

Do not:
- put actions such as "Create" into destination navigation unless the product model truly treats it as a persistent mode
- exceed the pattern's reasonable number of destinations just to avoid another navigation layer
- invent labels/icons whose meaning is unclear

## Navigation stack
Use for hierarchical drill-down.

Back behavior must match platform expectations.

## Sidebar / rail
Use larger screens to improve reach and preserve context.

## Sheets
Use for focused tasks, supplementary content, or temporary workflows.

Do not use a sheet for every detail view.

## Dialogs / alerts
Reserve for decisions that deserve interruption.

Avoid turning ordinary editing into a chain of dialogs.

---

# 12. Menus and Context Actions

Menus are good for:
- secondary actions
- contextual operations
- infrequent commands

Do not hide the only path to a frequent action in an overflow menu.

Long press can expose a context menu, but critical actions need a discoverable non-gesture route.

---

# 13. Loading, Progress, Empty, Error, Offline

These are component states, not afterthoughts.

## Loading
Choose based on certainty:
- indeterminate progress when duration is unknown
- determinate progress when meaningful progress exists
- skeletons only when they help preserve layout understanding

Avoid decorative looping loaders that add anxiety without information.

## Empty
Explain:
- what is empty
- why it matters
- what action fills it, when appropriate

## Error
Explain:
- what failed
- impact
- recovery action

## Offline
Clarify:
- what remains available
- what cannot sync/load
- whether work is queued
- how to retry

---

# 14. Destructive Actions

Destructive actions should have:
- explicit wording
- clear consequence
- appropriate visual role
- undo when practical
- confirmation when consequences are difficult to reverse

Avoid confirmation dialogs for trivial reversible actions; excessive confirmation trains users to ignore them.

---

# 15. Gestures

Prefer familiar gestures:
- tap
- swipe
- drag
- long press
- pinch/zoom where appropriate

Rules:
- do not repurpose a standard gesture for a surprising unrelated action
- feedback should track the gesture where possible
- gesture-only critical actions need visible alternatives
- edge gestures must not fight system navigation
- drag/reorder must expose state and destination clearly

---

# 16. Pointer and Keyboard

Native mobile may still encounter:
- iPad pointer/trackpad
- hardware keyboard
- Android tablets/foldables
- desktop windowing
- accessibility switches

Therefore:
- focused state matters when keyboard navigation exists
- hover is optional and input-specific
- pointer affordances can enhance precision but must not replace touch behavior
- shortcut design should not remove visible routes for core actions

---

# 17. Platform-Specific Behavior Without Visual Fragmentation

A shared product can use different native controls without becoming two different brands.

Example:

**Preference row**

Shared intent:
- title + optional supporting text
- current state
- entire row readable at large text sizes
- 44/48-sized touch area
- screen reader announces label and state

iOS:
- use a native switch pattern appropriate to Settings-style interaction

Android:
- use a Material switch/list-item pattern with Android spacing and state treatment

Do not force one platform's switch geometry onto the other.

---

# 18. Accessibility Checklist Per Component

Before approving a custom component:

- [ ] Semantic role is clear
- [ ] Accessible label is meaningful
- [ ] State/value is announced
- [ ] Touch target is sufficient
- [ ] Large text does not clip essential content
- [ ] Contrast is sufficient
- [ ] Color is not the only state cue
- [ ] Gesture has an alternative if critical
- [ ] Focus order is sensible
- [ ] Decorative elements do not create screen-reader noise
- [ ] Loading/progress is announced when meaningful
- [ ] Reduced-motion behavior exists if the component moves substantially

---

# 19. Anti-Patterns

Reject these:

- mandatory hover styling for touch-only UI
- Tailwind/CSS strings as the component specification
- web focus-ring rules copied verbatim into native designs
- custom switches that do not expose state semantics
- tiny icon buttons with tiny hit regions
- all content wrapped in cards
- custom tab bars created only to look novel
- gestures with no discoverable alternative
- disabled controls whose label becomes unreadable
- spinner inside every button regardless of task
- destructive actions represented by ambiguous icons only
- iOS controls copied directly into Android or vice versa
- custom components that imitate screenshots but lose native behavior

---

# 20. Quality Test

A component recipe passes when:

1. A designer can explain why the component exists.
2. A user can predict what it does.
3. The component has the states it actually needs.
4. It remains usable with large text and assistive technology.
5. It fits the chosen product register.
6. It respects platform behavior.
7. A developer can map it to SwiftUI/UIKit/Compose/Views without guessing the interaction model.
8. Custom styling adds value beyond merely proving that the UI is custom.
