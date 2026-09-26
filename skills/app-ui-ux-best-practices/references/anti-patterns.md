# Native UI Design Anti-Patterns Reference

This is the mandatory guardrail for the native-app design skill.

The purpose is not to make every app look conservative. It is to stop AI-generated interfaces from confusing "stylized" with "good design," and to prevent web/prototype assumptions from leaking into iOS and Android product design.

---

# 1. AI-Generated Style Signatures

## The Slop Test

A design is suspect when several of these appear without product evidence:

- purple/blue gradient as default identity
- translucent rounded cards on every surface
- giant corner radii everywhere
- glowing accent borders
- floating pills for ordinary navigation
- gradient blobs used as fake content
- generic "premium" dark mode
- every section isolated in a card
- random 3D decoration
- excessive micro-labels
- ornamental motion on routine tasks
- an interface that looks like a concept shot but not a usable app

None of these techniques is universally banned. The failure is using them by habit rather than deriving them from the register, brand, content, or platform.

## Vague-word firewall

These words are not design decisions:
- premium
- elegant
- refined
- sophisticated
- clean
- modern
- minimal
- playful
- bold
- 高级感
- 精致
- 克制
- 现代
- 极简

Translate them into observable properties:
- saturation
- contrast
- type weight
- spacing
- density
- radius
- edge treatment
- imagery
- motion amplitude
- material depth

---

# 2. Native Platform Anti-Patterns

## ⛔ Pixel-identical cross-platform design

Do not force iOS and Android to share:
- identical navigation chrome
- identical switch geometry
- identical sheets/dialogs
- identical system-bar treatment
- identical back behavior
- identical typography metrics
- identical icon language
- identical motion curves

Share product identity and semantic intent. Let platform conventions differ.

## ⛔ Rebuilding system behavior for visual novelty

Do not custom-build ordinary:
- tab bars
- navigation bars
- back buttons
- switches
- text fields
- search fields
- pickers
- alerts
- sheets
- menus

merely so they look "more designed."

Customize only when the product value justifies it, and preserve native behavior/accessibility.

## ⛔ Fake operating-system chrome

Never draw product-content versions of:
- iOS/Android status bars
- battery/signal/Wi-Fi clusters
- Dynamic Island/notch
- iOS home indicator
- Android gesture handle/navigation buttons
- phone/tablet bezel
- software keyboard
- fake permission sheets
- fake system share sheet

Exception: the product itself is explicitly a device emulator, remote screen, OS preview, or design/mockup tool.

Design around real safe areas and system UI instead.

## ⛔ Ignoring the system back model

Do not:
- invent a nonstandard back gesture
- block Android back without a task reason
- put a custom left-arrow that behaves differently from platform expectations
- use "close" and "back" interchangeably when they have different task meanings

## ⛔ Edge gesture conflicts

Avoid important custom gestures that begin in areas reserved for system navigation unless the platform explicitly supports the interaction and the design handles conflicts.

---

# 3. Typography Anti-Patterns

## ⛔ "System font = no personality"

False.

System typography is often the correct choice for:
- body text
- settings
- dense data
- utility UI
- small labels
- accessibility-sensitive controls

Brand personality can come from:
- display/title type
- imagery
- color
- composition
- iconography
- motion
- copy

Do not reject SF/system typography or Android platform typography merely because it is common.

## ⛔ Mandatory external font providers

Do not require:
- Google Fonts
- emfont
- Adobe Fonts
- any specific vendor

Font sourcing depends on:
- licensing
- language support
- app bundle strategy
- brand
- performance
- accessibility

## ⛔ Fixed text that cannot scale

Reject layouts that work only at default text size.

Typical failures:
- fixed-height rows that clip multiline labels
- icon + text layouts with no wrapping strategy
- tiny captions carrying essential information
- buttons that truncate their only action label
- navigation titles that collide with actions

## ⛔ Too many hierarchy layers

Avoid:
Overline + Eyebrow + Heading + Subheading + Label + Body + Caption on ordinary utility screens.

Add a level only when it carries information.

---

# 4. Color Anti-Patterns

## ⛔ Single-hue everything

Do not tint:
- every control
- every icon
- every card
- every status
- every selection state

with the brand accent.

Use semantic roles.

## ⛔ Color-only meaning

Never communicate:
- error
- selected
- required
- destructive
- online/offline
- success

