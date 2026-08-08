# Embedded typeface

[JetBrains Mono](https://github.com/JetBrains/JetBrainsMono) v2.304, subset to
only the characters each graphic actually draws, and inlined into the SVGs as
base64 `@font-face`.

Why inline it at all:

* **Metrics.** The portrait's character grid assumes an advance width of exactly
  0.600 em. JetBrains Mono is 600/1000 units, so the geometry is unchanged — but
  a viewer whose default monospace is narrower (Consolas is ≈0.55) would
  otherwise see the portrait about 7% too narrow. Inlining pins it.
* **An external font URL cannot work here.** These SVGs are loaded through
  `<img>`, and a browser refuses to fetch subresources for an image document.
  A base64 data URI is the only mechanism, and it keeps the page free of
  third-party requests.

| file | weight | covers |
|---|---|---|
| `jbmono-ramp.woff2` | 400 | the 13 ramp characters in `ascii.svg` |
| `jbmono-head.woff2` | 600 | the letters used by the section headings |
| `jbmono-400.woff2` | 400 | basic latin, for the stat graphics |
| `jbmono-600.woff2` | 600 | basic latin, for the stat graphics |

Licensed under the SIL Open Font License 1.1 — see `OFL.txt`. Subsetting and
redistribution in this form are permitted; the reserved font name is unchanged.
