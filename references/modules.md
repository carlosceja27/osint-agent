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
- Arrest / booking coverage: arrest-aggregator and booking-log sites are often poorly indexed by general search engines, so a clean Google/Bing result is **not** a clean record. Search each site's **own internal search directly** (interactive/manual only) — do **not** rely on `site:` operators, which miss these poorly-indexed or anti-bot domains: `localcrimenews.com`, `mugshots.com`, `arrests.org`, `jailbase.com`, `recentlybooked.com`, `bustednewspaper`, plus county sheriff booking/arrest logs and the county Superior Court criminal case index. Arrest ≠ conviction.

Verification controls:
- Prefer original publisher pages and full transcripts over snippets.
- Capture date, outlet, author, headline, quoted statement, and context.
- Beware syndicated or copied articles that create false corroboration.

Evidence to capture: outlet name, URL, access date, author, headline, quoted statement, context, original vs syndicated status, transcript/archive links, and confidence level.

### Module E — Public records and official registries

Goal: verify records from primary official sources whenever possible.

Submodules:
- Courts: PACER, CourtListener, RECAP, state/county portals, official dockets.
- Criminal / booking records: county sheriff booking/arrest logs, county Superior Court criminal case index, NSOPW, and arrest-aggregator / mugshot sites (`localcrimenews.com`, `mugshots.com`, `arrests.org`, `jailbase.com`, `recentlybooked.com`, `bustednewspaper`) — interactive/manual searches only, on each site directly (they are poorly indexed by general search engines). In California and many states there is no public name-based criminal-history search, so treat this set as the check; never infer a clean record from a clean web search.
- Sanctioned API lane: CourtListener REST API (`https://www.courtlistener.com/api/rest/v4/search/`, types `r`=RECAP and `o`=opinions) for federal records — a lawful, scriptable source (unlike the gated portals below).
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
- Before any automation, check robots.txt and terms; never script or scrape CAPTCHA-protected, anti-bot, or disclaimer-gated portals (NSOPW, CA Megan's Law, county Odyssey court portals) — these are interactive/manual only. (Extends Module F's anti-bot-evasion prohibition.)

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

Goal: public-source, passive discovery of domains, subdomains, technology, exposure, and historical web infrastructure for defensive or investigative context. Also supports self-audit — an individual or organization assessing their own publicly visible footprint.

Passive footprint sweep — run sources in this order (registration → certificate transparency → passive DNS/subdomains → historical/archive → technology fingerprint → public host/service search). This is the lawful, passive alternative to a tool like theHarvester:

1. **Registration:** WHOIS/RDAP (ICANN Lookup, ARIN RDAP), registrar public records.
2. **Certificate transparency:** crt.sh, CertSpotter, Censys CT search — enumerate subdomains and issued certificates without touching the target.
3. **Passive DNS & subdomains:** SecurityTrails, ViewDNS, DNSDumpster, RapidDNS, Netlas — historical DNS resolution and subdomain enumeration from passive data only.
4. **Historical/archive:** Wayback Machine (CDX API), CommonCrawl — crawl history, exposed paths, and archived versions.
5. **Technology fingerprint:** BuiltWith, Wappalyzer, Netcraft — stack and hosting data derived from passive crawls.
6. **Public host/service search:** Shodan (public search), Censys public host search, URLScan.io — already-indexed scan data; do not initiate new scans against live targets.
7. **Passive aggregation CLIs:** theHarvester or Subfinder in passive mode only (API-backed, no active DNS brute-force).

See `source-directory.md` (Section I) for the full source menu with access notes and limitations.

Self-audit use: when auditing your own domain or organization, run the same passive sweep to surface what is publicly discoverable — exposed subdomains, email addresses in CT logs or public commits, and outdated or misconfigured infrastructure. Cross-reference `remediation.md` for hardening guidance on findings.

Example queries:
- crt.sh subdomain enumeration: `https://crt.sh/?q=%25.example.com&output=json`
- Wayback CDX API: `https://web.archive.org/cdx/search/cdx?url=*.example.com/*&output=json&fl=original,timestamp&limit=500`
- Reverse-IP (ViewDNS): `https://viewdns.info/reverseip/?host=203.0.113.10`
- Shodan org search: `org:"Example Corp" port:443`
- URLScan.io domain history: `https://urlscan.io/search/#domain:example.com`

