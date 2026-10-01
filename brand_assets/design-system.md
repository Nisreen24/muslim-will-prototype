# Muslim Will — Design System v1

Source of truth for colour and type, recorded 20 September 2026.
Everything under **Canonical** is fixed. Everything under **Derived** is computed from the canonical values and may be tuned. Everything under **Open** still needs a decision.

Companion files: `tokens.css` (CSS custom properties and font links) and `tokens.json` (the same values for design tools and code generation).

## Colour: a 60 / 30 / 10 system

### Canonical

| Share | Name | Hex | Role |
|---|---|---|---|
| 60% | Warm Parchment | `#F3EEE5` | The environment: page backgrounds, breathing room, warm neutral surfaces. |
| 30% | Deep Ink | `#172033` | Structure: typography, information hierarchy, navigation, structural elements. |
| 10% | Burgundy | `#7A263A` | Signature: primary calls to action, selected states, meaningful legal milestones. |

Rules

- Do not overuse Burgundy.
- Do not turn every interactive component Burgundy. Secondary and tertiary actions are Deep Ink: filled, outlined or plain text.
- One Burgundy element per screen is the norm. A selected state plus the primary action is the ceiling.
- The interface should feel inspired by premium legal documents, not a fashion brand, an Islamic decorative app, or generic SaaS UI.

Contrast (WCAG 2.x, computed)

| Pair | Ratio |
|---|---|
| Deep Ink on Warm Parchment | 14.1 : 1 |
| Burgundy on Warm Parchment | 8.4 : 1 |
| Parchment or white on Burgundy | 9.7 : 1 |

### Derived

All mixes are simple sRGB blends of the three canonical colours, so nothing new enters the palette.

| Token | Formula | Hex | Use |
|---|---|---|---|
| `ink-muted` | 70% Ink / 30% Parchment | `#595E68` | Secondary text, metadata. 5.6 : 1 on Parchment. |
| `ink-disabled` | 30% Ink / 70% Parchment | `#B1B0B0` | Disabled text and icons. Not for body copy. |
| `line` | 12% Ink / 88% Parchment | `#D9D5D0` | Hairlines, dividers, resting input borders. |
| `line-strong` | 24% Ink / 76% Parchment | `#BFBDBB` | Focused input border, table header rule, outlined buttons. |
| `surface-raised` | 60% White / 40% Parchment | `#FBF9F5` | Cards, sheets and inputs sitting on Parchment. |
| `surface-sunken` | 5% Ink / 95% Parchment | `#E8E4DC` | Grouped-list backgrounds, table header fills, ghost-button hover. |
| `burgundy-hover` | 85% Burgundy / 15% Ink | `#6B2539` | Primary button hover. |
| `burgundy-pressed` | 75% Burgundy / 25% Ink | `#612538` | Primary button pressed. |
| `burgundy-soft` | 10% Burgundy / 90% Parchment | `#E7DAD4` | Fill behind a Burgundy-stroked selected row. Never used alone as an accent. |

### Open

- **Semantic colours** (success, warning, error) are not defined. Proposal: keep the interface near-monochrome. Errors are Deep Ink text on a `burgundy-soft` field with an icon, never a Burgundy fill, so Burgundy keeps meaning "action, selection, milestone". Success is a Deep Ink check mark. If a distinct error hue is later required it must not read as Burgundy.
- **Dark theme** is not part of the system. The product is Parchment-first. If a dark theme is ever needed it requires a lightened Burgundy, because `#7A263A` on `#172033` is only 1.7 : 1.

## Typography

### Canonical

- **Display: DM Serif Display** (Google Fonts, regular and italic only).
- **UI: Manrope** (Google Fonts, variable 200 to 800; use 400, 500, 600, 700).

DM Serif Display is reserved for important headings and selected moments of legal or emotional significance: the question on a one-question screen, section titles, the document title, "Your will is signed".

Manrope is used for all functional UI copy: body text, forms, buttons, labels, navigation and metadata.

Never use DM Serif Display for buttons, form labels, tabs, dense UI, or long paragraphs.

### Scale (mobile first, size / line-height in px)

| Token | Face | Size / LH | Weight | Tracking | Use |
|---|---|---|---|---|---|
| `display-l` | DM Serif Display | 34 / 40 | 400 | -0.01em | Screen question, document title |
| `display-m` | DM Serif Display | 28 / 34 | 400 | -0.01em | Section titles |
| `display-s` | DM Serif Display | 22 / 28 | 400 | 0 | Card titles of significance |
| `title` | Manrope | 18 / 24 | 600 | 0 | List headers, sheet titles |
| `body-l` | Manrope | 17 / 26 | 400 | 0 | Explanations, rule text |
| `body` | Manrope | 15 / 22 | 400 | 0 | Default UI text |
| `button` | Manrope | 15 / 20 | 600 | 0 | All buttons |
| `label` | Manrope | 13 / 18 | 600 | 0.01em | Form labels, chips |
| `caption` | Manrope | 12 / 16 | 500 | 0.01em | Metadata, helper text |
| `overline` | Manrope | 11 / 16 | 700 | 0.08em, uppercase | Eyebrows, step markers |

Numbers: set `font-variant-numeric: tabular-nums` wherever amounts or fractions align. Fractions such as 1/8 and 1/3 are Manrope 600 in Deep Ink.

### Open

- **Arabic** is not yet specified and Manrope has no Arabic glyphs. Proposal: Amiri or Noto Naskh Arabic for Arabic display and body. Right-to-left mirrors steppers, chevrons, progress bars and back buttons. Numeral policy (Western vs Eastern Arabic) is per locale.

## Tone

Legal · Calm · Authoritative · Human · Precise · Warm · Contemporary.

## Shape, spacing and components

Defined in `components.md`: Jomo's structure (grouped cards on a quiet ground, stacked sheets, collapsible sections, pill buttons, floating tab bar, dashed create rows, expanding option rows) with this colour and type system substituted in. Radii are 16 (cards), 32 (sheets), pill (buttons, chips, controls), 12 (inputs). Screen margin 16, card gap 12, section gap 24, button height 56. This supersedes the 8 / 12 / 20 radii proposed in v1.
