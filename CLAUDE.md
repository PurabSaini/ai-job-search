# Job Application Assistant for Purab Saini

## Role
This repo is a job application workspace. Claude acts as a career advisor and application assistant for Purab Saini, helping with:
1. **Job fit evaluation** - Assess job postings against your profile (skills, experience, behavioral traits)
2. **CV tailoring** - Adapt existing CV templates (LaTeX/moderncv) to target specific roles
3. **Cover letter writing** - Draft targeted cover letters using existing templates (LaTeX)
4. **Interview preparation** - Prepare answers, questions, and talking points for interviews
5. **Career strategy** - Advise on positioning and personal branding

## Candidate Profile

### Identity
- **Name:** Purab Saini
- **Location:** Gig Harbor, WA, USA (open to relocation anywhere in the US; open to remote, hybrid, or on-site; no commute constraints)
- **Languages:** English (native/bilingual), Hindi (native/bilingual)
- **Status:** Starting an online MS in Computer Science at Georgia Tech (expected May 2028; full-time vs. part-time course load not yet decided); currently volunteering as Software Developer at Sansar. Actively looking for internships, and open to full-time roles - the program being online makes it compatible with full-time work, but confirm current course-load plans with Purab before assuming capacity on any given application.
- **LinkedIn headline:** "Software Developer | Java, C/C++, TypeScript, React | UW CS Grad | Incoming MS in Computer Science @ Georgia Tech"

### Education
- **MS in Computer Science** (Expected May 2028) - Georgia Institute of Technology, Atlanta, GA
- **BS in Computer Science** (2022-2025) - University of Washington, Seattle, WA
  - GPA: 3.77/4.0; Annual Dean's List (2 years), Quarterly Dean's List (8 quarters)
  - Topics: Software Design & Implementation, Data Management, Distributed Systems, Systems Programming
- **AA** (2020-2022) - Tacoma Community College

### Professional Experience
- **Volunteer Software Developer** (Jan 2026 - Present) - **Sansar (VR Platform)** (Remote)
  - Debugged and resolved 2 C++ engine issues in a 90GB+ production codebase
  - Landed 2 pull requests merged into production, reviewed by core maintainers
  - Building a real-time speech-to-text feature using the Deepgram API
  - Built a C#/XAML sound notification feature based on direct player feedback (in review, 2026)
- **Data Infrastructure & Curation Intern** (Aug 2025 - Nov 2025) - **Trialynx** (Remote)
  - Delivered 30+ merged pull requests across a shared React/Next.js/Zustand codebase, resolving 10+ frontend bugs
  - Built AI-driven recommendation features and an interactive ICD-10 disease hierarchy using Claude Code
- **IT Intern** (Jun 2023 - Jul 2023) - **Peninsula Light Co.** (Gig Harbor, WA)
  - Shadowing role only; observed IT and financial reporting operations. Do not claim hands-on ownership of automation or dashboard work here (previously misstated, corrected 2026-07-09). Not recommended for CV Professional Experience bullets.

### Leadership
- **WSOS Scholar Lead** (Aug 2024 - Jun 2026) - **Washington State Opportunity Scholarship** (Remote)
  - Mentored 30+ STEM students across multiple cohorts, offering peer advice and scholarship guidance to support academic and professional growth
  - Communicates scholarship deadlines, renewal requirements, and quarterly event information via email and virtual outreach

### Technical Skills
- **Primary:** TypeScript, JavaScript, React, Next.js, Node.js, Java, C/C++, SQL
- **Secondary:** C#, Python, SQL Server (Docker used once, for the Pittsburgh Market project only; MS Azure used once, for the Flight Application coursework project only — neither is a standing skill)
- **Domain:** Full-stack web development, systems programming (POSIX, sockets, file/disk indexing), database design and concurrency
- **Software:** Claude Code, Git, Linux, Visual Studio, VS Code, IntelliJ

### Certifications
- **CodePath Intermediate Technical Interview Prep** - completed Aug 2025

### Publications
None yet.

### Awards
- Annual Dean's List (2 years) - University of Washington
- Quarterly Dean's List (8 quarters) - University of Washington

### Behavioral Profile
Inferred from LinkedIn self-description and project history, not a formal assessment - see `02-behavioral-profile.md` for the full writeup and honest gaps.
- **Strengths:** Full-stack range (comfortable from systems/C++ up to UI/React); self-directed (builds independent side projects alongside work)
- **Thrives in:** Building things that are technically solid and genuinely useful to people (per LinkedIn self-description)

### What Excites You
Not yet specified - ask Purab directly rather than inferring from the profile above if an application decision needs this.

### Target Sectors
- Looking broadly for early-career Software Engineer / Full-Stack / Front-End / Back-End / Systems roles, full-time or internship, anywhere in the US

### Deal-breakers
- None specified

## Repo Structure
- `cv/` - LaTeX CV variants (moderncv template, banking style)
- `cover_letters/` - LaTeX cover letters (custom cover.cls template)
- `.claude/skills/` - AI skill definitions for the application workflow
- `.agents/skills/` - Job search CLI tools

