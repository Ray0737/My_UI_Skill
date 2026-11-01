# CI 3 · Thin Box

Corporate identity for a product app UI. An app interface: square boxes, light type, a sidebar shell. Built with Next.js and Tailwind, so everything runs on tokens.

Source: `tailwind.config.ts`, `app/globals.css`, `components/ui/button.tsx` and `CLAUDE.md` in that repo. Counts of Tailwind class uses come from a search of `app/` and `components/`. Sister guides: `CI-1-Curve-Bold.md`, `CI-2-Thin.md`.

---

## 1. Identity

| | |
|---|---|
| Name | the app name |
| Stack | Next.js, Tailwind only, `lucide-react` icons, `tailwindcss-animate` |
| Language | Thai UI text first, with an English toggle rolling out page by page |
| Tone | Plain and clear. No emoji, no em dashes in site copy |

In one line: **square boxes, light weights, blue primary, tokens for everything.**

---

## 2. Colour

Colours are HSL tokens in `app/globals.css`, used as `bg-primary`, `text-muted-foreground` and so on. Never use raw hex in components.

**Light theme**

| Token | Value |
|---|---|
| `--background` | `220 33% 98%` |
| `--foreground` | `226 44% 12%` |
| `--card` / `--popover` | `0 0% 100%` |
| `--primary` | `221 95% 31%` (`#043299`) |
| `--secondary` | `231 30% 94%` |
| `--muted` | `231 25% 94%` |
| `--muted-foreground` | `228 12% 44%` |
| `--accent` | `231 40% 92%` |
| `--mint` | `160 84% 39%` |
| `--destructive` | `0 72% 51%` |
| `--border` / `--input` | `230 20% 88%` |
| `--ring` | `221 95% 31%` |

**Dark theme:** background `225 18% 4%`, card `225 16% 7%`, text white, primary white on near-black, border `225 12% 14%`.

**Other rules**
- Pre-login pages (landing, login, signup) in light mode use a pure white page with pure black text.
- Several themes exist (Catppuccin Latte and Mocha, Gruvbox, Nord), edited as tokens and shown as live previews in Settings.

---

## 3. Typography

- **Family:** `line_seed_sans_th`, then IBM Plex Sans Thai, then sans-serif. Inter appears only in the landing-page footer.
- **Weights in the code:** `font-medium` 82 uses and `font-normal` 78 lead. `font-semibold` 22. `font-bold` only 3.
- **Sizes:** Tailwind scale. Buttons and sidebar rows are `text-sm`, medium.
- **Labels:** sidebar section labels are normal case, small and clean (the old uppercase wide-tracking style was dropped).
- **Copy:** no emoji, no em dashes (use a period, comma or colon), and never name competitor products in public copy.

---

## 4. Shape and icons

- **Radius tokens:** `--radius: .75rem` (lg). `md` is 2px less (10px), `sm` is 4px less (8px).
- **In practice sharp boxes win:** `rounded-none` is used 169 times, against `rounded-md` 37 and `rounded-lg` 22. Pills (`rounded-full`, 68 uses) are for tags and avatars.
- **Scrollbars:** thin, 8px, pill thumbs.
- **Icons:** `lucide-react` only.
- **Motion:** `fade-up` (.4s), `pulse-soft` (2s) and a short `flag-in` highlight.

---

## 5. Buttons

Component: `components/ui/button.tsx` (cva variants).

| Size | Classes |
|---|---|
| Default | `h-10 px-4 py-2` |
| Small | `h-9 px-3` |
| Large | `h-11 px-8` |
| Icon | `h-10 w-10` |

Base: inline-flex, centred, `gap-2`, `rounded-md`, `text-sm font-medium`, colour transitions, 2px focus ring, 50% opacity when disabled.

| Variant | Look |
|---|---|
| default | `bg-primary` with white text, hover at 90% |
| mint | `bg-mint` |
| destructive | `bg-destructive` |
| outline | 1px input border, transparent fill, accent on hover |
| secondary | `bg-secondary` |
| ghost | accent on hover only |
| link | primary text, underline on hover |

---

## 6. Layout

- **Container:** centred, 1rem padding, up to 1200px (`2xl`).
- **One sidebar** of about 256px, mounted once in `app/(app)/layout.tsx` and identical on every logged-in route (no per-route branching).
- **Sidebar order:** brand row, New Conversation, Explore Subjects, nav rows (Exam Bank, Flashcards, Notes, Curriculum, Org, Calendar), a scrollable Chats section, then a user row (avatar and name, opens Settings, dark-mode toggle and Logout).
- **Marketing nav** (`components/marketing-nav.tsx`) is separate, for public pages (`/`, `/about`, `/pricing`, `/terms`). New marketing pages go in its `navItems`, new app pages in the sidebar's.

---

## 7. Rules

1. Tailwind only. No CSS modules and no styled-components.
2. Match the existing design system before adding a component. Reuse tokens such as `bg-primary` and `text-muted-foreground`.
3. Use `lucide-react` for icons.
4. Thai copy first, English through the toggle, and keep the existing tone.
5. No emoji, no em dashes, no competitor names in public copy.
6. Edit theme colours as tokens, never as one-off values.

---

## 8. Do and don't

**Do**
- Prefer sharp square panels, and keep medium and normal weights.
- Use the shared `Button` and its variants.
- Keep the sidebar the same on every logged-in page.

**Don't**
- Add rounded cards everywhere. Square is the default.
- Use bold for emphasis where medium works.
- Hard-code colours.

---

## Shared rules

Language toggle, page blink, no tooltips, tap highlight, reduced motion and the optional photo hero are defined once in `../SKILL.md` and apply to this style too.