Boundaries:
- Discovery and defensive assessment only.
- No exploitation, brute forcing, credential attempts, bypass, intrusive scanning, or instructions enabling unauthorized access.
- Passive only — exclude active scanning (port scans, live crawls, DNS brute-force) and breach/credential databases.

Verification controls:
- Log each query: tool used, query string, timestamp, and whether the result is current or historical.
- Confirm material findings across at least two independent passive sources before treating as established.
- Flag data age — passive DNS and CT logs may reflect superseded configurations.
- Avoid surfacing or retaining sensitive infrastructure details beyond what the investigation requires.

Evidence to capture: domain/subdomain list, WHOIS/RDAP record with registrar and dates, DNS records (A, MX, NS, TXT), certificate transparency entries, technology stack and hosting provider, Wayback/CommonCrawl archive notes, indexed host/service data from Shodan or Censys, current vs historical status, cross-verified sources, and access date per query.

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

Goal: evaluate public claims, narratives, manipulated content, and information disorder using traceable, source-anchored methods.

Terminology:
- Misinformation: false or misleading information shared without proven intent to deceive.
- Disinformation: false or misleading information shared with intent to deceive or manipulate.
- Malinformation: genuine information used out of context to harm.

Sources/tools:
- Fact-check organizations: Snopes, PolitiFact, FactCheck.org, AFP/Reuters/AP Fact Check, Full Fact — corroborating signals, not primary verdicts; always trace back to the original source they cite.
- Fact-check meta-search: Google Fact Check Explorer, IFCN signatory directory — cross-check whether a claim has been assessed by multiple independent outlets.
- Claim-spread visualization: Hoaxy — maps amplification patterns across platforms.
- Outlet-bias context: Media Bias/Fact Check — opinionated aggregator; one contextual signal only, not an authoritative rating.
- Methodology references: Verification Handbook (EJC), First Draft verification guide.
- Cross-reference Module G for image/video verification (reverse search, metadata, provenance). See `source-directory.md` (Sections D/N) for the extended menu.

Primary and original sourcing outranks any fact-checker's summary. Fact-checkers are a starting pointer, not a conclusion.

Reverse-chronology claim-tracing workflow:
1. **Capture and archive** the claim and known variants — screenshot, archive.today link, and Wayback snapshot. Record platform, claimant, and timestamp at discovery.
2. **Reverse-trace spread** using Hoaxy, archive searches, and platform search sorted by date — identify the earliest datable instance and how the claim mutated across versions.
3. **Locate the original source** via reverse image/video search (TinEye, Google Lens, InVID/WeVerify), embedded metadata, and news/academic archive searches — establish whether it originated from a document, broadcast, event, or secondary repackaging.
4. **Verify the originating actor and accuracy** — assess whether the claim is accurate, altered, mistranslated, or stripped of context; note any changes between origin and the version under review.
5. **Corroborate against primary sources** (official records, original reporting, authoritative databases). If corroboration is unavailable or contradictory, mark the claim unverified or disputed with explicit reasoning.

Verification controls:
- Trace the claim to its earliest available source before consulting fact-checkers.
- Capture the claim, claimant, timestamp, platform, and spread pattern.
- Check independent coverage and original context.
- Note the earliest-source determination and which fact-checker(s), if any, were consulted — including whether their verdicts agree.
- Avoid labeling intent (misinformation vs disinformation) unless evidence directly supports it.

Evidence to capture: claim text and known variants, claimant, timestamp and platform of discovery, earliest-source URL and archive link, spread pattern, independent coverage links, original context notes, earliest-source determination method, fact-checker(s) consulted and verdict consistency, intent assessment (only if evidenced), confidence level, and access date.

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

### Module P — Cryptocurrency and blockchain (public-ledger) OSINT

Goal: trace public on-chain activity — wallets, transactions, and token flows — tied to a defined requirement such as journalism on fraud, scams, or sanctions evasion, or self-audit of one's own published wallet addresses.

Allowed sources/tools:
- Block explorers by chain: Blockstream.info (BTC), Etherscan / BscScan / PolygonScan / Solscan / Tronscan (respective chains), Blockchair (multi-chain).
- Sanctions and abuse databases: OFAC SDN crypto-address entries, OpenSanctions, Chainabuse, Bitcoin-Abuse-class databases.
- Wallet clustering and attribution tools: WalletExplorer; Arkham / Breadcrumbs or similar paid platforms — treat all labels as leads, not conclusions.
- See `source-directory.md` (Section P) for the full menu.

