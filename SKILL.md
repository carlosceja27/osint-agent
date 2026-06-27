---
name: osint
description: >
  Lawful open-source intelligence (OSINT) workflow for privacy self-audits, recurring
  online-presence monitoring, and journalism/public-interest investigations. Use when the
  user asks to research a person or entity from public sources, audit or monitor their own
  digital footprint or online presence, check data-broker/people-search or breach exposure,
  run opt-outs and remediation, verify claims/images/accounts, or produce a sourced
  investigation report with evidence logs and confidence labels. Strictly lawful OSINT —
  refuses social engineering, account access, and breach-dump handling.
version: 4.4
---

# OSINT Audit, Monitoring, and Public-Interest Investigation

## Purpose and modes

Guide lawful, ethical, source-grounded OSINT in three modes:

1. **Self-audit / privacy audit** — discover what is publicly findable about the user (or a consenting, documented subject) and how to reduce exposure.
2. **Monitoring** — recurring re-audit of a subject's own presence that diffs against a baseline and reports only changes. Read `references/monitoring.md` when this mode is selected.
3. **Journalism / public-interest investigation** — investigate a public figure, organization, claim, or issue using public sources while minimizing harm.

OSINT means intelligence produced from publicly available or lawfully accessible information, collected against a defined requirement, verified, analyzed, and reported for a legitimate purpose. Finding public content is not enough; it becomes OSINT only when scoped, logged, corroborated, and turned into a decision-useful product.

## Non-negotiable boundaries

Do not proceed if the request requires any of the following. If an adjacent request can be reframed safely, offer the lawful OSINT version instead.

- Accessing password-protected, private, restricted, or non-public accounts or systems.
- Bypassing access controls, rate limits, or paywalls by evasion, authentication, or technical exploitation.
- Exploit development, vulnerability exploitation, unauthorized scanning, brute forcing, credential stuffing, or credential theft.
- Social engineering, impersonation to elicit information, entrapment, deceptive relationship-building, phishing, or pretexting.
- Stalking, harassment, intimidation, doxxing, target lists, or instructions that facilitate harm.
- Raw breach-dump search, download, processing, or redistribution; credential exposure beyond legitimate notification services (e.g., Have I Been Pwned).
- Direct dark-web browsing or marketplace/forum interaction; use curated, lawful threat/breach-intelligence services only.
- Unnecessary collection about minors, victims, family members, home addresses, phone numbers, precise location patterns, or other sensitive data beyond the approved purpose.
- Using password-reset, login, or account-recovery flows to test whether an identifier is registered.

## Core posture

- **Requirement-driven:** start with a question, scope, jurisdiction, timeframe, and stop conditions.
- **Open ≠ true:** public data can be wrong, manipulated, stale, synthetic, or context-stripped.
- **Public ≠ fair game:** aggregating public fragments can create privacy harm (mosaic effect). Collect and report only what the approved purpose needs.
- **Primary beats aggregator:** official/original sources outrank people-search sites, reposts, screenshots, snippets, and tool outputs. Aggregators are leads, never facts.
- **Negative-confidence gate:** never state "no criminal records" (or similar) unless the arrest-aggregator / booking-log sweep and the county criminal index were actually run, or each is explicitly logged as not-run. A clean search-engine result is **not** a clean record — California and many states have no public name-based criminal-history search. Otherwise label the result "not verified."
- **Source ≠ content:** grade the source and the claim separately.
- **Reproducibility:** log enough (query, URL, date, match criteria) that another analyst could retrace the finding.
- **Intelligence cycle:** plan/direct → collect → process → analyze/produce → disseminate/feedback, iteratively.

## LLM operating rules

The model may: run intake; build collection and verification plans; generate queries and source lists; summarize and extract entities/dates/relationships from provided or fetched sources; draft evidence tables, timelines, maps, risk ratings, and reports; flag uncertainty, contradictions, and next verification steps.

The model must never:

- Fabricate sources, findings, URLs, quotes, screenshots, identities, or verification results.
- Present its own inference as evidence, or claim something was checked when it was not.
- Authenticate images, video, audio, identities, or geolocations by model judgment — it may only list indicators and verification steps. No detector, watermark, or provenance signal (C2PA/Content Credentials, SynthID) is dispositive alone; absence of provenance metadata proves nothing.
- Infer guilt, intent, identity, or relationships without cited evidence.
- Over-collect personal data because it is easy to find.

AI assistance is never citable as evidence. Every factual claim traces to a source URL or is labeled inference/unsupported.

## Execution environments

Detect which applies and say which mode you are operating in.

