---
domain: inaturalist.org
aliases: [iNaturalist, api.inaturalist.org]
updated: 2026-10-08
---

## Platform characteristics
- REST API `api.inaturalist.org/v1`, no key for reads, no bot wall; photos on public S3. Docs ask for under ~60 requests/min. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -A "$UA" "https://api.inaturalist.org/v1/observations?taxon_name=Ursus+maritimus&photo_license=cc0,cc-by,cc-by-sa&quality_grade=research&per_page=2&order_by=votes&photos=true" -o r.json
# photos[].url ends /square.jpeg; photos[].license_code, .attribution (ready credit string); observation uri, observed_on
curl -s -A "$UA" -o bear.jpg "https://inaturalist-open-data.s3.amazonaws.com/photos/9581603/large.jpeg"
```
- Sizes by swapping the last segment: `medium` 500 px, `large` 1024 px, `original` (2048 px in the test); also `small`, `square`. *(2026-10-08)*

## Known pitfalls
- Without `photo_license` the results include all-rights-reserved and NC photos. *(2026-10-08)*
- The extension varies (`.jpeg` or `.jpg`); take it from the API's `url`. *(2026-10-08)*
- Results are heavy (2 results = 1.2 MB; `fields=` did not trim): keep `per_page` small. Read JSON with `encoding='utf-8'` (GBK default fails). *(2026-10-08)*
