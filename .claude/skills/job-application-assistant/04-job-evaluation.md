# Job Evaluation Framework

## Scoring Dimensions

Evaluate each job posting against these five dimensions:

### 1. Technical Skills Match (0-100)
How well do the required/preferred skills align with the candidate's capabilities?

| Score | Meaning |
|-------|---------|
| 80-100 | Core requirements are primary skills |
| 60-79 | Most requirements match, 1-2 gaps that are learnable |
| 40-59 | Partial match, significant upskilling needed |
| 0-39 | Fundamental mismatch |

**Strong match areas:** TypeScript/JavaScript, React/Next.js, Java, C/C++, SQL, full-stack web development, systems programming (POSIX, sockets, file/disk indexing)
**Moderate match areas:** C#, Python, SQL Server, database schema design and concurrency
**Minimal/one-off exposure:** MS Azure (used once, for the Flight Application coursework project — do not score as a standing cloud-platform skill), Docker (used once, for the Pittsburgh Market project — do not score as a standing containerization skill), Scrapy/web scraping (brief use, for the Pittsburgh Market project — do not score as a standing data-pipeline skill)
**No hands-on exposure:** SSRS (Peninsula Light Co. was a shadowing role only — Purab observed SSRS dashboard work but did not build it himself; do not score as any level of skill match)
**Weak match areas:** [SKILLS_YOU_LACK - update as gaps surface from postings]

### 2. Experience Match (0-100)
Does work history align with what they're looking for?

| Score | Meaning |
|-------|---------|
| 80-100 | Direct experience in the same domain and role type |
| 60-79 | Related experience, transferable skills clear |
| 40-59 | Adjacent experience, would need to make the case |
| 0-39 | Unrelated experience |

**Strong:** Front-end/full-stack web development (React/Next.js/TypeScript at Trialynx) — primary and most current strength; systems/C++ engineering (Sansar VR platform)
**Moderate:** Data-adjacent work surfacing structured data to end users (Trialynx clinical trial recommendations)
**Dated/rusty:** Backend/database work (SQL Server, relational schema design) — from the Flight Application coursework project, several years old, not recent hands-on experience. Currently being rebuilt via an in-progress personal project (D&D Tool).
**Not real experience:** Peninsula Light Co. (IT Intern) was a shadowing role - Purab observed IT/financial reporting operations but did not do hands-on work. Do not count it toward experience match for any dimension.
**Entry-level:** All roles to date are internship/volunteer/early-career - candidate is a recent graduate (BS 2025) starting an MS, so most professional roles should be evaluated as entry-level/new-grad fit

### 3. Behavioral/Culture Fit (0-100)
Does the role and company culture match the behavioral profile?

| Score | Meaning |
|-------|---------|
| 80-100 | Culture strongly matches behavioral preferences |
| 60-79 | Mixed signals but mostly compatible |
| 40-59 | Some friction areas |
| 0-39 | Significant culture mismatch |

**Positive signals:** Postings that value mentorship, onboarding junior engineers, or cross-team/non-technical communication line up well with the WSOS Scholar Lead leadership experience (mentoring 30+ STEM students) - worth surfacing in the cover letter or an interview answer, even though it won't usually earn CV space over technical bullets on a 1-page limit.

**Red flags to research:** Department disorganization, work dominated by maintenance over development, poor chemistry with leadership, culture mismatches. Check reviews, media coverage, LinkedIn connections, and network contacts for insider perspective.

### 4. Location & Logistics (Pass/Fail + Notes)
- Within commute range: PASS
- Remote with occasional office: PASS
- Requires relocation: PASS
- Frequent international travel: FLAG (discuss with user)
- **Requires an immediate, full-time on-site start:** FLAG (discuss with user) - Purab is starting an online MS in Computer Science at Georgia Tech (expected May 2028) and hasn't yet decided full-time vs. part-time course load. The program is online so it doesn't block full-time work by itself, but don't assume capacity - confirm his actual course-load plan before treating this as a clean PASS.

### 5. Career Alignment & Motivation (0-100)
Does this role advance career goals and contain tasks that energize?

| Score | Meaning |
|-------|---------|
| 80-100 | Strongly aligned with career direction, clear growth path |
| 60-79 | Good role but only partially aligned with long-term goals |
| 40-59 | Decent job but doesn't build toward career goals |
| 0-39 | Dead end or backwards step |

**Career goals:** Early-career Software Engineer / Full-Stack / Front-End / Back-End / Systems roles, full-time or internship, anywhere in the US (see `01-candidate-profile.md` Target Sectors) - no narrower specialization or specific company targets identified yet.

