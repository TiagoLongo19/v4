# Convite de casamento: Isabel & Luís

Digital invitation for the wedding on 29 October 2027: ceremony at the Mosteiro de Grijó, then a copo-de-água at Quinta O Campo, Freamunde.

## Files
- `convite.html`: the page source (no `<!doctype>`; the claude.ai artifact wraps it).
- `index.html`: the standalone page built from `convite.html`. This is the file you publish.
- `img/`: illustrations and photos used by the page.
- `musica/the-moment.mp3`: background music, re-encoded and quieter than the original.
- `PLANO-ILUSTRACOES.md`: the illustration plan and venue notes.

## Editing
Near the end of `convite.html`, the `CONFIG` block holds the couple's phone numbers and the music file.
Near the top, replace `SITE` in the `og:` tags with the final address so the WhatsApp preview works.

## Building `index.html`
```sh
{ printf '<!DOCTYPE html>\n<html lang="pt-PT">\n<head>\n<meta charset="utf-8">\n<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">\n'; \
  sed -n '1,/^<\/style>/p' convite.html; printf '</head>\n<body>\n'; \
  sed -n '/^<\/style>/,$p' convite.html | tail -n +2; printf '</body>\n</html>\n'; } > index.html
```

## Publishing (Netlify)
Upload `index.html` together with `img/` and `musica/`. To deploy from git, connect this repository; no build step is needed.
