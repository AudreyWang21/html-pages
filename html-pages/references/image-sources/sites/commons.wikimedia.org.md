---
domain: commons.wikimedia.org
aliases: [Wikimedia Commons]
updated: 2026-10-08
---

## Platform characteristics
- MediaWiki API, no key. Search, licence and a sized image URL come back in one call. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"   # name the project; never an email
curl -s -A "$UA" "https://commons.wikimedia.org/w/api.php?action=query&generator=search&gsrsearch=Ulaanbaatar&gsrnamespace=6&gsrlimit=3&prop=imageinfo&iiprop=url|extmetadata|size&iiurlwidth=1280&format=json" -o s.json
# pages -> imageinfo[0] -> thumburl, descriptionurl, extmetadata.{Artist,LicenseShortName,DateTimeOriginal}.value
curl -s -A "$UA" -o a.jpg "<thumburl>" && file a.jpg
```
- For one known file: `titles=File:<name>` in place of the `generator=search` parameters. *(2026-10-08)*

## Known pitfalls
- Only listed thumbnail widths are served: 1280 worked, 1000 gave HTTP 400 with a 2 KB HTML page. Use `thumburl` verbatim and check with `file`. *(2026-10-08)* 500 px also works; 320, 800 and 1024 gave 400, and full-resolution originals often gave 429. *(2026-09)*
- A generic User-Agent (`python-requests`, bare curl) gets 429, which arrives as a ~2 KB HTML file that looks like a successful image download: check sizes. *(2026-09)* A project UA got none. *(2026-10-08)*
- Parallel agents share one IP quota: space requests 1–4 s apart, with backoff, and fetch only what the page needs, once. With ten agents fetching at once, Commons stayed rate-limited for most of one agent's run. *(2026-10-08)*
- Download with curl: Python `urllib` has failed SSL verification on café and eduroam Wi-Fi where curl succeeded. *(2026-09)*
- Reject AI-generated uploads: check the author field (one Ancoracysta file listed "google gemini"). *(2026-09)*
- The UA policy (`foundation.wikimedia.org/wiki/Policy:User-Agent_policy`) asks for contact info as "an email address, a website, or a wiki user", so a website meets it. A plain project name (`X/1.0 (personal non-commercial study page)`) works in practice. Never put an email address in it. *(2026-10-07)*
- `Artist` is an HTML snippet (strip tags); `DateTimeOriginal` can be empty. *(2026-10-08)*
- Printing API text in Python on this GBK console raises `UnicodeEncodeError`; set `PYTHONIOENCODING=utf-8`. *(2026-10-08)*
