# CV Templates and Tailoring Guide

<!-- BEGIN ACTIVE-TEMPLATE (managed by /add-template - do not edit by hand) -->
> **Active template override: `purab-resume`**
>
> A custom template is active. Where this block conflicts with the stock guidance below, this block wins. Structural advice below (tailoring, page-budget, cutting rules) still applies.
>
> - **Template skeleton:** `templates/cv/purab-resume/template.tex` — use this as the structural reference instead of the stock moderncv template
> - **Manifest:** `templates/cv/purab-resume/TEMPLATE.md` — read this for style rules and known pitfalls before drafting
> - **Compile with:** `pdflatex` (not `lualatex` — this template has no fontawesome5/fontspec dependency)
> - **Fonts:** Computer Modern, LaTeX default — no bundled fonts, no system font install needed. Uses `\input{glyphtounicode}` for ATS glyph mapping (see manifest Known pitfalls)
> - **Page limit:** exactly 1 page (`main_example.tex` remains exempt as the master reference)
> - **Output file:** unchanged (`cv/main_<company>.tex`) — no class/font files to copy, the template only needs standard TeX Live/MiKTeX packages
<!-- END ACTIVE-TEMPLATE -->

## Template: LaTeX moderncv (Banking Style)

All CVs use the moderncv LaTeX package with the "banking" style and "blue" color scheme.

**Output file:** `cv/main_<company>.tex`
**Compile with:** **lualatex** on MiKTeX/TeX Live. pdflatex often fails on modern MiKTeX installs with `fontawesome5` font-expansion errors; lualatex handles the same sources cleanly.
**Master reference:** `cv/main_example.tex` (comprehensive CV with all competencies, experience, and achievements - use as source when building targeted CVs). This file is exempt from the 1-page hard limit below - it exists to hold everything so tailored CVs can cut from it, and is never submitted directly. Only `main_<company>.tex` outputs must be exactly 1 page.

### Compile command

```bash
cd cv && lualatex -interaction=nonstopmode main_<company>.tex
```

Expected output: `Output written on main_<company>.pdf (1 page, ...)`. Any page count other than 1 is a failure that must be fixed before presenting to the user.

## Document Structure

```latex
\documentclass[11pt,a4paper,sans]{moderncv}
\moderncvstyle{banking}
\moderncvcolor{blue}

% Force both first and last name AND section headings to render in moderncv
% blue (color1). Default banking on lualatex+MiKTeX leaves these black, which
% looks inconsistent with the rest of the blue accent scheme.
\renewcommand*{\firstnamestyle}[1]{{\fontsize{24}{26}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\lastnamestyle}[1]{{\fontsize{24}{26}\bfseries\upshape\color{color1}#1}}
\renewcommand*{\sectionstyle}[1]{{\sectionfont\color{color1}#1}}

\usepackage[utf8]{inputenc}
\usepackage{needspace}
\usepackage{hyperref}
\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    filecolor=magenta,
    urlcolor=blue,
    pdftitle={[YOUR_NAME] - CV},
    pdfpagemode=FullScreen,
}
\usepackage[scale=0.91]{geometry}
\usepackage{import}
\usepackage{enumitem}
\setlist[itemize,1]{itemsep=2pt, topsep=1pt, partopsep=0pt, parsep=0pt}
\setlist[itemize,2]{itemsep=1pt, topsep=1pt, partopsep=0pt, parsep=0pt}
\linespread{0.95}

% Personal data
\name{[FIRST_NAME]}{[LAST_NAME]}
\address{[YOUR_ADDRESS]}{}{}
\phone[mobile]{[YOUR_PHONE]}
\email{[YOUR_EMAIL]}
\extrainfo{\href{[YOUR_LINKEDIN_URL]}{LinkedIn}, \href{[YOUR_GITHUB_URL]}{GitHub}}

\begin{document}
\makecvtitle

% No profile statement / summary section - straight from \makecvtitle into
% content (2026-07-11 preference). That space goes to Projects and Experience.
% Standing section order (2026-07-11 preference):
% 1. Education section (fold Honors/Dean's List into the relevant degree entry, not a separate section)
% 2. Professional Experience section
% 3. Projects section - load-bearing for early-career candidates with thin
%    professional history, not filler. See "Projects" under Section-by-Section
%    Tailoring below.
% 4. Technical Skills section (fold a single certification in as its own bolded line -
%    see "Single-Item Sections" below - break out a separate Certifications
%    section only for 2+ certifications)
% 5. Leadership section (optional, only if space allows - see "Leadership" below)
% No Languages section, no References section, no standalone Honors and Awards section by default (2026-07-09 preference) - see Page Budget below.

\end{document}
```

