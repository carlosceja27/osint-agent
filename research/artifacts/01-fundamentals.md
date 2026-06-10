# Artifact 01 — OSINT Fundamentals (The Inventory)

> Purpose: a structured inventory of the *durable fundamentals* that constitute OSINT as a discipline — the concepts that should anchor any OSINT skill regardless of which tools are current. Scope is **strictly OSINT**; adjacent disciplines (HUMINT, SIGINT, etc.) appear only where they define OSINT by contrast or describe how OSINT feeds all-source/fusion work.

---

## 1. Definitions (and why the wording matters)

There is no single universal definition, but the authoritative ones converge. The differences are operationally meaningful.

| Source | Definition | Notable wording |
|---|---|---|
| **US IC OSINT Strategy 2024–2026 (ODNI/CIA)** | "Intelligence derived exclusively from publicly or commercially available information that addresses specific intelligence priorities, requirements, or gaps." | Explicitly folds **commercially available information (CAI)** into OSINT; calls OSINT the **"INT of first resort."** |
| **US DoD Instruction 3115.12** | OSINT is intelligence "produced from publicly available information that is collected, exploited, and disseminated in a timely manner to an appropriate audience for the purpose of addressing a specific intelligence requirement." | Emphasizes the *production* chain, not just the source. |
| **NATO OSINT Handbook (2001)** | Intelligence "produced from publicly available information that is collected, exploited, and disseminated… to address a specific intelligence requirement." | Origin of the widely used four-tier source taxonomy (below). |
| **Academic (systematic-review consensus)** | "The search, collection, analysis, and use of information from open sources, as well as the techniques and tools used." | Treats OSINT as *both* a product and a method. |

**Key conceptual distinction — information vs. intelligence.** Open-source *information* is raw, publicly available content. *OSINT* exists only once that information has been **collected against a requirement, processed, analyzed, and disseminated**. "Doing OSINT" is not "finding stuff online"; it is the disciplined transformation of public data into decision-useful, sourced, verifiable intelligence.

**The contested "70–90%" claim.** It is widely repeated (in NATO statements, vendor marketing, and academic intros) that OSINT comprises 70–90% of all intelligence material. Treat this as a *rhetorical/heuristic* figure, not a measured statistic — it is unsourced in most citations and is used to argue for OSINT's importance, not as an empirical finding.

---

## 2. The NATO four-tier source taxonomy (still the cleanest mental model)

From the NATO OSINT Handbook — distinguishes *maturity* of open-source material:

1. **Open Source Data (OSD)** — raw, unfiltered primary material (a photo, a tweet, a sensor reading, a filing).
2. **Open Source Information (OSIF)** — data that has been collated, filtered, edited, or organized (a news article, a report, an edited dataset).
3. **Open Source Intelligence (OSINT)** — OSIF that has been deliberately discovered, discriminated, distilled, and disseminated to answer a specific requirement.
4. **Validated OSINT (OSINT‑V)** — OSINT for which there is **high confidence in provenance and accuracy**, typically because it has been corroborated by, or assessed alongside, classified or otherwise trusted sources.

→ This ladder (data → information → intelligence → validated) is the single most useful framing to teach the difference between "I found it" and "I can stand behind it."

---

## 3. Related sub-types / sourcing families *within* OSINT

These are **collection categories of open-source work**, not separate intelligence disciplines. Naming them helps an analyst plan coverage:

- **SOCMINT** — Social Media Intelligence (open social platforms). Now the hardest sub-type because of platform API closures (see Artifact 02).
- **Open-source GEOINT** — geospatial/geolocation work from commercial & free satellite imagery, mapping, Street View, and photo/video geolocation. (Distinct from classified national GEOINT.)
- **Open-source / publicly available IMINT** — imagery and video analysis and verification.
- **Open-source technical / cyber recon** — DNS, WHOIS/RDAP, certificate transparency, internet-scan data (Shodan/Censys), breach-notification data. Maps to MITRE ATT&CK **Reconnaissance (TA0043)**.
- **Financial / corporate OSINT** — registries, filings, sanctions, beneficial-ownership, leaks databases.
- **PAI** (Publicly Available Information) and **CAI** (Commercially Available Information) — see §6; these are *source categories* now central to policy.

---

## 4. The Intelligence Cycle (the spine of any OSINT workflow)

The classic 5-phase cycle, as applied to OSINT:

1. **Planning & Direction** — define the requirement / intelligence question; derive Essential Elements of Information (EEIs); build a collection plan; set scope, legal/ethical boundaries, and OPSEC posture *before* collecting.
2. **Collection** — gather PAI/CAI against the plan; record provenance and queries as you go (chain of custody starts here, not at reporting).
3. **Processing & Exploitation** — translate, transcribe, de-duplicate, normalize, extract entities, organize. (Where automation/AI now does the heavy lifting.)
4. **Analysis & Production** — turn information into intelligence: corroborate, weigh, apply structured analytic techniques, assign confidence, write the assessment.
5. **Dissemination & Feedback** — deliver to the consumer in a usable form; capture feedback, which re-tasks the next cycle.

