# Deep Research Report: Modern OSINT Practices & Fundamentals (2026)

**Prepared:** June 2026
**Purpose:** Inform an update to the existing `osint_audit` skill.
**Scope:** Strictly **Open-Source Intelligence (OSINT)**. Adjacent disciplines (HUMINT, SIGINT, GEOINT-as-a-national-discipline) appear *only* where they define OSINT by contrast or describe OSINT's role in all-source/fusion work — never as topics in their own right.
**Geographic scope of government sources:** United States + NATO members in Western Europe (Türkiye excluded), plus NATO/EU intergovernmental bodies.
**Companion material:** ten modular, LLM-consumable artifacts in [`artifacts/`](artifacts/) (see [index](00-INDEX.md)). This report is the **synthesis**; the artifacts are the **structured detail** an LLM should load to actually edit the skill.

---

## Executive Summary

OSINT in 2026 is a mature, mainstreamed intelligence discipline experiencing its most disruptive period since the web itself. Six findings frame everything below:

1. **The fundamentals are stable; the environment is not.** The durable core — the *information → intelligence* ladder, the intelligence cycle, source/credibility grading, corroboration, "open ≠ true" — is unchanged and well-documented in NATO and US doctrine. What has changed is the **operating environment**.

2. **Generative AI is the defining disruptor — and it cuts both ways.** Governments (US IC & DIA OSINT strategies) bet OSINT's future on **AI/ML and human–machine teaming**. Simultaneously, AI is **undermining OSINT's core epistemic assumptions**: synthetic media erodes "if you can locate it, it's probably real," LLMs *confabulate* corroboration and confidently mislabel fakes, and non-deterministic AI breaks **reproducibility**. The net: the analyst's job is shifting from *finding* to *validating and contextualizing*.

3. **Open social-media access has collapsed.** X's API paywall and Meta's **CrowdTangle shutdown (Aug 2024)** → IRB-gated Content Library killed the cheap, scriptable SOCMINT of the 2010s. SOCMINT is now the hardest pillar to do well.

4. **A new verification layer exists: content provenance.** **C2PA/Content Credentials** (now ISO/IEC 22144) and **SynthID** watermarking are the emerging standard — necessary additions to any verification workflow, though never dispositive alone.

5. **There is now a citable methodological standard.** The **Berkeley Protocol on Digital Open Source Investigations** (UC Berkeley HRC + UN OHCHR) provides tool-agnostic phases, forensic-capture/chain-of-custody requirements, and a **digital/physical/psychosocial security** triad. It is the single most valuable framework the existing skill is missing.

6. **OSINT has institutionalized.** It is foundational to the US IC ("the INT of first resort"), driving a NATO "cultural change" (Exercise *Northern Raven* 2024), central to the **Ukraine** war's information environment, embedded in cyber threat intelligence, and a multi-billion-dollar commercial sector with published tradecraft worth reading.

**Bottom line for the skill:** the existing `osint_audit` is operationally strong and ethically sound but **conceptually thin, US-centric, and pre-AI-era**. The highest-value upgrades are (a) a fundamentals/posture preamble, (b) an AI/synthetic-media verification layer with an explicit "the LLM is not a fake-detector" rule, (c) a SOCMINT reality check, (d) UK+EU legal coverage, (e) psychosocial-safety guidance, and (f) Berkeley-Protocol-grade evidence handling. Full gap analysis: [`artifacts/09`](artifacts/09-skill-gap-analysis.md).

---

## 1. The Fundamentals Inventory (what OSINT *is*)

*(Full detail: [`artifacts/01-fundamentals.md`](artifacts/01-fundamentals.md))*

**Definition convergence.** OSINT is *intelligence produced from **publicly or commercially** available information, collected against a requirement, then processed, analyzed, and disseminated.* The US IC's 2024 definition explicitly folds in **commercially available information (CAI)** and brands OSINT **"the INT of first resort."** The load-bearing distinction is **information vs. intelligence**: finding public content is not OSINT; *disciplined transformation of it into sourced, verifiable, decision-useful product* is.

