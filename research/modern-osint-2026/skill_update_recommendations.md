# Skill Update Recommendations

Date: 2026-06-08

Target skill inspected: `skill.md`

Do not directly replace the skill yet. These are patch-ready recommendations for a future update.

## What the current skill already does well

- Defines self-audit and journalism/public-interest modes.
- Requires intake, planning, user approval, execution, reporting, and monitoring phases.
- Includes strong prohibitions against social engineering, password-protected access, raw breach dumps, harassment, and direct dark-web browsing.
- Provides broad modules: web, social, professional, news, public records, data brokers, images, campaign finance, nonprofit records, infrastructure, breaches, archives, geospatial, relationship mapping, and international records.
- Includes evidence logging fields and report structures.

## Highest-impact improvements

### 1. Add “OSINT fundamentals before modules”

Insert after Ethics/Legal Boundaries:

```markdown
## OSINT Fundamentals Before Searching

Before selecting modules, define:
1. Requirement/question: What decision or report will this OSINT support?
2. Lawful basis and authorization: Why is this collection allowed and appropriate?
3. Scope: subject, geography, timeframe, source categories, exclusions, and stop conditions.
4. Source hierarchy: prefer primary/original/official sources; use aggregators only as leads.
5. Identity-resolution criteria: what signals prove a record belongs to the subject?
6. Evidence logging: query/path, URL, access date, archive/screenshot, source tier, confidence, relevance.
7. Verification plan: how provenance, authenticity, date/time, location, and corroboration will be checked.
8. Minimization: collect and report only what is necessary for the approved purpose.
```

### 2. Add source-tier labels

For every module, require one of:
- Primary official/original source
- Secondary professional source
- Aggregator/index
- Archive/cache
- Tool-derived lead
- Vendor/business-published context

### 3. Upgrade confidence labels

Current labels are Confirmed/Likely/Possible. Add:
- Disputed: credible sources conflict.
- Not found: searched defined sources and found no matching record; never treat as proof of absence.

Require matching criteria:

```markdown
Confidence requires a reason. Example: “Likely — exact full name and city match, but no date-of-birth or official ID.”
```

### 4. Add AI-assisted OSINT controls

```markdown
## AI-Assisted OSINT Rules

LLMs may help generate search plans, query variants, summaries, entity extraction, translation drafts, and verification checklists.
LLMs are never evidence. Any factual claim from an LLM must be traced to a source URL or marked as unsupported synthesis.
Do not paste sensitive unnecessary personal data into third-party tools.
Do not let an LLM infer guilt, intent, identity, or relationships without cited evidence.
```

### 5. Strengthen cyber/infrastructure OSINT boundary

```markdown
Cyber/infrastructure OSINT is limited to public-source discovery and defensive exposure assessment: WHOIS/RDAP, DNS, certificate transparency, public search engines, official advisories, and public threat reports. Do not exploit, bypass, brute-force, authenticate without permission, or provide instructions that enable unauthorized access.
```

### 6. Add “sourced edge” requirement for network maps

Every relationship-map edge should have:
- Source URL
- Source tier
- Relationship type
- Matching criteria
- Confidence
- Date accessed

### 7. Add pre-delivery claim audit

```markdown
Before final report delivery:
- Every factual claim has a source or is labeled inference.
- Every sensitive detail has a relevance justification or is redacted.
- Every uncertain match has confidence and matching criteria.
- The report includes “what was not found” and “limitations.”
- No HUMINT, social engineering, unauthorized access, exploit, or raw breach-dump steps are included.
```

## Deprecated or caution items

- Avoid treating people-search/data-broker outputs as facts. They are lead generators requiring primary-source verification.
- Avoid “dark web intelligence” language unless using curated, lawful breach/threat intelligence providers and reporting only high-level exposure findings.
- Avoid implying Yandex/face search or reverse-image search confirms identity by itself; it provides leads requiring corroboration.
- Avoid “all major platforms checked” claims unless the exact platform list and access limitations are logged.

## New source anchors to add to the skill

- Berkeley Protocol: https://www.ohchr.org/en/publications/policy-and-methodological-publications/berkeley-protocol-digital-open-source-investigations
- IC OSINT Strategy 2024–2026: https://www.dni.gov/index.php/newsroom/reports-publications/reports-publications-2024/3897-the-ic-osint-strategy-2024-2026
- College of Policing open-source internet research: https://www.college.police.uk/app/investigation/investigative-strategies/internet-intelligence-and-investigations/open-source-internet-research
- EDPB social media targeting guidance: https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-82020-targeting-social-media-users_en
- Verification Handbook: https://verificationhandbook.com/
- Bellingcat Online Investigation Toolkit: https://bellingcat.gitbook.io/toolkit
- GIJN Online Research Tools: https://gijn.org/resource/online-research-tools/
