# Native Design Audit Reference

Use this audit after a native app direction, design system, screen set, or implemented UI is substantially complete.

The audit evaluates:
- product/register fidelity
- platform fidelity
- visual coherence
- interaction completeness
- accessibility
- adaptivity
- motion
- anti-AI quality
- implementation-readiness

Severity levels:
- **Critical** — breaks core usability, accessibility, platform behavior, or creates a misleading system experience
- **High** — materially harms product quality or consistency
- **Medium** — noticeable quality issue
- **Low** — polish opportunity

---

# Audit 0: Product Register Fidelity

- [ ] Energy matches the product evidence
- [ ] Finish matches the product evidence
- [ ] Density matches the actual task
- [ ] Weight matches hierarchy and brand
- [ ] Seriousness matches audience/context
- [ ] The design did not drift toward a generic "clean premium" default
- [ ] Brand expression appears in the right places rather than everywhere

Red flags:
- every app becomes quiet + polished + sparse
- every consumer app becomes playful + rounded
- every "premium" app becomes black + glass + muted gold
- every utility app becomes Linear-like by habit

---

# Audit 1: Platform Fidelity

## iOS / iPadOS

- [ ] Navigation hierarchy is understandable
- [ ] Back/dismiss semantics match the task
- [ ] System sheets/dialogs/menus are used where appropriate
- [ ] Safe areas and system UI are respected
- [ ] No fake status bar / Dynamic Island / home indicator
- [ ] Standard controls are not needlessly redrawn
- [ ] Dynamic Type behavior has been considered
- [ ] VoiceOver semantics are defined for custom controls
- [ ] Reduce Motion behavior exists for custom motion
- [ ] iPad adaptation is defined if the product supports iPad
- [ ] Pointer/keyboard are considered where relevant

## Android

- [ ] System back behavior is respected
- [ ] Predictive-back compatibility is not undermined by custom navigation
- [ ] Edge-to-edge/system insets are handled conceptually
- [ ] No fake status/navigation bars
- [ ] 48dp touch targets are preserved
- [ ] TalkBack semantics are defined for custom controls
- [ ] Navigation bar/rail/drawer choice matches hierarchy and size
- [ ] Larger widths adapt instead of stretching phone UI
- [ ] Material/system components are used where they improve predictability
- [ ] Dynamic color is intentional rather than assumed

## Cross-platform

- [ ] Product identity is shared
- [ ] Platform behavior is allowed to differ
- [ ] No forced pixel-identical control set
- [ ] Typography and icons feel native on each platform
- [ ] Differences are explainable, not accidental

Critical findings:
- custom UI impersonates system permission/security surfaces
- critical back behavior is broken
- touch targets are routinely inaccessible
- essential content is blocked by system insets

---

# Audit 2: Information Architecture

- [ ] Top-level destinations are distinct and stable
- [ ] Actions are not confused with destinations
- [ ] Frequent actions are discoverable
- [ ] Secondary actions are not over-promoted
- [ ] Modal presentation is used for temporary/focused tasks
- [ ] Hierarchical content uses hierarchical navigation
- [ ] Search has a clear place in the information architecture
- [ ] Destructive actions are appropriately separated
- [ ] Large-screen composition is defined when relevant

Red flags:
- five tabs where two are actions
- every detail appears in a bottom sheet
- everything hidden in one overflow menu
- one phone column stretched across tablet width

---

# Audit 3: Visual Coherence

## Color
- [ ] Semantic roles are clear
- [ ] Brand color is not used for everything
- [ ] Light/dark appearances are coherent
- [ ] Status meaning is not color-only
- [ ] Translucent surfaces preserve contrast

## Typography
- [ ] Hierarchy is understandable at a glance
- [ ] Body/UI type is readable
- [ ] Custom fonts are justified
- [ ] System typography is not rejected merely for being common
- [ ] Text can scale
- [ ] Numeric alignment uses tabular numerals where useful
- [ ] Too many hierarchy levels are avoided

## Geometry
- [ ] Radius roles differ by component purpose where appropriate
- [ ] Not every surface is a rounded card
- [ ] Border/shadow use is intentional
- [ ] Material metaphor is coherent but not literal/gimmicky

## Imagery
- [ ] Real/product-specific imagery is used where content needs imagery
- [ ] No generic gradient blob substitutes for real content
- [ ] Cropping and aspect behavior are specified
- [ ] Image treatments remain coherent across screens

---

# Audit 4: Interaction Completeness

For each important interactive component:

- [ ] Default state
- [ ] Pressed/active state
- [ ] Focused state when keyboard/pointer input applies
- [ ] Selected/checked state when applicable
- [ ] Disabled state
- [ ] Loading/progress state where needed
- [ ] Error state where needed
- [ ] Success/completion state where needed

Optional:
- [ ] Hover in pointer environments
- [ ] Long press/context menu
- [ ] Dragging/reordering
- [ ] Expanded/collapsed

Touch:
- [ ] iOS ordinary touch targets are designed around 44×44 pt hit regions
- [ ] Android touch targets are at least 48×48 dp
- [ ] Dense layouts preserve hit size

Inputs:
- [ ] label strategy is clear
- [ ] keyboard/IME behavior is considered
- [ ] validation timing is humane
- [ ] errors are actionable
- [ ] placeholder is not the only persistent label for important data

---

# Audit 5: Accessibility

## Perceivability
- [ ] Text and controls have sufficient contrast
- [ ] Color is not the only information channel
- [ ] Useful images have descriptions
- [ ] Decorative images do not create screen-reader noise
- [ ] Content remains understandable in light/dark modes

