# Template: purab-resume

- **Type:** CV
- **Engine:** pdflatex
- **Page limit:** 1 page (`main_example.tex` master reference is exempt, per standing framework rule)
- **Fonts:** Computer Modern (LaTeX default) - no `fontenc`/`lmodern`, no `fontspec`, no bundled font files, no system font install required. ATS glyph mapping is handled via `\input{glyphtounicode}` + `\pdfgentounicode=1` instead (see Known pitfalls).
- **Class/packages:** `article` (standard) + `latexsym`, `fullpage`, `titlesec`, `marvosym`, `color`, `verbatim`, `enumitem`, `hyperref`, `fancyhdr`, `babel`, `tabularx` (all standard TeX Live/MiKTeX packages, no custom `.cls`)

## Compile command

    cd cv && pdflatex -interaction=nonstopmode main_<company>.tex

One pass is sufficient for this skeleton.

## Style rules

- **Black and white only** - no color accents anywhere. Do not add `\color{}` calls to headings or names.
- **Header:** Name in `\Huge \scshape`, centered; contact line directly below in `\small`, pipe-separated (`|`): phone, email (mailto link), LinkedIn, GitHub. **No location in the header** (2026-07-13 preference) - omit it entirely, do not add it back on future CVs.
- **Denser than `jakes-resume`:** 10pt base font (vs. 11pt), tighter section spacing (`\titleformat{\section}` uses `-6pt`/`-7pt` vs. `jakes-resume`'s `-4pt`/`-5pt`), and more usable vertical space (`\addtolength{\textheight}{1.4in}` vs. `1.0in`, `\topmargin` `-.7in` vs. `-.5in`). Use this template over `jakes-resume` when content needs to be packed tighter to fit 1 page.
- **Section headings:** small-caps, left-aligned, with a horizontal rule (`\titlerule`) immediately under the heading - produced by the `\titleformat{\section}` override, not manual `\hrule`.
- **Entries:** `\resumeSubheading{Title}{Date}{Subtitle}{Location}` right-aligns the date/location against the title/subtitle using `tabular*` - never reorder these four arguments.
- **Bullets:** `\resumeItemListStart ... \resumeItem{...} ... \resumeItemListEnd` for role/project bullets; the outer `\resumeSubHeadingListStart/End` wraps each section's list of entries. Do not mix in a plain `itemize` - the custom commands carry the negative `\vspace` that keeps the template dense.
- **Section order:** Education, Experience, Projects, Technical Skills, Leadership - matches this framework's standing 2026-07-11 order. The Leadership section is included in the skeleton (unlike `jakes-resume`, which only notes it can be appended); drop the section entirely for roles where it doesn't add value, rather than leaving it empty.
- **No profile/summary section** - matches this framework's 2026-07-11 preference; go straight from the header into Education.
- **Dates:** month-level (`Sep 2022 -- Jun 2025`), right-aligned via the `tabular*` second column - same convention as `jakes-resume`.
- **Bolding:** one bolded metric/term per bullet max, same rule as the stock template's ATS guidance.

## Known pitfalls

- **`\input{glyphtounicode}` requires `glyphtounicode.tex` on the TeX search path.** Unlike `jakes-resume` (which omits this file and relies on `fontenc`+`lmodern` instead), this template pulls in the original public "Jake's Resume" approach directly. Confirmed present via `kpsewhich glyphtounicode.tex` on this machine's MiKTeX install (ships under `tex/generic/pdftex/`), and the test compile in this registration succeeded with clean, cleanly-extracting text and no `(cid:*)` markers. If a future machine's TeX distribution doesn't ship this file, switch to the `fontenc`+`lmodern` approach used in `jakes-resume` instead.
- **`OT1/cmr/bx/sc` font shape warning is cosmetic.** pdflatex substitutes a non-small-caps bold shape for the header name (`\Huge \scshape` combined with `\textbf`) because true bold small-caps isn't in the default Computer Modern set. The rendered output is correct (regular bold small-caps look, no visual break) - do not chase this warning.
- **Negative `\vspace` values are load-bearing for density**, not incidental - `\resumeItem`'s trailing `\vspace{-2pt}` and `\resumeSubheading`'s trailing `\vspace{-7pt}` are what make this template denser than `jakes-resume`. Don't strip them out when editing entries.
- **`\raggedbottom` + `\raggedright` are both set globally** - this is normal for this template (avoids awkward full-justification stretching in a narrow single-column layout), not a bug to "fix".
- **pdflatex, not lualatex/xelatex** - no `fontspec`/`fontawesome5` dependency, so the lualatex workaround this framework used for the old moderncv template is not needed here.
