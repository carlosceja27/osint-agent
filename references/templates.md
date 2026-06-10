# OSINT Templates

Copy the relevant template, fill placeholders, and delete unused rows; templates implement the workflow defined in SKILL.md.

## Quick intake (low-risk self-audit)

Use this for rapid scoping when the user is auditing their own data.

Subject: {subject} | Consent Confirmed: [ ]
Identifiers in scope: {identifiers}
Sources allowed/excluded: {allowed_sources} / {excluded_sources}
Output depth wanted: {depth}
Output format: {HTML report (suggest first; use `report-template.html`) | Markdown document} | Save to: {user-confirmed private path, never the skill directory}

Note: Escalate to full intake if the subject is not the user, risk factors exist, or mode is journalism.

## Full intake form

Use this when a comprehensive scope must be established before any collection begins.

### A. Mode and authority
Mode: [ ]
Authority/Justification: [ ]
Constraints (legal/safety/org): [ ]

### B. Requirement and scope
Question to answer: [ ]
Decision/Report supported: [ ]
Geography/Jurisdiction: [ ]
Timeframe: [ ]
Allowed source categories: [ ]
Excluded source categories: [ ]
Languages: [ ]
Output depth: [ ]
Output format (suggest HTML first; `report-template.html`): [ ]
Save location (private path, never the skill directory): [ ]

### C. Subject identifiers
**For a person:**
Full name and variants: [ ]
Approximate age/birth year: [ ]
Current/prior region/city: [ ]
Usernames/domains/affiliations: [ ]
Emails/phones (if required): [ ]

**For an entity:**
Legal name and aliases: [ ]
Jurisdiction of registration: [ ]
Officers/addresses/domains/filings/etc: [ ]

### D. Safety and minimization
Common-name collisions/ambiguity: [ ]
Must-avoid categories (e.g., family, medical): [ ]
Endangerment risks: [ ]
Redaction by default: [ ]

## Search and verification plan skeleton

Use this to present a structured methodology for user approval.

1. Scope summary: [Mode, purpose, subject/entity, geography, timeframe, sources allowed, sources excluded]
2. Collection requirements: [Questions, EEIs, stop conditions]
3. Source hierarchy: [Primary, secondary, aggregators, archives, tool-derived, vendor context]
4. Identity-resolution strategy: [Matching signals, collision handling, labeling logic]
5. Modules to run:
   - Module: {module_name} | Goal: {goal} | Sources/Tools: {sources} | Queries: {queries} | Evidence: {evidence} | Verification: {controls} | Risks: {risks} | Stop conditions: {stop_conditions}
6. Evidence handling: [Logging plan, storage types, minimization/redaction]
7. Safety notes: [OPSEC, graphic-content precautions, legal/ethical caveats]

Do you approve this OSINT plan as written? Anything to add, remove, narrow, or re-prioritize before collection begins?

## Evidence log

Use this table to record every piece of data found during the investigation.

| Finding ID | Requirement / EEI | Source name | Source tier | URL | Archive URL | Accessed | Query/path | What it shows | Identity match | Source reliability | Information credibility | Confidence | Relevance | Sensitivity | Verification steps | Limitations |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F-001 | {requirement} | {source_name} | {tier} | {url} | {archive_url} | {date_timezone} | {query} | {fact} | {match_logic} | {A-F} | {1-6} | {confidence} | {relevance} | {sensitivity} | {steps} | {limitations} |

CSV header for spreadsheet use:

```
Finding ID,Requirement / EEI,Source name,Source tier,URL,Archive URL,Accessed,Query/path,What it shows,Identity match,Source reliability,Information credibility,Confidence,Relevance,Sensitivity,Verification steps,Limitations
```

## Single-finding entry

Use this for logging individual findings in text-heavy or chat-based environments.

Finding ID: {id}
Requirement / EEI: {requirement}
Source name: {source_name}
Source tier: {tier}
URL: {url}
Archive URL: {archive_url}
Accessed: {date_timezone}
Query/path: {query}
What it shows: {fact}
Identity match: {match_logic}
Source reliability: {A-F}
Information credibility: {1-6}
Confidence: {confidence}
Relevance: {relevance}
Sensitivity: {sensitivity}
Verification steps: {steps}
Limitations: {limitations}

