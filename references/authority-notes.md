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

## Future editing rules

- Do not add HUMINT/social-engineering workflows.
- Do not add exploit or unauthorized cyber steps.
- Do not turn vendor tools into endorsements or requirements.
- Keep modules source-tiered and verification-gated.
- Keep the web prompt short enough to paste into normal LLM chats.
- Keep safety boundaries near the top.