only through hue.

Use text, iconography, shape, label, or other redundant cues.

## ⛔ Dark mode as inversion

Dark appearance is not:
`white → black`, `black → white`.

Re-evaluate:
- tonal hierarchy
- separators
- surface depth
- imagery
- disabled states
- material translucency
- accent saturation

## ⛔ Low-contrast "premium" UI

Muted gray-on-gray interfaces are not inherently refined.

If information becomes harder to read, the design failed.

---

# 5. Container/Card Anti-Patterns

## ⛔ Cardification

Do not put every section into a rounded card.

Prefer:
- spacing
- grouping
- dividers
- list sections
- typography
- background surfaces
- native grouped layouts

when they communicate structure more directly.

## ⛔ Nested card stack

Card inside card inside card usually indicates weak information architecture.

## ⛔ Giant radius everywhere

Radius is a geometry role, not a global aesthetic slider.

Buttons, media, sheets, tags, and cards may deserve different geometry.

## ⛔ Shadow as hierarchy substitute

If every container needs a shadow to be understood, fix structure first.

---

# 6. Navigation Anti-Patterns

## ⛔ Bottom navigation for actions

Top-level navigation represents destinations/modes.

Do not use a bottom tab solely for:
- Add
- Scan
- Upload
- Create
- Camera

unless the product truly models that item as a persistent top-level mode.

## ⛔ Too many peer destinations

If navigation is crowded, revisit IA instead of shrinking labels and icons.

## ⛔ Hiding frequent actions in overflow

Overflow is for secondary or infrequent commands.

## ⛔ Gesture-only navigation

Swipe can enhance navigation, but the user should not need to discover a hidden gesture to reach essential content.

## ⛔ Phone layout stretched to tablet

Large screens need adaptive composition:
- panes
- sidebar/rail
- constrained content
- richer context

not simply 1.5× spacing.

---

# 7. Component Anti-Patterns

## ⛔ Tiny icon hit targets

A small visible icon can have a larger invisible hit region.

Do not equate visual size with tappable size.

## ⛔ Custom controls without semantics

A visually beautiful custom switch/button/slider that screen readers cannot interpret is incomplete.

## ⛔ Disabled = unreadable

Disabled content may reduce emphasis, but important labels must remain perceptible.

## ⛔ Placeholder-only labels

For important inputs, placeholder text should not be the only persistent explanation of the field.

## ⛔ Infinite spinners everywhere

Use the loading pattern that communicates the actual wait:
- immediate state
- progress
- skeleton
- queued/offline
- retry

---

# 8. Gesture Anti-Patterns

## ⛔ Critical action only by swipe

If swipe-to-delete exists, provide another discoverable route where the action matters.

## ⛔ Surprise gesture mapping

Do not make a standard gesture perform an unrelated branded trick.

## ⛔ No cancellation

Drag/swipe interactions should visually track the gesture and allow cancellation when appropriate.

## ⛔ Excessive long-press dependence

Long press is useful for secondary/contextual actions, not primary discovery.

---

# 9. Motion Anti-Patterns

## ⛔ "Every interaction needs a special animation"

Standard native transitions are often the right choice.

## ⛔ Fighting spatial logic

If a view arrives from one direction, dismissing it in an unrelated direction without meaning can disorient users.

## ⛔ Decorative motion in high-frequency workflows

Frequent actions should be brief and precise.

Reserve expressive motion for:
- onboarding
- celebration
- rare transformations
- meaningful direct manipulation
- brand-defining moments

## ⛔ Bounce as personality

Do not sprinkle spring overshoot over every component.

## ⛔ Motion as the only feedback

State changes need perceptible non-motion cues too.

## ⛔ Ignoring reduced motion

Any meaningful custom motion needs an accessibility fallback.

See `motion-system.md`.

---

# 10. Icon Anti-Patterns

## ⛔ Mixing platform libraries casually

Do not mix:
- SF Symbols
- Material Symbols
- Lucide
- emoji
- custom filled icons

inside one UI without a coherent icon system.

## ⛔ "Unexpected" icons that reduce comprehension

Common actions often deserve common symbols.

Brand novelty is not a reason to replace a universally understood search, share, back, or disclosure symbol with an obscure metaphor.

## ⛔ Decorative emoji as product UI icons

Emoji rendering differs by platform and is usually poor for consistent control semantics.

---

