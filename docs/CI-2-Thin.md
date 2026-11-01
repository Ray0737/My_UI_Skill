# CI 2 · Thin

Corporate identity for a colour-page organisation site. The same quiet system as Curve Bold, with colour added: every page is white plus one page colour, type stays regular weight and corners stay modest.

Source: the site's own CI page. Sister guides: `CI-1-Curve-Bold.md`, `CI-3-Thin-Box.md`.

---

## 1. Identity

| | |
|---|---|
| Name | the site name |
| Who | a school programme or club |
| Pages | Home, About, Join, Alumni, Works, Docs, Tools, CI, Moment, Env, Q&A |
| Copyright line | © year and site name |

In one line: **white plus one colour, regular weight, modest curves, separate cards.**

---

## 2. Colour

Pages alternate between white and one page colour.

**Page colours**

| Colour | Value | Pages |
|---|---|---|
| Navy | `#292d7a` | Home, Works, Moment, Docs, Env, CI |
| Red | `#f5423d` | About |
| Green | `#8acd6e` | Join |

**Neutrals**

| Colour | Value | Use |
|---|---|---|
| White | `#ffffff` | Every other section |
| Ink | `#000000` | Text on white |
| Deep navy | `#14163f` | Text on green and on white cards |
| Muted | `#5c5c5c` | Captions |
| Surface | `#f4f4f4` | Code, quiet fills |
| Photo filter | black at 84% | The only thing a photo gets |

**Accents**

| Colour | Value |
|---|---|
| Yellow | `#fff48c` |
| Mint | `#a5f2cc` |
| Lilac | `#f5cfff` |
| Orange | `#ffb162` |

Rules
- Text on red and navy is white. Text on green and the accents is deep navy, because white is too faint there.
- No more than three accents in one view.
- Photos: dark filter only. No tint, no blend. Hero photos use 84% black, Life at PSM uses 90%.

---

## 3. Typography

One typeface, one weight, for Latin and Thai: **LINE Seed Sans TH, regular.** No bold and no capitals. Size and colour make the hierarchy.

| Role | Size | Use |
|---|---|---|
| Display | `clamp(2rem, 7vw, 4.4rem)` | Hero titles |
| Heading | 1.5rem | Section titles, stacked above their line |
| Title | 1.05rem | Card titles |
| Body | 14px, line height 1.7 | Text |
| Small | .72rem to .8rem | Labels, captions, footer |

---

## 4. Shape and icons

| Element | Radius |
|---|---|
| Cards | 14px |
| Buttons | 8px |
| Pills | 999px |

- A colour band between two white sections gets curved edges, a faint dot grid and rings.
- Icons: Bootstrap Icons, saved with the site. They carry meaning and are never decoration. Link cards use them large, 64px.
- Icons in use: mortarboard, door-open, trophy, camera, palette, journal-text, images, github.

---

## 5. Layout

The same frame on every page.

1. **Nav:** site name left, pages centred, Q&A, Instagram and GitHub right. No blur. Clear over a photo, the page colour over a colour, white over white.
2. **Hero:** a photo under a dark filter only, or the page colour. One centred title, one short line under it and a "See more" cue. Every hero is the same height.
3. **Body:** content is 1200px wide. Section headings sit above their line, left aligned.
4. **Sections** alternate white and the page colour.
5. **Footer** on every page: all page links, then the official channels, each with a redirect arrow, then "Back to top".

---

## 6. Components

**Cards.** Separate cards, never joined into one box.
- Each has its own outline and a 12px gap to the next.
- No lines inside a card. Parts are split by spacing.
- A card that links fills with the page colour on hover (white on a colour section). Text and icon turn white.
- Link cards: year or label top left, one big centred icon, then the title and the action at the bottom.

**Link lists.** Ruled rows with a label, short text and a redirect arrow.

**Tags and tabs.** No bubbles. Tags are plain text. Tabs are underlined text.

**Buttons.** 8px radius, regular weight.

---

## 7. Photos

1. Only a dark filter goes over a photo.
2. Photos are resized copies, 1000 to 1800px wide. Originals are never edited.
3. Hero photos 84% black. Life at PSM 90%.

---

## 8. Do and don't

**Do**
- Use white plus one page colour per page and alternate sections.
- Keep text regular weight, no capitals.
- Use deep navy text on green and on the accents.

**Don't**
- Use bold or all caps.
- Put more than three accents in one view.
- Join cards into one box or draw lines inside a card.
- Add bubbles, tints or blends on photos.
