# TEMPT Profile: Resume Review

## Metadata

| Field | Value |
|-------|-------|
| **Name** | Resume Review |
| **Version** | 1.0 |
| **Created** | 02-05-2026 |
| **Freshness Class** | weeks |
| **Primary Use Case** | Resume critique, ATS optimization, career-change positioning, interview readiness, hiring-manager appeal |

---

## Trigger Keywords

### Tier 1 — Unambiguous (Auto-load silently)

```
resume, résumé, CV, curriculum vitae, cover letter,
ATS, applicant tracking, applicant tracking system,
Workday, Greenhouse, Lever, iCIMS, Taleo, BambooHR, SmartRecruiters,
job application, job posting, job description, JD,
hiring manager, recruiter, headhunter, talent acquisition,
work experience, professional summary, career objective,
bullet points, action verbs, quantified results, STAR method,
skills section, education section, certifications section,
resume format, chronological resume, functional resume, hybrid resume,
keyword optimization, resume keywords, resume score,
LinkedIn profile, LinkedIn optimization
```

### Tier 2 — Likely (Auto-load with confirmation)

```
job search, job hunt, applying, application,
interview, phone screen, behavioral interview, technical interview,
career change, career transition, career pivot, career switch,
employment gap, gap explanation, layoff, career break,
promotion, advancement, leadership experience,
transferable skills, soft skills, hard skills,
portfolio, work samples, projects section,
references, recommendation, endorsement,
networking, informational interview, cold outreach,
salary, compensation, negotiation, offer letter
```

### Tier 3 — Ambiguous (Ask if sole match)

```
experience, skills, summary, objective, profile, position, role,
background, qualifications, achievements, accomplishments,
format, template, layout, design, structure
```

---

## Freshness Requirements

| Data Type | Freshness Threshold | Auto-Inject |
|-----------|---------------------|-------------|
| ATS parsing behavior | <4 weeks | "[ATS name] [current year] parsing" |
| Hiring trends / market data | <4 weeks | "[industry] hiring trends [current month] [year]" |
| Resume format best practices | <8 weeks | "[year] resume best practices" |
| Job posting analysis | <7 days | "latest" or "recent" |
| Industry salary data | <4 weeks | "[role] salary [year] [location]" |
| LinkedIn algorithm changes | <4 weeks | "LinkedIn [current year] algorithm" |
| Interview question trends | <8 weeks | "[role] interview questions [year]" |
| Career-change frameworks | <12 weeks | no injection |

**Default freshness:** <4 weeks

**Stale handling:** Flag ⚠️ STALE SOURCE → re-query with current date → note if still stale. Resume advice older than 8 weeks MUST be cross-referenced with a current source.

---

## Source Priority

1. **ATS Documentation & Research** — How systems actually parse
   - Official ATS vendor documentation (Greenhouse, Lever, Workday)
   - Jobscan, ResumeWorded (ATS scoring methodology)
   - HR technology publications

2. **Hiring Manager Primary Sources** — What decision-makers say
   - Recruiter/hiring manager surveys (LinkedIn Talent Solutions, Indeed Hiring Lab)
   - Published hiring manager interviews and AMAs
   - Corporate talent acquisition blog posts

3. **Career Authority Publications** — Established expertise
   - Harvard Business Review (career section)
   - Ask a Manager (askamanager.org)
   - The Muse, TopResume, Jobscan blog
   - NACE (National Association of Colleges and Employers)

4. **Industry-Specific Sources** — Domain expectations
   - Industry-specific job boards (Dice, AngelList, Hired for tech)
   - Professional association career resources
   - Glassdoor interview reviews and company insights

5. **Labor Market Data** — Context for positioning
   - Bureau of Labor Statistics (BLS)
   - LinkedIn Economic Graph / Workforce Reports
   - Indeed Hiring Lab, ZipRecruiter trends

**Avoid:** Generic "top 10 resume tips" listicles, outdated template sites, sources without author credentials, AI-generated resume advice without editorial oversight

---

## Additional BB Pairs

| Dimension | Builder | Breaker | Trigger |
|-----------|---------|---------|---------|
| Hiring Decision | Tech Hiring Manager | Talent Bar Guardian | experience, qualifications, role fit |
| Resume Quality | Professional Resume Reviewer | Format Rebel | format, structure, bullets, summary |
| ATS Compatibility | ATS Optimizer | Human Readability Advocate | keywords, ATS, parsing, score |
| Interview Readiness | Simulated Interviewer | Interview Coach | interview, questions, gaps, weaknesses |
| First-Pass Filtering | Recruiter Screener | Candidate Advocate | screening, filtering, volume hiring |
| Career Positioning | Career Coach | Reality Checker | career change, transition, transferable |
| Domain Fit | Industry Specialist | Generalist Framer | industry, domain, specialization |

### Pair Descriptions

