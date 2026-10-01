# Muslim Will — Component System v1 (Jomo structure, our colour and type)

Recorded 20 September 2026 from about forty Jomo screens on Mobbin (home, rules, session sheets, settings, onboarding, paywall). The structure, shapes, sizes, hierarchy and navigation below are copied from Jomo as observed. Colour and type are substituted from `design-system.md`. Sizes are in iOS points, estimated from 393-point-wide screenshots; treat them as ±2.

Precedence: the user's brand rules in `design-system.md` win over Jomo wherever the two conflict. Where Jomo uses its blue, we apply the Burgundy budget; where Jomo uses black, we use Deep Ink; where Jomo uses SF Pro, we use Manrope, with DM Serif Display only at the moments Jomo uses its biggest display type.

## 1. What Jomo's system is

- **Grouped-card layout on a quiet ground.** Every screen is a stack of white cards on a light grey ground. Cards hold rows; rows hold an optional leading icon, a title, an optional grey subtitle and a trailing value or control. Hairline dividers between rows are inset to the text edge.
- **Sheets, stacked.** Almost everything opens as a bottom sheet with a grab handle and large top radius. Sheets stack: the sheet behind scales down slightly and dims. A sheet has a centred bold title; editing sheets put a round close button left and a round confirm button right.
- **Collapsible sections.** Grey bold section headers with a small chevron ("⌄ Suggestions", "⌄ Limits") collapse their content.
- **One floating action.** A full-width pill button floats above the tab bar ("+ Start blocking"). Sheets end with one or two pill buttons pinned to the bottom.
- **Pill-shaped everything interactive.** Buttons, segmented controls, chips, tab bar and search fields are fully rounded. Cards and option rows are rounded rectangles.
- **Dashed "create" affordance.** Adding something is a dashed-outline row or card with placeholder text and a small plus circle.
- **Expanding option rows.** In a list of radio options, the selected row expands in place to reveal its settings and a preview.
- **Big number heroes.** Tab screens open with one very large number and a status chip under it.
- **Friendly extras Jomo has that we drop:** a sky-photo gradient behind the home hero, a 3D phone mascot, emoji as row icons, photo-backed suggestion cards and orange gradients for premium features.

## 2. Surfaces and elevation

| Level | Jomo | Ours | Shadow |
|---|---|---|---|
| Ground | light grey `#F2F3F5` | Warm Parchment `#F3EEE5` | none |
| Card, row group, option row | white | `surface-raised` `#FBF9F5` | `0 1px 2px rgba(23,32,51,.04)` |
| Sunken field (segmented track, search, stepper, chip) | `#EEEFF2` | `surface-sunken` `#E8E4DC` | none |
| Sheet | white, top radius 32 | `surface-raised` | `0 -8px 32px rgba(23,32,51,.12)` |
| Floating (tab bar, floating CTA, round icon buttons, secondary white pill) | white, blurred | `surface-raised` at 92% with backdrop blur 20 | `0 8px 24px rgba(23,32,51,.12)` |
| Dimmed sheet behind | scaled 0.94, dimmed | same, dim with Ink at 35% | |

## 3. Layout and spacing

| Token | Value | Where |
|---|---|---|
| `screen-margin` | 16 | left and right of every screen and sheet |
| `card-padding` | 16 | inside cards and option rows |
| `card-gap` | 12 | between cards in a stack |
| `section-gap` | 24 | between a section header and the previous section |
| `row-height` | 52 | single-line row; 64 with subtitle |
| `button-height` | 56 | primary and secondary pills |
| `button-height-sm` | 40 | round icon buttons, chips with tap targets |
| `tab-bar-height` | 64 | plus safe area |
| `sheet-top-inset` | 12 | grab handle to title |
| `bottom-dock` | 16 | button block above safe area |

## 4. Shape

| Token | Value | Where |
|---|---|---|
| `radius-card` | 16 | cards, option rows, list groups, banners |
| `radius-sheet` | 32 | top corners of sheets |
| `radius-pill` | 999 | buttons, segmented controls, chips, search, tab bar, floating CTA |
| `radius-input` | 12 | text fields inside cards |
| `radius-thumb` | 8 | small squares such as app icons or the selected tab background (12) |
| Dashed create affordance | `radius-card`, 1.5px dashed `line-strong` | |

These replace the 8 / 12 / 20 radii proposed earlier in `design-system.md`.

## 5. Type mapping

Jomo is SF Pro at every size. We keep its sizes and weights in Manrope and use DM Serif Display only where Jomo uses its largest display sizes.

