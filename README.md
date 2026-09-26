<div align="center">

# OJO Native Design Skills

**A native-mobile UI/UX design skill for AI coding agents — adapted from OJO Design Skills for iOS/iPadOS and Android.**

Native targets: **SwiftUI · UIKit · Jetpack Compose · Android Views/XML**

</div>

---

This fork adapts the original [OJO Design Skills](https://github.com/touchine-ojo/OJO-Design-Skills) methodology for **native app design only**.

It keeps OJO's strongest design ideas:

- product-register derivation
- Convention vs Innovation tracks
- anti-AI-slop guardrails
- brand-driven visual direction
- Material Metaphor
- semantic design tokens
- motion purpose
- design audit

and removes or replaces web-specific assumptions such as:

- Tailwind/CSS as the design output
- DOM/ARIA as accessibility rules
- mandatory hover states
- browser breakpoints
- web font-provider requirements
- React/component-library assumptions
- browser/GPU animation recipes
- website-style hero defaults

The skill is intentionally **design-first and framework-agnostic**. SwiftUI/UIKit and Compose/Views are implementation targets, not separate visual systems.

## Design principle

A native app should be:

**distinctive without fighting the platform.**

The skill separates:

1. **Product identity** — shared across platforms
2. **Platform behavior** — allowed to differ between iOS and Android
3. **Implementation framework** — SwiftUI/UIKit/Compose/Views should not dictate the visual identity

It does **not** force pixel-identical cross-platform UI.

---

## What the skill covers

- Product type and platform assessment
- Information architecture and native navigation
- Design research
- Visual-direction exploration
- Brand methodology / Material Metaphor
- Semantic design tokens
- Native component specifications
- Touch states and gestures
- iOS / Android platform mapping
- Motion and haptics
- Dynamic Type / font scaling
- VoiceOver / TalkBack
- Reduced motion
- Safe areas / edge-to-edge / system bars
- iPad / Android large-screen adaptation
- Loading / empty / error / offline states
- Native design audit

## Platform scope

### Apple
- iPhone
- iPad
- SwiftUI
- UIKit
- mixed SwiftUI/UIKit projects

The design layer follows Apple Human Interface Guidelines and platform behavior rather than treating SwiftUI and UIKit as different design systems.

### Android
- phones
- tablets
- foldables / adaptive layouts where relevant
- Jetpack Compose
- Android Views/XML
- mixed Compose/View projects

Kotlin is treated correctly as the implementation language; Compose and Views/XML are the UI implementation systems.

---

## Quick start

Install into Codex:

```bash
curl -fsSL https://raw.githubusercontent.com/iknowshitaboutcoding/OJO-Design-Skills/main/scripts/install.sh | bash -s -- --target codex
```

Claude Code:

```bash
curl -fsSL https://raw.githubusercontent.com/iknowshitaboutcoding/OJO-Design-Skills/main/scripts/install.sh | bash -s -- --target claude-code
```

Other supported targets:

| Client | `--target` |
| --- | --- |
| Codex | `codex` |
| Claude Code | `claude-code` |
| ZCode | `zcode` |
| DeepCode | `deepcode` |
| WorkBuddy | `workbuddy` |
| OpenCode | `opencode` |
| Generic agent | `generic` |

Install from a local checkout:

```bash
./scripts/install.sh --target codex
```

Preview without writing:

```bash
./scripts/install.sh --target codex --dry-run
```

---

## Skill

### `app-ui-ux-best-practices`

The folder name is kept for installer compatibility, but the skill frontmatter is now:

```text
native-app-ui-ux-best-practices
```

The workflow is:

```text
Product + platform brief
        │
        ├─ Information architecture
        │
        ├─ Native-platform research
        │
        ├─ Convention or Innovation track
        │
        ├─ Visual direction
        │
        ├─ Semantic tokens
        │
        ├─ Native component specs
        │
        ├─ Motion + haptics
        │
        ├─ Accessibility + adaptivity
        │
        └─ Native design audit
```

---

## Reference structure

The skill ships with native-adapted references:

- `anti-patterns.md`
- `visual-tokens.md`
- `component-recipe.md`
- `component-libraries.md` — now a native platform-component reference
- `motion-system.md`
- `material-metaphor.md`
- `icon-guidelines.md`
- `hero-enrichment.md` — now native visual-enrichment guidance
- `design-audit.md`

## Important behavior

The skill does **not**:

- require React, React Native, Expo, or web frameworks
- require a paid MCP
- require Mobbin, Firecrawl, or any other paid research service
- require third-party font services
- output Tailwind classes as the design specification
- redesign every native component for brand novelty

External design-research services may still be used if the user already has access to them, but they are optional.

---

## Platform sources

The skill is designed to defer to current official platform guidance where behavior matters:

- [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/)
- [Android mobile design guidance](https://developer.android.com/design/ui/mobile/)
- [Material Design 3](https://m3.material.io/)
- [Android accessibility guidance](https://developer.android.com/guide/topics/ui/accessibility/)

Because platform guidance evolves, agents should prefer current official documentation over hardcoded old implementation assumptions.

---

## Upstream and license

This project is a fork/adaptation of:

[**touchine-ojo/OJO-Design-Skills**](https://github.com/touchine-ojo/OJO-Design-Skills)

The original methodology and this adaptation are distributed under the repository's **MIT License**.

The goal of this fork is not to replace OJO's web-oriented skill. It is to preserve its design methodology while making the rules safe and useful for native mobile products.
