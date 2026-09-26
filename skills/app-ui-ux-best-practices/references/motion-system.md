# Native Motion System Reference

Motion in native apps is part of interaction design, not decoration.

The motion system must remain meaningful whether the UI is implemented in SwiftUI, UIKit, Jetpack Compose, or Android Views/XML. Specify perceived behavior first; framework APIs come later.

Official platform behavior takes priority over generic web animation recipes.

---

# 1. Motion Purpose Test

Every custom animation must serve at least one purpose.

## Feedback
Confirms input or state.

Examples:
- press response
- selection change
- successful drop
- toggle transition
- validation result

## Guidance
Directs attention or clarifies what changed.

Examples:
- revealing a newly inserted row
- highlighting the origin of a changed state
- drawing attention to an error that needs action

## Continuity
Explains spatial or object relationships.

Examples:
- expanding an item into detail
- sheet presentation
- list-detail transition
- drag and drop

## Brand expression
Creates a recognizable emotional quality.

Examples:
- rare onboarding transitions
- celebration
- a distinctive content transformation
- product-specific direct manipulation

If motion serves none of these, remove it.

---

# 2. Native Motion Principle

Prefer the platform's built-in motion for standard navigation and standard components.

Why:
- it matches user expectations
- it usually handles interruption well
- it coordinates with system gestures
- it tends to respect platform accessibility behavior
- it reduces the risk of custom motion fighting navigation semantics

Custom motion is most valuable in:
- domain-specific interactions
- content transformations
- branded moments
- direct manipulation
- complex state changes that benefit from explanation

Do not replace a correct system transition merely because it looks "too default."

---

# 3. Perceived Physics Before Parameters

Describe motion using perceptual language:

- instant
- crisp
- snappy
- controlled
- damped
- heavy
- elastic
- soft
- abrupt
- floating
- continuous

Then map that to the platform's animation system.

Do not define one universal stiffness/damping pair and assume it feels identical across:
- SwiftUI springs
- UIKit spring timing
- Compose spring specs
- Android physics/Animator APIs

Frameworks expose different models and units.

---

# 4. Motion Archetypes

Use archetypes as design intent, not fixed constants.

| Archetype | Feel | Good for |
|---|---|---|
| Click | immediate, decisive | buttons, toggles, selection |
| Slide | controlled spatial travel | sheets, drawers, reordering |
| Flow | soft, atmospheric | rare transitions, calm experiences |
| Thunk | weighty, final | meaningful placement/confirmation |
| Bounce | playful overshoot | games, celebration, toy-like products |
| Drift | slow, light | ambient/meditative moments |

Select the archetype from:
- product register
- material metaphor
- object weight
- interaction frequency
- task seriousness

High-frequency UI should usually use Click or restrained Slide behavior.

---

# 5. Navigation and Presentation

## iOS / iPadOS

Respect the spatial model of:
- navigation stacks
- sheets
- full-screen covers
- popovers
- tab switching
- interactive dismissal

Do not invent unrelated directions for enter and exit.

If a system transition already communicates the relationship correctly, use it.

Custom transitions must:
- remain interruptible where practical
- preserve back/dismiss expectations
- avoid disorienting scale/zoom in frequent flows
- respond sensibly to Reduce Motion

## Android

Respect:
- system back / predictive back
- navigation hierarchy
- sheet/dialog semantics
- container transforms or Material motion patterns when they clarify relationship
- edge-to-edge and system gesture regions

Do not animate in ways that contradict back navigation or make predictive back feel disconnected from the destination.

---

# 6. Gesture-Driven Motion

Direct manipulation should track the gesture closely.

Examples:
- drag
- swipe action
- pull-to-refresh
- reorder
- scrubber
- interactive dismissal
- sheet drag

Rules:
- movement follows the user's input
- resistance communicates limits
- release resolves predictably
- cancellation is possible when appropriate
- state remains clear during the gesture
- system-edge gestures are respected

Avoid animations that continue independently while the user is still directly manipulating the same object unless the behavior is intentional and understandable.

---

# 7. Press Feedback

Custom buttons and tappable surfaces need immediate feedback.

Possible feedback:
- slight scale compression
- tint/state layer
- opacity/brightness shift
- depth reduction
- highlight
- subtle haptic for meaningful actions

