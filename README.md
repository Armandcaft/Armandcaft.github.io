# armandcaft.github.io

Personal developer portfolio of **Christian Tchuente** — backend-leaning Software Engineer (.NET / C#).

Live: <https://armandcaft.github.io>

- Single self-contained `index.html` — no build step.
- Bilingual (FR / EN) with a runtime language switch; English is the in-markup source of truth.
- Dark, modern-bold design system (indigo `#6D5EF6` accent). Fonts: Space Grotesk / Inter / JetBrains Mono.

## Editing copy

Every translatable element carries a `data-i18n="key"` attribute; translations live in the `I18N` object at the bottom of `index.html`. **Any new visible string must be added to both `en` and `fr`.** Re-check parity after edits:

```bash
node -e '
const fs=require("fs"),html=fs.readFileSync("index.html","utf8");
const d=JSON.parse(html.match(/const I18N = (\{[\s\S]*?\n\})\s*;/)[1]);
const en=Object.keys(d.en),fr=Object.keys(d.fr);
const used=[...new Set([...html.matchAll(/data-i18n="([^"]+)"/g)].map(x=>x[1]))];
console.log("EN",en.length,"FR",fr.length,
 "| missingFR",en.filter(k=>!(k in d.fr)),
 "| missingEN",fr.filter(k=>!(k in d.en)),
 "| unresolved",used.filter(k=>!(k in d.en)));
'
```

## CV files

`assets/Christian_Armand_Tchuente_CV_{EN,FR}.pdf` — linked from the hero and Experience sections (the download href swaps with the active language). Replace in place to update; keep the filenames.