Example queries:
- Look up an address's full transaction history on the relevant block explorer.
- Check an address against the OFAC SDN list or OpenSanctions.
- Trace a transaction hash to sender, receiver, value, and timestamp.
- Map token transfers across hops to identify consolidation or dispersion patterns.

Boundaries:
- Public-ledger data and lawful tools only.
- Never acquire or use stolen private keys, hacked exchange data, or de-anonymization-for-hire services targeting individuals.
- Do not attempt to pierce privacy coins or mixer outputs through non-public means.

Verification controls:
- A blockchain address is not an identity. Clustering heuristics and exchange/entity labels are investigative leads only — not proof of ownership or wrongdoing.
- Mixers, privacy coins (e.g. Monero, shielded pools), and cross-chain bridges break or obscure tracing; note the gap explicitly rather than inferring through it.
- Confirm any entity attribution with at least one independent, non-blockchain corroborating source before naming a person or organization.
- Log each query: address or hash queried, chain, explorer used, date of query, and whether a label/attribution came from the tool or from independent corroboration.

Stop when the trail enters a custodial exchange, a mixer, or a privacy-coin conversion beyond public-ledger visibility, or when entity attribution cannot be raised above "possible" with available public evidence.

Evidence to capture: wallet address(es), chain and network, transaction hash(es), timestamps, value and token type, explorer URL and query date, any exchange/entity labels with their source, OFAC/OpenSanctions hit details if applicable, and corroborating sources used for any attribution.

### Module Q — Transport and asset tracking (public broadcast data)

Goal: track corporate or private aircraft, commercial fleets, and maritime vessels using public ADS-B and AIS broadcast data, for public-interest journalism (e.g., sanctions evasion, illicit shipping, undisclosed corporate travel) or auditing one's own registered asset.

Allowed sources/tools:
- Aircraft (ADS-B): FlightAware, Flightradar24 (respects FAA privacy-blocking requests), OpenSky Network (research and non-commercial use only).
- Aircraft (unfiltered): ADS-B Exchange ignores FAA and equivalent privacy-blocking requests — use deliberately and only where a public-interest justification is documented.
- Vessels (AIS): MarineTraffic, VesselFinder, AISHub.
- Registration and ownership reference: FAA aircraft registry (N-number lookup), ICAO 24-bit hex decoders, Equasis (vessel ownership, operator, port-state control detention history), IMO/MMSI registries.
- See `source-directory.md` (Section Q) for the full menu.

Example queries:
- Look up a tail number or N-number to identify registered owner and aircraft type.
- Resolve an ICAO 24-bit hex to a specific aircraft registration.
- Check a vessel's IMO or MMSI for port-call history, flag state, and operator.
- Cross-reference a registered owner name against corporate registry or sanctions lists.

Boundaries:
- Asset and entity tracking for a documented, legitimate public-interest requirement only.
- Never use this module to build a real-time pattern-of-life on a private individual, track movements to or from a residence, or produce output that could enable stalking or harassment — that is out of scope and may be unlawful.
- Do not chain live position data to a home address or personal schedule to locate a specific person.
- Confirm applicable local law before tracking private aircraft in jurisdictions that legally restrict such activity.

Verification controls:
- ADS-B and AIS positions can be spoofed, deliberately delayed, or gap-filled with interpolations — corroborate significant position claims across at least two sources.
- Registration records reflect the legal registrant, not necessarily the beneficial owner; shell companies, trusts, and management companies are common — pursue ownership chains through corporate registries.
- A flight or voyage record establishes asset movement, not who was aboard; do not assert passenger identity without independent evidence.
- Log each query: identifier queried (tail/N-number, ICAO hex, IMO, MMSI), source platform, query date, and any caveats on data freshness or filtering status.

Stop when the asset or entity question is answered to the required evidential standard, or when continuing would shift the focus from asset tracking toward surveillance of an individual's personal movements.

Evidence to capture: aircraft tail/N-number or vessel IMO/MMSI, ICAO hex (aircraft), registered owner and operator, flag state (vessels), flight or voyage records with timestamps and positions, source platform and query date, ownership-chain sources, and any corroborating corporate or sanctions-list references.