Avoid:
- large scale jumps
- content movement that changes layout
- bounce on every tap
- delay before feedback begins

System controls may already handle press feedback; do not double-animate them.

---

# 8. Haptics

Haptics are a parallel feedback channel, not visual decoration.

Useful roles:
- selection
- success
- warning
- error
- meaningful impact
- threshold crossing
- completed drag/drop

Avoid:
- haptic on every ordinary tap
- haptic that contradicts the visual result
- repeated haptic during continuous scrolling
- relying on haptic as the only confirmation

Describe the semantic role, then map to platform APIs.

---

# 9. Duration Guidance

Do not treat duration values as universal laws.

Useful ranges for custom UI motion:

### Immediate feedback
roughly 80–180 ms perceived response

Use for:
- press
- selected state
- icon/tint change

### Local transition
roughly 180–350 ms

Use for:
- expand/collapse
- local content replacement
- small panel changes

### Presentation / major transition
roughly 250–500 ms

Use for:
- custom sheet/panel transitions
- larger transformations
- onboarding step transitions

### Brand emphasis
may exceed these ranges when rare and justified, but should not block task progress.

The correct duration depends on:
- travel distance
- object size
- gesture velocity
- product register
- platform
- accessibility settings

Exit motion often feels better slightly faster than entry, but do not force a fixed 75% formula.

---

# 10. Easing Guidance

Choose easing from purpose.

### Entrance
Usually decelerates into rest.

### Exit
Usually leaves decisively.

### Direct manipulation
Tracks the gesture rather than following a canned timing curve.

### Spatial movement
Should preserve continuity and perceived momentum.

### Raw/graphic registers
Hard cuts or abrupt snaps can be legitimate brand choices.

### Calm/polished registers
Damped, smooth settling may fit better.

Do not use:
- linear motion by accident
- elastic bounce as default personality
- long ease-in delays that make controls feel unresponsive

---

# 11. Material-Informed Motion

A material metaphor can influence perceived physics.

Examples:

### Glass
- precise
- light-to-medium inertia
- clean settling
- restrained depth change

### Paper
- layered
- directional reveal
- slight edge/stack relationship

### Fabric
- softer deformation
- controlled fold/expand feeling

### Metal
- crisp
- heavier
- short travel
- decisive settling

### Mist
- low positional travel
- opacity/atmospheric change
- avoid blocking reading

### Raw print / zine
- hard cuts
- stepped changes
- abrupt offset shifts
- intentionally imperfect timing

Do not literalize the metaphor with gimmicks. A financial app inspired by stone does not need every card to "fall" with heavy physics.

---

# 12. Lists

Do not automatically stagger every row when a list appears.

Stagger can help when:
- a small group is introduced once
- the sequence itself matters
- onboarding/celebration benefits from rhythm

Avoid stagger for:
- scrolling lists
- search results
- repeatedly refreshed data
- long feeds
- settings

Content should usually become available immediately.

When inserting/removing/reordering an item, animate the affected spatial relationship rather than replaying the entire list.

---

# 13. Loading Motion

Choose the loading pattern from the task.

### Immediate
No loader if the result appears almost instantly.

### Indeterminate
Use when the wait exists but progress cannot be measured.

### Determinate
Use when progress is meaningful.

### Skeleton
Useful when preserving content structure helps orientation.

### Offline/queued
A spinner may be wrong if the real state is "waiting for network" or "queued."

Avoid endless decorative pulsing around text.

---

# 14. Reduced Motion

Reduced-motion behavior is mandatory for meaningful custom motion.

## iOS
Respond to Reduce Motion.

Good substitutions:
- fade instead of large translation
- instant state change
- shorter/tighter spring
- remove depth/zoom animation
- preserve direct gesture tracking when it aids control

## Android
Respect relevant user/system accessibility animation preferences and avoid making core comprehension depend on motion.

Good substitutions:
- instant or simplified transition
- crossfade
- reduced travel
- reduced overshoot
- no ambient loop

Do not simply set every animation to 0.01 ms if that creates unreadable state changes. Preserve comprehension.

---

# 15. Motion and Large Content Changes

