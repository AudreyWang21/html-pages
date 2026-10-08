---
domain: nationaalarchief.nl
aliases: [Nationaal Archief, Anefo, hub3.nationaalarchief.nl, service.archief.nl]
updated: 2026-10-08
---

## Platform characteristics
- The human photo-collection site is a JS app; its backend search (`hub3`) is open JSON, records are RDF, images are IIIF on `service.archief.nl` (any width, up to 5000 px). No key, no bot wall. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
# 1. search: items[].summary.objectID (UUID), meta.spec (keep ones containing "foto"), summary.description (Dutch caption)
curl -s -A "$UA" "https://hub3.nationaalarchief.nl/api/search/v2?q=Mongolie+Anefo&rows=3"
# 2. metadata (turtle): caption, date, place, creator, policy URI
curl -sL -A "$UA" "https://hub3.nationaalarchief.nl/doc/beschrijving/<UUID>"
curl -sL -A "$UA" "https://hub3.nationaalarchief.nl/doc/foto/<UUID>"
curl -sL -A "$UA" "https://hub3.nationaalarchief.nl/doc/fotorecord/<UUID>"
# 3. image path is only in the detail page HTML, inside escaped JSON
curl -sL -A "$UA" "https://www.nationaalarchief.nl/onderzoeken/fotocollectie/<UUID>" -o p.html
grep -o 'IIIF=[^"\ ]*\.jp2' p.html      # strip the backslashes from \/ to get /xx/xx/.../<uuid>.jp2
# 4. download
curl -s -A "$UA" -o a.jpg "https://service.archief.nl/iipsrv?IIIF=<path>.jp2/full/1200,/0/default.jpg"
```
- Credit "Nationaal Archief / Fotocollectie Anefo" with the record link `http://hdl.handle.net/10648/<UUID>` (redirects to the record page). *(2026-10-08)*

## Known pitfalls
- Search wants Dutch or period spellings: `Ulaanbaatar` gave 0, `"Ulan Bator"` gave 3. *(2026-10-08)*
- Anefo's own photos are CC0, but items from other agencies are not necessarily (the test record, China Press, had rights holder "unknown"). Read rights per record; there was no plain CC0 field. *(2026-10-08)*
- Much of Anefo is mirrored on Wikimedia Commons (category "Anefo"). *(2026-10-08)*