| Jomo role | Jomo | Ours |
|---|---|---|
| Hero number on a tab screen ("1h32") | SF 64–72 bold | DM Serif Display 56 / 60, tabular figures |
| Onboarding headline ("The app that ends bad screen time") | SF 26 bold centred | DM Serif Display 30 / 36 centred |
| Tab screen title ("Rules") | SF 28 bold, left | Manrope 700 28 / 34 |
| Tab screen subtitle ("3 actives") | SF 13 regular grey | Manrope 500 13 / 18 `ink-muted` |
| Sheet title ("Block screens") | SF 17 bold centred | Manrope 700 17 / 22 |
| Section header ("Customization") | SF 20 bold grey | Manrope 700 18 / 24 `ink-muted` |
| Card title with icon ("Time Limit") | SF 17 semibold | Manrope 700 17 / 22 |
| Row title | SF 15 regular | Manrope 500 15 / 20 |
| Row subtitle | SF 13 regular grey | Manrope 400 13 / 18 `ink-muted` |
| Trailing value ("4h25") | SF 15 semibold grey | Manrope 600 15 / 20 `ink-muted`, tabular |
| Button | SF 17 semibold | Manrope 600 16 / 20 |
| Chip | SF 12 semibold | Manrope 600 12 / 16 |
| Helper text under a control | SF 12 regular grey | Manrope 400 12 / 16 `ink-muted` |
| Stat label / value pair ("Pickups 40") | SF 13 grey over SF 20 bold | Manrope 500 13 over Manrope 700 20 |

Serif appears in exactly two places per journey: the hero and the one-question headline. Everything in a sheet is Manrope.

## 6. Colour mapping

| Jomo role | Jomo colour | Ours | Note |
|---|---|---|---|
| Primary pill button ("Save", "Continue") | black | Burgundy `#7A263A`, text `on-burgundy` | The one Burgundy element on most screens |
| Floating CTA ("+ Start blocking") | blue gradient | Burgundy, flat | Same element as primary; a screen has the floating CTA or a bottom primary, never both |
| Secondary pill ("New template", "I already have an account") | white with shadow | `surface-raised` with floating shadow, Ink text | |
| Tertiary pill ("Later", "Cancel", "No") | light grey | `surface-sunken`, Ink text | |
| Round confirm button on sheets (✓) | blue circle | Burgundy circle; disabled: `burgundy-soft` | Counts as the sheet's Burgundy element |
| Round close / help / more buttons | white circle | `surface-raised`, Ink glyph | |
| Selected radio in an option list | blue circle, white check | Burgundy circle, `on-burgundy` check | Selected state |
| Unselected radio | thin grey circle | 1.5px `line-strong` circle | |
| Toggle on | blue | Deep Ink | Settings are not answers, so not Burgundy |
| Segmented control | white segment on grey track | `surface-raised` segment on `surface-sunken` track | |
| Selected chip toggle ("✓ Yes") | blue fill | Deep Ink fill, Parchment text | |
| Text link ("Learn more", "Get inspired") | blue | Deep Ink 600, underlined | |
| Info banner ("Will be blocked: 2 categories") | light blue field, blue text | `surface-sunken` field, Ink text | |
| Status chip, active ("Blocking") | blue tint, blue text | `burgundy-soft` field, Burgundy text | Legal milestone family: "Signed", "Witnessed" |
| Status chip, neutral ("Upcoming", "All day") | grey tint | `surface-sunken`, `ink-muted` text | |
| Success toast ("Template created!") | green | Deep Ink field, Parchment text, check icon | Near-monochrome by design |
| Destructive action ("Delete this rule") | red tint, red text | `burgundy-soft` field, Burgundy text | Rare, deliberate |
| Premium / trial gradient | orange gradient | Burgundy, flat | No gradients in the system |
| Section header text | grey | `ink-muted` | |
| Dividers | hairline grey | `line` | |
| Dashed create affordance | grey dashed | `line-strong` dashed, `ink-muted` placeholder | |
| Home hero background | sky photo gradient | Warm Parchment, no image | |

Burgundy budget per screen, from this mapping: the primary action (pill or floating CTA or sheet confirm) plus at most one selected answer, plus status chips only when they mark a signed or witnessed state.

## 7. Components

### Navigation
- **Floating tab bar.** Pill, height 64, 16 from each edge, `surface-raised` with blur and the floating shadow. Four items with icon over 11-point label. Selected item: Deep Ink rounded square (radius 12) behind a Parchment icon and label. Tabs for us: Home, Will, People, Vault.
- **Tab screen header.** Title 28 / 700 at left with a 13-point `ink-muted` subtitle; one or two round 40-point icon buttons at right.
- **Sheet chrome.** Grab handle 36 × 5 `line-strong`, title centred, round close (left) and round confirm (right) when the sheet edits something; otherwise just the title. Sheets stack.
- **Popover menu.** Small `surface-raised` card with radius 16 and a caret, holding a segmented control and a short list with a check on the selected row.

### Cards and rows
- **Card.** Radius 16, padding 16, `surface-raised`, card shadow. Title row with leading icon, title 17 / 700, trailing chevron or count chip.
- **Row group.** A card whose rows are separated by inset hairlines. Row: leading 20-point icon in `ink-muted`, title 15 / 500, optional subtitle 13 `ink-muted`, trailing value 15 / 600 `ink-muted` plus chevron, or a control.
- **Collapsible section.** Header 18 / 700 `ink-muted` with a 12-point chevron; tapping collapses the cards beneath.
- **Stat trio.** Three columns separated by hairlines: label 13 `ink-muted` over value 20 / 700.
- **Dashed create card or row.** 1.5px dashed `line-strong`, placeholder text in `ink-muted`, 24-point plus circle at right.