**Hiring Decision: Tech Hiring Manager / Talent Bar Guardian**
- Builder (Tech Hiring Manager): Evaluates "would I bring this person in for an interview?" Looks for signal: impact, scope, technical depth, progression. Simulates the 30-second decision.
- Breaker (Talent Bar Guardian): Argues the bar isn't met. Finds missing proof of impact, vague claims, scope inflation, missing technical specifics. Asks "compared to the other 50 resumes on my desk, why this one?"

**Resume Quality: Professional Resume Reviewer / Format Rebel**
- Builder (Professional Resume Reviewer): Evaluates structure, visual hierarchy, bullet quality (action verb + context + quantified result), narrative arc across roles, professional summary effectiveness.
- Breaker (Format Rebel): Challenges resume conventions that may hurt the candidate. Questions whether "standard" formatting is optimal for THIS person's story. Flags when convention hides the candidate's actual strengths.

**ATS Compatibility: ATS Optimizer / Human Readability Advocate**
- Builder (ATS Optimizer): Ensures keyword density matches target job descriptions, formatting won't break parsing (tables, columns, headers, graphics), file format compatibility, section naming conventions.
- Breaker (Human Readability Advocate): Pushes back when ATS optimization makes the resume robotic, keyword-stuffed, or unnatural. Argues that a resume that passes ATS but reads poorly to a human fails at the next stage.

**Interview Readiness: Simulated Interviewer / Interview Coach**
- Builder (Simulated Interviewer): UNIQUE PAIR — Reads the resume and generates the 5-10 most likely interview questions a hiring manager would ask based on its content. Identifies gaps, inconsistencies, and curiosity points that will become interview questions.
- Breaker (Interview Coach): Evaluates whether the resume sets up favorable interview conversations. Flags claims that will be hard to defend, experience that invites tough follow-ups, and missing context that forces awkward explanations.

**First-Pass Filtering: Recruiter Screener / Candidate Advocate**
- Builder (Recruiter Screener): Simulates the 6-second scan. What jumps out? What's the instant "yes pile" or "no pile" signal? Evaluates against high-volume screening heuristics — title match, company recognition, years of experience, location.
- Breaker (Candidate Advocate): Argues for the candidate when surface-level screening would reject them. Identifies buried strengths, non-obvious qualifications, and framing improvements that survive the 6-second filter.

**Career Positioning: Career Coach / Reality Checker**
- Builder (Career Coach): Helps position the candidate's story for maximum impact. Reframes experience, identifies transferable skills, crafts narrative bridges between past and target roles. Especially active for career changers.
- Breaker (Reality Checker): Tests whether the positioning is credible or aspirational fiction. Asks "would a hiring manager actually buy this bridge?" Flags overreach, missing proof points, and credibility gaps in the career narrative.

**Domain Fit: Industry Specialist / Generalist Framer**
- Builder (Industry Specialist): Evaluates domain-specific expectations — what a tech resume must include vs. a finance resume vs. healthcare. Flags missing industry signals (certifications, tools, terminology, portfolio expectations).
- Breaker (Generalist Framer): Argues that transferable framing may serve the candidate better than deep specialization signaling. Catches over-niching that limits options, and suggests broader positioning when the candidate's target is wide.

---

## Subset Commands

### Career-Change Context

| Command | Effect | BB Pair Priority | Research Focus |
|---------|--------|------------------|----------------|
| `career-change` | Full career transition mode | Career Coach/Reality Checker + Recruiter Screener/Candidate Advocate elevated to primary | Transferable skills frameworks, career pivot success stories, bridge positioning |
| `gap-explain` | Employment gap framing | Interview Coach + Recruiter Screener elevated | Gap explanation best practices, current hiring manager attitudes toward gaps |
| `promotion-push` | Internal/external advancement | Tech Hiring Manager + Industry Specialist elevated | Scope escalation language, leadership signal, progression narrative |
| `entry-level` | Early career / new grad | Recruiter Screener + Career Coach elevated | Education-to-experience bridging, project framing, internship positioning |
| `executive` | Director+ level positioning | Tech Hiring Manager + Industry Specialist elevated | Executive resume conventions, board-level language, P&L / org-scope framing |

### Usage

```
"TEMPT this, career-change"
"TEMPT this resume, gap-explain"
"TEMPT this, promotion-push"
```

Multiple subset commands can be combined:
```
"TEMPT this, career-change, gap-explain"
```

---

## Anchoring Instructions

### Search Query Modifications

- **Always include target role/industry** when provided by the Prompter
- **Append current year** to all resume best practice searches
- **Include ATS system name** if the target company's ATS is known
- **Add "hiring manager perspective"** to balance ATS-only advice
- **Cross-reference resume advice** with at least one hiring-manager-sourced opinion

### Resume-Specific Anchoring

When a resume document is provided:

1. **Read the full resume** via `view` tool — tag all claims as [CONTEXT]
2. **Extract target role** (from resume objective, Prompter statement, or infer from experience)
3. **Search current job postings** for that role to establish keyword baseline
4. **Search ATS compatibility** guidance for the resume's format
5. **Search industry-specific** resume expectations if domain is identifiable

### Verification Requirements

