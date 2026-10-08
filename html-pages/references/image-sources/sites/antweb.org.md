---
domain: antweb.org
aliases: [AntWeb, static.antweb.org]
updated: 2026-10-08
---

## Platform characteristics
- `www.antweb.org` (pages and images) and `api.antweb.org` are behind a Cloudflare challenge (403). The images are reachable by a detour: find them through GBIF, then fetch from `static.antweb.org`. Ants only: sharp stacked specimen photos, licence via GBIF reads CC BY-SA / GFDL. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
# AntWeb's GBIF dataset key: 13b70480-bd69-11dd-b15f-b8a03c50a862
curl -s -A "$UA" "https://api.gbif.org/v1/occurrence/search?datasetKey=13b70480-bd69-11dd-b15f-b8a03c50a862&scientificName=Camponotus%20pennsylvanicus&mediaType=StillImage"
# results[].media[]: identifier (www.antweb.org/images/...), license, creator, rightsHolder, references
# swap the host to static.antweb.org:
curl -sSL -A "$UA" -o ant.jpg "https://static.antweb.org/images/casent4031384/casent4031384_h_1_high.jpg"   # 1600x1200
```
- View letters in the file name: `_h_` head, `_d_` dorsal, `_p_` profile, `_l_` label. *(2026-10-08)*

## Known pitfalls
- The host swap may stop working if they tighten the CDN. *(2026-10-08)*
