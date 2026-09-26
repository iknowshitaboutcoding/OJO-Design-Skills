# Native Visual Enrichment Reference

This reference replaces the old web "hero" model with a native-app model.

Native apps rarely need a website-style hero section. High-value visual treatment should appear where it improves onboarding, identity, content comprehension, or a key product moment without turning ordinary app chrome into marketing art.

---

# 1. Enrichment Ladder

Choose the lowest level that achieves the product goal.

## Tier A — Type-led
Use:
- strong title hierarchy
- deliberate spacing
- expressive but readable typography
- restrained color

Best for:
- utilities
- productivity
- settings
- data-heavy products
- serious workflows

## Tier B — Content image
Use one meaningful:
- product image
- photo
- map/media thumbnail
- illustration
- render

Best for:
- detail screens
- catalog/media products
- lifestyle products
- onboarding

## Tier C — Editorial composition
Use:
- asymmetric image crops
- layered text/image composition
- edge-to-edge media
- controlled overlap
- stronger graphic hierarchy

Best for:
- culture/media
- creative tools
- lifestyle
- brand-forward consumer apps

## Tier D — Motion-enriched
Use:
- content transformation
- meaningful image/video motion
- onboarding transition
- direct manipulation
- rare branded animation

Best for:
- emotionally important product moments
- creative/entertainment products

## Tier E — Immersive
Use:
- full-screen media
- camera
- maps
- spatial/direct manipulation
- playback
- creation canvases

Only when immersion is part of the actual product task.

---

# 2. Native Placement

Strong visual enrichment belongs primarily in:
- onboarding
- empty/first-use states when helpful
- content detail
- media/player surfaces
- creation tools
- home/dashboard when content itself is visual
- celebration/completion
- product-specific interactive objects

Keep these more restrained:
- tab/navigation bars
- standard toolbars
- settings controls
- system-like dialogs
- form chrome
- destructive confirmations

Brand should not make standard system behavior harder to recognize.

---

# 3. Content Before Decoration

If the product naturally contains rich content, use that content.

Prefer:
- user's photo
- album art
- plant/pet/product image
- map
- chart
- document preview
- real screenshot
- generated illustration with product meaning

over:
- generic gradient orb
- random 3D shape
- abstract blob
- decorative phone mockup
- fake dashboard thumbnail

A blank screen does not automatically need illustration.

---

# 4. Image Treatment

Specify:
- aspect ratio
- crop behavior
- focal point
- corner treatment
- edge-to-edge vs contained
- dark/light appearance behavior
- loading state
- error state
- accessibility description where meaningful

Do not bake essential text into bitmap imagery.

---

# 5. Editorial Composition Safety

Expressive layouts may use:
- overlap
- rotation
- crop
- irregular edges
- collage
- large type
- dense imagery

But preserve:
- reading order
- touch targets
- text scaling
- safe areas
- localization
- screen-reader order
- clear primary action

The expressive layer can break the grid; the interaction layer still needs structure.

---

# 6. Motion-Enriched Surfaces

Motion should explain or reinforce:
- object transformation
- progress
- direct manipulation
- narrative step
- media state
- celebration

Do not add motion merely because a screen is visually important.

Respect reduced motion.

---

# 7. Onboarding

Onboarding enrichment should:
- explain value
- demonstrate behavior
- request permissions in context
- avoid long theatrical introductions before the user can act

A highly branded opening can still be short.

Do not:
- show five generic marketing slides
- ask every permission at launch
- make users wait through unskippable animation

---

# 8. Empty States

Choose among:
- plain text + action
- small domain illustration
- example content
- guided first item
- contextual education

Use a large illustration only when it adds meaning or brand value.

---

# 9. Home / Dashboard

A native home surface may have a strong visual anchor, but avoid website-style "hero banner + CTA" by default.

Better anchors can be:
- current status
- user's latest content
- time-sensitive task
- meaningful summary
- active project
- media object
- domain visualization

The home screen should help the user continue, not advertise the app back to them.

---

# 10. Immersive Surfaces

When the task is:
- camera
- map
- playback
- drawing
- scanning
- reading
- photo/video editing

allow content to dominate.

System controls may become more minimal, but:
- safe areas remain real
- system gestures remain accessible
- important controls remain reachable
- exit/back remains understandable

---

# 11. Cross-Platform Mapping

The same visual concept can be expressed differently.

Example:
**Full-bleed detail image**
- iOS may use navigation/title behavior that integrates with scrolling content.
- Android may combine edge-to-edge content with an appropriate top app bar behavior.

Do not force identical chrome around the image.

---

# 12. Anti-Patterns

Reject:
- website hero sections copied into app home screens
- giant slogan above routine utility content
- decorative 3D objects with no product meaning
- fake device frames
- fake OS chrome
- autoplay video that competes with primary action
- abstract gradients used because real content is missing
- huge artwork that pushes the first useful action offscreen
- immersive visuals on settings/forms where they add friction
- image treatment that collapses under large text

---

# 13. Output Contract

When a screen receives visual enrichment, specify:

**Purpose**
Why this surface deserves stronger expression.

**Tier**
A / B / C / D / E

**Primary asset**
Real content / photo / illustration / media / none

**Composition**
How text, media, and controls relate.

**Platform behavior**
How the surface integrates with navigation/system bars.

**Accessibility**
Text scaling, descriptions, contrast, reduced motion.

**Fallback**
What happens when media is unavailable, loading, or reduced-motion is enabled.

High visual ambition is welcome. It just needs to belong to the product rather than to a portfolio screenshot.
