# CI 1 · Curve Bold

Corporate identity for a personal portfolio site. White paper, black ink, one typeface, thin 10px curves. Documents what the site does today so a new page can match without guessing.

Extended with the decisions from a multi-page organisation site: pill nav, section header spacing, call-to-action card, icon link pills, image rules, accent per site, footer by size. Sections 11 to 16 are the additions.

Source of truth: the site's `style.css` and page files. Sister guides: `CI-2-Thin.md`, `CI-3-Thin-Box.md`.

---

## 1. Identity

| | |
|---|---|
| Name shown | the site name (nav logo, page titles `Page \| Site name`) |
| Logo | Bootstrap icon `bi-journal-code` + the site wordmark, left of the navbar |
| Favicon | Inline SVG: ink `#1a1a1a` rounded square (r=7 of 32) with a light glyph |
| Tone | Calm, personal, editorial. Short sentences. First person on the main page, third person on records pages. |
| Language | English plus Thai: every text carries its Thai in `data-th` and a TH button in the nav swaps it (see the shared rules in `SKILL.md`). Japanese and Thai names stay in their own script |

In one line: **white paper, black ink, one typeface, soft rounded boxes.** No colour decoration, no gradients, no shadows.

---

## 2. Colour

Everything is greyscale except the optional per-site accent (section 16).

| Token | Value | Use |
|---|---|---|
| `--cream` | `#ffffff` | Page background, card fill |
| `--warm-100` | `#f7f7f5` | Icon boxes, hover wash, sidebar hover, skeleton base |
| `--warm-200` | `#ececea` | Hairlines, active row background, skeleton shine |
| `--warm-300` | `#d8d6d1` | Stronger borders (`--line`) |
| `--warm-500` | `#8a8782` | Muted text, inactive tabs, labels, captions, icons |
| `--warm-700` | `#4a4842` | Secondary text, descriptions |
| `--ink` | `#1a1a1a` | Headings, active state, primary text, underline |
| `--accent` | per site | One accent per site, only for the primary action, status tags and hover (section 16). an organisation site may use red `#C41616`; a personal site may use none |

Rules
- Headings `--ink`, descriptions `--warm-700`, meta `--warm-500`.
- Active or selected = `--ink` text plus an ink underline. Never a coloured highlight.
- Photos supply the only colour on the page. Keep the chrome neutral.

---

## 3. Typography

- **One family:** `line_seed_sans_th`, self-hosted (`fonts/lineseedsansth_rg.woff2`, `font-display: swap`, preloaded). `--font-display`, `--font-body` and `--font-mono` all point to it.
- **One weight (regular).** No bold file exists, so emphasis is made another way:
  - Hover and active tabs: `text-shadow: 0 0 .6px currentColor` (looks bolder, no width change).
  - People names and the playing track: `font-weight: 700` (browser faux bold). These are the only real faux-bold spots.

| Role | Size | Notes |
|---|---|---|
| Body | 15px / 1.65 | antialiased |
| Section heading `.edu-title` | 15px | no all caps |
| Item title `.edu-item h4` | 15px / 1.35 | |
| Description line | 12.5 to 13.5px | `--warm-500` or `--warm-700` |
| Label `.label`, list headings | 9px | `.18em` to `.2em` tracking, uppercase, `--warm-500` |
| Nav link | 10.5px | `.1em` tracking, uppercase |
| Doc chapter title | 22px | centred, black |
| Doc body | 14px / 1.85 | justified |

Uppercase appears only in small labels and nav links on single-page sites. The multi-page pill nav (section 11) is sentence case. Doc pages use none.

---

## 4. Shape, lines and motion

- **Radius:** `--radius: 10px` for cards and images. Doc cards 8px. Icon boxes 46px square at 10px. Chips and pills 999px.
- **Lines:** `--line` = 1px `--warm-300`; `--line-light` = 1px `--warm-200`. Sections separate with a light hairline, not just space.
- **No shadows, no gradients.** One exception: the flat black overlay on a photo hero (section 12).
- **Motion:** `--transition: .25s cubic-bezier(.4,0,.2,1)`. Cards lift `translateY(-3px)` to `-4px` on hover. Smooth scroll on `html`.
- **Loading:** `.skeleton` shimmer (1.5s linear) for image placeholders.
- **Icons:** Bootstrap Icons 1.11.3 (CDN). 13px in tabs, about 1.1rem in icon boxes, 88px on Docs cards (64px on phones).

---

## 5. Layout

