# OSINT Module Library

Run only modules selected in the approved plan; method first, tool second (every function has a manual fallback if a tool dies); primary sources beat aggregators; archive volatile evidence on capture; log every finding using the evidence-log template in `templates.md`.

### Module A — Baseline web footprint

Goal: discover general public mentions and public web presence.

Sources/tools:
- Google, Bing, DuckDuckGo, Brave Search, regional search engines where relevant.
- News search, site search, filetype search, archived pages.

Example queries:
- `"{name}" "{city}"`
- `"{name}" "{employer}"`
- `"{name}" filetype:pdf`
- `"{username}" -site:{known_platform}`
- `"{company}" "{officer}"`

Verification controls:
- Use SIFT: Stop, Investigate source, Find better coverage, Trace to original.
- Treat snippets as leads; open the source before logging.
- Archive high-value or volatile pages.

Stop when results become repetitive or irrelevant under the approved depth.

Evidence to capture: source, URL, archive URL, access date, exact query/navigation path, content summary, source tier, identity match criteria, confidence, relevance, and minimization/redaction notes.

### Module B — Social media and SOCMINT

Goal: identify public social profiles, posts, account history, and public signals relevant to the requirement.

Modern access reality:
- Many platform APIs and historical research tools are closed, paywalled, restricted, or rate-limited.
- Do not assume bulk scraping is allowed or reliable.
- Prioritize native public UI, platform search, archives, user-provided exports, licensed lawful sources, and archive-on-capture.

Sources/tools:
- LinkedIn, X, Instagram, Facebook, TikTok, YouTube, Reddit, Bluesky, Threads, Mastodon, forums, and platform-specific public search.
- Wayback Machine and archive services for public profile history where lawful.

Verification controls:
- Confirm account identity through multiple signals: username continuity, display name, bio, links, historical posts, profile photos, affiliations, external links, and independent sources.
- Do not rely on follower count or platform verification alone.
- Distinguish original posts from reposts, screenshots, mirrors, and commentary.
- Redact irrelevant personal contacts, relatives, home locations, and bystander data.

Stop when major relevant platforms and known handles have been checked or when access limits prevent reliable collection.

Evidence to capture: public profile URLs, handle continuity, display name, bio, links, historical posts/photos, affiliations, external links, platform verification status, cross-references, redacted bystander data, access date, and archive URL.

### Module C — Professional, academic, and portfolio presence

Goal: find public professional profiles, publications, code, talks, portfolios, and credentials.

Sources/tools:
- LinkedIn, personal sites, GitHub/GitLab/Bitbucket, npm/PyPI/crates, ORCID, Google Scholar, institutional profiles, conference pages, Medium/Substack, Behance/Dribbble.

Verification controls:
- Confirm with cross-links, official affiliations, email/domain consistency, publication metadata, commit history, or institutional pages.
- For code platforms, watch for exposed email addresses or secrets; do not amplify sensitive material unnecessarily.

Evidence to capture: platform/profile URL, credential/affiliation source, publication/code metadata, commit history or institutional page link, email/domain consistency notes, access date, and archive URL.

### Module D — News, media, and public statements

Goal: find press coverage, interviews, press releases, podcasts, public appearances, and attributed statements.

Sources/tools:
- Google News, publisher archives, local outlets, PR Newswire, Business Wire, GlobeNewswire, Listen Notes, event pages, transcripts where available.

Verification controls:
- Prefer original publisher pages and full transcripts over snippets.
- Capture date, outlet, author, headline, quoted statement, and context.
- Beware syndicated or copied articles that create false corroboration.

Evidence to capture: outlet name, URL, access date, author, headline, quoted statement, context, original vs syndicated status, transcript/archive links, and confidence level.

### Module E — Public records and official registries

Goal: verify records from primary official sources whenever possible.

Submodules:
- Courts: PACER, CourtListener, RECAP, state/county portals, official dockets.
- Corporate: SEC EDGAR, state Secretary of State, UK Companies House, Canada Business Registries, Australian Business Register / ASIC routes, New Zealand Companies Register, OpenCorporates as a lead, and GLEIF LEI lookup for legal-entity identifiers.
- Property: county assessor/recorder/tax portals where lawful and relevant.
- Licenses: state/provincial/national licensing boards, bars, medical boards, contractor boards, FAA/FCC equivalents where relevant.
- Campaign finance: FEC, OpenSecrets, FollowTheMoney, state election databases.
- Nonprofits: ProPublica Nonprofit Explorer, Candid/GuideStar, charity regulators.
- Sanctions/debarment: OFAC, EU Sanctions Map, UN sanctions, World Bank debarment, national lists.
- Regulatory: OSHA, EPA ECHO, FDA warning letters, Federal Register, state regulators, EU/UK regulators.