### Color overrides

The three `\renewcommand*` lines in the preamble are required on lualatex+MiKTeX. Without them the firstname, lastname, and section headings render in black even though `\moderncvcolor{blue}` is set, which looks inconsistent with the rest of the blue accent scheme (links, bullet markers, contact icons). The override forces all three to use `color1` (moderncv's accent colour, which becomes blue under `\moderncvcolor{blue}`). Both names render bold; if you prefer the firstname in regular weight, change the firstnamestyle override from `\bfseries` to `\mdseries`. Don't drop the override - on most modern installs the defaults render visibly wrong.

### Space-efficient preamble (2026-07-11 density pass)

The stock moderncv banking defaults (34pt name, `scale=0.80` geometry, default itemize spacing) are noticeably less dense than Purab's original plain-template resume, which fit *more* content (an extra role, an extra project, more skill categories) on a single page. To close that gap without cutting real content, the preamble now includes:

- **Smaller name font**: `\fontsize{24}{26}` instead of `34/36` - the name block was the single biggest vertical space cost in the header.
- **Wider usable page area**: `\usepackage[scale=0.91]{geometry}` instead of `0.80` - more text area per page, not tighter text.
- **Tighter list spacing**: `\usepackage{enumitem}` with `\setlist[itemize,1]{...}` and `\setlist[itemize,2]{...}` reduce the default `itemsep`/`topsep` moderncv's banking style ships with, which otherwise adds visible gaps between Technical Skills bullets and between `\cventry` blocks.
- **Slightly tighter line spacing**: `\linespread{0.95}`.

This combination was validated against `cv/main_example.tex`'s full content (2 experience entries, 2 projects, 6 skills categories, 1 leadership entry - 14+ bullets total) fitting on exactly 1 page with no visible crowding. Apply this preamble to new `main_<company>.tex` files as the current baseline instead of the older, more spacious settings. See the `\enlargethispage` clipping warning above (under "Fixing common page-break problems") before pushing any of these values further to close a remaining near-miss.

### Spacing inside itemize lists (important)

**Do not place `\vspace{...}` between `\item` entries in an `itemize` list.** Even though the source looks symmetric, this pattern occasionally produces a noticeably oversized gap before a single item: the inter-item `\vspace` creates a paragraph break that interacts unpredictably with the list's internal `\itemsep`, so LaTeX renders one of the gaps wider than the rest. Remove the inter-item `\vspace` and let `itemize` use its native uniform spacing.

```latex
% WRONG - intermittently produces an oversized gap before one bullet
\begin{itemize}
\item \textbf{Foo}: ...
\vspace{1pt}
\item \textbf{Bar}: ...
\vspace{1pt}
\item \textbf{Baz}: ...
\end{itemize}

% RIGHT - uniform spacing using the list's native itemsep
\begin{itemize}
\item \textbf{Foo}: ...
\item \textbf{Bar}: ...
\item \textbf{Baz}: ...
\end{itemize}
```

Two related patterns are fine and should be kept:
- `\vspace{1pt}` immediately after `\section{...}` (between section heading and first item) - this is between the heading and the list, not between list items.
- `\vspace{3pt}` between top-level `\cventry` blocks in Professional Experience or Education - this gives breathing room between roles and renders consistently.

## Inline Bolding for Scannability (Best Practice)

A recruiter's first pass is a 6-8 second skim, not a read. Bold **one** key metric or technology term per Experience/Projects bullet with `\textbf{...}` so the strongest signal in each line survives a skim even if nothing else does:

```latex
\item Debugged and resolved \textbf{2 C++ engine issues} in a 90GB+ production codebase, landing 2 pull requests reviewed and merged by core maintainers
\item Delivered \textbf{30+ merged pull requests} across a shared React/Next.js/Zustand codebase, resolving 10+ frontend bugs
```

Rules:
- **One bold span per bullet, maximum.** Bolding more than one phrase defeats the purpose - if everything is bold, nothing stands out.
- Prefer bolding a number/metric over a plain noun phrase - metrics are what a skimming eye actually stops on.
- Don't bold in the Technical Skills section beyond the existing category labels (`\textbf{Category}:`) - that section is already a scannable list and doesn't need a second layer of emphasis.

## Single-Item Sections (Fold, Don't Isolate)

A standalone `\section{}` costs a heading line, an underline rule, and `\vspace` overhead - roughly 2-3 lines of page budget for the section itself, before any content. That's expensive for one line of substance. If a section would only ever hold a single item (e.g. one certification), fold it into an adjacent section instead of giving it its own header:
- **Certifications:** fold a single certification into Technical Skills as its own bolded line (`\textbf{Certifications}: CodePath Intermediate Technical Interview Prep (2025)`) rather than a standalone `\section{Certifications}`. Only break it out into its own section if there are 2+ certifications, or the posting specifically calls out a credential that deserves visual prominence.
- This is the same logic as folding Dean's List/GPA into the Education entry (see below) - apply it to any future single-item section, not just Certifications.

## Section-by-Section Tailoring

### No Profile Statement / Summary (2026-07-11 preference)
Purab does not want a summary or "elevator pitch" paragraph at the top of the CV. Go straight from `\makecvtitle` into the Education section (see Recommended Section Order below). That freed space goes to Projects and Professional Experience, which carry more concrete evidence per line than a summary paragraph does. Do not add one back in even if an older `main_<company>.tex` still has one - if editing a pre-2026-07-11 CV, remove its profile statement and redistribute the reclaimed lines to Projects/Experience bullets.

### Technical Skills Section (Best Practice)
Reorder and emphasize based on the role. Use bold category labels.

List **5-7 key competencies** in bullet format, tailored to the specific job: `\textbf{Category}: item, item, item`. **Keep it a plain scannable list - do not add a sentence explaining how each competency "adds value."** A hiring manager reads this section in under two seconds; sentence-per-item justification is cover-letter framing that belongs in the profile statement or experience bullets, not here. It also eats page budget the 1-page limit can't afford.

### Education
- Always include your highest degrees
- For senior roles, keep education brief (dates and titles only)
- Include thesis topics when relevant to the target role
- **Fold honors/awards into the relevant degree entry** (e.g. "GPA: 3.77/4.0; Annual Dean's List (2 years), Quarterly Dean's List (8 quarters)" as a line under the BS entry) rather than a standalone Honors and Awards section - default since 2026-07-09
- **Dates include the month, not just the year** (2026-07-12 preference) - e.g. `Aug 2026--May 2028`, `Sep 2022--Jun 2025`, not `2026--2028`. Applies to every `\cventry` date field across Education, Professional Experience, and Leadership. Pull the month from `01-candidate-profile.md` (every entry there already has month-level dates); ask Purab rather than guessing if a date is genuinely unknown (e.g. an unconfirmed program start month) - see the GT MS entry there for the confirmed Aug 2026 start.

### Professional Experience
- **Dates include the month, not just the year** - see the Education note above; same convention applies to every role entry.
- Rewrite bullet points to emphasize aspects most relevant to the target role
- Use 4-6 bullets for most recent role, 3-4 for previous, 2-3 for older
- **Emphasize measurable results** where possible: "Reduced processing time by X%", "Model adopted by the team"
- **Order bullets by impact, strongest first**, not by chronology or task order within the role. A reader typically only fully reads the first 1-2 bullets per role before moving on - the most impressive, most relevant achievement must lead.
- **Ban weak/passive verbs.** Never open a bullet with "Responsible for", "Worked on", "Helped with", "Assisted with", "Participated in", or "Involved in". These read as duty-listing, not ownership. Lead with a strong action verb tied to an outcome instead (e.g. not "Worked on a recommendation feature" but "Built an AI-driven recommendation feature that...").
- **Keep tense consistent per role.** Past roles (anything with an end date) use past tense throughout - "Delivered", "Built", "Resolved". For the current role, use past tense for work that's actually finished and present tense only for what's genuinely still in progress ("Developing a real-time speech-to-text feature" is fine if it's not shipped yet; once it ships, change it to "Built"/"Shipped"). Don't mix tense within the same bullet, and don't leave a bullet in present tense after the underlying work is done - this is a common staleness bug when a CV is reused across applications without a re-check.

### Projects
For an early-career candidate, Projects are frequently the **strongest evidence of raw engineering ability** available, especially systems-level or from-scratch work that a thin professional history (one internship, one volunteer role) can't otherwise demonstrate. Treat Projects as load-bearing, not "if space allows" filler:
- Prefer projects that show depth (built end-to-end, from scratch, or under a non-trivial constraint like concurrency or performance) over projects that are just "used framework X"
- 1-2 entries, 2-3 bullets each; same impact-first ordering and weak-verb ban as Professional Experience
- Coursework projects can be described factually (skills demonstrated, what was built) but must not be framed as independent/self-directed initiatives unless they genuinely were - see `01-candidate-profile.md` for which projects carry that constraint
- Link to the specific repo or live demo when one exists and is safe to share, not just the header-level GitHub profile link - a hiring manager screening a junior candidate will click through, and a link on the specific project is what actually gets clicked. **Currently none of Purab's project repos are public/shareable** (confirmed 2026-07-10), so default to the header-level GitHub profile link only. Re-check with Purab before adding a per-project link - don't assume a repo is public just because the project is listed.
- When a Project and an older, less-relevant role are competing for the same space, apply relevance-weighted cutting (below) rather than defaulting to cutting the Project - a relevant project usually outweighs an irrelevant role, even an older "professional" one

### Leadership (Optional Section)
Purab has one leadership entry: **WSOS Scholar Lead** (mentoring 30+ STEM students, Washington State Opportunity Scholarship, Aug 2024 - Jun 2026 - see `01-candidate-profile.md`). This is real, ongoing experience, not filler, but it is not a software-engineering bullet - treat it as a supporting signal, not a core section:
- Include only when there's page budget left after Experience/Projects/Education, or when the posting explicitly values mentorship, onboarding, or cross-team communication (see `04-job-evaluation.md` behavioral-fit notes)
- If included: 1 entry, 1-2 bullets, no more
- On a tight 1-page CV, this is one of the first things to cut under relevance-weighted cutting (below) - a technical bullet almost always outranks it for a SWE posting. It can still be worth raising in a cover letter paragraph or an interview answer even when cut from the CV.

### Handling Employment Gaps (Best Practice)
If there is a gap in your employment history:
- The gap should be explained matter-of-factly if needed
- Describe how professional development continued during the gap
- Frame as deliberate skill-building and career repositioning

### Publications
- Include Google Scholar link if applicable
- Select 3-4 most relevant publications (not always all of them)
- For non-academic roles, keep brief
- On a 1-page CV, only include if directly relevant to the target role - otherwise cut first

### Languages, Honors and Awards, References (removed by default, 2026-07-09)
- **No standalone Languages section.** Only mention a language in the profile statement or a bullet if the posting specifically calls for it.
- **No standalone Honors and Awards section.** Fold Dean's List / GPA honors into the relevant Education entry (see above).
- **No References section.** Do not add "Available upon request" or list references - omit entirely. If an employer's application form asks for references separately, that's handled outside the CV.

## Compile-and-Inspect Loop (MANDATORY)

After writing the CV and before presenting to the user, always compile and visually inspect the PDF. Iterate until the layout is clean. Workflow:

1. Run `lualatex -interaction=nonstopmode main_<company>.tex`
2. Check the output page count: must be exactly 1
3. Read the PDF via the Read tool and visually inspect the page
4. Check for **orphaned entries**: a `\cventry` title line must never sit alone near the bottom of the page with its bullets pushed to a second page

### Fixing common page-break problems

**Problem: content spills to a second page by a near-miss (1.02 pages)**
Add `\enlargethispage{3\baselineskip}` before the last section to reclaim a few lines (use a single value - `\enlargethispage{2-3\baselineskip}` is invalid LaTeX and silently renders a stray "-3" on the page instead of erroring). This is the standard LaTeX rescue for near-miss overflows - prefer this over cutting content for a marginal spill. If it has no visible effect after recompiling, the spill isn't actually marginal - move to a real content cut instead of increasing the value further.

**Danger: `\enlargethispage` can silently clip content instead of moving it - page count alone is not proof of success.** Pushing the value too high doesn't make LaTeX flow the overflow onto a second page - it prints the excess *past the bottom of the physical page*, where it's invisible in the rendered PDF and can even disappear from `pdftotext` extraction entirely (confirmed by direct testing: a value that dropped the page count from 2 to 1 also silently deleted the CV's last two bullet points from the text layer). **Never trust "N pages" alone after using `\enlargethispage`.** After every recompile, grep the `pdftotext -layout` output for a handful of phrases spanning the whole document - especially the very last line of content - to confirm nothing vanished. If a phrase is missing, the value is too high; step back down one increment at a time and re-verify. This applies whenever tightening spacing to hit a page target, not just to `main_example.tex`.

**Problem: 2 pages with substantial content on page 2**
Cut content — do not compress geometry or `\vspace` to force-fit. See "Relevance-weighted cutting" below for the rule. On a 1-page CV this is the normal failure mode; expect to cut bullets, not just whitespace.

**Problem: content finishes with a large empty gap at the bottom of the page**
Restore the highest-relevance item that was previously cut, or loosen bullet-count limits slightly (e.g. 4 bullets instead of 3 for the most recent role) - a 1-page CV that only fills two-thirds of the page looks thin.

## ATS Parseability

Most employers run CVs through an ATS before a human sees them, and the ATS reads the PDF's embedded **text layer**, not the rendered page. A CV can pass visual inspection and still extract as garbage. After the layout passes the compile-and-inspect loop, verify the text layer:

```bash
cd cv && pdftotext -layout main_<company>.pdf main_<company>.txt
```

`pdftotext` comes from [poppler](https://poppler.freedesktop.org/), not the TeX distribution - it is an **optional** dependency. If it is not installed, skip the mechanical check with a warning and rely on the visual PDF read for keyword coverage.

What to check in the extraction:

- **Contact details as literal text.** The stock template's fontawesome contact icons extract as truncated/mangled glyph names (e.g. `MOBILE-A` for the phone icon) and the contact-field separator extracts as a middle dot `·` - both harmless noise, because the actual address and number are printed beside them. The failure mode is a contact detail carried *only* by an icon or a hyperlink (like the `LinkedIn` link text, whose URL is not in the text layer): invisible to an ATS. The email address must always appear as printed text.
- **No garbled output.** `(cid:NNN)` markers or `�` characters mean a font is embedded without a Unicode mapping - an ATS sees the same garbage. This shows up with unusual fonts in custom templates, not with the stock moderncv setup under lualatex.
- **Reading order.** The stock banking style is single-column, so extraction order matches visual order. Custom templates (via `/add-template`) with sidebars or multi-column layouts can interleave unrelated lines; if extraction order is scrambled, the user is trading ATS compatibility for looks and should be told.
- **Keyword coverage.** Match the posting's required/preferred terms against the extracted text, in the posting's language. Prefer the posting's exact term over a synonym when it is truthfully applicable - ATS matching is often literal. Never add a keyword the profile does not support.

## Page Budget - Hard 1-Page Limit (2026-07-09)

The CV **must** fit on exactly 1 page when compiled. This is a hard constraint - no Languages section, no Honors and Awards section, no References section (see "Languages, Honors and Awards, References" above). Use these content limits as a guide:

| Section | Max budget |
|---------|-----------|
| Technical Skills | 5-7 items, each 1 line (matches Technical Skills guidance below; includes the folded Certifications line if there's only one) |
| Most recent role | 3-4 bullets |
| Previous role | 2-3 bullets |
| Older roles | cut entirely unless directly relevant, or 1-2 bullets |
| Projects | 1-2 entries, 2-3 bullets each - do not default-cut ahead of an irrelevant older role; use relevance-weighted cutting (below) |
| Education | 2 entries max; fold GPA/Dean's List honors into the entry as a single trailing line |
| Publications | 1-2 entries, only if directly relevant |
| Certifications | Fold into Technical Skills as a single bolded line unless there are 2+ certifications - see "Single-Item Sections" above |
| Leadership | Optional; 1 entry, 1-2 bullets max, only if space allows after everything above - see "Leadership" under Section-by-Section Tailoring |

**If in doubt, cut rather than squeeze.** Reducing `\vspace` or geometry scale to force-fit content makes the CV look cramped. At 1 page, expect to make real content cuts on almost every tailored CV - this is normal, not a sign something went wrong.

## Relevance-weighted cutting (the right way to shrink a CV)

**Cut by signal, not by section.** Static priority lists ("remove oldest education first, then shorten the earliest role...") are wrong when a relevant "lower-priority" item is competing with an irrelevant "higher-priority" item. An older-role bullet that speaks directly to the posting is worth more than a recent-role bullet that does not.

For every candidate line, score three things:

1. **Relevance to THIS posting** — does the line hit a named tool, keyword, or stated responsibility in the job ad?
2. **Uniqueness** — is it the only place this claim appears, or is it duplicated elsewhere in the CV?
3. **Narrative load** — does the cover letter depend on it? If cutting the line would force you to rewrite a cover-letter paragraph, it is load-bearing.

Cut the lowest-total-score line first, regardless of which section it sits in.

### Practical order of cuts (easiest → last resort)

1. **Redundancy.** If an achievement appears in both Technical Skills AND a role bullet, the Technical Skills version is usually the cleaner cut (the experience bullet is more concrete evidence).
2. **Low-relevance experience bullets.** A bullet about work that does not touch posting keywords, wherever it sits. This cuts across sections before touching the structural list.
3. **Low-relevance supporting content.** An older-role bullet that does not speak to the target role. A certification that does not touch the posting's stack. A language entry that can be condensed to one line. The optional Leadership entry (WSOS Scholar Lead) - unless the posting specifically values mentorship/communication (see `04-job-evaluation.md`), it is the default first cut on a tight page since it isn't a technical bullet. **A non-technical older role (e.g. admin/executive-assistant work) almost always scores below a relevant Project for an early-career SWE application - cut the role before cutting the project.**
4. **Low-relevance publications.** Keep 1-2 publications that best match the posting. Cut the rest before touching experience bullets.
5. **Last-resort structural cuts.** Oldest education entry, tightening an older role to 2 bullets. These only happen if the relevance-weighted cuts above have already been exhausted. (Certifications should already be folded into Technical Skills by default per "Single-Item Sections" above - that's not a cut reserved for last resort, it's the starting point.)

### Pitfalls to avoid

- Do not mechanically cut from the bottom of a static section list without checking relevance. "Cut the oldest role first" is wrong if that role is literally about the skill the posting asks for.
- Do not cut the one concrete example the cover letter leans on. Relevance is measured against the cover letter you wrote, not just the job posting — interviewers will have read both.
- Do not cut to fit if the fit is borderline (1.02 pages). Prefer `\enlargethispage{3\baselineskip}` on a late section for near-misses; reserve content cuts for genuine overflow (a real second page of content, not a few trailing lines).

## Recommended Section Order (2026-07-11 standing order)

No profile statement/summary (2026-07-11), no Languages, Honors and Awards, or References sections by default (2026-07-09) - honors fold into Education. This order applies to all role types:

1. Education (reverse chronological, honors folded in)
2. Professional Experience (reverse chronological)
3. Projects
4. Technical Skills (certifications folded in if only one)
5. Leadership (optional, only if space allows - see above)
