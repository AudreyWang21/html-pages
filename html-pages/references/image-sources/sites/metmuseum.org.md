---
domain: metmuseum.org
aliases: [Met Open Access, collectionapi.metmuseum.org]
updated: 2026-10-08
---

## Platform characteristics
- REST API at `collectionapi.metmuseum.org`, no key, no bot wall; images on `images.metmuseum.org`. Public-domain objects are CC0. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -A "$UA" "https://collectionapi.metmuseum.org/public/collection/v1.1/search?hasImages=true&isPublicDomain=true&q=Hokusai&limit=5"   # IDs only
curl -s -A "$UA" "https://collectionapi.metmuseum.org/public/collection/v1/objects/715874" > o.json   # isPublicDomain, primaryImage, objectURL, artistDisplayName, objectDate
curl -s -A "$UA" -o big.jpg "<primaryImage>" && file big.jpg
python -c "from PIL import Image; im=Image.open('big.jpg'); im.thumbnail((1400,1400)); im.save('out.jpg',quality=85)"
```

## Known pitfalls
- `/v1/search` was retired 2026-10-01 (HTTP 410); search is `/v1.1/search`. The object endpoint is still `/v1/objects/<id>`. *(2026-10-08)*
- The `isPublicDomain=true` search filter does not hold: a hit came back not public domain with empty image fields. Check `isPublicDomain` on each object. *(2026-10-08)*
- Sizes: `web-large` (swap `original` in the path) is only ~600 px; `original` was 4000 px. Nothing in between, so download the original and shrink it (PIL, if installed: one tester had it, another did not). *(2026-10-08)*
- Some original URLs contain spaces; percent-encode them (untested). *(2026-10-08)*
