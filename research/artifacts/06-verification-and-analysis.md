# Artifact 06 — Verification, Preservation & Analysis Methodology

> Purpose: the methodological core — *how to turn open-source information into defensible intelligence*. Three standards anchor this: the **Berkeley Protocol** (the overarching standard), the **Verification Handbook** (media verification), and **SIFT/lateral reading** (rapid source evaluation) — plus **structured analysis** and **confidence expression**.

---

## 1. The Berkeley Protocol on Digital Open Source Investigations (the standard to adopt)

**What it is:** the international standard (UC Berkeley Human Rights Center + UN OHCHR, launched Dec 2020; translated into all UN languages; in active use by Ukrainian war-crimes prosecutors and UN bodies) for the **identification, collection, preservation, verification, and analysis** of digital open-source information to a **legally admissible, ethically sound, methodologically rigorous** standard. It is deliberately **tool-agnostic** — principles that survive technology change.

**Four foundational principles:**
1. **Rigorous methodology** — disciplined, documented, repeatable process bridging technology, law, and ethics.
2. **Legal admissibility** — collection/preservation that can withstand evidentiary scrutiny.
3. **Ethical conduct** — "how we gather evidence matters as much as what we find" (security, dignity, minimization, do-no-harm).
4. **Operational feasibility** — works under real-world resource constraints.

**The six-phase investigative cycle (Berkeley Protocol, Ch. 6):**
1. **Online Inquiry** — identify potentially relevant sources via advanced search/OSINT techniques and continuous monitoring; **document search strategies**.
2. **Preliminary Assessment** — evaluate relevance and initial reliability; filter obvious unreliables.
3. **Collection** — capture with **forensic correctness**: digital artifacts remain **unchanged** during capture.
4. **Preservation** — secure, durable archiving balancing accessibility and protection (integrity over time).
5. **Verification** — multiple analytical approaches *in concert*: fact-checking, **metadata analysis, geolocation, chronolocation, cross-referencing/corroboration.**
6. **Investigative Analysis** — transform verified data into conclusions while **documenting analytical reasoning others can evaluate.**

**Preservation / chain-of-custody specifics it demands:**
- **Cryptographic hashing** of collected items (e.g., capture file + record its hash) to prove the item is unaltered.
- Capture **contextual metadata**: source URL, capture date/time (with timezone), tool used, collector identity, and the **query/navigation path** that found it.
- **Original + archived copy** (the page can change/disappear); maintain an evidence log and a documented custody trail.

**The three-part security framework (a Berkeley Protocol signature — and a gap in most skills):**
- **Digital security** — protect the investigation and investigator: managed attribution, isolated/secure devices, encryption, access control, avoiding tipping the subject (Artifact 07).
- **Physical security** — protect investigators, sources, witnesses, victims from physical retaliation.
- **Psychosocial security** — protect mental health from exposure to graphic/traumatic content (Artifact 07 §wellbeing).

→ **Adopt the Berkeley Protocol's vocabulary and phases as the skill's methodological backbone.** It is the most authoritative, citable, and modern framework available and directly upgrades evidence handling.

---

## 2. Verification Handbook (media-verification canon)

By Craig Silverman / European Journalism Centre (DataJournalism.com). Editions: original, **Investigative Reporting**, and **Disinformation & Media Manipulation**. Core verification of user-generated/online content checks four things:

1. **Provenance** — is this the *original* piece of content (not a re-upload/recycle)?
2. **Source** — who captured/uploaded it; what's their track record/access?
3. **Date** — when was it *actually* created (vs. uploaded)?
4. **Location** — where was it *actually* captured?

Methods: reverse image/video search, frame extraction, EXIF/metadata, weather/shadow cross-checks, witness/upstream tracing, and corroboration across independent uploads.

---

## 3. SIFT + lateral reading (fast source evaluation)

