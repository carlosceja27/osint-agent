# Artifact 05 — Industry Practitioners, Vendors & Research Organizations

> Purpose: per the request — **"businesses that conduct OSINT"** and the **papers/reports worth reading** that they publish. Organized by what each *does* and what it *publishes*. (No pricing per instruction; "freemium/commercial/free" noted only to set expectations.) This doubles as a map of where modern tradecraft is actually being written down.

---

## A. OSINT platform & tooling vendors (and their published research)

| Vendor | What they do | Notable published material to read |
|---|---|---|
| **Maltego** (DE) | Link-analysis / graph investigation platform; integrates many data "transforms." Acquired **Hunchly** (capture/chain-of-custody) to expand OSINT capture. | **"The Future of OSINT: From Open Sources to AI-Driven Fusion Intelligence"** (blog + whitepaper); "7 Practical OSINT Lessons from the Ukraine War"; law-enforcement ontology whitepapers. Strong conceptual/tradecraft content. |
| **Recorded Future** (US) | World's largest threat-intelligence company; OSINT-heavy CTI. Selected as a cornerstone for ODNI's **"Sentinel Horizon"** (access for all US IC agencies). | **Insikt Group** research (cybercrime, state-sponsored campaigns, influence ops) — analyst-validated, widely-cited reports. |
| **Babel Street** (US) | Multilingual OSINT, geospatial, cross-platform data fusion for gov/LE; FBI relies on it. | "Babel Street Insights"; multilingual/PAI tradecraft material. |
| **Palantir** (US) | Data-integration/analytics platform widely used for intelligence fusion (OSINT among inputs). | Engineering/impact blogs; less OSINT-method, more platform. |
| **Authentic8 — Silo for Research** (US) | **Managed-attribution** secure cloud browser for safe OSINT across surface/deep/dark web (used by 600+ orgs). | **OSINT Academy** (40+ training modules, built with **OSINT Combine**); strong blog on **managed attribution, anonymity/obfuscation, analyst mental health**. Among the best free tradecraft libraries. |
| **Fivecast** (AU) | Digital-intelligence/collection-and-analytics (ONYX) for national security, LE, financial crime, corporate security. | **"OSINT Fundamentals / The Intelligence Cycle"** blog series; risk-detection methodology. |
| **ShadowDragon** (US) | OSINT investigation tools/data (e.g., SocialNet) + training for LE/CTI. | Investigation guides; case-method content. |
| **Skopenow** (US) | AI-driven OSINT/investigations analytics (1,500+ customers incl. Fortune 500, federal). | Investigative analytics & due-diligence content. |
| **LifeRaft — Navigator** (CA) | Corporate-security/physical-threat SOCMINT & OSINT. Integrates Authentic8 Silo. | Corporate-security threat-intel reports. |
| **SANS Institute** (US) | Training & research; OSINT courses (**SEC497 Practical OSINT**, **SEC587 Advanced OSINT**), the annual **OSINT Summit**. | **"What is OSINT"** primer; **"Sock Puppets in OSINT"**; **"Enhance your CTI with the Admiralty System."** Excellent free, methodical blogs. |
| **OSINT Combine** (AU) | Training & tooling (e.g., NexusXplore); co-built Authentic8 OSINT Academy. | Mental-health-resilience and tradecraft posts; training curricula. |
| Others to know | **Digimind** (social listening), **Echosec/Flashpoint, DarkOwl, SpyCloud, Intel471, KELA, Cybersixgill** (dark-web/breach intel), **Social Links, Lampyre, SpiderFoot/Intel471** (automation). | Vendor threat reports; breach-exposure research. |