- Verify ATS advice against current ATS documentation, not generic tips
- Check claimed "best practices" against multiple authoritative sources
- Cross-reference keyword recommendations with actual job postings
- Note when advice is format-dependent (PDF vs DOCX vs plain text)

### Domain-Specific Flags

| Flag | Condition |
|------|-----------|
| ⚠️ CAREER CHANGE | Resume targets a different field than work history |
| ⚠️ EMPLOYMENT GAP | Gap > 6 months detected |
| ⚠️ OVER-QUALIFIED | Experience level significantly exceeds target role |
| ⚠️ UNDER-QUALIFIED | Experience level significantly below target role signals |
| ⚠️ ATS RISK | Format contains tables, columns, graphics, or non-standard sections |
| ⚠️ NO TARGET ROLE | No target role specified — advice will be generic |
| ⚠️ STALE RESUME | Resume dates suggest it hasn't been updated recently |
| ⚠️ INDUSTRY MISMATCH | Resume conventions don't match target industry norms |

---

## Output Format

### Resume-Specific TEMPT Output

In addition to the standard TEMPT prose summary, Resume Review outputs include:

```
## TEMPT Resume Review: [Candidate's Target Role]

**Overall Verdict:** [Strong Candidate / Needs Work / Major Revision Required]
**ATS Estimated Compatibility:** [High / Medium / Low] — [reason]
**6-Second Scan Result:** [Pass / Borderline / Fail] — [what stands out, what's missing]

**Winner:** [Builder/Breaker/Synthesis] | **Strength:** [Strong/Moderate/Contested]
**Sources:** X [SEARCH], Y [CONTEXT], Z [MODEL]

**Top 3 Strengths:**
1. [Strength] [SOURCE TAG]
2. [Strength] [SOURCE TAG]
3. [Strength] [SOURCE TAG]

**Top 3 Improvements (Priority Order):**
1. [Improvement] [SOURCE TAG] — [specific fix]
2. [Improvement] [SOURCE TAG] — [specific fix]
3. [Improvement] [SOURCE TAG] — [specific fix]

**Likely Interview Questions (from Simulated Interviewer):**
1. [Question] — triggered by [resume element]
2. [Question] — triggered by [resume element]
3. [Question] — triggered by [resume element]

**Career-Change Assessment** (if applicable):
- Bridge credibility: [Strong / Moderate / Weak]
- Missing proof points: [list]
- Recommended positioning: [summary]

---
💬 Say "show debate" to see the full structured BB transcript.
💬 Say "rewrite [section]" for a suggested revision of a specific resume section.
💬 Say "mock interview" for expanded interview simulation based on this resume.
```

---

## Conflict Behavior

| Conflict | Resolution |
|----------|------------|
| Freshness | This profile wins over profiles with longer thresholds |
| Sources | Hiring manager sources trump generic career advice |
| BB Pairs | Additive — all 7 pairs run by default |
| ATS vs Human | Neither auto-wins — tension is the point; flag when irreconcilable |

### Special Conflict: ATS Optimizer vs Human Readability

This is the most common irreconcilable tension in resume review. When ATS Optimizer and Human Readability Advocate deadlock:

1. **Present both versions** if the fix is section-specific (e.g., keyword-stuffed skills section vs. clean one)
2. **Default to ATS** if the resume is unlikely to reach a human without passing ATS first
3. **Default to Human** if the candidate is applying through referral, networking, or direct contact
4. **Flag for Prompter** if application method is unknown

---

## Example Activations

**Example 1: Standard Resume Review**
```
Query: "TEMPT this resume for a Senior Software Engineer role"
Detection: Tier 1 — resume, role
BB Pairs: All 7 (default)
Flags: None (pending resume review)
Research: Current SWE job postings, ATS best practices 2026, tech resume trends
```

**Example 2: Career Change**
```
Query: "TEMPT this resume, career-change" [teacher → UX designer]
Detection: Tier 1 — resume, career change
Subset: career-change (Career Coach/Reality Checker + Recruiter Screener/Candidate Advocate elevated)
Flags: ⚠️ CAREER CHANGE, ⚠️ INDUSTRY MISMATCH
Research: Teacher-to-UX transition stories, transferable skills frameworks, UX portfolio expectations
```

**Example 3: Gap Explanation**
```
Query: "TEMPT this resume, gap-explain" [18-month gap]
Detection: Tier 1 — resume
Subset: gap-explain (Interview Coach + Recruiter Screener elevated)
Flags: ⚠️ EMPLOYMENT GAP
Research: Current hiring manager attitudes toward gaps (post-COVID norms), gap framing best practices 2026
```

**Example 4: Cross-Profile**
```
Query: "TEMPT this resume for a cybersecurity analyst role"
Detection: Resume Review (Tier 1) + AI Cybersecurity (Tier 2 — confirm)
BB Pairs: Resume Review (7) + AI Cybersecurity domain pairs
Research: Cybersecurity hiring requirements, certification expectations (CISSP, CEH, CompTIA), security resume conventions
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 02-05-2026 | Initial profile — 7 BB pairs, career-change subset commands, weeks freshness, resume-specific output format |
