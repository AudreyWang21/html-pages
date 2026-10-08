---
domain: phylopic.org
aliases: [PhyloPic, api.phylopic.org]
updated: 2026-10-08
---

## Platform characteristics
- Organism silhouettes (PNG and SVG) for tree-of-life diagrams. JSON API, no key, no bot wall. Licences vary per image: CC0, PD mark, CC BY, CC BY-SA, CC BY-NC. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -sI https://api.phylopic.org/ | grep -i location          # current build number (558 on 2026-10-08)
curl -sL -A "$UA" "https://api.phylopic.org/images?build=558&filter_name=daphnia&page=0&embed_items=true" -o pp.json
# _embedded.items[]: attribution, _links.license.href, _links.rasterFiles[].href, _links.vectorFile
curl -s -A "$UA" -o daphnia.png "https://images.phylopic.org/images/<uuid>/raster/465x1024.png"
curl -s -A "$UA" -o daphnia.svg "https://images.phylopic.org/images/<uuid>/vector.svg"
```

## Known pitfalls
- Every call needs the current `build=`; a stale one returns HTTP 410 with the right number in the body. *(2026-10-08)*
- Two-word names can miss (`Picea glauca` gave nothing): search the genus. *(2026-10-08)*
- No working licence filter (the one tried 404'd); read the licence per item. Rasters only at listed sizes (~1024 px long side). *(2026-10-08)*
