# OSINT Skill Authority Notes

These notes summarize the research base used to update `skill.md` and `WEB_CHAT_PROMPT.md`. They are not required for normal use, but they help future editors preserve the research-backed design.

## Primary research packages used

- `research/OSINT-Research-Report-2026.md`
- `research/artifacts/01-fundamentals.md`
- `research/artifacts/02-modern-practices.md`
- `research/artifacts/03-government-doctrine.md`
- `research/artifacts/04-academic-foundations.md`
- `research/artifacts/05-industry-and-orgs.md`
- `research/artifacts/06-verification-and-analysis.md`
- `research/artifacts/07-ethics-legal-opsec-wellbeing.md`
- `research/artifacts/08-tooling-landscape.md`
- `research/artifacts/09-skill-gap-analysis.md`
- `research/artifacts/10-sources.md`
- `research/modern-osint-2026/modern_osint_deep_report.md`
- `research/modern-osint-2026/osint_fundamentals_inventory.md`
- `research/modern-osint-2026/modern_practices_matrix.md`
- `research/modern-osint-2026/skill_update_recommendations.md`
- `research/modern-osint-2026/llm_update_packet.md`

## Design choices encoded in the updated skill

1. Preserve the original skill’s strengths:
   - self-audit and journalism modes;
   - consent/public-interest gate;
   - phased workflow;
   - plan approval before collection;
   - evidence logging;
   - remediation and monitoring;
   - “what was not found.”

2. Add the missing conceptual foundation:
   - OSINT definition;
   - information-to-intelligence ladder;
   - intelligence-cycle checklist;
   - PAI/CAI distinction;
   - “open ≠ true” and “public ≠ fair game.”

3. Add modern AI/synthetic-media controls:
   - LLM is not a source;
   - LLM is not a media authenticator;
   - C2PA/Content Credentials/SynthID are optional signals, not dispositive proof;
   - detector tools are weak priors;
   - geolocation is no longer self-validating in an AI media environment.

4. Modernize SOCMINT:
   - platform/API restrictions and CrowdTangle-style access collapse mean bulk scripted social research cannot be assumed;
   - use native public UI, archives, user-provided exports, licensed lawful sources, and archive-on-capture.

5. Expand legal/ethical coverage:
   - US CFAA/privacy/CAI awareness;
   - UK JAPAN test and pattern-of-life threshold;
   - EU/GDPR extraterritorial and “publicly available ≠ exempt”;
   - EU AI Act caution for scraping/biometric/face database practices.

6. Re-anchor verification to recognized methods:
   - Berkeley Protocol-style capture, preservation, verification, analysis;
   - SIFT/lateral reading;
   - Verification Handbook four W’s;
   - ACH-lite and Key Assumptions Check;
   - confidence labels and optional Admiralty A-F / 1-6 grading.

7. Add psychosocial safety:
   - warn for distressing content;
   - low-exposure viewing;
   - breaks, separation, support.

8. Package for web LLMs:
   - no Hermes-specific tool calls required;
   - if the model cannot browse, it must say so and run offline planning mode;
   - output is proportional: concise answers for narrow questions, full reports for deep work.

## v4.4 — external-resource review, source directory, and new modules

A depth pass reviewed five public OSINT resources and folded in only what fits the lawful, source-tiered design (see CHANGELOG v4.4). Design choices:

- **Compiled an original source directory** (`references/source-directory.md`) rather than mirroring any external list — kept it to durable, high-value sources to resist link rot, and tagged every entry with an attribute legend (access · automation-safety · tier · OPSEC risk).
- **Adopted the OSINT-Framework attribute model** (function-first, with access/automation/tier metadata) as the directory's organizing convention.
- **Adopted theHarvester's passive-source taxonomy** to deepen Module I as a passive footprint sweep — passive lookups only; active scanning and breach/credential databases stayed excluded.
- **Rejected Osintgram wholesale** (credential-based scraping, ToS violation, contact-harvesting → stalking risk). Only its self-audit concept survived, reframed in `remediation.md` as "view your own profile as the public sees it" using native tools.
- **Added crypto/blockchain (Module P) and transport/asset tracking (Module Q)** as genuine coverage gaps, each guardrailed: crypto with "address ≠ identity / leads not proof," transport scoped to assets/entities with explicit anti-stalking boundaries so every enabled use stays lawful.
- **Excluded by policy, on review:** facial-recognition identity engines (PimEyes/Clearview-class — biometric/EU-AI-Act/stalking risk), breach-dump/password-lookup services, and any credential-based or ToS-evading scraper.

### Source licensing and credits

The directory is original curation; facts (which sources exist, their URLs, what they do) are not copyrightable and no descriptive prose was copied. Attribution for works that informed it:

- **jivoi/awesome-osint** — CC-BY-SA 4.0 (taxonomy breadth; attribute if any wording is later found to derive from it).
- **lockfale/OSINT-Framework** — MIT (attribute-tagging model).
- **sinwindie/OSINT** — restrictive license; taxonomy ideas only, no text reuse, no redistribution.
- **laramies/theHarvester** — GPLv2 (passive-source taxonomy reference; no code used).

## Future editing rules

- Do not add HUMINT/social-engineering workflows.
- Do not add exploit or unauthorized cyber steps.
- Do not turn vendor tools into endorsements or requirements.
- Keep modules source-tiered and verification-gated.
- Keep the web prompt short enough to paste into normal LLM chats.
- Keep safety boundaries near the top.
