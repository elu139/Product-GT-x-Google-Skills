# Launchpad design system

This documents the visual system used to build the high-fidelity Launchpad
wireframes, extracted directly from the generator script that produced them
(not reconstructed from memory), so someone else building a new Google
Skills feature can match it without reverse-engineering the HTML.

Reference: the live canvas at https://claude.ai/artifact/8zHpJmCc4bAYo5Vr3QvDi3
and the screen notes in [`README.md`](README.md).

## Known gaps, checked against the live site

Verified by loading https://www.skills.google/ directly and reading its
computed styles (not guessed from markup):

- **Font**: the real site loads `Google Sans` (headings) and
  `Google Sans Text` (body, buttons, nav) as actual webfonts, confirmed via
  `document.fonts`. These fonts aren't available through the public Google
  Fonts API (`fonts.googleapis.com`), which is how our wireframes could
  reach them; Google serves them from its own infrastructure to its own
  properties. Our wireframes substitute **Inter** as a stand-in for the same
  reason a build outside Google's infra would need to: everything else
  (sizes, weights, line-height) should carry over unchanged once the real
  font is available.
- **Primary color**: the live site's root stylesheet sets
  `--md-sys-color-primary: #0b57d0`, a Material Design 3 token. Our
  wireframes used `#1a73e8` throughout, which is the older/Material-2-era
  Google blue still visible in the Google Cloud console screenshots we
  built from. **This is a real discrepancy.** A production build should use
  `#0b57d0` as the primary, not `#1a73e8`. See `README.md` for the full
  comparison.
- The live hero stat numbers ("77%", "90%", "133%") render at 48px, weight
  700, with the positive one colored `rgb(69,140,71)` / `#458C47`, a
  different, more muted green than our `GRN` token (`#188038`).

These were not available when the wireframes were first built (no live-site
reference was checked at the time); they're recorded here so a real
implementation uses the live tokens, not the wireframe approximations.

## Color tokens

| Token | Hex | Use |
|---|---|---|
| `BLUE` | `#1a73e8` | Primary actions, links, selected states, active nav |
| `BLUED` | `#1967d2` | Link text, text on light-blue backgrounds (darker than `BLUE` for contrast on white) |
| `BLUEL` | `#d3e3fd` | Selected nav pill background |
| `BLUEBG` | `#e8f0fe` | Info/context panel backgrounds (e.g. "what the mentor will see") |
| `INK` | `#1f1f1f` | Primary text |
| `SEC` | `#5f6368` | Secondary text, icons, metadata |
| `BOR` | `#dadce0` | Default borders |
| `BG` | `#f8f9fa` | Page background |
| `LINE` | `#e8eaed` | Dividers, neutral chip backgrounds, progress-bar track |
| `GRN` | `#188038` | Positive signals (progress deltas, "earned" states) |
| `GRNL` | `#e6f4ea` | Positive chip/panel backgrounds |
| `AMB` | `#f9ab00` | Stars, streak flame, badge icon accents |
| `PUR` | `#7b1fa2` | Pod/peer-feature accents (distinct from mentor-blue) |
| `PURL` | `#f3e8fd` | Pod accent panel backgrounds |
| `RED` | `#d93025` | Reserved for errors/destructive actions (defined, not yet used in current screens) |

Avatar background colors cycle through a fixed 7-color palette so each
person in a list is visually distinct without assigning meaning to color:
`#1a73e8, #188038, #c5221f, #7b1fa2, #e37400, #00796b, #3949ab`, all paired
with white text.

## Typography

- Font stack: `'Google Sans','Google Sans Text',Inter,Roboto,Arial,sans-serif`
  (Inter loaded as the working substitute, see above).
- Body text: 13-14px, weight 400, `line-height:1.45`.
- Emphasized/labels: same size, weight 500.
- Page titles: 28-32px, weight 500, slight negative letter-spacing (`-0.4px`
  to `-0.5px`).
- Section headings within a card: 16-20px, weight 500.
- Metadata/captions: 11-12px, weight 400, `SEC` color.
- No weight above 500 is used anywhere. No italics except one quoted
  learner request, styled with `font-style:italic` for emphasis only.

## Spacing and shape

- Base spacing unit is 4px; most gaps are 8, 10, 12, 14, 16, or 20px.
- Page padding: `24px 32px 40px`.
- Card-to-card gap in a layout: 20px.
- Card corner radius: **16px** (primary content cards).
- Smaller inset panel radius ("flat" panels: info boxes, chips-as-blocks):
  **12px**.
