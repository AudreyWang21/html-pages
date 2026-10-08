---
domain: rijksmuseum.nl
aliases: [Rijksmuseum, data.rijksmuseum.nl, id.rijksmuseum.nl]
updated: 2026-10-08
---

## Platform characteristics
- The new Linked Art endpoints need no key (the old `rijksmuseum.nl/api` did). Images are IIIF on `iiif.micr.io`, any width. Records are CC0, images Public Domain Mark. Art, prints and objects only. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
# 1. search -> object IDs only
curl -s -A "$UA" "https://data.rijksmuseum.nl/search/collection?title=Potosi&imageAvailable=true"
# 2. object: title (identified_by Name), maker (produced_by.part[].carried_out_by[].notation), date (produced_by.timespan),
#    record page (subject_of[].digitally_carried_by[].access_point[].id), VisualItem id (shows[0].id)
curl -sL -A "$UA" -H "Accept: application/ld+json" https://id.rijksmuseum.nl/200186006 -o obj.json
# 3. VisualItem -> digitally_shown_by[0].id (DigitalObject) -> access_point[0].id = IIIF URL
curl -sL -A "$UA" -H "Accept: application/ld+json" https://id.rijksmuseum.nl/202186006
curl -sL -A "$UA" -H "Accept: application/ld+json" https://id.rijksmuseum.nl/5001011141041087412211176
# 4. image at any width (or full/max)
curl -s -A "$UA" -o potosi.jpg "https://iiif.micr.io/ggcfE/full/1600,/0/default.jpg"
```
- Other working search params: `creator=`, `type=painting`, `description=`. *(2026-10-08)*

## Known pitfalls
- Titles are mostly Dutch: `title=yurt` gave 0, `title=tent` 199; try Dutch words and `description=`. *(2026-10-08)*
- Four metadata requests per image; space them out. *(2026-10-08)*
