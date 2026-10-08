---
domain: ndl.go.jp
aliases: [NDL Digital Collections, National Diet Library, dl.ndl.go.jp, ndlsearch.ndl.go.jp]
updated: 2026-10-08
---

## Platform characteristics
- IIIF images and manifests, no key. Mostly books, periodicals and documents: find pictures by searching for prints and picture books. Rights labels come through [jpsearch.go.jp](jpsearch.go.jp.md). *(2026-10-08)*

## Valid URL patterns
```bash
UA="<Project>/1.0 (personal non-commercial study page)"
curl -s -G -A "$UA" "https://ndlsearch.ndl.go.jp/api/opensearch" --data-urlencode "any=浮世絵" --data "cnt=5"   # RSS/XML search
curl -s -A "$UA" "https://dl.ndl.go.jp/api/iiif/<pid>/manifest.json"                                         # title, attribution
curl -s -A "$UA" -o x.jpg "https://www.dl.ndl.go.jp/api/iiif/<pid>/R0000001/full/1200,/0/default.jpg"         # pages R0000001, R0000002...
```

## Known pitfalls
- Not every item is open; check the rights label. *(2026-10-08)*