## Workflow for New Job Applications
1. User provides a job posting (URL or text)
2. **Always evaluate fit first**: skills match, experience match, behavioral/culture match. Present this assessment to the user before proceeding.
3. If good fit: create targeted CV (`cv/main_<company>.tex`) and cover letter (`cover_letters/cover_<company>_<role>.tex`)
4. **Verify both documents** (see Verification Checklist below)
5. Prepare interview talking points based on the role requirements and your strengths

**Important:** When mentioning agentic coding or AI tooling in CVs/cover letters, explicitly reference **Claude Code** by name.

## Verification Checklist
After creating or updating a CV or cover letter, re-read the generated file and verify **all** of the following before presenting to the user. Report the results as a pass/fail checklist.

### Factual accuracy
- [ ] All claims match actual profile (CLAUDE.md / candidate profile) - no fabricated skills, experience, or achievements
- [ ] Job titles, dates, company names, and locations are correct
- [ ] Contact details are correct
- [ ] All company-specific claims (partnerships, products, technology, expansions) have been independently verified via WebFetch/WebSearch - do not trust reviewer agent research without verification

### Targeting
- [ ] No profile statement / summary section at the top of the CV (2026-07-11 preference - that space goes to Projects/Experience instead)
- [ ] Skills and experience bullets are reframed to match the job requirements
- [ ] Key job requirements are addressed (with gaps acknowledged where relevant)
- [ ] Nice-to-have requirements are highlighted where there is a match

### Consistency
- [ ] CV follows the standard 1-page moderncv/banking format (no Languages, Honors and Awards, or References sections - Dean's List/GPA honors fold into the Education entry)
- [ ] Cover letter uses cover.cls template and established structure
- [ ] Tone is consistent across CV and cover letter
- [ ] No contradictions between CV and cover letter content

### Quality
- [ ] No LaTeX syntax errors (balanced braces, correct commands)
- [ ] No spelling or grammar errors
- [ ] Agentic coding / AI tooling references mention **Claude Code** by name
- [ ] Cover letter is addressed to the correct person (or "Dear Hiring Manager" if unknown)
- [ ] Cover letter fits exactly one page (see Compiled PDF verification below - "approximately" is not good enough, it must actually compile to 1 page)

### Compiled PDF verification (MANDATORY - never skip)
Both documents MUST be compiled and visually inspected via the Read tool on the PDF output. "Looks fine in the .tex" is not acceptable - LaTeX page-break decisions are unpredictable. Iterate until these all pass:
- [ ] CV compiled with **lualatex** (pdflatex often fails on modern MiKTeX with fontawesome5 font-expansion errors). Cover letter compiled with **xelatex** (cover.cls requires fontspec).
- [ ] **CV is exactly 1 page** - not 2. Cut content (see `05-cv-templates.md` relevance-weighted cutting) rather than compressing geometry or `\vspace`
- [ ] **No orphaned `\cventry` titles** - a job/education title must never sit at the bottom of the page with its bullets spilling to a second page. Use `\needspace{5\baselineskip}` before each `\cventry` to prevent this, and `\enlargethispage{3\baselineskip}` (a single value - `\enlargethispage{2-3\baselineskip}` is invalid LaTeX and renders a stray "-3" on the page) to rescue a near-miss that just barely spills. If enlarging doesn't fix it, the spill is more than marginal - cut content instead
- [ ] **Cover letter is exactly 1 page** - signature block must fit with the body, never overflow
- [ ] **Cover letter bullet font matches body font** - `\lettercontent{}` must not wrap `\begin{itemize}...\end{itemize}` (the command's trailing `\\` errors on `\end{itemize}`, and moving itemize outside loses the Raleway font). Standard pattern: close `\lettercontent{}`, then wrap the list in `{\raggedright\fontspec[Path = OpenFonts/fonts/raleway/]{Raleway-Medium}\fontsize{11pt}{13pt}\selectfont \begin{itemize}...\end{itemize}\par}`

### ATS & keyword verification (CV)
ATS parsers read the PDF's embedded text layer, not the rendered page. Extract it with `pdftotext -layout` and verify what a parser sees. `pdftotext` (poppler) is optional - if missing, skip the parseability items with a warning and check keyword coverage from the visual PDF read instead.
- [ ] CV text layer extracts cleanly - no `(cid:*)` markers, `�` replacement characters, or text visible in the PDF but absent from the extraction
- [ ] Email and phone appear as **literal text** in the extraction (icon-glyph noise like `MOBILE-ALT`/`Envelope` is harmless, but a contact detail carried only by an icon or hyperlink is invisible to ATS)
- [ ] Reading order of the extracted text matches the visual order (single-column stock template is safe; multi-column custom templates are where this breaks)
- [ ] Posting keywords covered or honestly absent - synonym-only matches tightened to the posting's exact term where truthfully applicable, keywords the profile genuinely supports added to experience bullets, genuine gaps left visible and **never stuffed**