**Motivation filter:** Evaluate not just whether you *can* do the tasks, but whether the tasks will *energize* you. Consider:
- Tasks that energize: Building things that are technically solid and genuinely useful to people; full-stack range work that spans systems-level and UI-level tasks rather than narrow specialization (see `02-behavioral-profile.md`); building with or on top of AI/agentic tooling (Claude Code, agent frameworks) as a core part of the work, not just an occasional habit (confirmed 2026-07-13)
- Tasks that drain: **Not yet gathered.** Don't infer a specific answer - ask Purab if a posting's day-to-day tasks are ambiguous enough to matter for the decision.
- Non-task factors: leadership style, department culture, company values, degree of autonomy

**Life situation alignment:**
- **Security / Flexibility**: See the online-MS course-load caveat under Location & Logistics (dimension 4) above - don't repeat the full explanation here, just flag if a posting's demands (hours, start date) look incompatible with it.
- **Professional development**: Not yet specified beyond the Career goals above - don't infer more specific priorities.

### 6. Salary Benchmark (Optional)

If the salary lookup tool is configured (`salary_data.json` exists), look up the company:
```
python salary_lookup.py "<Company Name>" --json
```

If a city is known from the posting, add `--city "<City>"` to narrow results.

Present findings as:
```
### Salary Benchmark
| Metric | Value |
|--------|-------|
| [Category] index | XX.X (+/-X.X% vs baseline) |
| Overall index | XX.X (+/-X.X% vs baseline) |
```

Interpret results relative to the baseline defined in the data file's metadata. For index-based data, higher typically means above-market compensation.

If the salary tool is not configured, skip this section.

## Output Format

Present the evaluation as:

```
## Job Fit Evaluation: [Role] at [Company]

| Dimension | Score | Notes |
|-----------|-------|-------|
| Technical Skills | XX/100 | [brief note] |
| Experience Match | XX/100 | [brief note] |
| Behavioral Fit | XX/100 | [brief note] |
| Location | PASS/FAIL | [brief note] |
| Career Alignment | XX/100 | [brief note] |

**Overall Score: XX/100** (weighted average of scored dimensions)

### Verdict: [Strong Fit / Good Fit / Moderate Fit / Weak Fit / Poor Fit]

### Key Strengths for This Role
- [bullet points]

### Gaps to Address
- [bullet points]

### Recommendation
[1-2 sentences: apply/skip/apply with caveats]

### Company Research Checklist
- [ ] Checked company website (mission, values, recent news)
- [ ] Checked review sites (Glassdoor, Jobindex, etc.)
- [ ] Checked LinkedIn for team size, recent hires, connections
- [ ] Checked media for restructuring, growth, or workplace issues
- [ ] Identified network contacts who may know the team/manager
```

## Weighting
- Technical Skills: 30%
- Experience Match: 25%
- Behavioral Fit: 15%
- Career Alignment: 30%

(Location is pass/fail, not weighted)

## Thresholds
- **Strong Fit** (75+): Definitely apply, tailor everything
- **Good Fit** (60-74): Apply, address gaps in cover letter
- **Moderate Fit** (45-59): Consider carefully, discuss with user
- **Weak Fit** (30-44): Probably skip unless strategic reasons
- **Poor Fit** (<30): Skip

## Calibration from Past Applications

No completed applications with outcome data yet - `/setup` populates this section from `documents/applications/<company>_<role>/outcome.md` files once real interview/offer/rejection signal exists. Nothing to calibrate against until then.

## Pre-Application: Call the Employer (Best Practice)

Before writing the application, consider whether the candidate should call the contact person listed in the posting. **Only call if there are substantive questions** - never call just to "be remembered."

### When to Suggest Calling
- The posting has unclear or ambiguous requirements
- It's unclear which competencies are essential vs. nice-to-have
- The role description is vague about day-to-day tasks
- There's a named contact person who invites questions

### Good Questions to Ask
- "What are the primary challenges in this role?"
- "How is time typically divided across the listed responsibilities?"
- "Which competencies are most critical for success in this position?"
- "What does success look like in the first 6-12 months?"

### Rules for the Call
- Prepare a 30-second "elevator pitch" about your background in case they ask
- The call's purpose is **gathering information**, not delivering a pitch
- Take notes - use what you learn to tailor the application
- Reference the conversation naturally in the cover letter ("After speaking with [name], I was especially drawn to...")
