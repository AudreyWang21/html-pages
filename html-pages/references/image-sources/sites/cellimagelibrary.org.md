---
domain: cellimagelibrary.org
aliases: [Cell Image Library, cildata.crbs.ucsd.edu]
updated: 2026-10-08
---

## Platform characteristics
- Cell and protist microscopy, some electron micrographs. Server-rendered HTML search, no key; the tested record was public domain (credit requested as courtesy); read each record. Slow server. A REST API exists but needs a key (not pursued). *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -A "$UA" "https://www.cellimagelibrary.org/images?k=Paramecium&simple_search=Search" | grep -oE '/images/[0-9]+' | sort -u
curl -s -A "$UA" -o rec.html "https://www.cellimagelibrary.org/images/39247"            # JSON-LD: description, creator, datePublished, DOI; licence text
curl -s -A "$UA" -o cell.jpg "https://cildata.crbs.ucsd.edu/media/images/39247/39247.jpg"   # full JPEG (5370 px in the test)
```
- 512 px: `https://cildata.crbs.ucsd.edu/media/thumbnail_display/<id>/<id>_thumbnailx512.jpg`. Other guessed sizes 404; the `.tif` is ~48 MB. *(2026-10-08)*

## Known pitfalls
- Use the `k=` + `simple_search=Search` form; other search forms gave an empty response. *(2026-10-08)*
