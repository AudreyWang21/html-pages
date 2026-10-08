---
domain: bugwood.org
aliases: [Bugwood Images, forestryimages.org, invasive.org, bugwoodcloud.org]
updated: 2026-10-08
---

## Platform characteristics
- Open JSON API at `api.bugwood.org/rest/api`, no key, no Cloudflare. Trees, forest pests, diseases, fungi, weeds, invasives. The developer docs are geo-blocked from the test setup (CloudFront), so the parameters below were found by trial. *(2026-10-08)*
- No licence field: the licence is site-wide, non-commercial use with citation. Credit photographer and organisation. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -sL -A "$UA" "https://api.bugwood.org/rest/api/subject?term=Picea%20glauca"     # items[].id (white spruce = 2737)
curl -sL -A "$UA" "https://api.bugwood.org/rest/api/image?sub_id=2737&rows=5"         # rows[]: imgnum, photographer, organization
curl -s -A "$UA" -o spruce.jpg "https://bugwoodcloud.org/images/1536x1024/0008142.jpg"
```
- One image: `image?imgnum=0008142`. Record page: `https://www.forestryimages.org/browse/image/<imgnum>`. *(2026-10-08)*

## Known pitfalls
- Wrong parameter names (`q`, `search`) are silently ignored and return the full 159k list; check `total`. Always pass `sub_id` to `image`. *(2026-10-08)*
- Only listed sizes exist: `768x512` and `1536x1024` worked; `1024x683` returned a 111-byte XML error (403). Portrait sizes untested. *(2026-10-08)*
- Old `browse/search.cfm` URLs 404 (the front end is now a Next.js app). *(2026-10-08)*
