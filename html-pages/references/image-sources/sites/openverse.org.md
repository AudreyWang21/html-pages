---
domain: openverse.org
aliases: [Openverse, api.openverse.org]
updated: 2026-10-08
---

## Platform characteristics
- One search across Flickr, Wikimedia, iNaturalist, NASA, Rijksmuseum and others, no key. Anonymous quota from the headers: 20 requests/min and 200/day per IP, so a page needing many searches can spend it. Best as a finder; quality is patchy (many Flickr snapshots, titles sometimes unrelated). *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -A "$UA" "https://api.openverse.org/v1/images/?q=Ulaanbaatar&source=wikimedia,inaturalist,nasa&license_type=commercial&page_size=5" -o ov.json
# results[]: url (original on the source site), license, creator, foreign_landing_url, attribution, width, height
curl -sL -A "$UA" -o orig.jpg "<results[i].url>"
```
- Filters: `license_type=commercial` (drops NC/ND), `source=`, `category=photograph`. Smithsonian is not a valid source. *(2026-10-08)*

## Known pitfalls
- `/v1/images/<id>/thumb/` is ~600 px; `?w=1200` was not honoured. Use `url`. *(2026-10-08)*
- `by-nd` still appeared with `license_type=commercial`; read `license` per hit. No clean date field. *(2026-10-08)*
