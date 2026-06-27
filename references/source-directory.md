# OSINT Source Directory

This directory is the canonical source menu for the OSINT skill — each module in `modules.md` maps to a section here. Listing a source is not an endorsement and does not imply it is required; use what is warranted by the investigation and proportionate to the subject's privacy interests. URLs are navigational anchors, not guarantees: domain registrations change, services sunset, and paths shift. The skill deliberately avoids link-rot by favoring durable, high-value sources; verify any URL before relying on it operationally.

---

## Attribute Legend

Used in every table below.

| Attribute | Values | Notes |
|---|---|---|
| **Access** | `free` / `free+API-key` / `paid` | "free+API-key" = free tier with registration for programmatic access |
| **Automation** | `API` / `interactive-only` | `API` = ToS-friendly programmatic access exists. `interactive-only` = manual browser use only; do NOT script, scrape, or drive with automation tools |
| **Tier** | `primary` / `secondary` / `aggregator` / `archive` / `tool-derived` | Primary = official/original. Aggregators are leads, never facts; verify upstream |
| **OPSEC risk** | `low` / `med` / `high` | Factors that raise risk are noted inline (account required, foreign-state-controlled, query-logging, referrer leakage) |

---

## A — Search & Dorks

*Serves Module A. See also the [Google Dork Quick-Reference](#google-dork--advanced-operator-quick-reference) section below.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| Google (web) | google.com | General indexed-web search; dork-capable | free | interactive-only | secondary | med (query-logging) | Broad sweep |
| Bing | bing.com | Alternative index; catches different coverage | free | interactive-only | secondary | med | Corroboration |
| DuckDuckGo | duckduckgo.com | Non-personalised; lower tracking | free | interactive-only | secondary | low | Privacy-sensitive search |
| CommonCrawl | commoncrawl.org | Petabyte web-crawl corpus; bulk research | free | API | primary | low | Large-scale or historical |
| GDELT | gdeltproject.org | Global events/media index; research access | free | API | aggregator | low | News/events pattern |

---

## B — Social Media (Public-UI / Archive Aids)

*Serves Module B. All sources here are public-UI or archive aids only. Bulk scraping, credential-based access, and ToS/rate-limit evasion are excluded by policy. Post-API-closure platforms are interactive-only.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| X/Twitter advanced search | twitter.com/search-advanced | Temporal/keyword/account search on public posts | free | interactive-only | primary | med (account optional but logged) | Public post search |
| Reddit search | reddit.com/search | Public posts/comments by keyword, subreddit, user | free | interactive-only | primary | low | Community discourse |
| YouTube public search | youtube.com | Public video/channel search | free | interactive-only | primary | low | Video-first subjects |
| Bluesky search | bsky.app | AT Protocol public posts; growing index | free | interactive-only | primary | low | Decentralised social |
| Mastodon instance/hashtag search | instances.social | Federated; search per-instance or via hashtag | free | interactive-only | primary | low | Federated social |
| LinkedIn public UI | linkedin.com | Public professional profiles; limited post-API-closure | free | interactive-only | primary | high (account required; visit logged) | Professional subjects |
| Instagram public UI | instagram.com | Public posts/profiles only | free | interactive-only | primary | med (account may be required) | Visual/lifestyle subjects |
| Facebook public UI | facebook.com | Public pages/posts only | free | interactive-only | primary | high (account required; FB logs extensively) | Pages and public groups only |
| TikTok public search | tiktok.com | Public videos/creator pages | free | interactive-only | primary | high (ByteDance/Chinese-state concern; query-logging) | Short-form video subjects |
| Wayback Machine (profile history) | web.archive.org | Archived snapshots of public profiles and pages | free | API (CDX) | archive | low | Historical profile state |

> **Framing rule:** Social sources are used to surface already-public content. Do not attempt to access private/friends-only content, infer private connections, or aggregate social data in ways that exceed the original context of disclosure.

---

## C — Professional & Code

*Serves Module C.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| LinkedIn public UI | linkedin.com | Employment history, endorsements, public posts | free | interactive-only | primary | high (account required; visit logged) | Professional background |
| GitHub public API | api.github.com | Repos, commits, contributor metadata, orgs | free+API-key | API | primary | low | Developer identity; code contribution history |
| GitLab public API | gitlab.com | Same as GitHub for GitLab-hosted projects | free+API-key | API | primary | low | Open-source developer subjects |
| Bitbucket public repos | bitbucket.org | Public repository search | free | interactive-only | primary | low | Supplemental code hosting |
| Gravatar lookup | gravatar.com | Public profile from email MD5 hash | free | API | tool-derived | low | Self-audit; email-hash correlation |

---

## D / N — News & Fact-Checking

*Serves Modules D and N.*

### News Sources

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| Google News | news.google.com | News aggregation; temporal search | free | interactive-only | aggregator | med | First-pass news sweep |
| Bing News | bing.com/news | Alternative news index | free | interactive-only | aggregator | med | Corroboration |
| Publisher archives | (per-outlet) | Original reporting; paywalled content may require institutional access | varies | interactive-only | primary | low–med | Ground truth for claims |
| PR Newswire / Business Wire / GlobeNewswire | prnewswire.com / businesswire.com / globenewswire.com | Official press releases | free | interactive-only | primary | low | Corporate/org statements |
| GDELT | gdeltproject.org | Global events/media database; research access | free | API | aggregator | low | Pattern-of-coverage analysis |
| Media Cloud | mediacloud.org | Academic news research platform | free (research) | API | tool-derived | low | Academic/longitudinal analysis |
| Chronicling America | chroniclingamerica.loc.gov | Historic US newspapers (Library of Congress) | free | API | primary | low | Historical subjects |
| Listen Notes | listennotes.com | Podcast episode search | free+API-key | API | aggregator | low | Audio-format subjects |

### Fact-Checking

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| Google Fact Check Explorer | toolbox.google.com/factcheck/explorer | Indexed fact-checks across publishers | free | API | aggregator | low | Claim triage |
| Snopes | snopes.com | Long-form claim investigation | free | interactive-only | secondary | low | Viral claims |
| PolitiFact | politifact.com | US political claims rated on a scale | free | interactive-only | secondary | low | US political statements |
| FactCheck.org | factcheck.org | Nonpartisan US political fact-check | free | interactive-only | secondary | low | US political claims |
| AFP Fact Check | factcheck.afp.com | Multi-language AFP fact-checks | free | interactive-only | secondary | low | International claims |
| Reuters Fact Check | reuters.com/fact-check | Reuters-branded fact-checks | free | interactive-only | secondary | low | International claims |
| AP Fact Check | apnews.com/ap-fact-check | AP-branded fact-checks | free | interactive-only | secondary | low | International claims |
| Full Fact | fullfact.org | UK-focused fact-checking | free | interactive-only | secondary | low | UK claims |
| IFCN signatory directory | ifcncodeofprinciples.poynter.org | Lists credentialed fact-checkers globally | free | interactive-only | secondary | low | Vet unfamiliar fact-checkers |
| Hoaxy | hoaxy.osome.iu.edu | Claim-spread visualisation on social media | free | interactive-only | tool-derived | low | Misinformation propagation mapping |
| Media Bias/Fact Check | mediabiasfactcheck.com | Outlet-level bias/factuality ratings | free | interactive-only | aggregator | low | Caveat: editorial ratings, not peer-reviewed; one signal among many |
| Verification Handbook | verificationhandbook.com | Methodology guide (EJC) | free | n/a | secondary | low | Practitioner reference |

---

## E — Public Records & Registries

*Serves Module E. Many registry portals run on Tyler/Odyssey or similar vendor stacks with anti-bot controls — those are marked `interactive-only`.*

### Courts

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| PACER | pacer.gov | US federal court dockets and filings | paid | interactive-only | primary | low | Federal civil/criminal/bankruptcy |
| CourtListener + RECAP | courtlistener.com | Free federal court data; RECAP crowdsources PACER docs; REST API | free+API-key | API | primary | low | Federal dockets; RECAP-uploaded docs free |
| Justia Dockets | dockets.justia.com | Free federal docket summaries | free | interactive-only | secondary | low | Quick docket lookup |
| Google Scholar (case law) | scholar.google.com | US case law full text | free | interactive-only | secondary | low | Legal precedent research |
| State/county courts | (per-jurisdiction) | State civil, criminal, family, probate records | varies | interactive-only (anti-bot) | primary | low | State-level litigation |

### Corporate Registries

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| SEC EDGAR | sec.gov/edgar | US public company filings (10-K, S-1, proxy, etc.) | free | API | primary | low | US public companies |
| UK Companies House | find-and-update.company-information.service.gov.uk | UK company filings, directors, financials | free | API | primary | low | UK entities |
| Canada Business Registries | beta.canadasbusinessregistries.ca | Federal and provincial Canadian registries | free | interactive-only | primary | low | Canadian entities |
| Australian ABR (ABN Lookup) | abr.business.gov.au | Australian Business Register | free | API | primary | low | Australian entities |
| NZ Companies Register | companies-register.companiesoffice.govt.nz | New Zealand companies | free | interactive-only | primary | low | NZ entities |
| OpenCorporates | opencorporates.com | Aggregator across 140+ national/sub-national registries | free+API-key | API | aggregator | low | Cross-jurisdiction sweep — verify upstream |
| GLEIF LEI | gleif.org | Global Legal Entity Identifier register | free | API | primary | low | Financial-sector entities |

### Campaign Finance

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| FEC | fec.gov | US federal campaign finance filings | free | API | primary | low | Candidate/PAC contributions |
| OpenSecrets | opensecrets.org | FEC-derived analysis and donor lookup | free | API | aggregator | low | Contextual analysis — verify FEC |
| FollowTheMoney | followthemoney.org | State-level campaign finance | free | API | aggregator | low | State political money |

### Nonprofits / Foundations

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| IRS 990 downloads | irs.gov/charities-non-profits | Machine-readable 990 bulk data | free | API | primary | low | Direct from IRS; authoritative |
| ProPublica Nonprofit Explorer | projects.propublica.org/nonprofits | 990 search and display | free | API | aggregator | low | Fastest access to 990 data |
| Candid / GuideStar | candid.org | 990 aggregator, added context | free (limited) / paid | interactive-only | aggregator | low | Supplement IRS data |

### Sanctions & Debarment

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| OFAC SDN search | sanctionssearch.ofac.treas.gov | US Treasury Specially Designated Nationals list | free | API | primary | low | US sanctions |
| EU Sanctions Map | sanctionsmap.eu | EU consolidated sanctions list | free | interactive-only | primary | low | EU sanctions |
| UN Consolidated List | un.org/securitycouncil/sanctions/materials | UN Security Council sanctions | free | interactive-only | primary | low | UN-level sanctions |
| World Bank Debarment | worldbank.org (debarred-firms) | Firms debarred from World Bank contracts | free | interactive-only | primary | low | Procurement/corruption |
| SAM.gov | sam.gov | US federal contractor exclusions | free | API | primary | low | US government contracts |
| OpenSanctions | opensanctions.org | Aggregator across 100+ sanctions/PEP lists | free+API-key | API | aggregator | low | Cross-list sweep — verify upstream |

### Property

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| County assessor / recorder portals | (per-county) | Ownership, tax records, deeds, liens | free (usually) | interactive-only (anti-bot; Tyler/Odyssey) | primary | low | US property |
| UK Land Registry | landregistry.data.gov.uk | England & Wales registered land/property | free | API | primary | low | UK property |

### Licenses & Regulators

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| openFDA | open.fda.gov | Drug approvals, enforcement, adverse events | free | API | primary | low | Healthcare/pharma subjects |
| EPA ECHO | echo.epa.gov | Environmental compliance and enforcement | free | API | primary | low | Environmental subjects |
| OSHA | osha.gov/ords/imis | Inspection and violation records | free | interactive-only | primary | low | Workplace safety |
| State professional boards | (per-state) | Medical, legal, financial, contractor licenses | free | interactive-only (often anti-bot) | primary | low | Credential verification |

> **Note on NSOPW, CA Megan's Law, county Odyssey portals:** `interactive-only` — never scripted. Use only for direct-access, manual queries where specifically relevant. (See Module E.)

---

## G — Images & Media Verification

*Serves Module G. All provenance indicators are PROBABILISTIC, never dispositive. Absence of metadata proves nothing.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| Google Lens | lens.google.com | Reverse image search | free | interactive-only | tool-derived | med (query-logging; image uploaded to Google) | First-pass reverse image |
| Bing Visual Search | bing.com/visualsearch | Reverse image search; different index | free | interactive-only | tool-derived | med | Corroboration |
| Yandex Images | yandex.com/images | Reverse image; strong on photos | free | interactive-only | tool-derived | **high** (Russia-controlled; query-logging; avoid for sensitive subjects) | Use only where Google/Bing fail and risk is accepted |
| TinEye | tineye.com | Reverse image; earliest-date indexing | free+API-key | API | tool-derived | low | First-published-date tracking |
| InVID / WeVerify | invid-project.eu | Video keyframe extraction and metadata | free (browser extension) | interactive-only | tool-derived | low | Video verification |
| FotoForensics | fotoforensics.com | Error-level analysis (ELA); indicators only | free | interactive-only | tool-derived | med (image uploaded to third party) | Manipulation indicators |
| Forensically | 29a.ch/photo-forensics | ELA, clone detection, noise analysis; client-side | free | interactive-only | tool-derived | low (client-side) | Manipulation indicators |
| ExifTool | exiftool.org | Local metadata extraction (EXIF, IPTC, XMP) | free | CLI | tool-derived | low (local) | GPS, device, timestamp extraction |
| C2PA / Content Credentials Verify | verify.contentauthenticity.org | Check for C2PA cryptographic provenance signatures | free | interactive-only | tool-derived | low | Provenance chain (where present) |

> **Excluded by policy:** Facial-recognition identity engines (PimEyes, Clearview AI, or similar) — biometric / EU-AI-Act / stalking risk. Do not use, and do not list as an alternative. Reverse-image search of one's own photo for self-audit is fine; face-recognition identity lookup is not.

---

## H — Geospatial

*Serves Module H.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| Google Maps / Earth Pro | google.com/maps / earth.google.com | Satellite, street-level, terrain | free | interactive-only | primary | med (query-logging) | Baseline visual reference |
| Apple Maps | maps.apple.com | Alternative street-level imagery in some regions | free | interactive-only | primary | low | Cross-reference |
| OpenStreetMap | openstreetmap.org | Community-maintained; downloadable | free | API | primary | low | Infrastructure/place detail |
| Overpass Turbo | overpass-turbo.eu | OSM feature queries (amenities, roads, boundaries) | free | API | tool-derived | low | Structured OSM queries |
| SunCalc | suncalc.org | Shadow/azimuth calculation for date/time/location | free | interactive-only | tool-derived | low | Photo timestamp verification |
| Sentinel Hub | sentinelhub.com | ESA Sentinel satellite imagery | free (EO Browser) / API (paid) | API | primary | low | Change detection |
| NASA Worldview | worldview.earthdata.nasa.gov | Near-real-time NASA satellite products | free | interactive-only | primary | low | Environmental/event imagery |
| USGS EarthExplorer | earthexplorer.usgs.gov | Landsat and aerial archive | free | API | primary | low | Historic satellite coverage |
| Copernicus Data Space | dataspace.copernicus.eu | ESA Sentinel data download | free | API | primary | low | High-res SAR and optical |
| Mapillary | mapillary.com | Crowd-sourced street-level imagery | free+API-key | API | secondary | low | Coverage gaps in Street View |

---

## I — Domains / Infrastructure (Passive Only)

*Serves Module I. PASSIVE sources only. Active DNS brute-force, port scanning, vulnerability scanning, live-target crawling, and any credential/breach database use are excluded.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| ICANN Lookup | lookup.icann.org | Authoritative WHOIS / RDAP for gTLDs | free | interactive-only | primary | low | Registration records |
| ARIN RDAP | rdap.arin.net | IP/ASN registration records (Americas) | free | API | primary | low | IP ownership |
| crt.sh | crt.sh | Certificate Transparency log search; subdomain discovery | free | API (undocumented rate limits) | primary | low | Subdomain enumeration |
| CertSpotter | certspotter.com | CT log monitoring / historical certs | free+API-key | API | primary | low | Certificate history |
| SecurityTrails | securitytrails.com | Passive DNS history, subdomain enumeration | free (50/mo) / paid | API | secondary | med (account required; query-logged) | DNS history |
| ViewDNS | viewdns.info | Reverse DNS, IP, MX, reverse-IP | free+API-key | API | secondary | low | Quick passive DNS queries |
| DNSDumpster | dnsdumpster.com | Subdomain/DNS map | free | interactive-only | tool-derived | low | Visual DNS reconnaissance |
| RapidDNS | rapiddns.io | Passive subdomain lookup | free | interactive-only | secondary | low | Supplemental |
| Shodan | shodan.io | Public host/port/service/banner search | free tier / paid | API | secondary | med (query-logged) | Passive host intelligence |
| Censys | search.censys.io | Public host/TLS search | free tier / paid | API | secondary | med | TLS certificate/host research |
| URLScan.io | urlscan.io | URL scan, screenshot, DOM (prior-scan data is passive) | free / paid | API | secondary | low | URL intelligence; prior scan data |
| BuiltWith | builtwith.com | Technology fingerprinting | free / paid | API | tool-derived | low | CMS, stack, analytics identification |
| Wappalyzer | wappalyzer.com | Technology fingerprinting (browser or API) | free+API-key | API | tool-derived | low | Stack identification |
| Netcraft | netcraft.com | Site/server history, hosting, uptime intel | free / subscription | interactive-only | secondary | low | Long-term infrastructure history |
| Netlas | netlas.io | Attack-surface discovery (passive) | free tier / paid | API | tool-derived | low | Passive surface enumeration |
| theHarvester / Subfinder (passive modes) | github.com/laramies/theHarvester | Aggregate emails/hosts from passive sources | free | CLI | tool-derived | low | Passive aggregation — verify upstream |

---

## J — Breach Notification

*Serves Module J. Breach-notification services are in scope. Breach-DUMP search, password/hash exposure, and credential-stuffing services are excluded by policy.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| Have I Been Pwned | haveibeenpwned.com | Breach notification; checks email against known breach metadata | free / paid API | API | primary | low | Self-audit; subject-interest audit |
| Firefox Monitor | monitor.mozilla.org | HIBP-powered; user-friendly interface | free | interactive-only | secondary | low | Consumer-facing self-audit |

> **Excluded by policy:** Breach-dump databases, password or hash exposure services, credential-stuffing lookup tools — regardless of framing (e.g. "search by hash").

---

## K — Archives & Capture

*Serves Module K.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| Wayback Machine | web.archive.org | Archived web snapshots; CDX API for URL enumeration | free | API (CDX) | archive | low | Historical page state; deleted content |
| archive.today / archive.ph | archive.ph | On-demand page capture and permanent link | free | interactive-only (intermittent uptime) | archive | low | Capture-to-cite; note uptime variability |
| SingleFile (browser extension) | github.com/gildas-lormeau/SingleFile | Full-page capture as single HTML; can hash output | free | interactive-only | tool-derived | low | Integrity-preserving local capture |
| Conifer / Webrecorder | conifer.rhizome.org | WARC-format archiving for complex/interactive pages | free (limited) / self-host | interactive-only | tool-derived | low | Replay-grade capture of JS-heavy pages |
| Hunchly-class capture (or similar) | hunchly.com | Auto-capture with log/hash; investigation audit trail | paid | interactive-only | tool-derived | low | Continuous investigation capture |

> **Capture protocol:** Save all evidence with timestamps and a SHA-256 hash. Note Google Cache is largely deprecated and should not be relied upon.

---

## L — Network / Entity Mapping

*Serves Module L. Sourced edges only — do not infer connections not documented in a primary or primary-adjacent source.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| OpenCorporates | opencorporates.com | Cross-jurisdiction corporate graph | free+API-key / paid | API | aggregator | low | Ownership chains — verify upstream |
| OCCRP Aleph | aleph.occrp.org | Investigative data commons; leaks + registries | free (researcher account) | API | aggregator | low | Cross-source entity mapping |
| ICIJ Offshore Leaks | offshoreleaks.icij.org | Panama/Pandora/FinCEN/Paradise leaks database | free | interactive-only | primary | low | Offshore entity lookup |
| OpenSanctions | opensanctions.org | Sanctions, PEP, and debarment graph | free+API-key | API | aggregator | low | Sanctions/PEP cross-reference |
| Wikidata | wikidata.org | Structured knowledge graph; SPARQL endpoint | free | API (SPARQL) | secondary | low | Public entities; biographical data |
| Maltego or similar graph tools | maltego.com | Visual link analysis with transform ecosystem | paid (community tier free) | API/transforms | tool-derived | med (query-logging via cloud transforms) | Link-visualisation; transforms only as reliable as upstream |

---

## M — International

*Serves Module M. Also draws on corporate, sanctions, and court sections above.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| UK Companies House | find-and-update.company-information.service.gov.uk | UK directors, filings, PSC register | free | API | primary | low | UK entities |
| EU Sanctions Map | sanctionsmap.eu | EU consolidated sanctions list with search | free | interactive-only | primary | low | EU sanctions |
| Canada Business Registries | beta.canadasbusinessregistries.ca | Federal and provincial Canadian registry | free | interactive-only | primary | low | Canadian entities |
| Australian ABR | abr.business.gov.au | Australian Business Register | free | API | primary | low | Australian entities |
| NZ Companies Register | companies-register.companiesoffice.govt.nz | New Zealand companies | free | interactive-only | primary | low | NZ entities |
| OCCRP Aleph | aleph.occrp.org | Cross-border investigative data commons | free (researcher) | API | aggregator | low | Multi-jurisdiction entity research |
| ICIJ Offshore Leaks | offshoreleaks.icij.org | Multi-leak offshore entity database | free | interactive-only | primary | low | Offshore structures |
| UN Consolidated Sanctions List | un.org/securitycouncil/sanctions/materials | UN Security Council designations | free | interactive-only | primary | low | UN sanctions |
| World Bank Debarment | worldbank.org (debarred-firms) | Firms/individuals debarred from WB contracts | free | interactive-only | primary | low | Procurement/corruption |
| Interpol public notices | interpol.int/How-we-work/Notices | Public Red/other notices (not a law-enforcement DB) | free | interactive-only | secondary | low | Public notices only |

---

## O — Username / Alias Enumeration

*Serves Module O.*

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| WhatsMyName | whatsmyname.pro | Username presence check across ~700 platforms | free | interactive-only / API | tool-derived | low | Alias mapping |
| Sherlock | github.com/sherlock-project/sherlock | CLI username enumeration across platforms | free | CLI | tool-derived | low | Local-run; no query-logging |
| NameChk | namechk.com | Handle availability / presence check | free | interactive-only | tool-derived | low | Supplemental |
| Gravatar | gravatar.com | Public profile from email MD5 hash | free | API | tool-derived | low | Email → avatar/profile correlation |

> **Note:** Username presence is a signal, not a confirmed identity match. Cross-verify against profile content, account age, and activity patterns before asserting attribution (Module O).

---

## P — Crypto / Blockchain

*Serves Module P.*

> **Caveat:** A blockchain address is not an identity. Clustering heuristics and attribution labels are investigative leads, not proof. Mixing services and privacy chains (Monero, shielded pools, mixer outputs) limit traceability. Use only public ledger data and lawful tools.

### Block Explorers

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| Blockstream.info | blockstream.info | Bitcoin explorer | free | API | primary | low | BTC transaction/address |
| Etherscan | etherscan.io | Ethereum explorer | free+API-key | API | primary | low | ETH/ERC-20 |
| BscScan | bscscan.com | BNB Chain explorer | free+API-key | API | primary | low | BSC |
| PolygonScan | polygonscan.com | Polygon explorer | free+API-key | API | primary | low | MATIC |
| Solscan | solscan.io | Solana explorer | free+API-key | API | primary | low | SOL |
| Tronscan | tronscan.org | TRON explorer | free | API | primary | low | TRX |
| Blockchair | blockchair.com | Multi-chain explorer (BTC, ETH, BCH, LTC, others) | free+API-key / paid | API | primary | low | Cross-chain |

### Sanctions / Abuse

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| OFAC SDN (crypto addresses) | sanctionssearch.ofac.treas.gov | OFAC-designated crypto addresses | free | interactive-only | primary | low | Sanctions |
| OpenSanctions | opensanctions.org | Aggregated lists including crypto addresses | free+API-key | API | aggregator | low | Cross-list check |
| Chainabuse | chainabuse.com | Community-reported abuse addresses (scams, ransomware) | free | API | secondary | low | Abuse signal — community-sourced, verify |

### Attribution (Leads Only)

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| WalletExplorer | walletexplorer.com | BTC clustering / wallet labels; partially archived | free | interactive-only | tool-derived | low | Clustering leads — verify; coverage declining |
| Arkham / Breadcrumbs or similar | arkhamintelligence.com / breadcrumbs.app | Paid attribution platforms; graph visualisation | paid | interactive-only / API | tool-derived | med (account required) | Labels are commercial estimates — never dispositive |

---

## Q — Transport / Asset Tracking

*Serves Module Q.*

> **Guardrail:** Sources in this section are for asset and entity tracking in the public interest (corporate jets, commercial fleets, vessels linked to investigated entities). They are NOT for real-time pattern-of-life monitoring of individuals, home or movement tracking, or any purpose that amounts to stalking. Do not chain live position data with a registry to locate or surveil a specific person. Some jurisdictions restrict tracking private aircraft even where data is technically accessible — confirm local law.

### Aircraft

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| FlightAware | flightaware.com | Commercial and general aviation tracking | free / paid | API (paid) | secondary | low | Flight history; respects FAA blocking |
| Flightradar24 | flightradar24.com | Live and historical ADS-B; respects FAA privacy blocking | free / paid | API (paid) | secondary | low | Broad aviation coverage |
| OpenSky Network | opensky-network.org | Research-grade ADS-B; non-commercial use | free (research) | API | secondary | low | Academic/non-commercial; coverage varies |
| ADS-B Exchange | adsbexchange.com | Unfiltered ADS-B — **does not honor FAA privacy blocking or LADD opt-outs** | free / paid API | API | secondary | **med** (unfiltered; use only where public interest justifies) | Specific public-interest cases where a target has opted out of other trackers |
| FAA registry | registry.faa.gov | US aircraft registration (N-number, owner, type) | free | interactive-only | primary | low | Ownership/registration |
| ICAO-hex decoder (e.g. ADSBdb, OpenSky) | adsbdb.com | ICAO 24-bit address → registration lookup | free | API | tool-derived | low | Hex-to-tail correlation |

### Vessels

| Source | URL | Purpose | Access | Automation | Tier | OPSEC | Fit |
|---|---|---|---|---|---|---|---|
| MarineTraffic | marinetraffic.com | AIS vessel tracking; port calls; voyage history | free / paid | API (paid) | secondary | low | Commercial vessel movements |
| VesselFinder | vesselfinder.com | AIS tracking; IMO/MMSI lookup | free / paid | interactive-only | secondary | low | Corroboration |
| AISHub | aishub.net | AIS data-sharing network | free (contributor) / paid | API | secondary | low | Research/bulk AIS |
| Equasis | equasis.org | Vessel ownership, safety inspections, flag history | free (registration) | interactive-only | primary | low | Ownership chain; PSC inspection history |

---

## Google Dork / Advanced-Operator Quick-Reference

> **Scope statement:** Dorks surface already-public, already-indexed pages. They do not bypass access controls, reveal non-public data, or pierce authentication. Never construct dorks intended to reach login-gated, private, or restricted content.

| Operator | Syntax | Use |
|---|---|---|
| `site:` | `site:example.com keyword` | Restrict results to a domain or subdomain |
| `filetype:` / `ext:` | `filetype:pdf site:example.com` | Surface indexed documents of a specific type |
| `inurl:` | `inurl:"/profile"` | Find pages with a string in the URL |
| `intitle:` | `intitle:"index of"` | Find pages with a string in the `<title>` tag |
| `intext:` | `intext:"John Smith" site:gov` | Full-text search within indexed page content |
| `"exact phrase"` | `"Chief Financial Officer" "Acme Corp"` | Require exact phrase match |
| `-term` | `site:example.com -jobs` | Exclude a term from results |
| `OR` / `\|` | `"J. Smith" OR "John Smith"` | Alternative terms |
| `before:` / `after:` | `keyword after:2022-01-01 before:2023-01-01` | Limit to a date range (Google; support variable) |
| `cache:` | `cache:example.com/page` | View a cached copy (reliability declining; largely deprecated) |

**Self-audit example** — what a search engine has indexed about you:

```
"Your Name" site:linkedin.com OR site:twitter.com OR site:github.com
"your.email@example.com" filetype:pdf OR filetype:xlsx
"Your Name" "Your City" -site:yourownsite.com
```

Run results through the capture workflow (Module K) before taking remediation action so you have a dated record of what existed.

---

## Credits & Licensing

This directory is original editorial curation. The following prior works informed its structure and scope; none of their descriptive prose was reproduced:

- **jivoi/awesome-osint** (github.com/jivoi/awesome-osint) — CC-BY-SA 4.0. Source taxonomy informed category breadth. If any wording is later found to derive from that list, the CC-BY-SA 4.0 attribution requirement applies.
- **lockfale/OSINT-Framework** (github.com/lockfale/OSINT-Framework) — MIT. The attribute-tagging model (access, automation, tier) is inspired by that framework's function-first categorisation.
- **sinwindie/OSINT** (github.com/sinwindie/OSINT) — restrictive license; taxonomy ideas only, no text reused.
- **laramies/theHarvester** (github.com/laramies/theHarvester) — GPLv2. The passive-source taxonomy (domains, emails, hosts as distinct surfaces) informed Section I and the passive-only framing.

Facts — which sources exist, their URLs, and what they do — are not copyrightable. No proprietary descriptive prose was copied from any of the above.
