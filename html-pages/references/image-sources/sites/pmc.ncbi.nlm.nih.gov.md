---
domain: pmc.ncbi.nlm.nih.gov
aliases: [PMC, PubMed Central, Europe PMC, pmc-oa-opendata]
updated: 2026-10-08
---

## Platform characteristics
- Agents are blocked from the websites: PMC article pages give a reCAPTCHA check, `europepmc.org/articles/.../bin/...` a Cloudflare 403, and NCBI `oa.fcgi` returned 404. The `cdn.ncbi.nlm.nih.gov/pmc/blobs/...` figure URLs need a hash from the PMC page, so they only work when you already have them from a browser. *(2026-10-08)*
- The agent route, no key: Europe PMC REST (EBI) for papers and licence, then the PMC open-data S3 bucket for figure files. *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
# 1. papers + licence (pmcid, title, license, pubYear, authors)
curl -s -A "$UA" "https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=%22mongolian%20gazelle%22%20AND%20OPEN_ACCESS%3Ay%20AND%20LICENSE%3A%22cc%20by%22&format=json&resultType=core&pageSize=5"
# 2. captions + figure file names (<fig> ... xlink:href), <license>
curl -s -A "$UA" "https://www.ebi.ac.uk/europepmc/webservices/rest/PMC10469424/fullTextXML"
# 3. per-paper metadata (license_code, citation, DOI); list files with ?list-type=2&prefix=<PMCID>
curl -s -A "$UA" "https://pmc-oa-opendata.s3.amazonaws.com/PMC10469424.1/PMC10469424.1.json"
# 4. figure
curl -s -A "$UA" -o fig1.jpg "https://pmc-oa-opendata.s3.amazonaws.com/PMC10469424.1/12864_2023_9574_Fig1_HTML.jpg" && file fig1.jpg
```

## Known pitfalls
- Figures are whatever the publisher deposited: ~700 px wide in both samples. The paper's PDF is in the same folder if a page crop is worth it. *(2026-10-08)*
- Content-Type is `binary/octet-stream`; check with `file`. *(2026-10-08)*
- The bucket holds the open-access subset only. Licence is per paper, and a figure can carry its own third-party licence (read the caption); NC/ND papers suit a private page only. *(2026-10-08)*
- Europe PMC's `supplementaryFiles` is a slow ZIP of supplements, not figures. *(2026-10-08)*
