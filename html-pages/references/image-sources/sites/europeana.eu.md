---
domain: europeana.eu
aliases: [Europeana, api.europeana.eu]
updated: 2026-10-08
---

## Platform characteristics
- Pan-European aggregator of museums, archives and libraries, including ethnographic collections with Asian, African and American material. The public demo key `wskey=api2demo` works; it is shared and could be throttled or retired. A personal key is a free sign-up form. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -A "$UA" "https://api.europeana.eu/record/v2/search.json?wskey=api2demo&query=Mongolia+yurt&qf=TYPE:IMAGE&media=true&reusability=open&rows=5&profile=rich" -o eu.json
# items[]: edmIsShownBy[0] (image at the provider), rights[0] (licence URI), guid (record page), dcCreator, year, dataProvider
curl -sL -A "$UA" -o x.jpg "<edmIsShownBy>" && file x.jpg
```

## Known pitfalls
- `reusability=open` is essential; still read `rights` per item and reject "unknown". *(2026-10-08)*
- Image size is whatever the provider hosts, and some `edmIsShownBy` links are viewer pages, not images. Europeana's own `edmPreview` stays at 400 px (`size=w800` returned the same file). *(2026-10-08)*
- Searches are noisy ("Potosi" was mostly a ship). Use `python -I -X utf8` to print titles on this console. *(2026-10-08)*