- **Container:** max 1080px, centred, 1.5rem side padding.
- **Navbar:** fixed, 64px (`--navbar-h`), white at 92% with `backdrop-filter: blur(10px)`, 1px `--warm-200` bottom line, z-index 1000. `body` has `padding-top: var(--navbar-h)`.
- **Spacing:** section padding `1.75rem 0`; heading to content `1.5rem`; list gaps `1rem` to `1.25rem`; chips `.5rem`.
- **Grid:** `bootstrap-grid` only (no other Bootstrap parts).
- **Doc pages:** 220px sticky chapter sidebar plus a 720px centred justified column ; a work page is a single 680px column.

---

## 6. Components

**Navbar.** Logo left, Instagram, GitHub and mail icons right.

**Profile block.** Avatar and name, then the tab strip.

**Tab strip (`.info-tabs`).** About · Favorites · Photography · Moments · Contributions · People · Docs, each an icon plus label. Scrolls sideways on narrow screens, bar hidden. Inactive `--warm-500`; hover `--ink` plus thin text-shadow; active `--ink` plus a 2px ink underline on the strip's hairline. Panels are `.info-tab-panel`; the URL hash opens a tab (`index.html#docs`).

**Section (`.about-sec`).** Heading and content with a light hairline below.

**Icon-row item (`.edu-item`).** 46px `--warm-100` box with a grey icon, then title, one grey line and optional chips. Used for interests, skills, education, work and contact. Work and Contact sit in 2 columns, 1 on phones.

**Chips.** Outlined pill, 13.5px, `--warm-700`, small icon before the text.

**Poster cards (`.movie-card`).** Image on top, caption (title plus year or genre) below. `.mov-2` is 3 across at 16:9; `.fav-4` is 4 across at 4:3. Rows wrap, never scroll. Group titles (`.movie-group`) split categories. A missing image hides itself.

**Photo covers (`.ig-post` in `.ig-grid`).** Plain portrait covers, 4 per row, all 2:3 and cropped to fill, title only (no counts), 2 per row on tablet and phone. Used for photo albums. Each links to an album page.

**Song lists (`.music-extra`).** Name-only lists in auto-fill columns, about 230px wide. Numbered rows (01, 02…) between hairlines, a count after each heading, and a link arrow that appears on hover. Every name searches YouTube in a new tab. Film scores use the same layout.

**People tab.** Centred 640px column. Rows are plain with a bold name, role in small grey and an arrow; each opens a message (`<details>`).

**Docs cards (`.doc-card`).** At least 300px tall, large black icon centred at the top, then the small label, title, one-line caption and "Open" pinned to the bottom so they line up across the row.

**Lightbox.** Full-screen viewer with `<` and `>` buttons and arrow keys.

**Footer.** Centred small links and a grey copyright line.

---

## 7. UX rules

1. One page with tabs for depth; long reading goes to its own page.
2. No scrollbars inside content. Rows wrap. Only the tab strip scrolls sideways on tiny screens, bar hidden.
3. No carousels. Show everything and wrap it.
4. Every image has a caption or title.
5. Predictable hover: colour to ink, thin text-shadow on tabs, 3 to 4px lift on cards, underline on caption links.
6. State by darkness, not colour. Active is darker plus an underline.
7. External links open in a new tab (`target="_blank" rel="noopener"`).
8. Fail gracefully: broken images hide, `localStorage` is wrapped in try/catch, plain content works without JS.
9. Accessibility: `aria-label` (never a `title` attribute, so no hover tooltips) on icon tabs, icon links and player buttons, `alt` on images, real `<button>` and `<a>`, `lang="en"`.
10. Privacy: personal source files (`data/`) stay gitignored and unpublished. No contact details, addresses, birth dates or server info in the docs.

---

## 8. Responsive behaviour

| Width | Change |
|---|---|
| ≤ 1100px | Year grid 4 across (3 across at ≤ 768px) |
| ≤ 992px | Player stacks (player above playlist) |
| ≤ 768px | Tab-card rows 2 across; photo covers 2 across; doc sidebar stacks |
| ≤ 600px | Work and Contact 1 column; posters shorter (210px); doc and doc-card text smaller |
| ≤ 480px | Card rows 1 across |

---

## 9. Files and assets

- Static site: HTML, one `style.css`, inline page scripts. No build step.
- Images: `.webp` under `pic/` (`pic/site`, `pic/photos`…), thumbnails suffixed `-t`, `loading="lazy"`.
- Fonts in `fonts/`. Audio in `src/` (only tracks that actually play).
- Page titles: `Page | Site name`.

---

## 10. Do and don't

**Do**
- Reuse `.about-sec`, `.edu-item`, `.skill-chip` and `.movie-card` before inventing a block.
- Keep one family, one weight, greyscale.
- Let photos carry the colour.