When content changes significantly:
- preserve focus
- preserve scroll context where possible
- do not move the target under the user's finger
- explain relationship through layout/motion only when useful
- avoid layout jumps

Examples:
- inserting a row near the current position should not unexpectedly throw the user to the top
- changing a filter should make the new result set clear without replaying decorative entrance animations

---

# 16. Keyboard / IME Motion

The software keyboard is system UI.

Design:
- focused input remains visible
- primary action remains reachable when appropriate
- content does not jump unpredictably
- sheet/form layout responds to keyboard height and platform behavior

Do not specify fixed keyboard heights or fake keyboard animations.

---

# 17. System Bars and Edge-to-Edge

Status bars, gesture navigation, and home indicators are not animated product components.

Do not:
- animate fake status icons
- draw a custom home indicator
- move content using hardcoded top/bottom values tied to one device

If content moves under system bars, the transition should preserve contrast and safe interaction regions.

---

# 18. Continuous / Ambient Motion

Use only when it provides:
- live status
- environment/brand ambience
- progress
- direct manipulation feedback

Rules:
- low attentional cost
- far from long-form reading when decorative
- pauses/stops when offscreen where practical
- reduced-motion alternative
- no critical information available only through the loop

Avoid:
- breathing cards
- endlessly floating buttons
- random particles
- pulsing decorative gradients

unless the product experience genuinely calls for them.

---

# 19. Motion Specification Template

For each custom motion:

## [Motion name]

**Purpose**
Feedback / Guidance / Continuity / Brand

**Trigger**
User action or system event

**Affected elements**
What moves/changes

**Perceived behavior**
snappy / damped / heavy / elastic / abrupt / etc.

**Spatial logic**
Where it comes from and where it goes

**Timing**
Range or relative speed

**Interruption**
Can the user reverse/cancel/interact during motion?

**Haptics**
none / selection / success / impact / etc.

**Reduced motion**
fade / instant / reduced travel / no loop / other

**iOS mapping note**
Only when useful

**Android mapping note**
Only when useful

---

# 20. Framework Mapping Examples

## SwiftUI
Use the design spec to choose:
- state-driven animation
- transition
- matched geometry where appropriate
- transaction
- gesture
- sensory/haptic feedback
- reduce-motion environment handling

Do not write SwiftUI APIs into the design token itself.

## UIKit
Map to:
- UIViewPropertyAnimator
- transition coordinator
- custom presentation/transition APIs
- gesture recognizers
- haptic feedback generators
- accessibility motion settings

Again, preserve the design intent rather than reproducing SwiftUI syntax.

## Jetpack Compose
Map to:
- state animation
- AnimatedVisibility/content transition
- updateTransition
- animateContentSize
- spring/tween specs
- gesture APIs
- haptics/accessibility behavior

## Android Views/XML
Map to:
- property animation
- MotionLayout/Transition framework where appropriate
- view state animation
- gesture/drag systems
- accessibility/user animation settings

Compose and Views should produce the same product motion language.

---

# 21. Performance Principles

Native performance rules are framework-dependent, so the design skill should not make blanket claims such as "only transform and opacity."

Instead:

- prefer motion that can be rendered smoothly on target devices
- avoid animating enormous blurred surfaces unnecessarily
- avoid simultaneous expensive effects across many rows
- test large lists and image-heavy screens
- minimize continuous offscreen work
- reuse system/native transitions where they are optimized
- coordinate motion with scrolling and gestures
- profile custom complex effects during implementation

A design specification should identify high-cost effects so engineering can validate them.

---

# 22. Quality Gate

Before approving motion:

- [ ] The motion has a purpose
- [ ] Standard platform motion is retained where it is already correct
- [ ] High-frequency tasks remain fast
- [ ] Gesture-driven motion tracks input
- [ ] Spatial direction makes sense
- [ ] The user can continue working without waiting unnecessarily
- [ ] Reduced-motion behavior is defined
- [ ] Haptics are intentional
- [ ] No fake system chrome is animated
- [ ] iOS and Android may use different mechanics while preserving the same intent
- [ ] The motion fits the product register
- [ ] Complex effects are rare enough to justify their implementation/performance cost

The goal is not more animation. The goal is clearer, more tactile, more coherent interaction.
