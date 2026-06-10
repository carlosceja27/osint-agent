# Artifact 07 — Ethics, Legal Frameworks, OPSEC & Practitioner Well-being

> Purpose: the guardrails. Four pillars: **(1) Ethics**, **(2) Legal** (US + UK + EU, per requested scope), **(3) OPSEC / managed attribution**, **(4) Psychosocial safety**. The existing skill is already strong on ethics; this artifact deepens legal (esp. Europe), modernizes OPSEC, and adds the missing well-being dimension.

---

## 1. Ethics — the consensus principles

Drawing together SPJ (already in the skill), the Berkeley Protocol, the GELSI literature, and government doctrine:

- **Lawful & legitimate purpose** — a defined, justifiable reason before collecting (public-interest test for journalism; consent for self-audit).
- **Minimization & proportionality** — collect only what the requirement needs; the intrusion must be proportionate to the purpose (UK "JAPAN"; GDPR data-minimization; ICD privacy rules).
- **"Public ≠ fair game."** The GELSI consensus: *"the mere fact that some information is public does not mean privacy concerns should be discarded."* Aggregation of individually-public data can itself be a privacy harm (the **mosaic effect**).
- **"Open ≠ true."** Verify before asserting; assume datasets are polluted by error and deliberate disinformation.
- **Do no harm / dignity** — weigh harm to subjects, sources, bystanders (esp. minors, vulnerable people, victims); avoid enabling doxxing/harassment.
- **Transparency & accountability** — document methodology; disclose AI assistance; correct errors; enable replication.
- **Independence & objectivity** — bias-aware analysis (ICD 203); no fabrication; distinguish fact / assessment / assumption.
- **Special caution for CAI/data-broker data** — the ODNI 2023 CAI report is the field's clearest statement that *buyable* personal data carries heightened privacy/civil-liberties risk (Artifacts 01 §6, 03 §1.4).

---

## 2. Legal frameworks (by jurisdiction)

> Not legal advice; an awareness map. The investigator's jurisdiction **and** the subject's/data's jurisdiction can both apply.

### 2.1 United States
- **CFAA (Computer Fraud and Abuse Act)** — no access without/exceeding authorization (no password-protected accounts, no circumventing access controls). OSINT must stay on genuinely public access.
- **Privacy / civil-liberties:** US-person protections in IC/DoD rules (DoDI 3115.12; EO 12333; intelligence-oversight regime); **CAI guidance** emerging from the ODNI 2023 report.
- **State law:** **CCPA/CPRA** (CA) and other state privacy laws; **anti-stalking/harassment** statutes; **state public-records** rules vary.
- **Stored Communications Act / ECPA**, **fair use** (republishing media), **defamation** (publication risk).
- **California DROP** (data-broker deletion, effective 2026) — relevant to self-audit remediation (already in the skill).

### 2.2 United Kingdom (per requested European scope)
- **Human Rights Act / ECHR Article 8** — right to private life; the basis for the **"JAPAN"** test (Justified, Authorised, Proportionate, Auditable, Necessary).
- **RIPA 2000 + Investigatory Powers Act 2016** — the key threshold: passive viewing of public content is generally fine, but it becomes regulated **directed surveillance** or requires a **CHIS authorisation (RIPA s.29)** when the investigator **builds a "pattern of life," repeatedly/systematically monitors an individual, retains a record over time, or interacts under a false identity to form a relationship.** Authorisations demand **necessity + proportionality**. **The threshold is low** — a few targeted look-ups can cross it.
- **UK GDPR + Data Protection Act 2018** — lawful basis, minimization, purpose limitation for personal data.
- College of Policing / NPCC "Internet Intelligence & Investigations" doctrine (Artifact 03 §3.1).

### 2.3 European Union
- **GDPR** — applies to processing personal data of people in the EEA **regardless of the investigator's location**; requires a **lawful basis**, **data minimization**, **purpose limitation**, and respects **data-subject rights**. "Publicly available" does **not** exempt processing from GDPR.
- **EU AI Act** (phasing in) — transparency/risk-tier obligations for AI systems; reaffirms data-protection rights; **certain AI practices** (e.g., untargeted scraping to build facial-recognition databases) are restricted/prohibited — directly relevant to automated face-matching in OSINT.
- **EU Charter Article 7** (private life) ≈ **ECHR Article 8**; CJEU extends privacy to professional activity.
- Sector frameworks: **Europol/CEPOL** LE-OSINT practice (Artifact 03 §3.2).