**The clearest mental model — the NATO four-tier ladder:** Open Source **Data** → Open Source **Information** → **OSINT** → **Validated OSINT** (high-confidence, corroborated). This is the difference between "I found it" and "I can stand behind it."

**Sub-types within OSINT (collection families, not separate disciplines):** SOCMINT (social media), open-source GEOINT/IMINT (imagery/geolocation), technical/cyber recon (DNS, certs, internet-scan), financial/corporate OSINT, and the **PAI vs. CAI** sourcing split.

**The spine — the Intelligence Cycle (5 functions):** Planning & Direction → Collection → Processing & Exploitation → Analysis & Production → Dissemination & Feedback. Modern caveat: it is **iterative, not linear** — treat it as a checklist of functions that must all happen.

**Core fundamentals that separate professional from casual work:** requirement-driven scope; lawful/ethical basis set *before* collecting; OPSEC/managed attribution; **provenance capture** (source, URL, timestamp, exact query, archived copy); **source/credibility grading**; **corroboration (≥2 independent sources)**; structured, bias-aware analysis; media verification; **reproducibility**; minimization/proportionality; confidence-rated reporting with explicit negative findings.

**Two enduring axioms to elevate:** **"open ≠ true"** (public data is polluted by error and disinformation) and **"public ≠ fair game"** (aggregating individually-public data — the *mosaic effect* — is itself a privacy act).

---

## 2. Modern & Emerging Practices (what has *changed*)

*(Full detail: [`artifacts/02-modern-practices.md`](artifacts/02-modern-practices.md))*

**(A) Generative AI is undermining OSINT's core assumptions** (Reuters Institute, 2025). Three assumptions under attack: *geolocation implies authenticity* (synthetic media + confabulating LLMs break it); *reproducibility* (LLM outputs vary by prompt/timing/identity/silent updates); *traceable objectivity* (models inherit training-data bias, underserving the Global South). Documented 2025 failures: Grok and Google Lens "authenticating" an AI "train attack"; ChatGPT/Gemini "verifying" synthetic Times Square and Gaza-border CCTV with invented detail; **leading prompts** flipping a model's geolocation from Kyiv to Los Angeles. **Rule to encode: never let an LLM declare media authentic — it cannot, and it invents corroboration.** The constructive side: AI is genuinely useful for translation, transcription, entity extraction, summarization, and triage — **human-in-the-loop, disclosed, never cited as a source.**

**(B) SOCMINT access collapse.** X API paywalled (legacy scrapers dead); CrowdTangle shut **14 Aug 2024**, replaced by the IRB-gated **Meta Content Library** (excludes for-profits/most newsrooms). Adaptation: archives + native UIs + licensed commercial access + **archive-on-capture**. Any skill listing open Twitter/Facebook scraping as live is outdated.

**(C) Content provenance — the new verification layer.** Two complementary standards: **C2PA/Content Credentials** (signed manifest, ISO/IEC 22144) and **SynthID**-style **invisible watermarks** (survive screenshot/crop). Add a provenance-check step — but absence proves nothing and presence can be spoofed/stripped; it's *one signal*.

**(D) Geospatial OSINT commoditized.** Free Sentinel-2/Landsat/NASA Worldview/Google Earth Pro + commercial Maxar/Planet/BlackSky + **SAR** (Capella, ICEYE) that sees through cloud/night. Geolocation + chronolocation (SunCalc/shadows) remain workhorses — but are **no longer self-validating** in the AI era.

**(E) Mainstreaming.** Ukraine is the inflection point (Bellingcat war-crimes mapping; Oryx loss-counting; Middlebury's Google-Maps "traffic-jam" warning). National-security adoption (US IC/DIA strategies; NATO's *Northern Raven*). Cyber threat-intel recon (Shodan/Censys; MITRE ATT&CK **TA0043**). Corporate due-diligence/KYC. And the industry's headline trend: **OSINT → AI-driven fusion**, with analysts moving from collectors to **validators/sense-makers**.

---

## 3. Government & Intergovernmental Doctrine (public knowledge)

*(Full detail: [`artifacts/03-government-doctrine.md`](artifacts/03-government-doctrine.md))*