### Selection
- **Option list.** Each option is its own card with a trailing radio. The selected option expands to show a preview and its settings beneath a hairline.
- **Segmented control.** Pill track `surface-sunken`, height 36, selected segment `surface-raised` with card shadow.
- **Chip toggle.** Pill, height 36, "✓ Label" when selected in Deep Ink.
- **Toggle.** iOS switch, on colour Deep Ink.
- **Stepper.** Round minus and plus buttons flanking a large value ("− 2 days +").
- **Wheel picker.** Native, embedded inside the sheet, with helper text beneath.
- **Checklist with categories.** Row with leading circle check, icon, label, trailing count and chevron; a sunken search pill pinned under the list.

### Buttons
- **Primary.** Pill, height 56, full width, Burgundy. Hover `burgundy-hover`, pressed `burgundy-pressed`, disabled `surface-sunken` with `ink-disabled` text.
- **Secondary.** Pill, height 56, `surface-raised`, floating shadow, Ink text. Sits left of the primary in a two-button dock ("New template · Schedule").
- **Tertiary.** Pill, `surface-sunken`, Ink text, used for "Later" and "Cancel".
- **Round icon.** 40-point circle, `surface-raised`, floating shadow.
- **Floating CTA.** Primary pill floating 12 above the tab bar with the floating shadow.

### Chips, status and feedback
- **Status chip.** Pill, height 24, icon plus 12 / 600 text. Neutral on `surface-sunken`; milestone on `burgundy-soft` with Burgundy text ("Signed", "Witnessed"); the completed milestone chip may be solid Burgundy.
- **Count chip.** Small pill with icon and number ("🔥 1" in Jomo becomes a witness count or document count for us).
- **Banner.** Radius 16, `surface-sunken`, 13-point Ink text, optional trailing chevron.
- **Toast.** Full-width radius 16 card at the top, Deep Ink with Parchment text and a check icon.
- **Modal alert.** Centred card radius 20 with a short title, body, and two pills (Cancel tertiary, Continue primary).
- **Action sheet.** Bottom sheet with a grey prompt line, then full-width pills: neutral on `surface-sunken`, destructive on `burgundy-soft` with Burgundy text, then Cancel.

### Inputs
- **Text field.** Radius 12 inside a card, `surface-raised` on the card or `surface-sunken` when standalone, 16-point text, 1px `line-strong`, focus ring 2px Ink.
- **Search.** Pill, `surface-sunken`, leading magnifier, trailing mic hidden for us.
- **Editable title.** Title with a small pencil glyph after it, as on Jomo's "Session ✎".

### Heroes and progress
- **Tab hero.** Overline 13 `ink-muted`, DM Serif Display 56 number or word, then a status chip ("✓ Under your goal" becomes "✓ Will up to date" or "1/3 bequest room used").
- **Bar chart card.** Card with a stat trio on top and a simple bar chart below; bars in Deep Ink, highlighted range in `burgundy-soft`, gridlines in `line`, a small chevron at the bottom to expand.
- **Progress bar.** 4-point track `surface-sunken`, fill Deep Ink; Burgundy only for the bequest cap meter.

## 8. Mapping to our screens

| Our screen | Jomo pattern |
|---|---|
| Home | Tab hero (estate readiness) + stat trio card (heirs, documents, bequest room) + floating CTA "Continue your will" |
| Will (journey list) | Rules screen: collapsible sections (You, Family, Estate, Bequests, Roles, Sign) with one card per section showing status chips and a dashed "Add…" row |
| One-question screen | Onboarding question list: serif headline, option cards with trailing chevron or radio, primary pill docked |
| Heir details / roles | Session sheet: editable title, collapsible rows (Relationship, Details, Shares), two-button dock |
| Relationship picker | App-group sheet: segmented control, checklist rows with count, search pill, banner with the consequence |
| Bequest allocation | Screen-time settings sheet: stepper around a large value, "Customise" row, helper text, progress bar under it |
| Witness status | Rules card: status chips (Invited, Confirmed, Signed) and a count chip |
| Settings and vault | Stacked settings sheets with row groups and toggles in Ink |
| Delete / revoke | Action sheet with the destructive pill |
| Paywall | Jomo Plus paywall: laurel line, headline, three plan cards with the middle one outlined in Burgundy and a "Most popular" chip, primary pill with a second line of small text |

## 9. Not copied

Sky-photo hero, phone mascot and illustrations, emoji row icons, photo-backed suggestion cards, gradients of any kind, orange and green semantic colours, "streak" flames. Row icons are a single 20-point line icon set in Deep Ink or `ink-muted`.
