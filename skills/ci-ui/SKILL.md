---
name: ci-ui
description: >
  Build or restyle a website or app UI with the user's three written corporate
  identities (CI): CI-1 Curve Bold (white, ink, one weight, 10px curves, grouped
  pill nav), CI-2 Thin (white plus one page colour, separate cards), CI-3 Thin Box
  (square-box app UI with a sidebar, Next.js and Tailwind). Use whenever starting a
  new page or site, adding a page, nav, hero, section header, card, call-to-action,
  footer or image to one of the user's sites (personal portfolio, organisation site, colour-page site, app UI), or
  when asked for "my CI", "the usual look" or "same style as the organisation site". Also use
  when updating one of the CI guides.
---

# ci-ui: the three CI styles

The full rules live in `references/`. Read the one that applies before writing code,
then add the shared rules below.

| Style | File | Use for |
|---|---|---|
| CI-1 Curve Bold | `references/ci-1-curve-bold.md` | Personal and multi-page org sites. White paper, black ink, greyscale, one weight, 10px curves, grouped pill nav. Extended with the organisation-site decisions. |
| CI-2 Thin | `references/ci-2-thin.md` | Org sites that want colour: every page is white plus one page colour, separate outlined cards, regular weight only. |
| CI-3 Thin Box | `references/ci-3-thin-box.md` | App interfaces: square boxes, sidebar shell, tokens, Next.js and Tailwind. |

## Workflow

1. If the user did not name a style, ask which one (CI-1, CI-2 or CI-3) before building. For
   a new page on an existing site, use that site's style.
2. Read the style file. For an existing site also read its `style.css` or Tailwind config
   and one finished page, and reuse the classes and tokens already there.
3. Build with the style's tokens only. Do not invent new colours, radii or components.
4. Apply the shared rules below, then check the "Do and don't" list at the end of the style file.
5. Check the result in a browser at desktop and at 600px. Say plainly what you did not test.

## Shared rules (all three styles)

**Language.** Sites are Thai and English by default. Every text node carries its Thai in a
`data-th` attribute and a `TH` / `EN` button in the nav swaps it. Save the choice in
`localStorage` inside try/catch, set `<html lang>`, and keep Thai in its own script. App
UIs (CI-3) are Thai first with the English toggle.

**Behaviour.**
- **Page blink:** a quick white dip between pages. Use cross-document view transitions:
  `@view-transition{navigation:auto}`, `html{background:#fff}`,
  `::view-transition-old(root){animation:vt-out .14s ease-in both}`,
  `::view-transition-new(root){animation:vt-in .24s ease-out .12s both}`. Keep the nav
  steady with `.nav{view-transition-name:nav}`. Browsers without support (Firefox, in-app
  browsers) get a plain `body` fade-in of about .2s as the fallback.
- **Reduced motion:** `@media(prefers-reduced-motion:reduce){@view-transition{navigation:none}}`
  and switch other animations off.
- **No hover tooltips.** Do not put `title` attributes on icons or links. Give icon-only
  controls an `aria-label` instead.
- **No tap highlight on phones:** `a,button,summary,[role=button]{-webkit-tap-highlight-color:transparent}`.
- External links open in a new tab with `rel="noopener"`.
- **Hover is brightness-only.** State change on hover is a shade of the existing colour, lighter
  or darker fill/text, never a hue swap, never an accent colour appearing out of nowhere. Active
  or current state follows the same rule: darker/filled plus an underline or outline, not a new
  colour.
- **Nav adapts to the background under it.** Over a dark photo hero the nav is translucent white
  pills/text; once the page scrolls past the hero (or on a page with no hero) the nav switches to
  its normal light-surface colours. One nav, two looks, swapped at the scroll boundary, not two
  separate components.
- **No native browser chrome.** Build custom controls, not OS-default widgets: no bare `<select>`,
  no native `<input type="date">` calendar, no native `alert`/`confirm`/`title` popups. Dropdowns,
  date pickers, menus and popovers are all hand-built to match the style's tokens (same radius,
  border, shadow rules as cards/pills in that CI).
- **Dropdowns animate open/close.** Never a hard show/hide. Transition height/opacity/transform
  (`max-height` or `grid-template-rows` plus `opacity`, `.15s`–`.25s` ease) so the menu, date
  picker or accordion panel eases in and out, consistent with `--transition` in that CI's tokens.
  Respect `prefers-reduced-motion` (cut to instant) same as the page blink.
- **Search fields use an underline, not a box.** A search input is bottom-border only (the
  underline thickens or inks on focus), not a bordered/filled box like other inputs.

**Optional photo hero (any style).** For a page with a good photo:
- Markup: a `<section class="hero-c hv dk ph">` with `style="--bg:url('x.webp');--bgs:url('x-sm.webp');--py:50%"`,
  inside it one `.hero-c-in` grid holding a 64px white icon (32px on phones), the `h1` and
  a one-line subtitle, then a white wave `<svg>` along the bottom edge.
- Look: the photo covers the section, centred at `--py` (set per page to choose the focus),
  under one flat black overlay at **78%** on every page. Fallback fill is the page colour.
  No tint and no blend.
- Size: `min-height:max(70svh,420px)` desktop, `max(52svh,360px)` at 600px and under.
- Text: white, left aligned inside a group that is centred in the hero. Title
  `clamp(26px,4vw,34px)` (20px on phones), subtitle 13px (11.5px on phones).
- Wave: `viewBox="0 0 1440 90"`, path `M0,50 C360,-10 1080,100 1440,30 L1440,90 L0,90 Z`,
  fill white, 76 to 104px high (52px on phones).
- Images: WebP, 1920px wide, plus an 800px `-sm.webp` for phones. Preload both in the
  `<head>` with `media="(max-width:600px)"` and `media="(min-width:601px)"` and
  `fetchpriority="high"`.
- The nav sits over the photo as translucent white pills until the page scrolls past it.

## Keeping the guides current

When a site's design decision changes, update the matching file in `references/` and the
source copy in the repo (for CI-1, `docs/CI-1-Curve-Bold.md`),
then tell the user what changed. Keep the three files as the single source of truth.

## Reference websites

Sites used as visual references for these styles:

- Chulalongkorn University: https://www.chula.ac.th/en/
- Anthropic: https://www.anthropic.com/
- Claude: https://claude.com/
- Fastwork: https://fastwork.com/
- 1DD: https://1dd.co/
