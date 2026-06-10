# OSINT Research Deliverables — Index

**Created:** June 2026
**Mission:** Deep research on modern OSINT practices + an inventory of OSINT fundamentals, to inform an update to the existing `osint_audit` skill (`../skill.md`).
**Constraints honored:**
- **Strictly OSINT** — no HUMINT/SIGINT/other-INT creep (referenced only as context for OSINT's role in fusion).
- **Government scope:** US + NATO Western-European members (Türkiye excluded) + NATO/EU bodies.
- **No pricing** — vendors are covered for the *practices and papers they publish*, not cost.
- **No replacement skill drafted** — this is research + a prioritized work order only.

---

## Read in this order

1. **[OSINT-Research-Report-2026.md](OSINT-Research-Report-2026.md)** — the headline synthesis report. Executive summary, the six requested research dimensions, key judgments, and how to use the research. **Start here.**

2. **Artifacts** (`artifacts/`) — modular, dense, LLM-consumable reference files. Each ends with *"Implications for the `osint_audit` skill."*

   | # | File | Covers |
   |---|---|---|
   | 01 | [fundamentals](artifacts/01-fundamentals.md) | Definitions, info→intelligence ladder, NATO taxonomy, intelligence cycle, Admiralty grading, PAI/CAI, the fundamentals checklist |
   | 02 | [modern-practices](artifacts/02-modern-practices.md) | AI disruption, SOCMINT collapse, content provenance, geospatial commoditization, mainstreaming/fusion |
   | 03 | [government-doctrine](artifacts/03-government-doctrine.md) | US (IC/DIA strategies, ICD lineage, CAI report), NATO (Handbook, *Northern Raven*), UK/EU/France/Germany/Nordics |
   | 04 | [academic-foundations](artifacts/04-academic-foundations.md) | GELSI review, AI-for-OSINT reviews, SATs/ACH/Heuer, source-eval theory |
   | 05 | [industry-and-orgs](artifacts/05-industry-and-orgs.md) | Vendors, threat-intel firms, due-diligence firms, NGOs/newsrooms, training — and their published work |
   | 06 | [verification-and-analysis](artifacts/06-verification-and-analysis.md) | Berkeley Protocol, Verification Handbook, SIFT, geo/chronolocation, synthetic-media checks, ACH, confidence |
   | 07 | [ethics-legal-opsec-wellbeing](artifacts/07-ethics-legal-opsec-wellbeing.md) | Ethics, US/UK/EU law, managed attribution, vicarious trauma |
   | 08 | [tooling-landscape](artifacts/08-tooling-landscape.md) | Modern tools **by function**, with 2026 caveats |
   | 09 | [skill-gap-analysis](artifacts/09-skill-gap-analysis.md) | **The work order** — strengths to keep, 14 gaps, tiered recommendations (tagged CORE/CONTEXT) |
   | 10 | [sources](artifacts/10-sources.md) | Annotated, reliability-flagged bibliography |

---

## The 60-second takeaway

The existing skill is **operationally strong, ethically sound, but conceptually thin, US-centric, and pre-AI-era.** The six highest-value upgrades (all in [artifact 09](artifacts/09-skill-gap-analysis.md), Tier 1):

1. Add a **Fundamentals & Posture** preamble (definitions, intelligence cycle, "open ≠ true," "public ≠ fair game").
2. Add an **AI/synthetic-media verification layer** — incl. the hard rule: *the skill's own LLM must never authenticate media or assert a geolocation as fact; it confabulates corroboration.*
3. **Modernize SOCMINT** for the post-CrowdTangle / API-paywall reality (archives + native UI + licensed sources + archive-on-capture).
4. **Expand legal to UK + EU** (ECHR Art 8 / JAPAN / RIPA pattern-of-life threshold; GDPR extraterritorial; EU AI Act).
5. Add a **psychosocial-safety** section (vicarious trauma; low-exposure viewing).
6. Re-anchor evidence handling to the **Berkeley Protocol** (forensic capture, hashing, chain of custody, digital/physical/psychosocial security).

**Keep** the two-mode design, consent/public-interest gate, phased human-in-the-loop workflow, evidence log, and negative-findings section — they already match best practice.

---

## When you're ready to update the skill

Use **[artifact 09](artifacts/09-skill-gap-analysis.md)** as the checklist. A suggested approach: feed `../skill.md` + artifacts 01, 02, 06, 07, 09 to the rewriting model first (the CORE changes), then 03/04/05/08 for citations and tooling. Verify forward-dated/low-confidence items against [artifact 10](artifacts/10-sources.md) before encoding them as fact.
