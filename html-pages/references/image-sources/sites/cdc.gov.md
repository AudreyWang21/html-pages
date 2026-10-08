---
domain: cdc.gov
aliases: [CDC PHIL, Public Health Image Library, wwwn.cdc.gov/phil]
updated: 2026-10-08
---

## Platform characteristics
- PHIL lives at `https://wwwn.cdc.gov/phil/` (phil.cdc.gov redirects there). Microbes, parasites, pathogenic fungi, disease. No API (`tools.cdc.gov/api/v2/resources/media` is for campaign graphics, not PHIL), no bot wall. *(2026-10-08)*
- Mostly public domain with credit to CDC and the photographer; some items are used by permission, so read each record's copyright text. *(2026-10-08)*

## Valid URL patterns
- Record: `https://wwwn.cdc.gov/phil/Details.aspx?pid=<id>` (plain GET): caption, date, provider, photo credit, copyright text. *(2026-10-08)*
- Low-res image, plain GET: `https://wwwn.cdc.gov/phil/PHIL_Images/<pid>/<pid>_lores.jpg` (700 px). *(2026-10-08)*
- Search is an ASP.NET postback (driven with Python stdlib in the test) (a GET with the term returns the empty form). With a cookie jar: GET `QuickSearch.aspx`, copy the hidden `__VIEWSTATE`, `__VIEWSTATEGENERATOR`, `__EVENTVALIDATION`, and POST them back with `ctl00$contentArea2$ucQuickSearch$txtQuickKeywords=<term>`, `ctl00$contentArea2$ucQuickSearch$bntSearch=Search`, `ctl00$contentArea2$ucQuickSearch$chkTypes$chkTypes_0=Photo`. Then regex `Details\.aspx\?pid=(\d+)`. *(2026-10-08)*
- Hi-res: the same viewstate POST on the detail page with `__EVENTTARGET=ctl00$contentArea2$ucDetails$hlHighResDownload` (returned a 3045 px PNG, 16 MB). *(2026-10-08)*

## Known pitfalls
- The hi-res file came labelled `image/tiff` but was a PNG: trust magic bytes. Guessed `<pid>.jpg` and `_hires.jpg` 404. *(2026-10-08)*
- No Paramecium or Daphnia; this is a pathogen library. *(2026-10-08)*