**SIFT** (Mike Caulfield) — a rapid, four-move triage for any source/claim:
- **S — Stop** (don't react/share before checking; check your own emotional trigger).
- **I — Investigate the source** (who is behind it, what's their agenda/expertise).
- **F — Find better/other coverage** (what do *other* sources say about the claim?).
- **T — Trace** claims, quotes, and media back to the **original context**.

**Lateral reading** — leave the page and open new tabs to check the source *against the wider web*, the way professional fact-checkers do, instead of reading "vertically" within the suspect page. Empirically outperforms intuition and even subject-expertise.

→ SIFT/lateral reading is the **lightweight front-end**; the Berkeley Protocol is the **heavyweight backbone**. Use SIFT for triage, Berkeley for anything that must hold up.

---

## 4. Geolocation & chronolocation (the OSINT verification workhorses)

- **Geolocation:** match landmarks, signage/language, road markings, architecture, vegetation, terrain, and shadows against **satellite imagery + Street View + OpenStreetMap/Overpass Turbo** and historical imagery (Google Earth Pro timeline). Bellingcat's toolkit/challenges are the training canon.
- **Chronolocation:** establish *when* via **shadow direction/length** (SunCalc / shadow-azimuth math), sun/season cues, foliage/snow, construction state in dated satellite imagery, and known dated events in-frame.
- **2026 caveat (Artifact 02 §A):** AI can fabricate plausible scenes and LLMs will *confabulate* geolocations. Geolocation remains powerful but is **no longer self-validating** — pair it with provenance and source corroboration.

---

## 5. Synthetic-media & provenance checks (new, mandatory layer)

In order of evidentiary weight, lowest-to-highest reliability — **use several, trust none alone**:
- **Provenance signals:** C2PA / **Content Credentials** manifest (e.g., verify.contentauthenticity.org); **SynthID** and other watermarks. *Absence ≠ fake; presence can be stripped/spoofed.*
- **Classic forensics:** reverse image search, error-level analysis (FotoForensics), EXIF/metadata, noise/lighting/shadow/reflection consistency.
- **Detector tools:** deepfake/synthetic detectors (probabilistic, adversarially fragile — treat as a weak prior).
- **Human contextual analysis:** local/linguistic knowledge, physics/architecture plausibility — currently the most reliable backstop.
- **Hard rule:** **never** rely on an LLM (including the skill's own model) to declare media authentic; it cannot, and will invent corroboration.

---

## 6. Structured analysis & bias control (turning verified facts into a judgment)

- **Corroboration rule:** ≥2 **independent** sources before a claim is reported as fact ("open ≠ true"). Watch for **circular reporting** (sources echoing one origin).
- **Analysis of Competing Hypotheses (ACH):** list all plausible explanations; matrix evidence against each; actively seek **disconfirming** evidence; prefer the **least-disconfirmed** hypothesis (Artifact 04 §2).
- **Key Assumptions Check:** write down what you're assuming; ask what breaks the analysis if an assumption is wrong.
- **Bias awareness:** confirmation bias, anchoring, mirror-imaging, premature closure (Heuer). For LLM-run OSINT, add **automation bias** and **confabulation** to the watch-list.

---

## 7. Expressing confidence (two compatible schemes)

- **Two-axis (Admiralty / NATO AJP-2.1):** source reliability **A–F** × information credibility **1–6** (e.g., **B2**). Best for per-item grading.
- **Analytic-confidence language (ICD 203 style):** **high / moderate / low confidence**, with **likelihood/probability** words used consistently (e.g., "likely," "probable," "almost certainly"), and explicit statement of **what is assessed vs. assumed vs. unknown**.
- Always include a **"what we could not establish / negative findings"** section to prevent false-certainty by omission.

---

## A reference verification/handling workflow (composite, skill-ready)

1. **Triage** with SIFT (Stop → Investigate → Find → Trace).
2. **Capture forensically** (Berkeley): archive original + snapshot, record URL/timestamp/timezone/tool/query, **hash** the artifact.
3. **Verify the four W's** (Verification Handbook): provenance, source, date, location.
4. **Geolocate / chronolocate** where applicable; **check provenance/watermarks** for AI content.
5. **Corroborate** with ≥2 independent sources; check for circular reporting.
6. **Analyze** with ACH + Key Assumptions Check; flag bias.
7. **Grade** (Admiralty A–F/1–6) and **state analytic confidence** (high/moderate/low).
8. **Document reasoning** so another analyst can reproduce it; record negative findings.

---

## Implications for the `osint_audit` skill

- The skill's "Verification Notes" (Phase 2 §4) and evidence log are good but **informal**. Re-anchor them to the **Berkeley Protocol** (named phases, **hashing**, forensic capture, custody) and add the **digital/physical/psychosocial security** triad.
- Add **SIFT** as the quick-triage method and **ACH + Key Assumptions Check** as the analysis method.
- Add the **synthetic-media/provenance layer** to image/video and geospatial modules, with the explicit "LLM is not a fake-detector" rule.
- Offer the **two-axis Admiralty grading** as an upgrade to (or mapping for) the current *Confirmed/Likely/Possible* labels, and keep the **negative-findings** section it already has (a genuine strength).