- Chip radius: **8px**.
- Pill radius (nav items, filters, buttons, status badges): **100px** (full
  capsule).
- Card shadow (Material-style, two layers):
  `0 1px 2px rgba(60,64,67,.3), 0 1px 3px 1px rgba(60,64,67,.15)`.
- Flat panels use a 1px solid border (`BOR`) instead of a shadow.

## Layout anatomy (every screen)

Every screen shares one page shell, generated once and reused:

1. **Top bar**, 64px tall, fixed, white background, 1px bottom border
   (`LINE`). Left to right: hamburger menu icon, "Google Skills" wordmark
   (21px, weight 500), a centered search field (max 560px wide, pill-shaped,
   `#f1f3f4` background), then right-aligned: star count, streak count, help
   icon, globe icon, 32px avatar.
2. **Left nav**, 88px wide, white background, 1px right border. Each item is
   an icon in a 56x34px pill (filled `BLUEL` and `BLUED` text when active,
   transparent and `SEC`/`#3c4043` otherwise) with an 11px label below. A
   small blue dot marks "new" items when inactive.
3. **Main content**, flexible width, `BG` background, padded.

Content within main is built from a small set of reusable blocks (see
below), composed in `flex-wrap:wrap` rows with `align-items:flex-start`, so
a side panel collapses under the main column on narrow widths rather than
breaking the layout. Pages are built fluid-width (`expand: "fill"` in canvas
terms), not fixed-width.

## Core components

All components are plain functions that return inline-styled HTML; there is
no CSS framework dependency, which keeps each screen a single self-contained
file.

| Component | Shape | Notes |
|---|---|---|
| **Card** | 16px radius, white, shadow, variable padding (usually 20-24px) | Primary content container |
| **Flat panel** | 12px radius, white or tinted background, 1px border, no shadow | Used for secondary info (context banners, tips) nested inside a card |
| **Chip** | 8px radius, 12px text, optional leading icon | Tags, status labels (e.g. "Verified mentor," "4 active") |
| **Pill** | 100px radius, 13px text | Filter toggles; selected state uses `BLUEBG` fill + `BLUE` border |
| **Button** | 100px radius pill, three kinds | `primary` (solid blue, white text), `tonal` (light blue fill, blue text), `outline` (white, bordered, blue text) |
| **Avatar** | Circular, initials, cycling color palette | Sized per context: 32px (top bar), 36-56px (lists), up to 88px (profile header) |
| **Verified badge** | Small circular icon, blue checkmark-shield glyph | Always paired with a mentor's name, never used alone |
| **Stars** | 5 inline star icons, filled amber up to the rating value | Paired with numeric rating and review count in parentheses |
| **Progress bar** | 6-10px tall, full-pill radius, `LINE` track, colored fill | Color signals meaning: blue for roadmap progress, green for pod/positive movement |
| **Icons** | Inline SVG, 24x24 viewBox, stroke-based (not filled), 1.6-2.4px stroke weight | A small fixed icon set (see below); no icon font, no emoji |

## Icon set

Icons are hand-drawn minimal stroke SVGs, not an imported library, so the
exact set is fixed. Current set: menu, search, dashboard, catalog, paths,
collections, credentials, subscriptions, organizations, rocket (Launchpad),
help, globe, star, flame, calendar, video, check, arrow, back, down-chevron,
clock, people, chat, doc, plus, verified-badge, home, bell, trend, lock,
play, edit, flag.

Anyone extending this needs to draw new icons in the same stroke style
(`stroke-width` 1.6-2.4, `stroke-linecap`/`stroke-linejoin` round, no fill
except on filled states like the verified badge or an active progress ring).

## Accessibility baseline already applied

- Real `<button>` and `<a href>` elements for every interactive control, not
  `onClick` on a div.
- Visually-hidden `<label>` on the search input.
- `aria-hidden="true"` on every decorative icon.
- Text colors chosen against `BG`/`#fff` for 4.5:1 contrast at body size.

## What to reuse vs. rebuild

A team building a new Skills feature can take directly:

- The color tokens and corner-radius scale above
- The page shell (top bar + left nav + content) structure
- The card/chip/pill/button component shapes

They should not assume the icon set, the avatar-initial pattern, or the
specific Inter substitution are final. Those were reasonable choices for a
prototype, not confirmed against Google's actual internal design system.
