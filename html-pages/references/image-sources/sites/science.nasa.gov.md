---
domain: science.nasa.gov
aliases: [NASA Earth Observatory, earthobservatory.nasa.gov, NASA Visible Earth]
updated: 2026-10-08
---

## Platform characteristics
- Earth Observatory moved into NASA Science: `earthobservatory.nasa.gov/...` 301s to `science.nasa.gov/earth/earth-observatory/...`. The site is WordPress with an open REST API, no key, no bot wall. *(2026-10-08)*
- NASA Visible Earth is retired: every `visibleearth.nasa.gov` URL redirects here, and old `eoimages.gsfc.nasa.gov` file URLs 404. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -A "$UA" "https://science.nasa.gov/wp-json/wp/v2/search?search=Ulaanbaatar&per_page=5"   # keep hits whose url has /earth-observatory/
curl -s -A "$UA" "https://science.nasa.gov/wp-json/wp/v2/posts/<id>?_fields=id,date,title,link,featured_media,acf"
curl -s -A "$UA" "https://science.nasa.gov/wp-json/wp/v2/media/<featured_media>"                 # source_url, caption, alt_text
curl -sL -A "$UA" -o out.jpg "<source_url>?w=1400" && file out.jpg
```

## Known pitfalls
- `source_url` with no params is 720 px, and the media record's `sizes` all point to that same file; set `?w=` yourself (1400 verified). *(2026-10-08)*
- No licence field. NASA imagery is generally public domain (credit "NASA Earth Observatory"), but read the caption for third-party credits. *(2026-10-08)*
- The `image-article` endpoint returned `[]`; use `/search` or `/posts`. *(2026-10-08)*
