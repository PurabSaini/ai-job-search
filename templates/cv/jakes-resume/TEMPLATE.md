# Template: jakes-resume

- **Type:** CV
- **Engine:** pdflatex
- **Page limit:** 1 page (`main_example.tex` master reference is exempt, per standing framework rule)
- **Fonts:** Latin Modern via `\usepackage[T1]{fontenc}` + `\usepackage{lmodern}` (standard TeX Live/MiKTeX packages, not raw Computer Modern - needed for correct ToUnicode glyph mapping, see Known pitfalls). No `fontspec`, no bundled font files, no system font install required.
- **Class/packages:** `article` (standard) + `fontenc`, `lmodern`, `titlesec`, `fullpage`, `marvosym`, `enumitem`, `hyperref`, `fancyhdr`, `tabularx`, `color` (all standard TeX Live/MiKTeX packages, no custom `.cls`)

## Compile command

    cd cv && pdflatex -interaction=nonstopmode main_<company>.tex

Run twice if hyperref/toc-style references ever get added (not needed for the base template - one pass is sufficient for this skeleton).

## Style rules

- **Black and white only** - no color accents anywhere (unlike the previous moderncv/banking template's blue scheme). Do not add `\color{}` calls to headings or names.
- **Header:** Name in `\Huge \scshape`, centered; contact line directly below in `\small`, pipe-separated (`|`), with phone, email (mailto link), LinkedIn, GitHub.
- **Section headings:** small-caps, left-aligned, with a horizontal rule (`\titlerule`) immediately under the heading - produced by the `\titleformat{\section}` override, not manual `\hrule`.
- **Entries:** `\resumeSubheading{Title}{Date}{Subtitle}{Location}` right-aligns the date/location against the title/subtitle using `tabular*` - never reorder these four arguments.
- **Bullets:** `\resumeItemListStart ... \resumeItem{...} ... \resumeItemListEnd` for role/project bullets; the outer `\resumeSubHeadingListStart/End` wraps each section's list of entries. Do not mix in a plain `itemize` - the custom commands carry the negative `\vspace` that keeps the template dense.
- **Section order:** Education, Experience, Projects, Technical Skills (matches this framework's standing 2026-07-11 order; Leadership can be appended the same way as Experience/Projects if space allows).
- **No profile/summary section** - matches this framework's 2026-07-11 preference; go straight from the header into Education.
- **Dates:** month-level (`Sep 2022 -- Jun 2025`), right-aligned via the `tabular*` second column - same convention as the previous moderncv template.
- **Bolding:** one bolded metric/term per bullet max, same rule as the stock template's ATS guidance.

## Known pitfalls

- **`glyphtounicode.tex` intentionally omitted.** The original public "Jake's Resume" source usually has `\input{glyphtounicode}` plus `\pdfgentounicode=1` for ATS ligature-mapping (fixes `ffi`/`fl` extracting as `(cid:*)`). The companion `glyphtounicode.tex` file is not part of standard MiKTeX/TeX Live and isn't bundled here. `\pdfgentounicode=1` alone (kept in the preamble), combined with `\usepackage[T1]{fontenc}` + `\usepackage{lmodern}` (Latin Modern Type1 fonts with standard Adobe glyph names, used instead of raw Computer Modern), gives a clean ToUnicode-mapped PDF - confirmed by direct testing.
- **Always pass `-enc UTF-8` to `pdftotext`** when running the framework's ATS text-layer check on this template: `pdftotext -enc UTF-8 -layout main_<company>.pdf main_<company>.txt`. Without `-enc UTF-8`, this poppler build's default output encoding renders the bullet (`•`) and en-dash (`–`) characters as `�` even though the PDF's actual ToUnicode CMap is correct - a false positive for "garbled extraction" that led to an incorrect first diagnosis during registration. Confirm with `-enc UTF-8` before concluding a font/encoding fix is needed.
- **Negative `\vspace` values are load-bearing for density**, not incidental - `\resumeItem`'s trailing `\vspace{-2pt}` and `\resumeSubheading`'s trailing `\vspace{-7pt}` are what make this template fit more content per page than moderncv did. Don't strip them out when editing entries.
- **`\raggedbottom` + `\raggedright` are both set globally** - this is normal for this template (avoids awkward full-justification stretching in a narrow single-column layout), not a bug to "fix".
- **pdflatex, not lualatex/xelatex** - unlike the previous moderncv template, this one has no `fontawesome5` dependency, so the lualatex workaround this framework used previously is not needed here. Do not switch engines without reason.
