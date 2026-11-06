# LINE Seed Sans TH

The one typeface CI-1 uses (`line_seed_sans_th`, see `docs/CI-1-Curve-Bold.md` section 4). Pulled from
the eai.spsm site settings, self-hosted the same way there: one static weight, `woff2` only,
`font-display: swap`, preloaded in `<head>`.

## Files here

- `lineseedsansth_rg.woff2` — Regular weight, the only weight CI-1 loads. Bold text is browser
  faux-bold (`font-weight:700`), never a second font file (see CI-1 doc, "Type" section).

## `@font-face`

```css
@font-face{
  font-family:"line_seed_sans_th";
  src:url(fonts/lineseedsansth_rg.woff2) format("woff2");
  font-display:swap
}
```

Preload it in `<head>` on every page that renders text above the fold:

```html
<link rel="preload" href="assets/fonts/lineseedsansth_rg.woff2" as="font" type="font/woff2" crossorigin>
```

## License

LINE Seed is a typeface released by LINE Corporation. It is free to use under LINE's own Seed
font license (not OFL, not MIT) — read the terms at
[seed.line.me](https://seed.line.me/index_en.html) before using it outside this project or in a
commercial product. No separate license/`.wlf` file was found alongside the font in the source
site (`eai-spsm/eai.spsm`) to vendor here; if you have LINE's original license file, add it next
to the `.woff2` as `LICENSE.txt` instead of relying on this note.
