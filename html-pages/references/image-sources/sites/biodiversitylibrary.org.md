---
domain: biodiversitylibrary.org
aliases: [Biodiversity Heritage Library, BHL, bhl-open-data]
updated: 2026-10-08
---

## Platform characteristics
- Website, name search and the API-key sign-up page are behind a Cloudflare challenge (403 to curl). `api3` returns 401 without a key; the key is free but must be requested with an email. *(2026-10-08)*
- Page images are reachable keyless through the BHL open-data S3 bucket and the Internet Archive. Finding the right plate without the API is the hard part. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
# find a book (Internet Archive search over the BHL collection)
curl -s -A "$UA" "https://archive.org/advancedsearch.php?q=collection%3Abiodiversity+AND+title%3A%28fishes+of+north+america%29&fl%5B%5D=identifier&fl%5B%5D=title&fl%5B%5D=year&rows=3&output=json"
# page images, keyed by IA identifier + 4-digit page number
B=https://bhl-open-data.s3.us-east-2.amazonaws.com
curl -s -A "$UA" -o p.webp "$B/web/americanfishespo00good/americanfishespo00good_0040_large.webp"   # also _full/_medium/_small/_thumb
curl -s -A "$UA" -o p.jpg  "$B/jpg/americanfishespo00good/americanfishespo00good_0040.jpg"          # original JPEG
curl -sL -A "$UA" -o p2.jpg "https://archive.org/download/americanfishespo00good/page/n40_w1200.jpg"
# a known BHL PageID, keyless (302 to the bucket)
curl -sL -A "$UA" -o pg.webp "https://www.biodiversitylibrary.org/pageimage/3680350"
```
- Rights per item: `$B/data/item.txt.gz` (18 MB; range requests work) has CopyrightStatus, RightsStatement, LicenseType. *(2026-10-08)*

## Known pitfalls
- `pageimage/` needs `-L`; without it you get a 218-byte "Object moved" stub. The IA `download/` URL needs `-L` too. *(2026-10-08)*
- IA page numbers (`nNN`, zero-based) differ from the bucket's 4-digit numbers by an offset; look before trusting. *(2026-10-08)*
- `web/` files are WebP: browsers show them, but take the `jpg/` copy if a toolchain needs JPEG. *(2026-10-08)*
- Most items are public domain, but later 20th-century ones may not be; check CopyrightStatus. *(2026-10-08)*