Verification controls:
- Record jurisdiction, case/filing/license number, date, status, parties, and disposition.
- Do not equate arrest with conviction, filing with finding, allegation with fact, or active entity with lawful conduct.
- Use aggregators only to locate primary records.
- For common names, require additional identifiers before attributing.

Evidence to capture: jurisdiction, registry name, case/filing/license number, date, status, parties/disposition, entity identifiers (e.g., LEI), cross-references, attribution caveats, and access date.

### Module F — Data brokers, people-search, and CAI

Goal: in self-audits, identify personal-data exposure and opt-out/remediation steps; in journalism, use only as leads that require primary verification.

CAI warning:
Commercially Available Information can reveal sensitive location, contact, relationship, and identity patterns. Treat it as high-risk personal data.

Sources/tools:
- TruePeopleSearch, Whitepages, Spokeo, BeenVerified, Intelius, PeopleFinders, FamilyTreeNow, That’s Them, Nuwber, Radaris, and other lawful broker/people-search sites.
- Paid deletion services may be mentioned for remediation, not endorsed.

Agent note: broker and people-search sites commonly block automated fetching with anti-bot measures. Do not attempt to bypass them — that is access-control evasion. Fall back to search-engine-indexed snippets as leads, ask the user to open specific listings manually, and log blocked sources as "not checked — access blocked" rather than claiming coverage.

Verification controls:
- Never treat broker data as confirmed fact.
- Do not publish home addresses, relatives, phone numbers, or exact locations unless directly necessary and legally/ethically justified.
- For self-audit, provide opt-out links, dates, status, recheck dates, and OPSEC tips — see `remediation.md` for the opt-out directory (including California DROP) and tracker template.

Evidence to capture: broker/service name, URL, access date, data fields exposed, opt-out links/status, recheck dates, OPSEC recommendations, and minimization notes.

### Module G — Images, video, and synthetic-media verification

Goal: identify, verify, and contextualize public images/video.

Sources/tools:
- Reverse image/video search: Google Lens, Bing Visual Search, Yandex where lawful, TinEye.
- Frame extraction, EXIF/metadata tools, InVID/WeVerify, FotoForensics, maps, Street View, satellite imagery.
- Provenance: Content Credentials / C2PA verification where available, SynthID or watermark checks where available.

Hard rule:
The LLM must never declare an image/video authentic or fake by itself. It may list indicators and verification steps only.

Verification controls:
- Four W’s: provenance, source, date, location.
- Check whether the item is original, reuploaded, cropped, edited, mirrored, AI-generated, or stripped of metadata.
- Use multiple signals; no detector or watermark is dispositive.
- Note that absence of provenance metadata proves nothing.

Evidence to capture: image/video URL, reverse search results (tools used), EXIF/metadata findings, provenance status, editing/AI indicators, geolocation/time clues, confidence level, and access date.

### Module H — Geospatial and chronolocation

Goal: verify locations and time clues from public images/video/maps.

Sources/tools:
- Google Maps/Earth, Street View, OpenStreetMap, Overpass Turbo, Sentinel Hub, NASA Worldview, Landsat/Sentinel, SunCalc, weather archives, public satellite imagery.

Verification controls:
- Match landmarks, terrain, road markings, architecture, language, signage, vegetation, shadows, weather, and historical imagery.
- Do not treat geolocation as proof of authenticity in the synthetic-media era.
- Report confidence and unresolved uncertainties.

Evidence to capture: location clues, matched landmarks/terrain/signage/weather/shadows, historical imagery comparison, confidence level, unresolved uncertainties, map/satellite source URLs, and access date.

### Module I — Domains, web infrastructure, and cyber OSINT

Goal: public-source discovery of domains, subdomains, technology, exposure, and historical web infrastructure for defensive or investigative context.

Allowed sources/tools:
- WHOIS/RDAP, ICANN Lookup, DNS records, SecurityTrails/ViewDNS, crt.sh certificate transparency, BuiltWith/Wappalyzer, Wayback Machine, Shodan/Censys public search, URLScan.io, DNSdumpster, public advisories and threat reports.

Boundaries:
- Discovery and defensive assessment only.
- No exploitation, brute forcing, credential attempts, bypass, intrusive scanning, or instructions enabling unauthorized access.

Verification controls:
- Log query, timestamp, source, and whether the result is current or historical.
- Confirm important findings across multiple public sources.
- Avoid exposing sensitive infrastructure details unless needed and responsible.

Evidence to capture: domain/subdomain, WHOIS/RDAP record, DNS records, technology stack, certificate transparency logs, infrastructure exposure notes, current vs historical status, cross-verified sources, and access date.

