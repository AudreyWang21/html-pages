---
domain: nps.gov
aliases: [NPS NPGallery, npgallery.nps.gov]
updated: 2026-10-08
---

## Platform characteristics
- NPGallery has no documented API, but the site's own JSON endpoints answer plain GETs, no key, no rate limit seen. Parks, landscapes, wildlife, trees, mushrooms; no microscopy. Assets carry a public-domain flag. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -A "$UA" -o r.json "https://npgallery.nps.gov/Search/Amanita%20muscaria"
# Results[].Asset: AssetID, Title, Description, AltText, PhotoCredit, ImageCreateDate, NPSUnits,
#   ResourceType (keep "Image"), ConstraintsInformation.Constraint ("Public domain")
curl -s -A "$UA" -o out.jpg "https://npgallery.nps.gov/GetAsset/<AssetID>/proxymdres.jpg"   # 1548 px
```
- Record page: `https://npgallery.nps.gov/AssetDetail/<AssetID>`. Other sizes: `proxyhires.jpg` (3096 px), `proxylores.jpg`, `thumbxlarge.png` (200 px), `original.jpg`. *(2026-10-08)*

## Known pitfalls
- The term goes in the path: `?searchtext=` is ignored and returns generic hits. Matching is fuzzy, any-words. *(2026-10-08)*
- Plain `/GetAsset/<id>` (no size) returns the full original, 23 MB in the test, and ignores size params: always name `proxymdres.jpg`. *(2026-10-08)*
- Check `Constraint` per asset; some NPS assets can carry other constraints. *(2026-10-08)*
