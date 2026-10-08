---
domain: gallica.bnf.fr
aliases: [Gallica, BnF]
updated: 2026-10-08
---

## Platform characteristics
- SRU search returns XML, no key. Strong on the French world: Asia, Africa, Indochina, Latin America, press photos (Meurisse, Rol). French search terms work best. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -A "$UA" "https://gallica.bnf.fr/SRU?operation=searchRetrieve&version=1.2&query=%28gallica%20all%20%22Mongolie%22%29%20and%20dc.type%20all%20%22image%22&maximumRecords=2" -o gal.xml
# dc:title, dc:creator, dc:date, dc:rights ("domaine public"), dc:identifier (ark:/12148/... record URL)
curl -s -A "$UA" -o x.jpg "https://gallica.bnf.fr/iiif/ark:/12148/<id>/f1/full/1200,/0/native.jpg" && file x.jpg
```
- `<ark URL>.highres` also returned the native high-res JPEG. *(2026-10-08)*

## Known pitfalls
- The commonly cited `<ark>/f1/full/1200,/0/native.jpg` (without `/iiif/`) returned HTTP 500 as a 2.6 KB HTML page. Use the `/iiif/ark:/...` form. *(2026-10-08)*
- Some records are reserved or in copyright; read `dc:rights`. The terms mention rate limits, so be gentle. *(2026-10-08)*
