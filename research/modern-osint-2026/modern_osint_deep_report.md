# Modern OSINT Practices and Fundamentals Research Report

Date: 2026-06-08

Package purpose: provide source-grounded research artifacts that an LLM can use to improve the existing OSINT skill at `skill.md`.

Scope: strictly OSINT. This report covers lawful and ethical use of publicly available or legitimately accessible information; source discovery; verification; evidence handling; public records; social/web/platform research; imagery/video/geolocation verification; archival research; public cyber/infrastructure exposure discovery; and AI-assisted analysis controls. It intentionally excludes HUMINT tradecraft, social engineering, covert access, credential theft, raw breach-dump handling, doxxing/stalking playbooks, and offensive exploitation.

## Executive summary

Modern OSINT is no longer just “search the web.” Public guidance and mature practice converge around six ideas:

1. OSINT is a disciplined intelligence/research workflow, not a tool list. The US Intelligence Community’s public OSINT strategy treats OSINT as an intelligence discipline requiring governance, discovery, tradecraft, and integration with other analysis ([GOV-01: Intelligence Community OSINT Strategy 2024–2026](https://www.dni.gov/index.php/newsroom/reports-publications/reports-publications-2024/3897-the-ic-osint-strategy-2024-2026)). The Berkeley Protocol similarly frames digital open-source investigation as a methodical process with planning, preservation, verification, analysis, and presentation ([GOV-03: Berkeley Protocol on Digital Open Source Investigations](https://www.ohchr.org/en/publications/policy-and-methodological-publications/berkeley-protocol-digital-open-source-investigations)).

2. The key fundamentals are scoping, legality, proportionality, source hierarchy, identity resolution, collection logging, preservation, verification, analysis, minimization, and transparent reporting. The existing skill already contains many search modules; it should add a stronger fundamentals layer that explains why each module exists and what quality controls must be applied.

3. Verification is the center of modern OSINT. Mature practice asks: Who created the source? When? Where? Is the content original? Has it been altered? Can it be corroborated independently? Verification handbooks and the Berkeley Protocol stress provenance, preservation, source assessment, and chain of custody ([PRO-04: The Verification Handbook](https://verificationhandbook.com/), [GOV-03: Berkeley Protocol on Digital Open Source Investigations](https://www.ohchr.org/en/publications/policy-and-methodological-publications/berkeley-protocol-digital-open-source-investigations)).

4. Modern OSINT must treat privacy, safety, and data-protection obligations as operational constraints, not afterthoughts. Social media and personal data collection can trigger legal/ethical duties even when the data is public. EU/UK data-protection guidance is especially important for minimization, purpose limitation, and documentation ([GOV-09: Guidelines 8/2020 on the targeting of social media users](https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-82020-targeting-social-media-users_en), [GOV-10: Guide to the UK GDPR](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/)).

5. Automation and AI are useful but dangerous without scoping and validation. Tools such as SpiderFoot, Maltego, Shodan, certificate-transparency search, and vendor threat intelligence resources can speed discovery, but they increase false positives, overcollection, and context collapse unless every hit is tied back to source reliability and identity-resolution criteria ([PRO-09: Maltego blog and resources](https://www.maltego.com/blog/), [PRO-10: Shodan Help Center](https://help.shodan.io/), [PRO-11: SpiderFoot documentation](https://github.com/smicallef/spiderfoot)).

6. Business-published OSINT material is valuable when it teaches practice, but vendor claims should not become the authority. Use business/vendor publications for examples of methods, tool categories, and operational patterns; use government, academic, and professional verification sources for normative guidance.

## Working definition of OSINT

OSINT is the planned collection, processing, evaluation, analysis, preservation, and reporting of information from openly available or lawfully accessible sources to answer a defined intelligence, investigative, defensive, journalistic, compliance, or self-audit question.

Important boundaries:

- Openly available does not mean consequence-free. Public personal data may still require minimization, justification, and careful handling ([GOV-09: Guidelines 8/2020 on the targeting of social media users](https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-82020-targeting-social-media-users_en), [GOV-10: Guide to the UK GDPR](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/)).
- OSINT is not HUMINT. Contacting people, eliciting information, impersonation, pretexting, or manipulation belongs outside this skill unless mentioned only as a boundary.
- OSINT is not unauthorized access. Querying public DNS, certificate transparency, EDGAR, Companies House, or a public web page is in scope; exploiting a vulnerable service is not.
- OSINT is not raw breached-data handling. Breach notification services such as Have I Been Pwned can be in scope for defensive/self-audit use; downloading stolen datasets is not ([PRO-16: Have I Been Pwned](https://haveibeenpwned.com/)).

## Fundamentals inventory narrative

### 1. Requirements and scope

Every OSINT task should start with a precise question, authorized purpose, subject, geography, source categories, exclusions, and stopping conditions. The UK College of Policing guidance emphasizes planning, proportionality, and recordkeeping for online research ([GOV-05: Open-source internet research](https://www.college.police.uk/app/investigation/investigative-strategies/internet-intelligence-and-investigations/open-source-internet-research)). The existing skill asks intake questions, but it should more explicitly convert answers into collection requirements and stop conditions.

### 2. Legality, ethics, and proportionality

Modern OSINT practice must document why collection is necessary and proportionate. This is especially important for private individuals, minors, sensitive records, and social platforms. EU/UK privacy guidance adds purpose limitation, data minimization, and lawful-basis concepts that should inform the skill even when a task is outside Europe ([GOV-09: Guidelines 8/2020 on the targeting of social media users](https://www.edpb.europa.eu/our-work-tools/our-documents/guidelines/guidelines-82020-targeting-social-media-users_en), [GOV-10: Guide to the UK GDPR](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/)).

### 3. Source hierarchy

Primary sources are preferred: court portals, corporate registries, government filings, official sanctions lists, official PDFs, archived originals. Aggregators and people-search sites can help discovery but must not be final authority. Examples: EDGAR for US public-company filings ([GOV-12: SEC EDGAR Full Text Search](https://www.sec.gov/edgar/search/)), Companies House for UK companies ([GOV-11: Companies House Find and update company information](https://find-and-update.company-information.service.gov.uk/)), Canada Business Registries ([GOV-16: Canada Business Registries search](https://beta.canadasbusinessregistries.ca/search)), Australian ABN Lookup ([GOV-17: Australian Business Register ABN Lookup](https://abr.business.gov.au/)), and New Zealand Companies Register ([GOV-18: New Zealand Companies Register](https://companies-register.companiesoffice.govt.nz/)).

### 4. Identity resolution

Names collide. The skill should require positive matching criteria: exact identifiers, date/location consistency, associated entities, official records, historical continuity, and independent corroboration. It should label ambiguous hits as possible, not verified. For sanctions, offshore leaks, and corporate records, false positives are common; ICIJ and OCCRP-style data require careful context ([PRO-06: OCCRP Aleph](https://aleph.occrp.org/), [PRO-07: ICIJ Offshore Leaks Database](https://offshoreleaks.icij.org/)).

### 5. Collection logging and reproducibility

Every finding should record query, source, URL, access date, archive/screenshot status, matching criteria, confidence, and relevance. The Berkeley Protocol provides the strongest public model for preservation and chain-of-custody thinking ([GOV-03: Berkeley Protocol on Digital Open Source Investigations](https://www.ohchr.org/en/publications/policy-and-methodological-publications/berkeley-protocol-digital-open-source-investigations)). Hunchly-style capture resources also illustrate browser-based evidence logging practices, with vendor caveats ([PRO-08: Hunchly: OSINT workflow and capture tool resources](https://hunch.ly/)).

### 6. Verification and corroboration

Verification is not a single tool action. It is a structured process: establish provenance, original source, date/time, location, author/account, content integrity, and corroborating records. The Verification Handbook and First Draft resources remain useful for claim, image, video, and social-content checks ([PRO-04: The Verification Handbook](https://verificationhandbook.com/), [PRO-05: First Draft Essential Guide to Verifying Online Information](https://firstdraftnews.org/long-form-article/essential-guide-to-verifying-online-information/)).

### 7. Bias, uncertainty, and analytical discipline

Academic misinformation literature shows that repetition, social popularity, and platform virality do not equal truth ([ACAD-05: The spread of true and false news online](https://doi.org/10.1126/science.aap9559), [ACAD-06: Misinformation and Its Correction: Continued Influence and Successful Debiasing](https://doi.org/10.1177/1529100612451018)). Analysts should separate collection notes from conclusions, mark confidence levels, track alternative explanations, and maintain a “what was not found” section.

### 8. Privacy, safety, and minimization

A modern OSINT skill should collect the least sensitive information needed to answer the question, redact unnecessary home/contact/family details, and pause when unexpected sensitive material appears. This is already partially present in the existing skill; it should become an acceptance criterion for every module.

### 9. Archiving and change control

Online evidence changes or disappears. Use the Wayback Machine or other archiving services where allowed and log snapshot dates ([PRO-15: Internet Archive Wayback Machine](https://web.archive.org/)). Archive only what is lawful and necessary; do not archive sensitive private details without a strong reason.

### 10. Reporting and actionability

Reports should separate facts, inferences, unknowns, and recommendations. For self-audits, include risk and remediation. For journalism/public-interest work, include publication readiness, right-of-reply needs, and items requiring non-OSINT follow-up without conducting that follow-up inside the OSINT skill.

## Modern OSINT practice areas

### Search and discovery

Search remains foundational, but modern practice uses repeatable query patterns, alternative search engines, language/geography variants, cached/archived pages, filetype searches, and platform-specific operators. The skill already includes search modules; it should add structured search logs and anti-overcollection stop rules.

### Public-record and entity research

Entity OSINT should privilege official registries. Use EDGAR, Companies House, Canada Business Registries, ABN Lookup, New Zealand Companies Register, sanctions lists, and court/regulatory portals before aggregators ([GOV-11: Companies House Find and update company information](https://find-and-update.company-information.service.gov.uk/), [GOV-12: SEC EDGAR Full Text Search](https://www.sec.gov/edgar/search/), [GOV-14: OFAC Sanctions List Search](https://sanctionssearch.ofac.treas.gov/), [GOV-15: EU Sanctions Map](https://www.sanctionsmap.eu/), [GOV-16: Canada Business Registries search](https://beta.canadasbusinessregistries.ca/search), [GOV-17: Australian Business Register ABN Lookup](https://abr.business.gov.au/), [GOV-18: New Zealand Companies Register](https://companies-register.companiesoffice.govt.nz/)).

### Social platform research

Modern social OSINT must handle platform fragmentation, API restrictions, deleted content, synthetic media, reposts, and impersonation. Source reliability should be based on account provenance, historical consistency, cross-platform continuity, and independent corroboration rather than follower count.

### Image/video/geolocation verification

Use reverse image search, frame extraction, metadata inspection, landmarks, shadows, weather, maps, satellite imagery, and archive checks. The Berkeley Protocol and verification handbooks provide the best public frameworks for preserving and validating digital evidence ([GOV-03: Berkeley Protocol on Digital Open Source Investigations](https://www.ohchr.org/en/publications/policy-and-methodological-publications/berkeley-protocol-digital-open-source-investigations), [PRO-04: The Verification Handbook](https://verificationhandbook.com/)).

### Cyber/public infrastructure OSINT

Lawful cyber OSINT includes public WHOIS/RDAP, DNS, certificate transparency, exposed-service search, public vulnerability advisories, vendor reports, and official threat landscapes. It must stop at discovery and defensive risk assessment. Shodan help docs, crt.sh, ENISA, and vendor resources are relevant, but exploit instructions are not ([PRO-10: Shodan Help Center](https://help.shodan.io/), [PRO-14: crt.sh Certificate Search](https://crt.sh/), [GOV-08: ENISA Threat Landscape 2024](https://www.enisa.europa.eu/publications/enisa-threat-landscape-2024)).

### Misinformation/disinformation verification

Use precise labels. Wardle and Derakhshan’s information-disorder framework distinguishes misinformation, disinformation, and malinformation ([ACAD-03: Information Disorder: Toward an interdisciplinary framework for research and policymaking](https://rm.coe.int/information-disorder-report-november-2017/1680764666)). EUvsDisinfo’s methodology is useful for documenting why a case is classified as disinformation, while academic literature warns against relying on virality as credibility ([GOV-19: EUvsDisinfo methodology](https://euvsdisinfo.eu/methodology/), [ACAD-05: The spread of true and false news online](https://doi.org/10.1126/science.aap9559)).

### Automation and link analysis

Automation is useful for broad discovery, link analysis, and monitoring, but every automated result should carry source, query, timestamp, confidence, and human validation status. Tools like Maltego and SpiderFoot illustrate the pattern; the skill should emphasize validation gates rather than tool enthusiasm ([PRO-09: Maltego blog and resources](https://www.maltego.com/blog/), [PRO-11: SpiderFoot documentation](https://github.com/smicallef/spiderfoot)).

### AI-assisted OSINT

AI can summarize, cluster, translate, extract entities, draft query plans, and generate verification checklists. It should not be treated as a source. LLM outputs need citations, extraction logs, and independent verification. The skill should instruct the LLM to distinguish observed evidence from model inference and to cite primary sources for facts.

## Implications for the existing OSINT skill

The current skill is strong as a search-module cookbook. The research package recommends improving it in five ways:

1. Add a “Fundamentals Before Modules” section: requirements, legality, source hierarchy, identity resolution, evidence logging, verification, minimization, and reporting.
2. Add source-tier labels to every module: primary, secondary, aggregator, tool/vendor, archive, or derived source.
3. Add a uniform confidence model: confirmed, likely, possible, disputed, and not found; require matching criteria for each.
4. Add an AI-assisted OSINT section: allowed uses, prohibited uses, hallucination controls, citation requirements, and validation gates.
5. Add an LLM update checklist so future skill edits preserve safety boundaries and do not drift into HUMINT, social engineering, or offensive cyber.

## Limitations

This package uses public web sources and stable institutional pages. Some government and academic links may block automated checks, move PDFs, or require manual browser access. Vendor/professional sources are included for practice value, not as neutral authority. Academic search-route entries are included where a fast package benefits from future deeper literature expansion; they are clearly labeled as routes rather than single-source evidence.