> Market context (attribute, don't over-rely): multiple market-research firms size the OSINT market in the high-single-digit **$B (2025–26)** growing toward **$30–60B by ~2035**, with Recorded Future, Palantir, Babel Street, Maltego, Thales, Google, Digimind among leaders. Useful only to show OSINT is now a mature commercial sector.

---

## B. Threat-intelligence & cyber firms that *do* OSINT at scale

These publish some of the most rigorous public OSINT-derived analysis (attribution, campaigns, infrastructure):

- **Mandiant (Google Threat Intelligence)** — incident-response + OSINT fusion; ~500 analysts/30+ countries; widely-read APT/threat reports (the "APTxx" naming tradition).
- **Microsoft Threat Intelligence (MSTIC) / Defender TI** — telemetry + OSINT; nation-state and influence-operation reporting; threat-actor taxonomy.
- **CrowdStrike, Cisco Talos, Dragos (ICS/OT), Group-IB, Sophos, Unit 42 (Palo Alto)** — regular public threat reports built substantially on OSINT + telemetry.

→ For the skill, these matter as **models of sourced, confidence-rated, reproducible public reporting** and for **infrastructure/cyber OSINT** technique.

---

## C. Corporate investigations, due diligence & risk advisories (OSINT as a service)

"Businesses that conduct OSINT" in the **due-diligence / KYC-AML / integrity** sense — they publish methodology and trend pieces:

- **Kroll** — investigations, due diligence, cyber threat intelligence; publishes **Threat Intelligence Reports** and due-diligence guidance.
- **Control Risks, S-RM, Nardello & Co., K2 Integrity, Hakluyt, PGI (Protection Group International)** — corporate intelligence / enhanced due diligence with dedicated multilingual OSINT teams; publish risk outlooks and (PGI, S-RM) practical OSINT/CTI explainers.
- **Big-4 forensic units** (Deloitte/PwC/EY/KPMG) — integrity due diligence & investigations practices; publish on third-party-risk and investigative analytics.

---

## D. NGOs, newsrooms & non-profits — the open tradecraft & verification leaders

Often *more* methodologically transparent than commercial vendors; their public guides are primary teaching material.

- **Bellingcat** (NL) — the defining open-source investigation collective. Publishes the **Online Investigation Toolkit** (50+ geolocation/satellite/verification tools), step-by-step case guides, **geolocation challenges**, and the influential **"How to Maintain Mental Hygiene as an Open Source Researcher."** Banned as "undesirable" by Russia (2022) — a marker of OSINT's geopolitical weight.
- **Centre for Information Resilience (CIR)** (UK) — runs **"Eyes on Russia"**; conflict-mapping and verification.
- **DFRLab (Atlantic Council)** — disinformation/influence-operations open-source research; co-founded the **Election Integrity Partnership**.
- **Graphika** — network/influence-operation analysis.
- **Citizen Lab (Univ. of Toronto)** — spyware/surveillance and digital-rights investigations (e.g., Pegasus).
- **Stanford Internet Observatory** — major disinformation-research center; **wound down/restructured in 2024** amid legal/political pressure (note: cite as a cautionary example of the political risk now attached to this work).
- **OCCRP** (incl. **Aleph** data platform) & **ICIJ** (Offshore Leaks: Panama/Paradise/Pandora) — investigative-journalism data/leaks for financial-crime OSINT (already in the skill).
- **OSINTCurious / The OSINT Curious Project** — community tradecraft (the "10-minute tips," vicarious-trauma guidance).
- **First Draft (legacy) → verification community; EJC/DataJournalism.com** — the **Verification Handbook** series (Artifact 06).

---

## E. Academic & training centers

- **UC Berkeley Human Rights Center** (Berkeley Protocol; Investigations Lab).
- **King's College London — Centre for Science & Security Studies (CSSS)** — OSINT tools/methods research and teaching.
- **University of Washington — Center for an Informed Public**; **Middlebury Institute (CNS/Monterey)** (the Ukraine "traffic-jam" warning).
- Professional certs/courses: **SANS SEC497/SEC587**, **IICI** (foundational open-source investigation), **NATO School Oberammergau N2-04**, **CEPOL** (EU LE), **McMaster/IACA** and university OSINT modules.

---

## What to actually read first (curated shortlist for the skill author)

1. **Bellingcat Online Investigation Toolkit + guides** — the practical canon.
2. **Berkeley Protocol** (OHCHR/Berkeley) — the methodology/ethics standard (Artifact 06).
3. **Verification Handbook** (EJC) — verification canon.
4. **IC OSINT Strategy 2024–2026** (ODNI/CIA) + **DIA OSINT Strategy 2024–2028** — government direction (Artifact 03).
5. **GELSI systematic review** — the governance/ethics map (Artifact 04).
6. **Reuters Institute "AI is undermining OSINT's core assumptions"** — the modern-threat brief (Artifact 02).
7. **Maltego "Future of OSINT"** + **SANS OSINT blogs** + **Authentic8 OSINT Academy** — vendor tradecraft.

---

## Implications for the `osint_audit` skill

- The skill's tool appendix lists mostly **free utilities**; it should acknowledge the **professional vendor/managed-attribution layer** (Maltego, Silo for Research, etc.) and the **NGO verification canon** (Bellingcat, Verification Handbook, Berkeley Protocol) as authoritative references, even if the skill itself stays free-tool-first.
- It already cites OCCRP/ICIJ; adding **Bellingcat, CIR, DFRLab** strengthens the journalism mode.
- "Businesses that conduct OSINT" also means **due-diligence/risk firms** — relevant if the skill ever extends to corporate/entity vetting; their published method pieces are good source material.
- Use these orgs' **public reports as the model** for the skill's output: sourced, confidence-rated, reproducible, with an explicit methodology section.
