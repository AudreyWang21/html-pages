---
domain: flickr.com
aliases: [Flickr Commons]
updated: 2026-10-08
---

## Platform characteristics
- The REST API needs a key, but the classic public feeds do not. A per-institution feed filters to that Commons account's rights-cleared uploads; it is also the agent route to Library of Congress photos (loc.gov search is Cloudflare-walled). *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
# Library of Congress NSID 8623220@N02. https://www.flickr.com/commons/institutions/ lists each account's /photos/<alias>/ slug;
# the feed id needs the NSID (like 204243057@N08), which that page embeds in its source
curl -s -A "$UA" "https://api.flickr.com/services/feeds/photos_public.gne?id=8623220@N02&tags=mongolia&format=json&nojsoncallback=1"
# items[]: title, link (record page), date_taken, author, media.m (240 px); swap _m for _b (1024 px) or _c (800 px)
curl -s -A "$UA" -o a.jpg "https://live.staticflickr.com/3205/3005523647_3ace2ffc71_b.jpg"
# licence: grep the photo page for "No known copyright restrictions" / "license":7
curl -s -A "$UA" "https://www.flickr.com/photos/library_of_congress/3005523647/" | grep -o '"license":[0-9]*'
```

## Known pitfalls
- Tag search only, and only the most recent ~20 items per tag; no free-text search without a key. *(2026-10-08)*
- Without `id=` the feed searches all of Flickr, not Commons, with no licence field. *(2026-10-08)*
- `_h`, `_k`, `_o` returned HTTP 410; ~1024 px is the practical maximum. *(2026-10-08)*
- Feed JSON can carry stray escapes: `json.loads(..., strict=False)`. *(2026-10-08)*