### Module J — Breach exposure and credential-risk checks

Goal: self-audit exposure through legitimate notification or curated services.

Allowed sources/tools:
- Have I Been Pwned, Firefox Monitor, official breach notifications, identity-monitoring services the user lawfully uses, curated threat-intelligence summaries.

Agent note: the Have I Been Pwned API requires a paid key — unauthenticated automated queries will fail. Without a user-provided key, ask the user to check their own addresses on the HIBP website (or paste the results in), and log those checks as "user-checked". Do not count a failed API call as "checked".

Boundaries:
- Do not search, download, process, or redistribute raw stolen datasets.
- Do not reveal passwords, hashes, or credential material.

Evidence to capture: email/phone checked, service used, breach name, date, exposed data types, remediation recommendation, and access date.

### Module K — Archives and deleted/changed content

Goal: recover historical public web content and preserve volatile evidence.

Sources/tools:
- Wayback Machine, archive.today/archive.ph, page caches where available, platform archives, user-provided saved pages, SingleFile browser extension for full-page capture, and Hunchly-class auto-capture tools with hashing for forensic-grade preservation. Note: hash saved copies (SHA-256) and keep an original plus a working copy.

Verification controls:
- Capture original URL, archive URL, snapshot date, what changed, and limitations.
- Do not archive or republish unnecessary sensitive personal data.

Evidence to capture: original URL, archive/snapshot URL, snapshot date, content changes noted, capture tool used, SHA-256 hash of saved copy, original vs working copy paths, and access date.

### Module L — Relationship and network mapping

Goal: map relationships among people, entities, addresses, filings, donations, events, and domains using public records.

Sources/tools:
- Official registries, corporate filings, nonprofit filings, campaign finance, sanctions lists, court records, OpenCorporates, OCCRP Aleph, ICIJ Offshore Leaks, Maltego or graph tools if available.

Sourced-edge rule:
Every graph edge must include source URL, source tier, relationship type, matching criteria, confidence, date accessed, and caveats.

Warnings:
- Avoid guilt by association.
- Shared address, shared agent, or co-appearance is not proof of control, intent, or wrongdoing.

Evidence to capture: node identifiers (person/entity/address), edge type, source URLs for each connection, matching criteria, confidence level, date accessed, caveats/association warnings, and minimization notes.

### Module M — International and cross-border records

Goal: search public international registries and databases when cross-border activity is relevant.

Sources/tools:
- UK Companies House, EU Sanctions Map, national company registries, Canada Business Registries, Australian and New Zealand registries, OCCRP Aleph, ICIJ Offshore Leaks, OpenSanctions, UN sanctions, World Bank debarment, Interpol public notices.

Verification controls:
- Expect transliteration/name variants and false positives.
- Verify against primary registries whenever possible.
- Record jurisdiction-specific caveats.

Evidence to capture: registry/jurisdiction name, record URL, access date, name variants/transliterations, cross-border links, primary verification status, jurisdiction-specific caveats, and confidence level.

### Module N — Misinformation, disinformation, and claim verification

Goal: evaluate public claims, narratives, manipulated content, and information disorder.

Terminology:
- Misinformation: false or misleading information shared without proven intent to deceive.
- Disinformation: false or misleading information shared with intent to deceive or manipulate.
- Malinformation: genuine information used out of context to harm.

Verification controls:
- Trace the claim to its earliest available source.
- Capture the claim, claimant, timestamp, platform, and spread pattern.
- Check independent coverage and original context.
- Avoid labeling intent unless evidence supports it.

Evidence to capture: claim text, claimant, timestamp, platform, earliest source URL, spread pattern, independent coverage links, original context notes, intent assessment (if supported), confidence level, and access date.

### Module O — Username, alias, and avatar enumeration

Goal: discover public accounts tied to a username, handle, or alias (core to privacy self-audits).

Sources/tools:
- Manual username search on major platforms.
- Search-engine queries such as `"{username}"` and `"{username}" site:{platform}`.
- WhatsMyName-style public username-checking sites used lawfully.
- Gravatar public-profile checks for user-provided emails (self-audit only).
- Reverse image search of the subject's own avatar (self-audit or with documented consent only).

Verification controls:
- The same username does not prove the same person — require multiple matching signals (bio, links, photo, posting history, cross-links) before attribution.
- Label unconfirmed accounts "possible".
- Never use password-reset, login, or account-recovery flows to test whether an email or phone is registered (prohibited).
- Minimize collection of bystander accounts.

Stop condition: when candidate platforms are exhausted or matches cannot be raised above "possible".

Evidence to capture: username/handle searched, platform URLs, match signals (bio/links/photo/history), attribution status ("confirmed" vs "possible"), consent/self-audit notation, and access date.
