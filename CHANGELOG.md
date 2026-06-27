# OSINT Skill Changelog

## v4.4 — 2026-06-23

Depth pass that reviewed five public OSINT resources — jivoi/awesome-osint (CC-BY-SA 4.0), lockfale/OSINT-Framework (MIT), sinwindie/OSINT, laramies/theHarvester (GPLv2), and Datalux/Osintgram (GPLv3) — and folded in only what fits the skill's lawful, source-tiered, verification-gated design. Orchestrated by Claude (Opus): Haiku subagents fan-out-compiled candidate source lists per category; Sonnet subagents applied the ethics/legal filter and drafted the prose in-voice; Opus integrated and ran the final boundary gate. Osintgram was rejected as a tool (credential-based Instagram scraping, ToS-violating, contact-harvesting → stalking-adjacent); only its self-audit concept was salvaged and reframed.

- **New `references/source-directory.md`:** vetted, tiered, ethics-filtered source menu by category, each section mapped to a module. Adopts an attribute legend (access type · automation-safety · source tier · OPSEC risk) inspired by OSINT-Framework. Includes a Google-dork / advanced-operator quick-reference. Curated for durable high-value sources, not a link dump. Excludes facial-recognition identity engines (PimEyes/Clearview-class), breach-dump/password lookups, and credential scrapers.
- **Module I deepened:** consolidated passive domain/email footprint sweep (registration → CT → passive DNS → archive → tech fingerprint → public host search), the lawful passive alternative to theHarvester; expanded certificate-transparency and passive-DNS sources; added a self-audit-your-own-domain framing. Active scanning and breach/credential databases remain excluded.
- **Module N deepened:** added concrete fact-check sources (Snopes, PolitiFact, AFP/Reuters/AP, Full Fact, IFCN directory, Google Fact Check Explorer, Hoaxy) and a five-step reverse-chronology claim-tracing workflow. Primary sourcing still outranks any fact-checker summary.
- **New Module P — Cryptocurrency & blockchain (public-ledger) OSINT:** public explorers, OFAC/OpenSanctions address checks, abuse databases, clustering tools — with hard caveats (address ≠ identity; clustering/labels are leads not proof; public-ledger + lawful tools only; no stolen keys/de-anon-for-hire).
- **New Module Q — Transport & asset tracking (public ADS-B/AIS):** flight and vessel tracking scoped to assets/entities for public-interest work, with explicit anti-stalking boundaries (no real-time pattern-of-life on individuals; no chaining live position to a home/registry; respect jurisdictions that restrict private-aircraft tracking). ADS-B Exchange listed with an unfiltered-data caveat.
- **Remediation:** new "Platform exposure self-audit" section — view your own profile as the public sees it (logged-out / native "view as" tools) with a per-platform exposure-defaults table. The ethical reframe of Osintgram's only salvageable idea.
- **SKILL.md:** module table extended to P/Q; `source-directory.md` added to the reference dispatch table and Phase-3 routing.

## v4.3 — 2026-06-13

Criminal-record hardening after a live consent-based self-audit missed an arrest booking record (on a poorly-indexed arrest-aggregator) and stated an over-confident "no records" negative. Drafted with ChatGPT 5.5 (via codex), independently reviewed by Gemini Pro (via agy) — which caught a false-negative flaw (relying on search-engine `site:` operators for sites that block crawlers) — orchestrated and QA'd by Claude.