### 2.4 Cross-cutting "bright lines" (jurisdiction-agnostic don'ts)
- No unauthorized access (no hacking, no password-protected/private accounts, no defeating access controls).
- No social engineering / deception to *extract* information from people (distinct from passive managed-attribution personas — see §3).
- No accessing/redistributing **raw breach dumps or stolen data** — use legitimate notification/intel services only.
- No harassment, stalking, intimidation, or doxxing; heightened protection for minors and vulnerable subjects.
- Respect platform terms where legally relevant; understand that *terms-of-service* breach ≠ criminal, but can carry civil/account risk and ethical weight.

---

## 3. OPSEC & managed attribution (modernized)

Protecting the investigation and the investigator — and **not contaminating the target**. The skill's "use a VPN, burner email, dedicated accounts" is the right instinct but under-developed.

**Managed attribution = deliberately controlling what your research activity reveals about you.** Layers:
- **Network:** VPN/residential egress as appropriate; avoid attributable office IPs; never log into research personas from personal infrastructure.
- **Browser/device isolation:** dedicated VM or **isolated cloud browser** (e.g., Authentic8 **Silo for Research**); separate browser profiles/containers; clean **fingerprint** (user-agent, language, timezone, fonts) so it doesn't scream "investigator."
- **Identity separation:** **research personas / "sock puppets"** — non-attributable accounts kept strictly apart from personal identity, with consistent, pre-built, believable backstories; rotate intelligently; monitor for platform pushback.
  - *Ethical/legal boundary:* sock puppets for **passive observation and access** are accepted tradecraft; using them to **deceive, befriend, entrap, or elicit** moves toward CHIS/undercover territory (UK) and social-engineering prohibitions — requires authorization (LE) or is off-limits (most other contexts).
- **Tradecraft hygiene:** dedicated devices/accounts to avoid cross-contamination; clean metadata; don't trigger "viewed your profile" notifications; assume the target may be watching; archive before the target can delete.
- **Counter-OSINT (self-protection):** investigators should self-audit their own footprint — the skill's self-audit mode is, usefully, also OPSEC training.

> Note: the existing skill *prohibits* "sock puppets/deception" wholesale. That's appropriate for an **unsupervised consumer/journalist** tool, but the modern professional reality is more nuanced: **non-deceptive research personas are standard OPSEC**, while **deceptive elicitation** is the actual red line. Consider distinguishing these rather than banning the concept entirely.

---

## 4. Psychosocial safety — vicarious trauma (the missing pillar)

OSINT routinely exposes practitioners to graphic content (violence, CSAM-adjacent material, atrocity footage, abuse) — often **without the filtering/debriefing** that classified-collection or content-moderation roles build in. This is now a recognized occupational-health issue.

- **Vicarious / secondary trauma:** "mental distress experienced as an outcome of interacting with graphic online media." Symptoms: intrusive imagery, hypervigilance or numbing, sleep disruption/nightmares, difficulty concentrating, anxiety/depression.
- **Protective practices (from Bellingcat × Dart Centre, OSINT Combine, Authentic8, OSINTCurious, dutchosintguy, MHS4OSINT):**
  - **Reduce sensory load:** mute audio, grayscale, thumbnail/blur, smaller windows, avoid autoplay/loops; only view at full fidelity when necessary.
  - **Dose & break:** time-box exposure; scheduled breaks; don't binge traumatic material; "lower the temperature" between items.
  - **Separate work/personal** time and devices; routines to "leave it at work."
  - **Peer support & debrief**; normalize help-seeking; organizational duty of care; clinical support when needed.
  - **Build resilience proactively** (resilience predicts lower anxiety/depression post-exposure).

→ This belongs in *any* modern OSINT skill that may surface distressing material — at minimum a **content-warning + well-being note** and an offer to apply low-exposure viewing techniques.

---

## Implications for the `osint_audit` skill

1. **Legal section is US-only — expand to UK + EU** per the requested scope: add **ECHR Art 8 / JAPAN**, **RIPA/IPA "pattern-of-life" threshold**, **GDPR extraterritorial reach + "public ≠ exempt"**, and **EU AI Act** limits on face-matching/scraping.
2. **Reframe the data-broker module** around the **ODNI CAI** rationale and the **mosaic effect**, not just opt-out mechanics.
3. **Modernize OPSEC**: add **managed attribution** (isolated browser/VM, fingerprint, persona separation) and **distinguish non-deceptive research personas (OK) from deceptive elicitation (red line)** rather than a blanket ban.
4. **Add a psychosocial-safety section**: content warnings, low-exposure viewing techniques, dosing/breaks, peer support — referencing Bellingcat/Dart Centre.
5. Keep and elevate the existing strengths: SPJ ethics, minimization, "no raw breach dumps," consent gate, public-interest test.