**Caveats the modern literature stresses:** the "cycle" is idealized and linear; real OSINT is iterative and non-linear (you re-plan mid-collection; verification loops back). Treat it as a *checklist of functions that must all happen*, not a rigid sequence.

---

## 5. Source reliability & information credibility grading — the Admiralty / NATO System

A core fundamental the field inherited from military intelligence and standardized in **NATO AJP‑2.1**. Two **independent** axes (the "6×6" or "Admiralty Code"):

**Source reliability (A–F):**
- **A** — Completely reliable (proven track record)
- **B** — Usually reliable
- **C** — Fairly reliable
- **D** — Not usually reliable
- **E** — Unreliable
- **F** — Reliability cannot be judged

**Information credibility (1–6):**
- **1** — Confirmed by other independent sources
- **2** — Probably true
- **3** — Possibly true
- **4** — Doubtful
- **5** — Improbable
- **6** — Truth cannot be judged

A finding is graded as a pair, e.g. **B2**. Crucially, **source ≠ content**: a normally-reliable source can carry an uncorroborated claim (B6); an unknown source can carry a confirmed fact (F1). Much raw OSINT legitimately arrives **F6** and must be upgraded by corroboration. This two-axis discipline is more rigorous than a single "confidence" label.

---

## 6. PAI vs. CAI — the modern sourcing distinction that drives policy

- **Publicly Available Information (PAI)** — lawfully and freely accessible to the public.
- **Commercially Available Information (CAI)** — information available for *purchase* (data brokers, location data, ad-tech datasets, marketing/identity graphs). The US IC OSINT Strategy explicitly counts CAI within OSINT.

Why it matters: the **June 2023 ODNI Senior Advisory Group declassified report on CAI** found the IC buys large volumes of CAI, that CAI "can reveal sensitive and intimate information about individuals," and that agencies often did not know how much they held or how it was used. CAI is the hottest legal/ethical fault line in OSINT — the place where "it's public/buyable" collides hardest with privacy. (See Artifacts 03 and 07.)

---

## 7. The three "generations" of OSINT (a useful historical lens)

From the GELSI systematic review (Springer, *AI & Society*, 2023):

1. **First generation** — manual document retrieval and translation (pre-digital; "the original OSINT" of monitoring foreign press/broadcasts).
2. **Second generation** — digital tooling: linguistic, geospatial, network/link-analysis, and visual-forensics tools operated by humans.
3. **Third generation** — AI-dependent, automated collection and analysis at scale.

The review's warning: AI embodies "crystallized intelligence" (pattern application), whereas OSINT's value historically came from bridging crystallized *and* "fluid" intelligence (creative, contextual problem-solving). Over-automation risks degrading OSINT into rigid pattern-matching.

---

## 8. What separates professional OSINT from casual searching (the fundamentals checklist)

A practitioner-grade OSINT effort exhibits **all** of the following — these are the load-bearing fundamentals:

- [ ] **Requirement-driven** — a defined question and scope, not open-ended snooping.
- [ ] **Lawful & ethical basis** — established *before* collection; documented.
- [ ] **OPSEC / managed attribution** — the investigator does not contaminate or tip off the subject (Artifact 07).
- [ ] **Provenance capture** — every finding records source, URL, timestamp, the exact query/path used, and an archived copy (chain of custody).
- [ ] **Source/credibility grading** — explicit, two-axis where possible (§5).
- [ ] **Corroboration** — ≥2 independent sources before a claim is treated as fact ("open ≠ true").
- [ ] **Structured analysis** — bias-aware techniques (ACH and others; Artifact 06), not just intuition.
- [ ] **Verification of media** — geolocation, chronolocation, reverse search, metadata, provenance signals (Artifacts 02, 06).
- [ ] **Reproducibility** — another analyst using the same public inputs can reach the same finding (now threatened by non-deterministic AI; Artifact 02).
- [ ] **Minimization & proportionality** — collect only what the requirement needs.
- [ ] **Confidence-rated, sourced reporting** — with an explicit "what we could *not* establish."

---

## Implications for the `osint_audit` skill

- The skill is **operationally strong but conceptually thin**: it jumps straight to search modules with no grounding in the information→intelligence ladder, the intelligence cycle, or source/credibility grading. Adding a short **"Fundamentals"** preamble would let the LLM reason about *why* a step matters, not just execute it.
- The skill's single-axis confidence labels (*Confirmed / Likely / Possible*) could be **upgraded toward the two-axis Admiralty/NATO model** (or at least cross-referenced to it) for defensibility.
- The skill should explicitly name **PAI vs. CAI**, because its Module F (data brokers) *is* CAI collection and carries the heightened privacy concerns the 2023 ODNI report flagged.
- Reinforce the **"open ≠ true"** principle as a first-class rule, not just a verification footnote.
