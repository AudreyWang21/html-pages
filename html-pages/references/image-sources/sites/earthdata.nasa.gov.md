---
domain: earthdata.nasa.gov
aliases: [NASA Worldview, GIBS, wvs.earthdata.nasa.gov]
updated: 2026-10-08
---

## Platform characteristics
- Worldview snapshot API: one keyless URL returns a satellite image of any bounding box and date. MODIS true colour, ~250 m resolution. Credit NASA Worldview / EOSDIS GIBS. *(2026-10-08)*

## Valid URL patterns
```bash
curl -s -A "<Project>/1.0 (personal non-commercial study page)" -o gibs.jpg "https://wvs.earthdata.nasa.gov/api/v1/snapshot?REQUEST=GetSnapshot&LAYERS=MODIS_Terra_CorrectedReflectance_TrueColor&CRS=EPSG:4326&TIME=2024-07-15&BBOX=46,105,49,110&FORMAT=image/jpeg&WIDTH=1200&HEIGHT=1200"
```
- `BBOX` is south,west,north,east in degrees. Only this layer was tested. *(2026-10-08)*

## Known pitfalls
- Daily raw imagery, so clouds appear: pick a clear date. *(2026-10-08)*
