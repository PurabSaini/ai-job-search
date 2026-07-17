# Writing Style Guide

## Critical Rules

1. **NO em-dashes (--).**  Use commas, periods, or restructure the sentence instead.
2. **NO cliches or filler phrases.** Cut: "I am passionate about", "I believe I would be a great fit", "leverage my skills", "hit the ground running", "drive results", "synergies".
3. **NO generic buzzwords** without concrete backing. Every claim must be supported by a specific example or fact. This includes soft self-assessment claims that sound concrete but aren't tied to anything checkable - e.g. "Ships fixes independently once a problem is reported, without needing a detailed spec" is a buzzword in disguise unless it's anchored to a specific instance elsewhere in the document (a named bug, a named PR). Either attach the specific example or cut the sentence.
4. **NO apologetic or overly humble language.** Not "I think I could contribute" but "I bring X, demonstrated by Y."
5. **NO unverified company claims.** Every company-specific statement in a cover letter (partnerships, product names, technology descriptions, expansions) must be independently verified via WebFetch or WebSearch before inclusion. Do not trust reviewer agent research at face value. If a claim cannot be verified, rephrase it in general terms or omit it.
6. **Reframe emphasis, not substance.** Some framing of experience toward the target role is expected. But apply the **interview backtrack test**: could the candidate comfortably explain this bullet in an interview without backtracking? If they'd have to say "well, what I actually meant was..." then it's too far. Specifically:
   - **OK:** Reordering experience to lead with what's most relevant; using natural synonyms for the target domain; emphasizing one aspect of a broad role.
   - **Flag it:** Combining academic + industry experience into a single claim that implies it was all industry; describing work using the posting's specific terminology when the actual work was adjacent but not the same.
   - **Never:** Claiming experience the candidate doesn't have; implying they worked in a domain they haven't.
   When a bullet falls in the "flag it" zone, present it to the user after drafting with: "This bullet is a stretch because X. Keep, soften, or drop?" If the evaluation experience match score is below 50, warn before proceeding to drafting that extensive reframing would be needed.

## Tone
- **Warm but direct.** Friendly and approachable, but confident without arrogance.
- **Conversational professional.** Not stiff corporate-speak, not casual chat. Think: how a confident person talks in a good job interview.
- **First person, active voice.** "I built" not "a system was developed by the candidate."
- **Demonstrate, don't state.** Instead of "I am a team player", write a specific example of teamwork and its outcome.

## Application Headline (Best Practice)

The subject line / headline of the application should be engaging and specific, not generic.

**Bad:** "Application for Sales Engineer Position" / "Ansogning til stilling som ingeniør"
**Good:** "[Your specialty] specializing in [relevant keyword from posting]"

Formula: **[Title/education] + [relevant keyword from the job posting]**

## Scannable Structure (Best Practice)

Employers scan applications quickly. Structure for easy reading:
- Use descriptive subheadings that reflect content (not just "Introduction" / "Body")
- Include industry-specific keywords in headings where natural
- Write concisely - eliminate filler language
- One page maximum (hard rule)

## Forward-Looking Framing (Best Practice)

The cover letter is **not a CV repetition**. It should be forward-looking:
- Focus on **tasks you can solve for the employer**, not just what you've done before
- Describe your approach: methods, tools, knowledge you'll bring
- Explain what positive outcomes the employer can expect from hiring you
- Use 1-2 brief past examples only to back up forward-looking claims

## Cover Letter Structure

### Opening Paragraph
- State the role and why you're writing (1 sentence)
- Immediately connect your background to the role (1-2 sentences)
- Make it specific to this company/role, not a template opener

### Body Paragraphs - Task-Solving Focus
- Lead with the most relevant experience for this specific role
- Frame content around **which of their tasks you can solve and how**
- Describe your approach: methods, tools, and knowledge you'll bring
- Use bullet lists for concrete skills/achievements when appropriate (3-5 bullets)
- Each bullet should be specific and outcome-oriented
- Include at least one example that shows initiative
- Include 1-2 brief examples of past success, but keep the focus forward-looking

### Motivation / Why This Company (place early)
- The **first section** after the opening should explain why you're applying to *this specific company*
- Use language and themes from the job posting and company website
- Focus on how you'll contribute to their goals, not what you gain from employment
- If you spoke with someone at the company, reference the conversation naturally

### Company-Specific Paragraph
- Show you've researched the company (mention specific projects, values, or market position)
- Explain why this company specifically, not just "a company like yours"
- Connect domain knowledge to their business context

### Closing
- Brief, confident, forward-looking
- "I look forward to hearing from you" or "I would welcome the opportunity to discuss..."
- No begging or over-enthusiasm

## Bullet Point Style
- Start with action verb or bold category label
- Be specific: numbers, tools, outcomes
- Vary the structure (not every bullet starts the same way)
- Keep tense consistent within a role/section: past tense for finished work, present tense only for what's genuinely still in progress. Don't let a bullet stay in present tense after the work has shipped - re-check tense whenever reusing a bullet across applications.

## Language for Different Role Types

### Technical/ML roles
- Lead with programming languages, ML frameworks, specific model architectures
- Mention datasets, data volumes, pipeline complexity
- Include independent projects

### Domain-specific roles
- Lead with domain expertise and specific methods
- Frame technical skills as tools that enhance domain analysis

### Consulting/Advisory roles
- Lead with stakeholder communication, project coordination, client interaction
- Emphasize ability to bridge technical and business perspectives

### Leadership/Senior roles
- Lead with project management, mentoring, course development
- Frame advanced degrees as evidence of independent project delivery

## Multi-language Applications
- Default to the language of the job posting
- Cover letters in the posting's language should feel natural, not translated
- Slightly warmer, more personal tone may be acceptable in some languages

## Patterns Observed in Past Applications

Mined from 4 submitted cover letters (Vestmark, Built, Glean, Notion) via `/setup` on 2026-07-13:

- **Motivation paragraph formula:** All 4 letters open the "why this company" paragraph with the exact phrase **"What draws me to [Company] specifically is..."**. Treat this as the default opener for that paragraph rather than inventing a new transition each time.
- **Default ambiguity/ownership proof point:** 3 of 4 letters (Vestmark, Built, Glean) reuse the Sansar cursor-disappearance bug, near-verbatim ("tracing a cursor-disappearance bug through an unfamiliar 90GB+ production codebase at Sansar took exactly that kind of open-ended investigation"), as the go-to example for "I can work through ambiguous problems without a detailed spec." It's a strong, real example - fine to keep reusing, but vary the wording per letter so it doesn't read as copy-pasted across applications from the candidate's side, and swap in a different proof point if a posting's ambiguity angle doesn't fit this bug well.
- **Closing paragraph default:** 3 of 4 letters (Vestmark, Glean, Notion) close with the plain "I look forward to hearing from you." Built used a team-specific variant instead ("I would welcome the chance to talk through where I would start on the Implementations team.") when the posting named a specific team - use that variant when a team name is available and it reads naturally, otherwise default to the plain closer.
