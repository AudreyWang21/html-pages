---
domain: si.edu
aliases: [Smithsonian Open Access, api.si.edu, ids.si.edu]
updated: 2026-10-08
---

## Platform characteristics
- Search at `api.si.edu/openaccess/api/v1.0/search` (via api.data.gov): no key gives 403; `api_key=DEMO_KEY` works at once with `X-Ratelimit-Limit: 10` (≈10/hour, by the tester's reading; api.data.gov also caps DEMO_KEY per day); one test ran out after about 8 calls. A personal key needs its own sign-up (asks for an email); not done. *(2026-10-08)*
- Image delivery on `ids.si.edu` needs no key and does not count against the limit. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -G -A "$UA" "https://api.si.edu/openaccess/api/v1.0/search" --data-urlencode "q=Mali mask AND online_visual_material:true" --data "api_key=DEMO_KEY&rows=5" -o si.json
# rows[].content.descriptiveNonRepeating: online_media.media[].{content,idsId,usage.access}, metadata_usage.access, record_link
curl -sL -A "$UA" -o pic.jpg "<media[0].content>" && file pic.jpg   # e.g. https://ids.si.edu/ids/deliveryService/id/ark:/65665/<media-id>
```
- To filter for CC0 in the query, add `AND media_usage:CC0` (worked with `online_media_type:"Images"`). *(2026-10-08)*
- Restrict by museum with `unit_code:"NMAH"` (worked in one test; a guessed code in another returned nothing, so verify codes). *(2026-10-08)*

## Known pitfalls
- Save the search JSON and reuse it; every search call spends the hourly cap. *(2026-10-08)*
- Size params (`max`, `max_w`) were ignored: images come at one default size (~1500-2000 px); `/90` gives a 90 px thumb. Shrink afterwards (PIL, if installed). *(2026-10-08)*
- `online_media_type:"Images"` matched records with no media in one test; `online_visual_material:true` is safer. *(2026-10-08)*
- `deliveryService?id=<idsId>&max_w=1400` also worked (and still returned 1796 px). *(2026-10-08)*
- Print with `PYTHONIOENCODING=utf-8`: an accented title crashed a script on this GBK console. *(2026-10-08)*
- Broad searches surface herbarium sheets first. Fields vary by museum (`record_link` can be missing), so parse with `.get`. *(2026-10-08)*
- Only CC0 items are free to use (`usage.access` / `metadata_usage.access`). *(2026-10-08)*