# 11. Copy Anti-Patterns

## ⛔ Generic AI copy

Avoid:
- "Something went wrong"
- "Nothing here yet"
- "Get Started" when a more specific action exists
- "Unlock your potential"
- "Seamless experience"
- "Elevate your..."
- over-explaining obvious UI

## Action labels

Prefer a clear outcome:
- Save changes
- Create account
- Delete 5 items
- Add plant
- Retry upload

instead of vague:
- OK
- Submit
- Continue
- Yes

when the specific outcome matters.

## Error messages

Useful errors answer:
1. What happened?
2. What is affected?
3. What can the user do?

Do not blame the user.

## Empty states

An empty state can:
- explain the value
- give one useful next action
- stay visually quiet when no action is needed

Do not turn every empty state into a marketing illustration.

---

# 12. Localization Anti-Patterns

Reject:
- concatenated sentence fragments
- fixed-width controls based on English
- flags as language selectors
- layouts that fail with longer translations
- icons whose cultural meaning is assumed
- hardcoded LTR ordering

Design for:
- text expansion
- RTL where supported
- locale-specific dates/numbers
- pluralization
- script-specific font behavior

---

# 13. Layout Implementation Anti-Patterns — Native Version

These are design decisions that tend to create fragile native implementations.

| Anti-pattern | Why it fails | Better approach |
|---|---|---|
| Fixed heights around text | large text/localization clips | content-driven height |
| Absolute placement for normal UI | device/text changes overlap | constraints/stacks/adaptive layout |
| Hardcoded safe-area offsets | fails across devices | system insets/safe-area guides |
| Fixed phone width on tablet | wastes space | adaptive panes/max widths |
| Text drawn into images | not scalable/readable | real text layer |
| Tiny visible + tiny hit target | hard to touch | larger semantic hit region |
| Magic spacing to align system chrome | breaks by OS/device | platform guides/insets |
| Custom keyboard avoidance by fixed offset | fails with IME variations | system keyboard/inset behavior |

Intentional overlap, collage, or asymmetric composition is allowed in expressive content surfaces if reading order, hit targets, and adaptivity remain sound.

---

# 14. Native Brand-First Process

Before visual decisions:

1. What is the product's actual value?
2. Who uses it, how often, and in what physical context?
3. Which platform behaviors should be invisible/familiar?
4. Where should the brand be memorable?
5. What is content vs chrome?
6. Which deviations from the platform are worth the usability cost?

A strong native brand usually does **not** need to redesign every standard control.

---

# 15. Re-drawn Chrome Audit

Treat these as critical findings unless the product itself is a device/OS simulation:

- hardcoded 9:41-style status row
- fake battery/Wi-Fi/signal cluster
- fake Dynamic Island/notch
- fake home indicator
- fake Android navigation buttons/gesture bar
- phone-shaped outer frame
- fake keyboard
- custom-drawn permission dialog pretending to be the OS
- product screenshot embedded in a fake device when the deliverable is the working UI

Replace with:
- real safe-area/inset behavior
- edge-to-edge content where appropriate
- system permission/presentation patterns
- actual device preview only in marketing/mockup deliverables

---

# 16. Platform-Fidelity Check

Ask:

### iOS
- Does this respect Apple navigation and presentation conventions?
- Is the design comfortable with Dynamic Type?
- Are standard controls customized rather than unnecessarily rebuilt?
- Are SF Symbols/system icon behaviors used where they help comprehension?
- Does Reduce Motion have a sensible result?

### Android
- Does the design respect system back and edge-to-edge?
- Are 48dp targets preserved?
- Does TalkBack get meaningful roles/states?
- Does the layout adapt beyond compact phone width?
- Are Material patterns used where they improve predictability rather than applied as a mandatory visual skin?

### Both
- Is the shared brand stronger than the forced sameness?
- Do differences feel native rather than inconsistent?

---

# 17. Final Anti-Slop Test

A native interface passes when:

- it could plausibly ship, not just screenshot well
- it has real content hierarchy
- the platform behavior is familiar
- the brand is visible without repainting all system chrome
- custom controls earn their complexity
- accessibility does not feel bolted on
- loading/error/empty/offline states are considered
- typography is legible and scalable
- motion is purposeful
- the design does not reveal a default AI aesthetic

The goal is not "less design." The goal is **more intentional design with fewer accidental patterns**.
