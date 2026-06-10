# Artifact 09 — Gap Analysis & Improvement Recommendations for `osint_audit`

> Purpose: bridge research → skill update. This **analyzes** the existing skill against the research and **recommends** changes. Per instruction, it does **not** draft a replacement skill — it tells a future author/LLM *what* to change and *why*, with priorities. References are to the existing `skill.md` (osint_audit v2.0).

> **Scope-fit reminder:** `osint_audit` is a **person/entity-centric investigative workflow** with two modes (privacy self-audit; public-interest journalism). Much of the research (military/NATO doctrine, CTI/red-team recon, conflict GEOINT) is **contextual framing**, not core scope. Recommendations below are tagged **[CORE]** (directly improves the skill's mission) or **[CONTEXT]** (useful framing/reference, lower priority).

---

## 1. What the skill already does well (preserve these)

- **Two-mode design** with an explicit **consent/public-interest gate** — ethically sound and rare.
- **Phased, human-in-the-loop workflow** (Intake → Plan → **Review gate** → Execute → Report → Monitor) — already embodies "human-in-the-loop," which the AI-era literature demands.
- **Strong SPJ-based ethics**, minimization, "no raw breach dumps," "no password-protected access."
- **Excellent breadth of modules (A–P)** and **public-records depth** (esp. US).
- **Evidence logging + archive URLs + "What Wasn't Found"** section — genuinely good practice (negative findings prevent false certainty).
- **Data-broker opt-out directory** and **monitoring cadence** — practical and current (incl. CA DROP 2026).

→ **Do not regress these.** The recommendations *augment*, not replace.

---

## 2. Gaps, mapped to research artifacts

| # | Gap | Evidence / Source artifact | Severity |
|---|---|---|---|
| G1 | **No conceptual foundation** — jumps to modules with no definition, information→intelligence ladder, intelligence cycle, or source-grading theory. | Artifact 01 | High **[CORE]** |
| G2 | **No synthetic-media / AI-content handling.** Image (G) & Geospatial (M) modules assume reverse-search/ELA suffice; no provenance (C2PA/SynthID); no warning that **LLMs can't detect fakes & will confabulate**. | Artifacts 02, 06 | **Critical [CORE]** |
| G3 | **SOCMINT module (B) is out of date** — lists `site:twitter.com`-style dorks as if open access persists; ignores API closures, CrowdTangle shutdown, archive-on-capture. | Artifact 02 §B | High **[CORE]** |
| G4 | **Legal coverage is US-only** — CFAA/CCPA/GDPR mentioned once; no UK (JAPAN, RIPA/IPA pattern-of-life threshold) or EU (GDPR extraterritorial, EU AI Act) despite requested European scope. | Artifacts 03, 07 | High **[CORE]** |
| G5 | **No psychosocial-safety / vicarious-trauma guidance** — skill can surface graphic material (criminal records, abuse, conflict) with no content-warning or low-exposure technique. | Artifact 07 §4 | High **[CORE]** |
| G6 | **OPSEC is shallow & possibly over-restrictive** — "VPN + burner email" only; no managed attribution (isolated browser/VM, fingerprint, persona separation); blanket sock-puppet ban conflates **research personas (standard)** with **deceptive elicitation (the real red line)**. | Artifact 07 §3 | Medium **[CORE]** |
| G7 | **Verification/evidence handling is informal** — good logging, but no Berkeley-Protocol-grade **forensic capture + hashing + chain of custody**, no named verification standard. | Artifact 06 §1 | High **[CORE]** |
| G8 | **Analysis layer is thin** — "cross-reference + confidence label" with no structured technique (ACH/Key Assumptions) and no bias-awareness (incl. the LLM's own confabulation/automation bias). | Artifacts 04 §2, 06 §6 | Medium **[CORE]** |
| G9 | **Single-axis confidence** (Confirmed/Likely/Possible) — no mapping to the **Admiralty/NATO A–F × 1–6** standard or ICD-203 analytic-confidence language. | Artifacts 01 §5, 06 §7 | Medium **[CORE]** |
| G10 | **No PAI/CAI framing** — Module F (data brokers) *is* CAI collection but isn't tied to the ODNI 2023 CAI findings, the mosaic effect, or heightened-risk handling. | Artifacts 01 §6, 03 §1.4, 07 | Medium **[CORE]** |
| G11 | **Tooling appendix pre-dates** provenance tools, forensic capture (Hunchly), OpenSanctions, Overpass Turbo, Censys/Amass, SAR/Sentinel. | Artifact 08 | Medium **[CORE]** |
| G12 | **No SIFT/lateral-reading triage** for quickly assessing sources/claims before deep collection. | Artifact 06 §3 | Low-Med **[CORE]** |
| G13 | **No citation of recognized authority** — asserts good practice without anchoring to ICD 203/206, NATO/Admiralty, Berkeley Protocol, GELSI. | Artifacts 03, 04 | Low **[CORE]** |
| G14 | **No positioning vs. modern OSINT context** (defense adoption, Ukraine inflection, fusion, CTI) — fine for scope, but a one-paragraph "where this fits" would orient users. | Artifacts 02 §E, 03, 05 | Low **[CONTEXT]** |

---

## 3. Prioritized recommendations

### Tier 1 — do first (highest value, on-mission)
1. **Add a "Fundamentals & Posture" preamble** [G1]: 1 page — OSINT definition, information→intelligence ladder, the intelligence cycle as a function-checklist, **"open ≠ true," "public ≠ fair game,"** and human-in-the-loop. Lets the model *reason*, not just execute.
2. **Insert an AI/synthetic-media verification layer** [G2] across Modules G & M and the Verification section: provenance checks (C2PA/Content Credentials, SynthID), classic forensics, **and a hard rule: the skill's own LLM must never declare media authentic or geolocate as fact — it confabulates corroboration.** Include the 2025 failure examples as cautionary notes.
3. **Modernize SOCMINT (Module B)** [G3]: state the access reality (API/scraper closures, CrowdTangle→Content Library), prioritize **archives + native UI + licensed sources**, mandate **archive-on-capture**, drop dead tools.
4. **Expand legal to UK + EU** [G4]: add **ECHR Art 8 / UK "JAPAN" + RIPA/IPA pattern-of-life threshold**, **GDPR extraterritorial reach & "public ≠ exempt,"** **EU AI Act** limits on scraping/face-matching. Keep US.
5. **Add a psychosocial-safety section** [G5]: content warning, low-exposure viewing (mute/grayscale/blur/no-autoplay), dosing/breaks, peer support — cite Bellingcat × Dart Centre.

### Tier 2 — strong upgrades
6. **Re-anchor verification/evidence to the Berkeley Protocol** [G7]: name its 6 phases; add **forensic capture + cryptographic hashing + custody**; add the **digital/physical/psychosocial security** triad.
7. **Add a structured-analysis step** [G8]: **SIFT** triage (front-end) + **ACH-lite + Key Assumptions Check** (analysis), with an explicit **bias watch-list incl. automation bias/confabulation**.
8. **Modernize OPSEC into "managed attribution"** [G6]: isolated browser/VM, fingerprint control, persona separation; **distinguish non-deceptive research personas (acceptable) from deceptive elicitation (prohibited / LE-authorized only).**
9. **Offer two-axis confidence** [G9]: map current labels to **Admiralty A–F × 1–6** and/or ICD-203 high/moderate/low; keep "What Wasn't Found."
10. **Reframe data brokers as CAI** [G10]: tie Module F to **ODNI 2023 CAI** rationale + **mosaic effect** + minimization, alongside the existing opt-out mechanics.

### Tier 3 — polish & durability
11. **Refresh tooling** [G11] per Artifact 08; consider a **by-function taxonomy** (ages better than brand lists).
12. **Add SIFT cheat card** [G12] and **authority citations** [G13] (ICD 203/206, NATO/Admiralty, Berkeley, GELSI, Verification Handbook).
13. **One-paragraph "where this fits"** [G14] situating the skill in modern OSINT.

---

## 4. Suggested structural shape (for the eventual rewrite — NOT drafted here)

Conceptually, the updated skill would gain **three new layers** wrapped around the existing module engine:
- **A "posture" layer up front** (fundamentals, ethics+legal incl. EU/UK, OPSEC/managed attribution, well-being, AI-use governance).
- **The existing collection modules** (A–P), refreshed for SOCMINT reality + provenance + tooling.
- **A strengthened "make it defensible" layer** (Berkeley-grade capture/hashing, SIFT+ACH analysis, two-axis confidence, reproducibility, negative findings).

The two-mode design, phased workflow, review gate, and reporting structure **stay** — they're assets.

---

## 5. Explicitly out of scope for this skill (don't bloat it)
- Full military/NATO collection-management doctrine, CTI red-team recon playbooks, and deep conflict-GEOINT tradecraft are **[CONTEXT]** — reference them in a "further reading / where this fits" note, but do **not** turn the privacy/journalism skill into a defense-OSINT manual.
- No pricing/vendor-procurement content (per instruction).
- Keep adjacent INTs (HUMINT/SIGINT) out except as the one-line "OSINT feeds all-source fusion" framing.