## Text scaling
- [ ] Essential text survives large sizes
- [ ] Fixed-height containers do not clip content
- [ ] Buttons retain understandable labels
- [ ] Navigation remains usable
- [ ] Multi-line behavior is specified

## Screen readers
- [ ] Roles are correct
- [ ] Labels are meaningful
- [ ] values/states are announced
- [ ] logical groups are grouped
- [ ] reading/focus order makes sense
- [ ] custom actions exist where gestures would otherwise be required

## Motor/access
- [ ] Touch targets are sufficient
- [ ] Controls have spacing
- [ ] gesture-only critical actions have alternatives
- [ ] destructive actions do not depend on precision gestures

## Motion
- [ ] Reduced-motion behavior is defined
- [ ] looping/large movement is not required to understand content
- [ ] motion can be interrupted where appropriate

Critical findings:
- essential action inaccessible to screen reader
- critical control below minimum usable hit region with no expanded target
- large text makes a core workflow impossible
- color is the sole indicator of an important state

---

# Audit 6: Loading / Empty / Error / Offline

- [ ] Initial loading state exists
- [ ] Refresh/reload behavior is clear
- [ ] Empty state explains what matters
- [ ] Empty state action is useful when appropriate
- [ ] Error state explains failure and recovery
- [ ] Offline state distinguishes cached/queued/unavailable behavior
- [ ] Permission-denied state has a recovery path
- [ ] Loading does not trap the user behind unnecessary animation
- [ ] progress is determinate when meaningful progress is available

---

# Audit 7: Destructive / Irreversible Actions

- [ ] Destructive action is clearly named
- [ ] Visual destructive role is consistent
- [ ] confirmation is used only when consequences warrant it
- [ ] undo is offered when practical
- [ ] batch destruction communicates scope
- [ ] user is not asked to confirm trivial reversible actions repeatedly

---

# Audit 8: Motion Quality

- [ ] Every custom motion has a purpose
- [ ] Standard system transitions are retained where appropriate
- [ ] frequent interactions are brief
- [ ] spatial direction makes sense
- [ ] gesture-driven motion tracks input
- [ ] haptics have semantic purpose
- [ ] custom motion fits the product register
- [ ] reduced-motion fallback exists
- [ ] no fake system chrome is animated

Red flags:
- bounce everywhere
- stagger every list
- decorative ambient motion beside reading content
- long animation blocks input
- navigation direction contradicts hierarchy

---

# Audit 9: Adaptivity

## iOS/iPadOS
- [ ] safe areas
- [ ] Dynamic Island/camera regions
- [ ] portrait/landscape where supported
- [ ] iPad resizable layouts / split views where relevant
- [ ] keyboard and pointer where relevant
- [ ] constrained readable widths on large canvases

## Android
- [ ] edge-to-edge insets
- [ ] compact/medium/expanded behavior where relevant
- [ ] foldable/tablet composition where relevant
- [ ] navigation transforms appropriately
- [ ] keyboard/IME does not cover focused actions
- [ ] desktop/multi-window behavior is considered if supported

Reject "responsive" specs that consist only of web-style numeric breakpoints without describing the layout transformation.

---

# Audit 10: Anti-AI Detection

## 30-second scan

Look for:
- purple/blue gradient default
- every section in a glass card
- huge radii everywhere
- identical cards repeated down the screen
- too many helper labels
- fake status bar/device frame
- icon library inconsistency
- giant generic empty-state illustration
- vague copy
- ornamental 3D
- random soft shadows
- animation on everything
- one accent color applied indiscriminately

## Golden rule

Can each distinctive design choice be traced to:
- product need
- platform behavior
- brand direction
- content
- accessibility
- material/visual physics

If not, it may be decorative habit.

---

# Audit 11: Implementation Readiness

The design does not need framework code, but the spec must be concrete enough to implement.

- [ ] dimensions use pt for iOS and dp for Android when platform-specific
- [ ] semantic tokens are defined
- [ ] component states are defined
- [ ] touch targets are defined
- [ ] navigation behavior is defined
- [ ] large-text behavior is defined
- [ ] safe-area/inset behavior is defined
- [ ] scrolling behavior is defined
- [ ] keyboard behavior is defined for input-heavy screens
- [ ] image cropping/loading behavior is defined
- [ ] motion intent is defined
- [ ] platform differences are documented

The spec fails if a developer must guess basic interaction behavior from screenshots.

---

# Quick Pre-Flight

## 30-second visual scan
- Does it look like this product rather than a generic AI app?
- Is hierarchy obvious?
- Is brand expression concentrated rather than everywhere?
- Are there too many cards/radii/shadows?
- Do icons belong to one coherent language?

## 2-minute interaction scan
- Can I identify top-level destinations?
- Can I identify the primary action?
- Do controls respond immediately?
- Does back/dismiss behavior make sense?
- Are loading/error/empty states available?
- Would large text break this?
- Is anything only discoverable by gesture?

## Platform scan
- Does iOS feel iOS-native?
- Does Android feel Android-native?
- Are they recognizably the same product without pretending to be the same OS?

---

# Output Format

## Native Design Audit: [Product]

### Executive summary
Short assessment of design health and highest-risk issues.

### Critical
Only issues that break usability, accessibility, or platform trust.

### High priority
Issues that materially weaken navigation, coherence, or interaction.

### Medium
Quality and consistency improvements.

### Low / polish
Nonessential refinements.

### Positive findings
Call out decisions worth preserving.

### Recommended next pass
A focused order of operations, not a giant redesign wishlist.

Do not score the design with arbitrary numbers. Explain observable issues and their impact.