- **Collection:** new arrest-aggregator / booking-log sweep (localcrimenews, mugshots, arrests.org, jailbase, recentlybooked, county sheriff booking logs, county criminal index) — searched on each site directly, interactive/manual only, because general search engines miss them.
- **Controls:** codified the CourtListener REST API as the sanctioned federal lane, plus a mandatory robots.txt/ToS-diligence rule — never script CAPTCHA / anti-bot / disclaimer-gated portals (NSOPW, Megan's Law, county Odyssey).
- **Negative-confidence gate:** never claim "no criminal records" unless the aggregator sweep + county criminal index were run or logged as not-run; a clean web search is not a clean record (no public name-based criminal search in CA and many states).
- **Reporting:** dedicated "Criminal, Court & Arrest Records" report block with a baked-in arrest ≠ conviction callout.
- **Remediation:** arrest / mugshot-site removal guidance — never pay; relief tracks the case outcome; submit the sealing (§851.91) / expungement (§1203.4) order to force removal.
- **Workflow:** late-finding re-sync across report, evidence log, tracker, and regenerated exports (the prior run shipped a stale PDF).
- Frontmatter version corrected (was 4.1; 4.2 was the template design pass) → 4.3.

## v4.2 — 2026-06-09

Design-system pass on `references/report-template.html`, applying the interface-design skill. Audited by Gemini 3.1 Pro (via agy), implemented by qwen3-coder-next (local), QA'd and finished by Claude. Score went 5/10 → 7/10 → all critical findings resolved.

- **Accessibility:** `:focus-visible` outlines on links; smooth-scroll gated behind `prefers-reduced-motion`; content links underlined by default (color is no longer the only link signal); severity callout icons changed from same-shape colored circles to shape-distinct glyphs (⚠ / ❗ / ✓) so meaning survives colorblindness and grayscale printing; step/section number badges now dark-on-light (≥4.5:1).
- **Design tokens:** text type scale locked to 12/14/16/20px (+30px display, clamp hero); all spacing snapped to the 8pt grid; decorative indigo hue removed (confidence chip is now neutral; gradients are cyan-family only) — red/amber/green retained deliberately as semantic risk colors; no pure #fff/#000.
- **Print:** CSS custom properties redefined inside `@media print` (previously dark-mode token colors leaked onto paper), including darkened risk hues (`--red/--yellow/--green`) so risk-colored text stays legible on paper; gradient-text elements get solid fallbacks, cards/rows avoid page breaks, links print in a legible blue.
- **Semantics/polish:** `<header>` element, `text-wrap: balance` on headings, `text-wrap: pretty` on body.

## v4.1 — 2026-06-09

Field-test fixes after a live self-audit run by an external agent (Antigravity CLI / Sonnet 4.6). The run validated the v4 design — quick-path intake, plan/approval gate, progressive disclosure, honest negative findings all worked unprompted — and exposed four gaps, now fixed:

- **Output format intake:** quick path and full intake now ask document format, suggesting HTML first, plus an explicit save location.
- **`references/report-template.html` (new):** styled, self-contained HTML report template derived from the field run's improvised output, improved — external Google Fonts removed (a personal-data report must not phone home), full evidence-log columns (URL, query, archive), Top Risks & Quick Wins section, print stylesheet.
- **Report save-location rule:** reports contain personal data — write only to a user-confirmed private path (default `~/osint-monitoring/{subject-slug}/reports/`), never the skill directory; state the exact path written. Archive volatile high-value findings before reporting.
- **Agent notes in modules.md:** Module J — HIBP API needs a paid key; failed API calls don't count as "checked"; have the user check manually. Module F — broker sites block bots; don't bypass anti-bot measures (access-control evasion); use indexed snippets as leads and log blocked sources as "not checked — access blocked".

## v4.0 — 2026-06-09

Restructured from a 727-line monolithic `skill.md` into the standard Agent Skills format with progressive disclosure. Drafting assisted by local models (qwen3.6, gemma4) under Claude orchestration; all content QA'd against the v3 preserve list and the acceptance checklist in `research/modern-osint-2026/llm_update_packet.md`.

- **New layout:** lean `SKILL.md` orchestrator + `references/` (modules, templates, monitoring, remediation, legal-ethics) loaded on demand. v3 archived at `v3/skill.md`.
- **Trigger-oriented frontmatter** so agents reliably activate the skill (footprint audits, broker/breach checks, presence monitoring, investigations).
- **New Monitoring mode (mode 3):** standing scope approved once, private workspace conventions (state lives outside the skill dir), baseline snapshot, run-over-run NEW/CHANGED/REMOVED diffing, alert thresholds, cadence table (`references/monitoring.md`).
- **New execution-environments section:** explicit rules for tool-enabled agents (cite only actually-fetched URLs, archive-on-capture, no subject PII to third-party AI tools, parallel modules with one evidence log) vs. web chat vs. offline mode.
- **Remediation directory restored and updated** (`references/remediation.md`): California DROP (live Jan 1 2026; broker processing mandatory Aug 1 2026), Google "Results about you", per-broker opt-out table, tracker template — v3 had generalized v2's directory away.
- **New Module O:** username/alias/avatar enumeration with identity-attribution controls; explicit ban on password-reset/login-flow registration checks (also added to global boundaries).
- **Quick-path intake** for low-risk self-audits; full intake reserved for journalism/third-party/sensitive work.
- **Fill-in templates** (`references/templates.md`): intake forms, plan skeleton, evidence log (markdown + CSV), sourced-edge table, timeline, report skeletons, pre-delivery checklist.
- **Tooling refresh:** GLEIF (Module E), URLScan.io/DNSdumpster (Module I), SingleFile and Hunchly-class capture with SHA-256 hashing (Module K).
- **WEB_CHAT_PROMPT.md rewritten** for v4, including a paste-a-baseline monitoring variant for web chats.

## v3.0 — earlier 2026

Added fundamentals/posture preamble, AI/synthetic-media rules (LLM is not a source or media authenticator), modernized SOCMINT for the post-API era, UK/EU legal coverage (JAPAN test, RIPA/IPA, GDPR, EU AI Act), psychosocial safety, SIFT + ACH-lite, Admiralty grading, cross-model usage guidance. Single-file format.

## v2.0 and earlier

Original two-mode workflow (self-audit, journalism) with module library, plan-approval gate, evidence logging, broker opt-out directory, and monitoring cadence.