**Agent with tools (web search/fetch, filesystem, e.g. Claude Code):**
- Every cited URL must come from an actual search/fetch performed this session; record the query and access date as you go.
- Archive volatile or high-value pages on capture (Wayback Machine, archive.today) where lawful; log the archive URL.
- Respect robots, rate limits, and terms; no scraping evasion, login walls, or automation that impersonates a person.
- Do not send subject identifiers to third-party AI services or tools beyond the approved search engines and sources themselves. For self-audit subjects, prefer local processing of collected data.
- Independent modules may run in parallel, but keep one shared evidence log. Persist the evidence log and report as files when a filesystem exists (monitoring mode has its own workspace conventions — see `references/monitoring.md`).

**Web chat with browsing:** distinguish browsed facts (URL + access date) from model knowledge; never blend them.

**No live access:** say so explicitly and run offline mode — build the plan, provide query templates and official portals, analyze only user-pasted material, and mark every unvisited source "not yet checked."

## Workflow

### Phase 1 — Intake

**Quick path** (only when: subject is the user themself, self-audit or monitoring mode, no sensitive categories involved). Ask just:
1. Confirm the subject is you (or show documented consent).
2. Which identifiers are in scope (names, usernames, emails, domains)? Request only what will actually be checked — a full date of birth is rarely needed (birth year is usually enough for disambiguation).
3. Source categories allowed/excluded (public web, public records, brokers/CAI, breach-notification services)?
4. Output depth (concise answer, evidence table, full report)?
5. Output format — suggest HTML report first (styled, self-contained; template in `references/report-template.html`), or a Markdown document — and where to save it. Default save location is the user's private workspace (e.g., `~/osint-monitoring/{subject-slug}/reports/`), never the skill directory; confirm the path before writing.

**Full intake** (journalism mode, third-party subjects, any sensitive category, or elevated risk): use the full intake form in `references/templates.md` — mode and authority, public-interest justification, requirement and decision supported, jurisdiction, timeframe, languages, source categories in/out, minimum necessary identifiers, common-name collision handling, must-avoid categories, redaction default (recommend yes).

### Phase 2 — Plan and approval gate

Before collecting, output a Search and Verification Plan (skeleton in `references/templates.md`): scope summary; collection requirements/EEIs and stop conditions; source hierarchy (primary → secondary → aggregator/index → archive → tool-derived → vendor context); identity-resolution strategy; selected modules only; evidence-handling and minimization plan; safety/legal notes. Then ask:

> "Do you approve this OSINT plan as written? Anything to add, remove, narrow, or re-prioritize before collection begins?"

Do not collect without approval. Exception: monitoring mode runs under a previously approved standing scope (`references/monitoring.md`); re-approve only when scope changes or something outside it surfaces.

### Phase 3 — Collection (module library)

Read `references/modules.md` for the full library — sources, example queries, verification controls, and stop conditions per module. Run only modules selected in the approved plan.

| Module | Focus |
|---|---|
| A | Baseline web footprint (search engines, dorks, news) |
| B | Social media / SOCMINT (post-API-closure reality, archive-on-capture) |
| C | Professional, academic, code, and portfolio presence |
| D | News, media, and public statements |
| E | Public records and official registries (courts, corporate, licenses, campaign finance, nonprofits, sanctions, regulators) |
| F | Data brokers, people-search, and CAI (leads only; high-risk personal data) |
| G | Images, video, and synthetic-media verification |
| H | Geospatial and chronolocation |
| I | Domains, web infrastructure, and cyber OSINT (discovery/defensive only) |
| J | Breach exposure via legitimate notification services only |
| K | Archives and deleted/changed content (forensic capture, hashing) |
| L | Relationship and network mapping (sourced edges only) |
| M | International and cross-border records |
| N | Mis/disinformation and claim verification |
| O | Username, alias, and avatar enumeration (core to self-audits) |
| P | Cryptocurrency and blockchain OSINT (public-ledger; address ≠ identity) |
| Q | Transport and asset tracking (public ADS-B/AIS; assets/entities only, not individuals) |

For the full per-category source menu — with access type, automation-safety, source tier, and OPSEC-risk tags — read `references/source-directory.md`; each module maps to a section there.

For every finding capture: source, tier, URL, archive URL, access date, exact query/path, what it shows, identity-match criteria, confidence, relevance, sensitivity/redactions.

### Phase 4 — Verification and analysis

For any important finding:
1. **SIFT** — Stop; Investigate the source; Find better coverage; Trace to the original.
2. **Capture** — URL, timestamp/timezone, query, archive/screenshot; hash (SHA-256) saved files, keep original + working copy.
3. **Four W's** — provenance, source, date, location.
4. **Corroborate** — two independent sources for factual claims; watch for circular/syndicated reporting that fakes corroboration.
5. **Analyze** — for contested or high-impact findings, ACH-lite: list hypotheses, seek disconfirming evidence, check key assumptions, prefer the least-contradicted hypothesis, state what would change the assessment. Watch automation bias — including over-trusting your own outputs.
6. **Grade** — assign confidence with a stated reason.

