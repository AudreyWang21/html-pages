---
domain: jpsearch.go.jp
aliases: [Japan Search]
updated: 2026-10-08
---

## Platform characteristics
- Cross-search over hundreds of Japanese databases (ColBase, NDL, museums, ukiyo-e archives). No key. The Web API parameters are undocumented (the developer page covers only SPARQL). *(2026-10-08)*

## Valid URL patterns
```bash
curl -s -G -A "<Project>/1.0 (personal non-commercial study page)" "https://jpsearch.go.jp/api/item/search/jps-cross" --data-urlencode "keyword=Hokusai" --data-urlencode "size=100" -o jp.json
# list[].common: title, titleEn, contributor, temporal, contentsRightsType, linkUrl, thumbnailUrl
```
- For NDL records (`dignl-*` ids), swap `256,` for `1200,` in the IIIF thumbnail URL (see [ndl.go.jp](ndl.go.jp.md)). *(2026-10-08)*

## Known pitfalls
- No working rights filter (`rights=`, `r-rights=`, `r-contents=`, `database=` changed nothing). Fetch `size=100` and keep `contentsRightsType` in pdm, cc0, ccby; many top hits are in copyright or unlabelled. *(2026-10-08)*
- Image size depends on the source database: NDL scales, others gave small thumbnails only. *(2026-10-08)*
