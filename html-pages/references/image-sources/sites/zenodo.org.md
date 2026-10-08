---
domain: zenodo.org
aliases: [Zenodo, Plazi, Biodiversity Literature Repository, biosyslit]
updated: 2026-10-08
---

## Platform characteristics
- The Biodiversity Literature Repository community (`biosyslit`, fed by Plazi) republishes figures from open-access taxonomy papers as single records with the paper's licence. Good for microscopy, protists and rare taxa that Commons lacks. No key for light use. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -sS -A "$UA" 'https://zenodo.org/api/records?q=%22Paramecium%22&communities=biosyslit&type=image&size=5'
# hits[]: id, metadata.license.id, metadata.creators, metadata.title/description (caption), related_identifiers (parent article DOI), links.self_html
curl -sSL -A "$UA" -o fig.png "https://zenodo.org/api/records/16815822/files/figure.png/content"
```

## Known pitfalls
- The IIIF form `/api/iiif/.../full/1000,/0/default.jpg` gave HTTP 400; download the original file. *(2026-10-08)*
- Size is whatever the article had (517x801 in the test), and figures are often multi-panel: crop. *(2026-10-08)*
- Licence is mostly CC BY 4.0, but some records are NC: read `license.id`. Credit the parent article's authors. *(2026-10-08)*