**Confidence labels:** Confirmed (corroborated by primary or multiple independent sources) · Likely (strong signals, one gap) · Possible (lead only — never state as fact) · Disputed (credible sources conflict) · Not found (approved sources checked; not proof of absence). Optional two-axis Admiralty grading: source reliability A–F × information credibility 1–6 (e.g., B2).

Identity resolution: a matching name or username is a lead, not a match. Require multiple independent signals before attributing anything to the subject; document the criteria.

### Phase 5 — Reporting

Match output to the request — narrow question gets the concise-answer template, not a dossier. Report skeletons (self-audit, journalism, concise answer, evidence log, sourced-edge table, timeline) are in `references/templates.md`; for HTML output use `references/report-template.html` (self-contained, no external resources). Every report separates facts, assessments, assumptions, and unknowns, and always includes **what was not found** and **limitations**. Risk-rate self-audit findings High/Medium/Low per the template definitions.

Report files contain personal data: save them only to a user-confirmed private location (default `~/osint-monitoring/{subject-slug}/reports/`), never into the skill directory, and tell the user the exact path written. Archive volatile high-value findings (e.g., a broker listing or third-party page exposing contact data) before reporting, since they may change or disappear.

**Late-finding sync:** if a new finding arrives after the report, evidence log, or tracker is drafted, update all three together, bump the report date/timestamp, regenerate every export (HTML, PDF), and re-run the pre-delivery checklist before delivery — a partial update that leaves a stale export is worse than no update.

### Phase 6 — Remediation and monitoring

For self-audit remediation (broker opt-outs incl. California DROP, search-engine removal, breach/credential hygiene, platform hardening, tracker template): read `references/remediation.md`. For recurring presence monitoring (standing scope, baseline, run-over-run diffing, alert thresholds, cadence): read `references/monitoring.md`. For journalism monitoring: docket/registry/filing alerts and archiving as the story develops.

## Legal, ethics, OPSEC, and well-being

Read `references/legal-ethics.md` before collection when: the subject or data crosses US/UK/EU jurisdictions; brokers/CAI are in scope; systematic or repeated monitoring of a third party is proposed; graphic or distressing content is possible; or managed-attribution questions arise (research personas vs. prohibited deceptive elicitation). Minimum always-on rules: this is not legal advice; necessity and proportionality govern collection; redact sensitive details by default; warn before graphic content and use low-exposure viewing.

## Reference files

| File | Read when |
|---|---|
| `references/modules.md` | Selecting or executing any collection module |
| `references/source-directory.md` | Choosing sources for a module — vetted, tiered, attribute-tagged source menu by category |
| `references/templates.md` | Producing intake, plan, evidence log, or any report |
| `references/report-template.html` | User chose HTML output (suggest it first) — fill placeholders, keep self-contained |
| `references/monitoring.md` | Monitoring mode (mode 3), baselines, recurring runs |
| `references/remediation.md` | Opt-outs, removals, breach response, exposure reduction |
| `references/legal-ethics.md` | Jurisdictional, OPSEC, persona, or well-being questions |
| `WEB_CHAT_PROMPT.md` | User wants a paste-able prompt for a web LLM chat |

## Pre-delivery checklist

- [ ] Mode, purpose, and scope were approved (or covered by a monitoring standing scope).
- [ ] Strictly lawful OSINT; no prohibited adjacent practices included.
- [ ] Every factual finding has a source or is labeled inference/unknown.
- [ ] Important claims corroborated or confidence-limited; identity-match criteria documented.
- [ ] Sensitive data minimized or redacted; relevance justified for anything sensitive retained.
- [ ] Source tier, query/path, URL, access date, and verification steps logged.
- [ ] AI assistance not cited as evidence; media/geolocation not authenticated by the model alone.
- [ ] Report includes confidence, limitations, and what was not found.

## Authority anchors

Berkeley Protocol on Digital Open Source Investigations (UN OHCHR/UC Berkeley) · ODNI IC OSINT Strategy 2024–2026 · College of Policing internet intelligence guidance (JAPAN test) · EDPB/ICO guidance on personal data and social media · Verification Handbook (EJC) · Bellingcat Online Investigation Toolkit and Bellingcat/Dart Centre well-being guidance · GIJN Online Research Tools · NATO/Admiralty source grading · ICD 203/206 analytic and sourcing standards.
