# Artifact 02 — Modern & Emerging OSINT Practices (2024–2026)

> Purpose: capture what has *changed* in OSINT recently, so the skill reflects 2026 reality rather than a 2019 playbook. Five forces dominate: **(A) generative AI as both threat and tool**, **(B) the collapse of open social-media access**, **(C) content provenance as a new verification layer**, **(D) the commoditization of geospatial intelligence**, and **(E) OSINT's mainstreaming into conflict, security, and corporate work**.

---

## A. Generative AI is undermining OSINT's core epistemic assumptions

The most important recent development. Per the Reuters Institute (2025, "AI is undermining OSINT's core assumptions"), three foundational assumptions are now under attack:

1. **"If you can locate it, it's more likely to be real."** Geolocation/chronolocation were OSINT's strongest authenticity tools. Now:
   - Synthetic video/imagery is approaching the fidelity needed to pass casual geolocation.
   - Worse, **LLMs confidently mislabel AI-generated content as real**, *inventing* corroborating detail (street names, station names, landmarks) that makes a fake look verified.

2. **Reproducibility / replicability.** OSINT's credibility rests on "anyone with the same public inputs can reproduce the finding." LLM outputs are **non-deterministic** — they vary with prompt wording, timing, user identity/metadata, and silent model updates. AI-assisted findings are not natively reproducible.

3. **Traceable objectivity.** Models "mirror the biases and blind spots of their training data," and underperform on the Global South and underrepresented regions where less open data exists — reintroducing invisible bias under a veneer of neutrality.

**Documented 2025 failure modes (cautionary examples to encode as warnings):**
- Grok and Google Lens both authenticated an AI-generated "train attack" image, adding fake route/station detail.
- ChatGPT and Gemini "verified" an AI-generated Times Square CCTV still, describing the Coca-Cola billboard as proof.
- ChatGPT assigned plausible coordinates (Erez, Kerem Shalom) to entirely synthetic "Gaza border CCTV."
- **Prompt-induced misclassification:** adding Arabic signage to a Spanish flood photo made Gemini place it in Morocco; telling Gemini "I read this was from the LA fires" made it re-describe a Kyiv missile-strike photo as Los Angeles, inventing firefighter details. → **Leading prompts corrupt AI verification.**

**What synthetic media still gets wrong (current human-detectable tells, but "temporary"):** architectural inaccuracies, inconsistent shadows/lighting, physics anomalies (blast/water/object interaction), mismatched infrastructure. Note: "synthetic content only needs to be *plausible*, not *perfect*," and high-fidelity location mimicry is expected to become achievable.

**The constructive flip side — AI as a force multiplier (when bounded):**
- The IC OSINT Strategy and DIA strategy both make **AI/ML and human-language technologies** central, framing **generative-AI tradecraft and human–machine teaming as "the foundation of OSINT in the future."**
- Legitimate uses: translation at scale; transcription; entity extraction; summarization of large corpora; triage/prioritization; pattern/anomaly surfacing across huge datasets; first-pass code/query generation.
- Academic framing (arXiv "OSINT Clinic," 2024): **AI-augmented, human-in-the-loop** collaborative investigation, not autonomous AI.

**Governing rules emerging for AI-assisted OSINT:**
- AI **supplements, never replaces** human judgment ("human in the loop").
- **Disclose** AI assistance in the workflow; never present AI output as a primary source.
- **Never treat an LLM as a verification oracle** (it cannot reliably detect fakes and will confabulate corroboration).
- Re-assert **transparency/traceability** as the truth-defense: document every step so others can replicate despite AI's non-determinism.
- Prefer practitioners with **local/contextual/linguistic expertise** — best equipped to catch AI manipulation.

---

## B. SOCMINT has gotten much harder — the "great closing" of platform access

The single biggest *operational* regression since 2023. Open social-media intelligence used to be cheap and scriptable; it isn't anymore.

- **X / Twitter:** API priced out of reach for most researchers/journalists; legacy scrapers (Twint, GetOldTweets3, many browser extensions) are dead. Real-time monitoring at scale is now costly or impossible for small teams.
- **Meta / CrowdTangle:** shut down **14 August 2024**. The replacement, the **Meta Content Library**, is gated behind academic IRB approval, routed through ICPSR (University of Michigan), **excludes for-profits** (most newsrooms), and has far fewer features. CrowdTangle had ~100k registered users; the Content Library reportedly reaches only a few hundred researchers.
- **Reddit, others:** tightened API terms/pricing in the same wave.

**Consequences for practice:**
- A widening capability gap between teams that adapted and teams "still running 2019 playbooks."
- More reliance on: native platform UIs + careful manual collection; archived/cached copies; paid commercial SOCMINT vendors (who hold licensed access); cross-platform pivoting; and "less-defended" platforms.
- Heightened importance of **archiving on capture** — social content "appears and disappears in real time."

→ Any skill that lists `site:twitter.com`/`site:facebook.com` dorks as if open access persists is **out of date**; queries still help for indexing, but the skill should flag access limits and pivot to archives + licensed sources.

---

## C. Content provenance & synthetic-media detection — the new verification layer

A genuinely new toolset that did not exist in earlier OSINT guides. The industry has converged on a **two-layer standard**:

1. **C2PA / Content Credentials** — the Coalition for Content Provenance and Authenticity (Adobe, Microsoft, BBC, Intel, Sony, Nikon, Truepic, OpenAI, Google, Meta). A **signed metadata manifest** (JSON-LD) cryptographically bound to a file, recording the capturing device/model and every edit. **C2PA 2.1 was ratified in 2025 and is now an ISO standard (ISO/IEC 22144).** Weakness: a screenshot or re-encode strips the manifest.
2. **Invisible watermarking — SynthID (Google) and equivalents** — a signal embedded across pixels/audio/tokens that survives cropping, compression, and screenshotting. Complements C2PA precisely where the manifest fails.

By 2025–2026, major generators (e.g., OpenAI image output) began embedding **both** SynthID watermarks and C2PA manifests.

**Practice implications:**
- Add a **provenance-check step**: inspect Content Credentials (e.g., verify.contentauthenticity.org / C2PA viewers) and run available watermark/detector tools.
- Understand the **limits**: absence of a credential proves nothing (most real content has none); presence can be spoofed/stripped; detectors are probabilistic and adversarially fragile. Provenance is **one signal among many**, never dispositive.
- Classic forensics still apply (reverse image search, ELA, metadata/EXIF, error/shadow/reflection analysis) but are **necessary-not-sufficient** against modern synthesis.

---

## D. Geospatial OSINT has been commoditized

GEOINT-from-open-sources is now a mainstream OSINT capability, driven by cheap/free imagery and a dense tool ecosystem.

- **Free/low-cost imagery:** ESA **Sentinel‑2** (~10 m, ~5-day revisit) via Copernicus/Sentinel Hub; USGS **Landsat 8/9** via EarthExplorer; **NASA Worldview** (near-real-time); **Google Earth Pro** (historical timeline + change detection).
- **Commercial/tasked:** **Maxar** (high-res, IC backbone), **Planet Labs** ("Dove" daily revisit), **BlackSky** (high-revisit low-latency), and crucially **SAR** providers — **Capella Space** and Finland's **ICEYE** — which image **through cloud and darkness**. **SkyFi** offers on-demand consumer tasking.
- **Techniques:** photo/video **geolocation** (cross-referencing landmarks, signage, terrain against Maps/Street View/OSM/Overpass Turbo); **chronolocation** (shadow length/azimuth via SunCalc; foliage/snow; known dated events); change detection; AI-assisted geolocation tools (e.g., GeoSpy) — used with caution given §A failure modes.
- **Context:** the Ukraine war made commercial satellite imagery a near-real-time public intelligence source (see §E).

---

## E. OSINT has mainstreamed — conflict, national security, cyber, and corporate

- **Conflict monitoring (the Ukraine inflection point):** the Russian invasion of Ukraine is widely described as OSINT's turning point — from "supplementary/less-trusted" to central. **Bellingcat** mapped civilian-target strikes and documented potential war crimes; **Oryx** became a leading source for visually-confirmed equipment losses; Middlebury Institute analysts famously flagged the invasion from a **Google Maps traffic jam** hours before it began. OSINT now contributes to **war-crimes accountability** (Berkeley Protocol, Europol's Ukraine OSINT taskforce; Artifact 03).
- **National-security adoption:** US IC and DIA OSINT strategies (2024); **NATO's "cultural change" push** and **Exercise Northern Raven (2024)** — 11 nations, the largest OSINT collection op in NATO history (Artifact 03).
- **Cyber threat intelligence (CTI):** OSINT is the reconnaissance backbone — **Shodan/Censys** for internet-exposed assets and attack surface, certificate transparency, breach data, dark-web monitoring; formalized as MITRE ATT&CK **Reconnaissance (TA0043)**. Standard in red-teaming, pentest recon, and CTI.
- **Corporate / financial:** due diligence, KYC/AML, third-party & supply-chain risk, M&A, brand/physical-security threat intelligence — now a large commercial market (Artifact 05). Vendor reporting notes a sizable share of 2025 breaches involved third-party/supply-chain reconnaissance.
- **Fusion intelligence:** the dominant industry narrative (e.g., Maltego's "Future of OSINT") is OSINT moving "from open sources to **AI-driven fusion**" — OSINT increasingly **integrated/consolidated with other intelligence streams** rather than standing alone, with analysts shifting from collectors to **validators and sense-makers** as automation absorbs routine collection.

---

## Cross-cutting shifts in the analyst's role

- From **finding** information (scarce, hard) → to **filtering, validating, and contextualizing** it (abundant, polluted).
- From **deterministic tools** → to **probabilistic AI** that must be supervised and disclosed.
- From **"is it findable?"** → to **"is it authentic, and can I prove how I know?"**
- Rising premium on: **provenance/traceability**, **local & linguistic context**, **AI literacy**, and **archival discipline**.

---

## Implications for the `osint_audit` skill

1. **Add a synthetic-media / AI-content caution** to Module G (Image) and Module M (Geospatial): reverse search + ELA + InVID are no longer sufficient; add **provenance checks (C2PA/Content Credentials, SynthID)** and an explicit warning that **LLMs (including the one running the skill) cannot reliably detect fakes and will confabulate corroboration.**
2. **Update SOCMINT (Module B)** to reflect API/platform closures: flag that open scraping is largely gone, prioritize archives + native UI + licensed sources, and **archive-on-capture**.
3. **Add an "AI-assisted workflow" governance note**: human-in-the-loop, disclose AI use, never cite AI as a source, preserve reproducibility via step documentation.
4. **Add geospatial depth**: Sentinel/Landsat/Maxar/Planet/SAR sources and chronolocation (SunCalc already present — extend it).
5. Position the skill within the broader **"validate & contextualize, don't just find"** posture that now defines modern OSINT.