**United States.** The **IC OSINT Strategy 2024–2026** (ODNI/CIA) and **DIA OSINT Strategy 2024–2028** make OSINT foundational and AI-centric. Governance lineage: **ICD 301** (2006, rescinded 2012) → **ICD 113** designates **CIA as OSINT Functional Manager**; the **Open Source Enterprise** (ex-Open Source Center, ex-FBIS) is the IC's OSINT center of excellence. **DoDI 3115.12** is standing DoD OSINT policy with privacy/oversight rules. **ICD 203 (Analytic Standards)** and **ICD 206 (Sourcing)** are the public "how to reason and source" backbone. The **ODNI 2023 declassified CAI report** is the government's own warning that buyable personal data carries acute privacy/civil-liberties risk.

**NATO.** The **NATO OSINT Handbook (2001)** still supplies the canonical taxonomy; **AJP-2.1** supplies the **Admiralty A–F × 1–6** grading. 2024 brought a "**cultural change**" push and **Exercise *Northern Raven*** (11 nations in Finland — NATO's largest OSINT collection op), plus formal training (NATO School Oberammergau N2-04).

**Western-European NATO members.** The **UK** has the most developed *public* LE-OSINT doctrine: College of Policing/NPCC **Internet Intelligence & Investigations**, the **"JAPAN"** test (Justified, Authorised, Proportionate, Auditable, Necessary), and the crucial **RIPA/IPA threshold** — passive viewing is generally fine, but **building a "pattern of life," sustained monitoring, retaining records, or persona-based interaction** crosses into regulated surveillance/CHIS; **the threshold is low**. The **EU** acts through **Europol** (Ukraine OSINT taskforce), **CEPOL** (standardized LE-OSINT training), and **EU INTCEN**, under **GDPR** (extraterritorial; "public ≠ exempt"), the **EU AI Act** (restricts untargeted scraping/face-DB building), and **Charter Art 7 ≈ ECHR Art 8**. **France** (ROSO), **Germany**, and the **Nordics/Netherlands** are major adopters but publish less document-grade doctrine.

**The citable consensus:** OSINT is foundational; AI + human–machine teaming is the future; work must be lawful/ethical/proportional/auditable with privacy safeguards; CAI is a heightened-risk category; analytic standards and source grading apply; validation/corroboration is what makes it *intelligence*.

---

## 4. Academic Foundations

*(Full detail: [`artifacts/04-academic-foundations.md`](artifacts/04-academic-foundations.md))*

The scholarship clusters around **OSINT+AI** and the **analytic-tradecraft tradition**. The **GELSI systematic review** (AI & Society, 2023) is the standout: it names the field's governance gap (only ~12% of 571 papers address Governance/Ethical/Legal/Social Implications, yet that work is disproportionately influential), articulates the **"three generations of OSINT"** (manual → digital-tool → AI-automated), warns that over-automation degrades OSINT from "fluid" to "crystallized" pattern-matching, and crystallizes **"open ≠ true"** and **Privacy-by-Design**. The 2024 *Int. J. Information Security* review and 2020 *J. Applied Security Research* SLR (a 9-step methodology) reinforce that OSINT's hard problems are **veracity, privacy/governance, and analytic rigor — not tools**.

The **analytic tradition** — Heuer's *Psychology of Intelligence Analysis*, **Analysis of Competing Hypotheses (ACH)**, and Heuer & Pherson's **Structured Analytic Techniques** — gives OSINT a named, defensible bias-control layer (evidence on ACH is positive-but-mixed; use it as discipline, not guarantee). The **Berkeley Protocol** is the scholarly-practitioner methodological standard (see §6). Source-evaluation theory (Admiralty/NATO, SIFT/lateral reading) rounds it out.

---

## 5. Businesses & Organizations That Conduct OSINT (and what they publish)

*(Full detail: [`artifacts/05-industry-and-orgs.md`](artifacts/05-industry-and-orgs.md))*

OSINT is now a substantial commercial sector. **Worth reading**, by category:

- **Platform/tooling vendors:** **Maltego** (graph analysis; *"The Future of OSINT: From Open Sources to AI-Driven Fusion"* whitepaper; acquired Hunchly), **Recorded Future** (largest threat-intel firm; **Insikt Group** reports; ODNI "Sentinel Horizon" cornerstone), **Babel Street** (multilingual; FBI-relied-upon), **Authentic8 Silo for Research** (**managed attribution** + a genuinely good free **OSINT Academy** built with **OSINT Combine**), **Fivecast** (OSINT-fundamentals blog series), **ShadowDragon**, **Skopenow**, **LifeRaft**, **Palantir**, **Digimind**.
- **Threat-intel firms** that publish rigorous OSINT-derived analysis: **Mandiant (Google Threat Intelligence)**, **Microsoft Threat Intelligence (MSTIC)**, CrowdStrike, Cisco Talos, Unit 42.
- **Corporate investigations / due diligence:** **Kroll**, Control Risks, **S-RM**, K2 Integrity, **PGI**, Big-4 forensic units — publish due-diligence and third-party-risk methodology.
- **NGOs/newsrooms (the open tradecraft leaders):** **Bellingcat** (the Online Investigation Toolkit, geolocation challenges, and the seminal mental-hygiene guide), **Centre for Information Resilience** ("Eyes on Russia"), **DFRLab**, **Graphika**, **Citizen Lab**, **Stanford Internet Observatory** (note: wound down/restructured in 2024 amid legal-political pressure — a cautionary signal), **OCCRP/Aleph**, **ICIJ**, **OSINTCurious**.
- **Training/standards:** **SANS** (SEC497/SEC587; the OSINT Summit; excellent free blogs), **Verification Handbook** (EJC), **Berkeley HRC**, **King's College London CSSS**, **CEPOL**, NATO School.

**Curated first reads:** Bellingcat Toolkit → Berkeley Protocol → Verification Handbook → IC/DIA OSINT strategies → GELSI review → Reuters Institute AI piece → Maltego/SANS/Authentic8 tradecraft. *(No pricing per request; "businesses that publish papers worth reading" is the lens.)*

---

## 6. Verification, Preservation & Analysis — the Methodological Core

*(Full detail: [`artifacts/06-verification-and-analysis.md`](artifacts/06-verification-and-analysis.md))*

The **Berkeley Protocol** is the standard to adopt: four principles (**rigorous methodology, legal admissibility, ethical conduct, operational feasibility**), a six-phase cycle (**Online Inquiry → Preliminary Assessment → Collection → Preservation → Verification → Investigative Analysis**), **forensic capture with cryptographic hashing and chain of custody**, and the **digital/physical/psychosocial security** triad. Layer on the **Verification Handbook**'s four W's (**provenance, source, date, location**), **SIFT + lateral reading** for fast triage, **geolocation/chronolocation**, the new **provenance/synthetic-media checks**, and structured analysis (**ACH + Key Assumptions Check**, bias-aware including **automation bias/confabulation**). Express confidence two ways: **Admiralty A–F × 1–6** per item and **ICD-203 high/moderate/low** analytic confidence — always with an explicit **"what we could not establish."**

---

## 7. Ethics, Legal, OPSEC & Well-being — the Guardrails

*(Full detail: [`artifacts/07-ethics-legal-opsec-wellbeing.md`](artifacts/07-ethics-legal-opsec-wellbeing.md))*

- **Ethics:** lawful purpose, **minimization/proportionality**, "public ≠ fair game" (mosaic effect), "open ≠ true," do-no-harm/dignity, transparency (incl. disclosing AI use), independence — with **special caution for CAI/data-broker data** per the ODNI 2023 report.
- **Legal (per requested scope):** **US** (CFAA, CCPA/CPRA, ECPA/SCA, fair use, IC/DoD US-person rules); **UK** (ECHR Art 8 → JAPAN; **RIPA/IPA "pattern-of-life" threshold**; UK GDPR/DPA 2018); **EU** (**GDPR** extraterritorial + "public ≠ exempt"; **EU AI Act** scraping/face-match limits; Charter Art 7). Jurisdiction-agnostic bright lines: no unauthorized access, no deceptive elicitation, no raw breach dumps, no harassment/doxxing, heightened protection for minors/vulnerable subjects.
- **OPSEC → managed attribution:** isolated browser/VM, clean fingerprint, **non-attributable research personas** — with the key nuance that **non-deceptive personas are standard tradecraft while deceptive elicitation is the red line** (a more accurate framing than a blanket sock-puppet ban).
- **Psychosocial safety (the missing pillar):** OSINT exposes practitioners to graphic content; **vicarious trauma** is a recognized occupational hazard. Mitigations (Bellingcat × Dart Centre): low-exposure viewing (mute/grayscale/blur/no-autoplay), dosing/breaks, work/personal separation, peer support, proactive resilience.

---

## 8. Key Judgments (for the skill author)

1. **Keep the skill's spine** — two-mode design, consent/public-interest gate, phased human-in-the-loop workflow, evidence log, negative-findings section. These already align with modern best practice; don't regress them.
2. **The single highest-value addition is an AI/synthetic-media verification layer** with the hard rule that the skill's own model must never authenticate media or assert a geolocation as fact. This is where current OSINT is most exposed and where an LLM-run skill is most dangerous if naïve.
3. **Adopt the Berkeley Protocol vocabulary and evidence standards** — it is authoritative, citable, tool-agnostic, and directly upgrades the skill's handling of capture, preservation, verification, and security.
4. **De-US-center the legal and add EU/UK** — required by the requested scope and genuinely needed; the UK "pattern-of-life" threshold is a concrete, transferable rule the skill lacks.
5. **Fix SOCMINT to 2026 reality** and refresh tooling by *function* so it ages better.
6. **Add the missing well-being pillar** — any skill that can surface distressing content should warn and offer low-exposure techniques.
7. **Respect scope discipline** — fold in military/CTI/conflict material only as "where this fits" context; this is a privacy/journalism skill, not a defense-OSINT manual, and it must stay strictly OSINT (no HUMINT/SIGINT creep).

---

## 9. How to Use This Research to Update the Skill

The artifacts are written to be **loaded directly by an LLM** doing the rewrite:
- **Concepts to add** → [`01-fundamentals`](artifacts/01-fundamentals.md), [`02-modern-practices`](artifacts/02-modern-practices.md).
- **Authority to cite** → [`03-government-doctrine`](artifacts/03-government-doctrine.md), [`04-academic-foundations`](artifacts/04-academic-foundations.md).
- **References & vendors** → [`05-industry-and-orgs`](artifacts/05-industry-and-orgs.md).
- **Methodology to implement** → [`06-verification-and-analysis`](artifacts/06-verification-and-analysis.md).
- **Guardrails to expand** → [`07-ethics-legal-opsec-wellbeing`](artifacts/07-ethics-legal-opsec-wellbeing.md).
- **Tools to refresh** → [`08-tooling-landscape`](artifacts/08-tooling-landscape.md).
- **The change list itself** → [`09-skill-gap-analysis`](artifacts/09-skill-gap-analysis.md) (prioritized, tagged CORE/CONTEXT).
- **Verify before encoding** → [`10-sources`](artifacts/10-sources.md) (reliability-flagged).

Per instruction, **no replacement skill has been drafted.** The next step — when you're ready — is to use [`09-skill-gap-analysis`](artifacts/09-skill-gap-analysis.md) as the work order.

---

## Caveats & confidence

- **High confidence:** the fundamentals, the existence/thrust of US & NATO doctrine, the Berkeley Protocol's role, the AI-disruption thesis, the SOCMINT access collapse, the vendor/NGO landscape.
- **Medium confidence / verify before encoding as fact:** specific forward-dated details (C2PA/SynthID adoption timeline, "2026" tool posts), the DIA strategy's exact issuing-org naming, precise figures.
- **Low confidence / flagged as rhetorical:** the "70–90% of intelligence is OSINT" claim and market-size numbers — widely cited, weakly sourced; attributed, not asserted.
- **Method note:** built from ~30 targeted web searches and document fetches (June 2026). Several primary government PDFs block automated fetchers; their substance was captured via official summaries and reputable secondary reporting, flagged in [`10-sources`](artifacts/10-sources.md).
