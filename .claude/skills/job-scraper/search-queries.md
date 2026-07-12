# Search Queries for Job Scraper

## Search Sites

This candidate is based in the United States, so the framework's built-in Danish job-portal tools (Jobindex, Jobbank, Jobdanmark, Jobnet) do not apply. Rely on:

Primary:
- **linkedin.com/jobs** - LinkedIn job listings (filter: United States, remote, or specific state)
- Google `site:` searches against LinkedIn and company career pages

Secondary (company career pages via Google):
- Direct Google searches with `site:` filters for known target companies

## Query Categories

Queries are grouped by priority. The candidate is open to any US location, remote, hybrid, or on-site, so location terms are optional filters rather than hard constraints.

### Priority 1: Software Engineer / Full-Stack

Strongest and most desired career direction (early-career, full-time or internship).

```
site:linkedin.com/jobs "Software Engineer" "entry level" OR "new grad" OR intern
site:linkedin.com/jobs "Full Stack Engineer" "entry level" OR "new grad" OR intern
site:linkedin.com/jobs "Full Stack Developer" TypeScript React
"software engineer intern" 2026 OR 2027
```

### Priority 2: Front-End / Back-End

Matches specific stack expertise (React/Next.js frontend, Java/SQL backend).

```
site:linkedin.com/jobs "Front End Engineer" React OR Next.js "entry level" OR intern
site:linkedin.com/jobs "Back End Engineer" Java OR SQL "entry level" OR intern
site:linkedin.com/jobs "Frontend Developer" TypeScript entry level
```

### Priority 3: Systems Engineer

Adjacent role type matching C/C++ and systems programming background.

```
site:linkedin.com/jobs "Systems Engineer" C++ "entry level" OR "new grad"
site:linkedin.com/jobs "Software Engineer" C++ systems intern OR "new grad"
```

### Priority 4: Broader Technical

Wider net for general early-career technical roles.

```
site:linkedin.com/jobs "new grad" software engineer 2026 OR 2027
site:linkedin.com/jobs "software developer" intern remote
```

## Location Filter

The candidate is open to relocating anywhere in the United States and is open to remote, hybrid, or on-site roles. There is no commute range or relocation constraint - do not filter out results by location. Optionally note whether a role is remote, hybrid, or requires on-site presence in a specific city, but do not treat any US location as disqualifying.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries
