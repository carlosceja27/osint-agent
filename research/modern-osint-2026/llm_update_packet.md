# LLM Update Packet for Existing OSINT Skill

Date: 2026-06-08

Purpose: Give an LLM concise, enforceable instructions for updating `skill.md` later. Do not execute the update until the user approves.

## Non-negotiable constraints

- Strictly OSINT.
- Do not add HUMINT, pretexting, elicitation, impersonation, social engineering, covert access, unauthorized access, exploit development, credential abuse, stalking, doxxing, or raw breached-data handling.
- Cyber/infrastructure OSINT must be public-source discovery and defensive exposure assessment only.
- LLMs are never sources; every factual claim must cite a source URL or be labeled synthesis/inference.

## Must preserve from existing skill

- Two modes: self-audit/privacy audit and journalism/public-interest investigation.
- Consent/public-interest intake.
- User review gate before execution.
- Evidence logging table.
- Report structures for self-audit and journalism.
- Data-broker opt-out/remediation content.
- Curated-service-only breach/dark-web rule.

## Must add

1. OSINT fundamentals section:
   - Requirements definition
   - Lawful boundary
   - Proportionality/minimization
   - Source hierarchy
   - Identity resolution
   - Collection logging
   - Verification
   - Analytical uncertainty
   - Archiving
   - Responsible reporting

2. Source tiering:
   - Primary official/original
   - Secondary professional
   - Aggregator/index
   - Archive/cache
   - Tool-derived lead
   - Vendor/business-published context

3. Confidence model:
   - Confirmed
   - Likely
   - Possible
   - Disputed
   - Not found, with caveat that absence of evidence is not evidence of absence

4. AI-assisted OSINT controls:
   - Allowed: planning, query expansion, summarization, translation drafts, entity extraction, checklist generation.
   - Required: source citations, extraction logs, human/primary-source validation.
   - Prohibited: inventing facts, inferring identity/guilt/intent without sources, processing unnecessary sensitive data.

5. Modern verification checklist:
   - Original source/provenance
   - Date/time
   - Location/geolocation
   - Author/account authenticity
   - Content integrity/manipulation
   - Independent corroboration
   - Archive/screenshot status

6. Network-map edge table:
   - Edge source URL
   - Source tier
   - Relationship type
   - Matching criteria
   - Confidence
   - Date accessed

## Source anchors to use

- ODNI IC OSINT Strategy 2024–2026: https://www.dni.gov/index.php/newsroom/reports-publications/reports-publications-2024/3897-the-ic-osint-strategy-2024-2026
- Berkeley Protocol: https://www.ohchr.org/en/publications/policy-and-methodological-publications/berkeley-protocol-digital-open-source-investigations
- College of Policing open-source internet research: https://www.college.police.uk/app/investigation/investigative-strategies/internet-intelligence-and-investigations/open-source-internet-research
- EDPB social-media guidance: https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-82020-targeting-social-media-users_en
- ICO UK GDPR resources: https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/
- Verification Handbook: https://verificationhandbook.com/
- Bellingcat Online Investigation Toolkit: https://bellingcat.gitbook.io/toolkit
- GIJN Online Research Tools: https://gijn.org/resource/online-research-tools/
- Pastor-Galindo et al. OSINT survey: https://ieeexplore.ieee.org/document/9139412
- Wardle/Derakhshan information disorder: https://rm.coe.int/information-disorder-report-november-2017/1680764666

## Acceptance checklist for updated skill

- The updated skill starts by asking mode, consent/public-interest, scope, and exclusions.
- It then generates a collection plan with source tiers and stop conditions.
- It requires approval before execution.
- It logs evidence with query/path, URL, access date, archive/screenshot, source tier, confidence, relevance, and matching criteria.
- It requires verification before reporting.
- It includes privacy minimization and redaction rules.
- It includes AI-assistance limits.
- It excludes prohibited adjacent practices.
- It has clear “what was not found” and limitations sections.