## Sourced-edge table (relationship mapping)

Use this to map connections between subjects and entities.

Edge ID | From | To | Relationship type | Source URL | Source tier | Matching criteria | Confidence | Accessed | Caveats
---|---|---|---|---|---|---|---|---|---
E-001 | {subject_a} | {subject_b} | {type} | {url} | {tier} | {criteria} | {confidence} | {date} | {caveat}

WARNING: Avoid guilt by association — a shared address, shared registered agent, or co-appearance is not proof of control, intent, or wrongdoing. Edges describe sourced connections only.

## Timeline table

Use this to organize events chronologically.

Date/time (with timezone) | Event | Source | Confidence | Notes
---|---|---|---|---
{timestamp} | {event_description} | {source} | {confidence} | {notes}

## Self-audit report skeleton

Use this structure for personal privacy and exposure audits. For HTML output, fill `report-template.html` instead — same sections, styled and self-contained.

1. Executive summary: [High-level overview of findings]
2. Scope and sources checked: [Methodology and sites searched]
3. Top exposure risks and quick wins: [Immediate threats and easy fixes]
4. Identity and contact exposure: [Names, emails, phone numbers]
5. Social media/public profile exposure: [Handles and platform presence]
6. Employment/education/professional exposure: [Work and school history]
7. Public records findings: [Registries and official documents]
8. Data broker / CAI findings: [Commercial data hits]
9. Breach exposure findings from legitimate notification services: [Leaked credential info]
10. Risk rating per finding: [High/Medium/Low based on impact]
11. Remediation and opt-out steps: [Actionable removal instructions]
12. Monitoring plan: [Ongoing checking strategy]
13. What was not found: [Gaps in the search]
14. Limitations and recheck schedule: [Constraints and next review date]

**Risk Ratings:**
- High: enables account takeover, stalking/doxxing, identity theft, physical risk, or serious reputational/legal harm.
- Medium: reveals sensitive associations, stale but meaningful personal history, or aggregated exposure.
- Low: ordinary public presence or low-impact exposure.

## Journalism / public-interest report skeleton

Use this structure for investigative reporting and public interest inquiries.

1. Executive summary: [Key takeaways and core findings]
2. Public-interest question and scope: [The justification for the investigation]
3. Methodology and source hierarchy: [How information was gathered]
4. Key findings by editorial question: [Direct answers to research goals]
5. Evidence table: [Reference to detailed evidence log]
6. Timeline: [Chronology of relevant events]
7. Relationship map / sourced edge table: [Network analysis results]
8. Verification notes and confidence: [Corroboration details]
9. What was not found: [Unanswered questions or missing data]
10. Contradictions and unresolved questions: [Conflicting information]
11. Publication readiness notes: [Editorial status]
12. Right-of-reply / source-contact notes: [Journalist tasks for external contact]
13. Redactions and minimize-harm notes: [Safety and privacy measures taken]
14. Limitations: [Methodological constraints]

## Concise answer template

Use this when providing a quick response to a narrow question.

Short answer: {answer}
Sources checked or required: {sources}
Confidence + reason: {confidence_reason}
Caveats: {caveats}
Recommended next verification step: {next_step}

## Pre-delivery checklist

Use this final check before delivering any OSINT output.

- [ ] The mode, purpose, and scope were approved.
- [ ] The work stayed strictly within lawful OSINT.
- [ ] No HUMINT, social engineering, unauthorized access, exploit, credential-abuse, raw-breach, stalking, or doxxing steps were included.
- [ ] Every factual finding has a source or is labeled as inference/unknown.
- [ ] Important claims were corroborated or confidence-limited.
- [ ] Identity-resolution criteria are documented.
- [ ] Sensitive data is minimized or redacted.
- [ ] Source tier, query/path, URL, access date, and verification steps are logged.
- [ ] AI assistance is not cited as evidence.
- [ ] Media/geolocation claims are not authenticated by the LLM alone.
- [ ] The report includes confidence, limitations, and what was not found.
