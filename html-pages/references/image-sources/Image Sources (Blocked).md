---
updated: 2026-10-08
---

# Image sources: blocked and retired

Sources an agent could not use from the test setup (curl, no keys), kept so the next agent skips the detour. The working ones are in [Image Sources](Image%20Sources.md). Dated hints: a wall can lift, so re-test before ruling a source out for good, and move a row back when it works.

| Source | Good for | Blocked by | Human in a browser? | Key? | Licence data? | Workaround | Tested |
|---|---|---|---|---|---|---|---|
| Art Institute of Chicago | art | Cloudflare challenge (403) on the IIIF image host `www.artic.edu/iiif`; the API on `api.artic.edu` works | yes, the same image URL opens | no | yes, via the API | use the Met or the Commons copy of the same work | 2026-10-08 |
| Library of Congress | historical photos | Cloudflare challenge on all `www.loc.gov` search and item pages; images on `tile.loc.gov` fetch if the URL is known | yes | no | blocked | discover via [Flickr Commons](sites/flickr.com.md), or paste `tile.loc.gov` links by hand | 2026-10-08 |
| Trove (NLA) | Australian pictures | API needs a key needed (free, with a Trove account); website behind an Anubis wall | yes | yes | via the API only | many Trove pictures are mirrored on Commons and Flickr Commons | 2026-10-08 |
| Finna (Finland) | Finnish museums | Cloudflare challenge (403) on the API | may | no | n/a | Finnish museum content reaches agents through Europeana | 2026-10-08 |
| National Palace Museum, Taiwan (open data portal) | Chinese art | no API; image links redirect to the listing, HEAD hits a "555 SecurityPage" | yes, a human can download | no | CC BY 4.0 / Open Government Data, stated on the page | download by hand in a browser | 2026-10-08 |
| Qatar Digital Library | Arab world, Gulf history | Cloudflare challenge (403) | likely | n/a | n/a | download by hand in a browser | 2026-10-08 |
| Biblioteca Digital Hispánica (BNE) | Spanish colonial Americas | HTTP 403 page to curl | likely | n/a | n/a | download by hand in a browser | 2026-10-08 |
| e-rara.ch | old books about Africa | "Verifying your browser" challenge | not checked | n/a | n/a | the set is also described on opendata.swiss (not pursued) | 2026-10-08 |
| Biblioteca Digital del Patrimonio Iberoamericano | 15 Ibero-American countries | "Verifying your browser" challenge on search | not checked | n/a | n/a | download by hand in a browser | 2026-10-08 |
| NASA Visible Earth | Earth from above | retired: every URL redirects to Earth Observatory; old `eoimages.gsfc.nasa.gov` file links 404 | n/a | n/a | n/a | [NASA Earth Observatory](sites/science.nasa.gov.md) | 2026-10-08 |
| Macaulay Library (Cornell) | bird photos | Anubis wall on every page, API path and terms page; and the licence is not open (reuse needs permission) | may, but reuse still needs permission | eBird key for the API, not useful | terms only | Commons or iNaturalist; Cornell's own embed code for non-commercial use | 2026-10-08 |
| USFWS National Digital Library | wildlife and habitat photos | old `digitalmedia.fws.gov` is gone (301 to fws.gov); Akamai 403s custom User-Agents on fws.gov; the new image search is a client-rendered JS app | yes, a browser shows results | no | little | images fetch with curl's default UA if you have the URL; FWS Flickr account; much is mirrored on Commons | 2026-10-08 |
| NOAA Photo Library | marine and weather photos | `photolib.noaa.gov` redirects to a CloudFront 403 / "Human Verification" page | may | n/a | n/a | NOAA's Flickr account `flickr.com/photos/noaaphotolib/` (Flickr API needs a key); NOAA Fisheries species pages for marine animals | 2026-10-08 |
| Canadian Museum of Nature | Canadian species | JS challenge ("One moment, please...") | likely | n/a | CC BY-NC per a web search, not verified | GBIF / iNaturalist for Canadian species | 2026-10-08 |
| Natural Resources Canada tree site (`tidcf.nrcan.gc.ca`) | Canadian trees | dead: host no longer resolves | n/a | n/a | n/a | GBIF / iNaturalist | 2026-10-08 |
| CalPhotos | plants, animals, fungi | Cloudflare Turnstile on every search and image-enlarge URL | yes, a human click passes | no | per image page, mostly CC BY-NC | download by hand in a browser | 2026-10-08 |
| PlantIllustrations.org (and mirror botanicalillustrations.org) | botanical illustrations | Cloudflare Turnstile "I am not a robot" gate | likely | n/a | public domain per its about page | the contributing libraries directly, e.g. BHL | 2026-10-08 |
| Kew POWO (and IPNI) | plant names, illustrations, herbarium sheets | Cloudflare challenge (403), including `/api/2` | yes | n/a | n/a | GBIF for plant occurrence photos | 2026-10-08 |
| Protist Information Server (Hosei) | protist micrographs | unreachable: TCP 443 and 80 time out from the test setup | maybe, from another network | n/a | images copyrighted by their authors, educational use | Zenodo / Plazi, Cell Image Library, Commons | 2026-10-08 |
| micro*scope (MBL) | protist micrographs | dead: `microscope.mbl.edu` and `starcentral.mbl.edu` do not resolve | n/a | n/a | n/a | as above | 2026-10-08 |
| Encyclopedia of Life image host (`content.eol.org`, `eol.org/pages`) | species images | Cloudflare 403 challenge; the `eol.org/api` JSON works | may | no | via the API | take the upstream `mediaURL` from the API (works case by case, use `-L`) | 2026-10-08 |
| AntWeb site and API (`www.antweb.org`, `api.antweb.org`) | ant specimen photos | Cloudflare challenge (403) | may | no | via GBIF | [GBIF + `static.antweb.org`](sites/antweb.org.md) | 2026-10-08 |
| Dryad (`datadryad.org/downloads/file_stream/<id>`) | data-paper figures and photos | Anubis proof-of-work wall: curl and WebFetch get the challenge page | yes, a browser click works | n/a | n/a | download by hand in a browser | 2026-09 |

Partly blocked sources stay in the main index with their route around the block: AntWeb (via GBIF and `static.antweb.org`), Encyclopedia of Life (as a finder), Biodiversity Heritage Library (website and API blocked, page images open), PMC (websites blocked, Europe PMC and the open-data bucket open).
