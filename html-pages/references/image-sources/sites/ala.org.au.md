---
domain: ala.org.au
aliases: [Atlas of Living Australia, ALA, biocache-ws.ala.org.au, images.ala.org.au]
updated: 2026-10-08
---

## Platform characteristics
- Occurrence search (biocache) plus an image service, no key, no bot wall. Most images are iNaturalist uploads from Australia: good for Australian fauna, flora, fungi and habitats. Castor had none; widespread species still show up (Picea glauca: 14,325 images, most NC). *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -sS -A "$UA" 'https://biocache-ws.ala.org.au/ws/occurrences/search?q=Amanita%20muscaria&fq=multimedia:Image&fq=license:%22CC-BY%204.0%20(Int)%22&pageSize=3&fl=uuid,images,recordedBy,license'
curl -sS -A "$UA" "https://images.ala.org.au/ws/image/<uuid>"                                # creator, licence URL, size, dateTaken
curl -sSL -A "$UA" -o x.jpg "https://images.ala.org.au/image/proxyImage?imageId=<uuid>"       # full original (1536x2048 in the test)
```
- `image/proxyImageThumbnailLarge?imageId=<uuid>` gives ~650 px. Other widths untested. *(2026-10-08)*
- Count licences first: add `&facets=license&pageSize=0&flimit=8`. Much of it is CC BY-NC. *(2026-10-08)*
