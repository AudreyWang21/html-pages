---
domain: mushroomobserver.org
aliases: [Mushroom Observer]
updated: 2026-10-08
---

## Platform characteristics
- JSON API `api2`, no key for reads, no bot wall. Fungi only: the name must exist in its database (Paramecium: "does not exist"). Volunteer-funded, so be gentle. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -sL -A "$UA" "https://mushroomobserver.org/api2/images?detail=high&format=json&name=Amanita+muscaria" -o mo.json
# results[]: license (string), copyright_holder, owner.legal_name, date, observation_ids, files[] (thumb/320/640/960/1280/orig)
curl -s -A "$UA" -o amanita.jpg "https://mushroomobserver.org/images/1280/7814.jpg"
```
- Record page: `https://mushroomobserver.org/<observation_id>`. *(2026-10-08)*

## Known pitfalls
- `per_page` is rejected; page with `page=N` (100 per page). *(2026-10-08)*
- The `license=` filter wants a numeric id (`license=CC` errors); filter the `license` string yourself. Most are "Creative Commons Wikipedia Compatible v3.0" (CC BY-SA-like); some are NC. *(2026-10-08)*
- A bad parameter returns a very long error trace. *(2026-10-08)*
