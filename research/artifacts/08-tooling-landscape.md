# Artifact 08 — Modern Tooling Landscape (by function, not brand)

> Purpose: refresh the tool picture for 2026. Organized **by investigative function** so the skill stays durable as individual tools come and go. Emphasis on *capabilities and caveats*, not pricing. The existing skill's Appendix D is solid but pre-dates the AI/provenance era and the SOCMINT access collapse.

> Selection principle (worth encoding in the skill): **prefer primary/official sources over aggregators; prefer tool-agnostic methods over any single tool; record the tool used as part of provenance.** The OSINT Framework (osintframework.com) remains a useful *menu* but is partly stale — treat as an index, not gospel.

---

## 1. Search & discovery
- **Search engines & dorking:** Google (operators in skill Appendix A), Bing, **DuckDuckGo**, **Yandex** (strong non-Western/reverse-image), **Brave**, Mojeek; specialized: **Marginalia** (indie web). Note Google's deprecation of `cache:` and some operators — verify operators still work.
- **Meta/aggregated search & dork helpers:** Google Programmable Search; dork generators.
- **Username/handle enumeration:** **Sherlock**, **Maigret**, **WhatsMyName**, Namechk, **holehe** (email→account presence).
- **Email/phone:** Have I Been Pwned (breach exposure), **Hunter.io**, EmailRep, **PhoneInfoga**; people-search/CAI aggregators (skill Module F) — treat as leads, verify against primary records.

## 2. Social media intelligence (SOCMINT) — *access-constrained in 2026*
- Reality: open APIs/scrapers largely **closed** (Artifact 02 §B). Approaches now:
  - Native platform search UIs + careful manual collection.
  - **Archives:** Wayback Machine, archive.today, and platform-specific archives for deleted content.
  - **Licensed/commercial** SOCMINT (Maltego transforms, Babel Street, Fivecast, LifeRaft, Social Links) where access is paid-for and lawful.
  - Academic access: **Meta Content Library** (IRB-gated), TikTok Research API, etc.
- Tools still useful: **Bluesky/Mastodon** search (more open by design); cross-platform pivot tools. Many legacy Twitter tools are **dead** — don't list them as live.

## 3. Imagery, video & media verification
- **Reverse image:** Google Lens, **Yandex Images** (strong faces), **TinEye** (first-seen/where), Bing Visual, **PimEyes** (face search — flag privacy/ethical/legal sensitivity).
- **Video:** **InVID/WeVerify** plugin (keyframes, magnifier, metadata), frame extraction, reverse-search per keyframe.
- **Forensics:** **FotoForensics** (ELA), **Forensically**, EXIF/metadata (**ExifTool**), noise/shadow/reflection analysis.
- **Provenance & synthetic detection (NEW — Artifacts 02/06):** **C2PA / Content Credentials** viewers (verify.contentauthenticity.org), **SynthID** detector, deepfake detectors (probabilistic). *None dispositive; combine and trust none alone.*

## 4. Geospatial / GEOINT
- **Free imagery:** Google Earth Pro (historical timeline), **Sentinel Hub/Copernicus (Sentinel-2)**, **USGS EarthExplorer (Landsat)**, **NASA Worldview**, Bing/Esri imagery.
- **Mapping/feature search:** OpenStreetMap, **Overpass Turbo** (query OSM features), Mapillary/KartaView (street-level), Google/Apple/Yandex Street View.
- **Commercial/tasked:** Maxar, Planet, BlackSky; **SAR** (Capella, ICEYE) for cloud/night; SkyFi (on-demand).
- **Chronolocation:** **SunCalc** / shadow tools; weather archives.
- **AI geolocation** (e.g., GeoSpy): emerging, use cautiously — subject to the AI-confabulation caveat (Artifact 02 §A).

## 5. Domain, network & infrastructure (cyber/technical OSINT)
- **DNS/WHOIS/RDAP:** ICANN Lookup, **SecurityTrails**, ViewDNS, **DNSdumpster**, WhoisXML.
- **Certificate transparency:** **crt.sh**, Censys certs.
- **Internet-scan / attack surface:** **Shodan**, **Censys**, **FOFA**, **ZoomEye**, **GreyNoise** (noise filtering); subdomain/asset discovery: **Amass**, **theHarvester**, Subfinder.
- **Web tech / history:** BuiltWith, **Wayback Machine**, **URLScan.io**, archive.today.
- Frame within **MITRE ATT&CK Reconnaissance (TA0043)** for CTI/red-team contexts.

## 6. Corporate, financial & legal records
- Global/entity: **OpenCorporates**, **OCCRP Aleph**, **ICIJ Offshore Leaks**, LittleSis; **GLEIF** (LEI), beneficial-ownership registers (varies/constrained post-2022 EU rulings).
- US: **SEC EDGAR**, state SoS, **PACER/RECAP & CourtListener**, FEC/OpenSecrets, ProPublica Nonprofit Explorer (all in skill).
- Sanctions/PEP: **OFAC**, EU Consolidated, UN, UK OFSI; **OpenSanctions** (aggregated, free) — add to skill.
- Europe: **UK Companies House**, EU **e-Justice/BRIS**, national registries (varies by country).

## 7. Collection management, capture & link analysis
- **Capture / chain of custody:** **Hunchly** (auto-capture + hashing — now Maltego-owned), Wayback/archive.today snapshots, **SingleFile**, hashing utilities. *Berkeley-Protocol-grade capture lives here.*
- **Link/graph analysis:** **Maltego**, **SpiderFoot** (automated multi-source), Recon-ng, **Obsidian/yEd/Gephi** for relationship mapping; **i2 Analyst's Notebook** (enterprise).
- **Managed attribution / safe access:** **Authentic8 Silo for Research**, isolated VMs (e.g., a dedicated Linux/Tails or **Tracelabs/CSI Linux**-style research environment), container browsers.

## 8. AI-assisted layer (use with the Artifact 02 governance rules)
- **LLMs** for translation, summarization, entity extraction, query drafting, transcription, code for parsing — **human-verified, disclosed, never cited as a source, never trusted to authenticate media.**
- **Caution:** AI geolocation/verification tools confabulate; treat outputs as leads requiring independent confirmation.

---

## Tool-selection guidance to encode in the skill
1. **Method first, tool second** — every function above has a manual fallback if a tool dies.
2. **Primary > aggregator** — verify people-search/CAI hits against official records.
3. **Record the tool** as provenance; **archive on capture**.
4. **Re-validate tool availability** — the SOCMINT space especially changes fast; don't present dead tools as live.
5. **Free-first is fine**, but name the **professional/managed-attribution** layer for higher-risk work.

---

## Implications for the `osint_audit` skill
- Appendix D is good but should: (a) **add provenance/synthetic-media tools** (C2PA viewers, SynthID, deepfake detectors); (b) **flag dead/curtailed SOCMINT tools** and pivot to archives + licensed access; (c) **add Hunchly-style forensic capture + hashing**; (d) **add OpenSanctions, Overpass Turbo, Censys, Amass**; (e) extend geospatial (Sentinel/Landsat/SAR).
- Keep the skill **free-tool-first** for its consumer/journalist audience, but cross-reference the managed-attribution/commercial layer for sensitive work.
- Consider replacing brittle brand lists with the **by-function taxonomy** above so the skill ages better.