**Don't**
- Add more than one accent colour, gradients (except the photo overlay), shadows or chat bubbles.
- Use all caps outside small labels and nav links.
- Add carousels, nested scrollbars or crops that hide the subject.
- Publish anything from `data/`.

---

## 11. Navigation (multi-page sites)

Single-page sites keep the section 5 navbar. A site with several pages uses this grouped pill nav.

- **Bar:** fixed, `--nav-h` 60px, white, same hairline. Pills on the left, icon pills and the language toggle on the right. On phones the pills collapse into a burger menu.
- **Pill:** 13px regular, `padding .4rem .85rem`, `gap .45rem`, fill `--warm-100`, radius 999px, a 15px icon before the label. Hover fill `--warm-200`. The current page is `--ink` fill with white text and a white icon.
- **Groups:** a pill with a small caret opens a dropdown of icon plus label rows. Open on hover (desktop) or tap. Group related pages, keep the top level to about five pills.
  - Home, Apply (single pills)
  - About: About, Universities Stats, Alumni, Accomplishment, FAQ
  - Moment: Life, Events, Gallery
  - Document: Material, Classwork Report, Tools
- **Right side:** icon-only pills (LINE, Instagram, GitHub), each with an `aria-label`, then the language toggle (`TH` / `EN`) with a translate icon.
- **Over a photo hero** the pills turn white at 16% with `backdrop-filter: blur(8px)` and white text. They go back to the normal fill once the page scrolls off the hero.
- The new page goes in the dropdown it belongs to, in the nav and in the footer.

---

## 12. Photo hero (optional)

Specified once in `SKILL.md` ("Optional photo hero"). In CI-1 use it for pages with a good photo: one photo, one flat 78% black overlay, white text, a white wave at the bottom. Pages without a photo keep the plain white header.

---

## 13. Section headers and spacing

Used for every content section (`.blk`).

| Part | Desktop | Phone (≤ 600px) |
|---|---|---|
| Title `h2` | 17px | 16px |
| Gap title to subtitle | 0 (they touch) | 0 |
| Subtitle `.lead` | 14px `--warm-500` | 12.5px |
| Gap subtitle to content | 2.4rem | 1.9rem |
| Gap between sections | 4.6rem bottom padding | 3.1rem |
| Gap between big list items | 3.4rem to 5rem | 3rem |

Title and subtitle read as one pair, then a clear gap before the content. Never a bold subtitle under a bold title.

---

## 14. Call-to-action card (`.cta-big`)

One card that sends the reader to a bigger page (for example "View the full curriculum").

- Centred column, 1px `--warm-200` border, radius 10px, padding `2rem 1.2rem`, `margin 0 0 3rem`.
- A 64px grey icon (52px on phones), a 18px title, a 14px `--warm-500` one-line description, then a small `Redirect` pill.
- The pill is the same size as a nav pill (13px, `.4rem .85rem`) in the site accent, with a small arrow icon.
- Hover: the card fill goes to `--warm-100`. The border does not change.
- Whole card is one link.

---

## 15. Icon link pills (`.lk`)

For "Official site", "View on Facebook" and similar links under an item.

- Pill: fill `--warm-100`, 13px `--warm-500`, `padding .3rem .75rem`, radius 999px, `gap .3rem`.
- A 15px leading icon (globe for a website, Facebook logo for Facebook), then the label, then a 10px arrow-up-right.
- Hover: fill `--warm-200`, text `--ink`.
- Rows wrap, `gap .3rem 1.1rem`, `margin-top .9rem`. Links open in a new tab.

---

## 16. Accent, footer, images

**Accent depends on the site.** Define one `--accent` token per site and use it only for the primary action pill, status tags (for example "Finalist") and link hover. An organisation site uses red `#C41616` (dark `#8f1010`). a personal site uses none and stays greyscale. Never use more than one accent.

**Footer depends on the site size.**
- Small personal site: centred small links and a grey copyright line (section 6).
- Multi-page organisation site: four columns (brand and school, Explore, More, Contact), then a thin bottom line with the copyright and, when it applies, an "Unofficial" notice. Every page in the nav is also in the footer.

**Images.**
1. WebP only. Never ship JPG or PNG photos.
2. Resize before saving: 1920px wide at quality about 76 for a full photo, 900px for a thumbnail. Keep the original out of the repo.
3. A hero photo also gets an 800px copy named `-sm.webp` for phones (≤ 600px).
4. Preload the hero (and its `-sm` copy) in the page `<head>` with `media` queries and `fetchpriority="high"`.
5. Everything else is `loading="lazy"` with `width` and `height` set.
