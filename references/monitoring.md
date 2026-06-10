# Monitoring Mode — Recurring Presence Audits

**Purpose:** Track exposure deltas over time for a specific subject without re-investigating from scratch. This mode focuses on change detection, trend analysis, and verification of remediation efficacy rather than initial discovery.

**Audience:** Self-audit subjects monitoring their own presence, or authorized monitors acting on behalf of a consenting subject. Journalism and public-interest monitoring are covered in the main skill; this mode is strictly for personal privacy self-monitoring.

**Consent Rule:** The subject must be the user running the skill, or the monitor must hold documented permission from the subject. Monitoring without consent is prohibited.

## Standing scope

A standing scope document defines the boundaries of monitoring for a given subject. The user approves this scope once; subsequent runs proceed automatically within these bounds unless the scope changes or a new sensitive category emerges.

**Standing Scope Template**

```markdown
# Standing Scope: {subject}

- **Subject Identifiers in Scope:**
  - {identifier_1}
  - {identifier_2}
  - ...

- **Allowed Source Categories:**
  - [ ] Data brokers / people search
  - [ ] Search engine results (organic)
  - [ ] Social media platforms
  - [ ] Professional networks
  - [ ] Public records databases
  - [ ] Breach notification services
  - [ ] Domain / code repositories
  - [ ] Other: {other_sources}

- **Excluded Categories:**
  - [ ] Private accounts / authenticated content
  - [ ] Financial data
  - [ ] Health records
  - [ ] Law enforcement databases
  - [ ] Other: {exclusions}

- **Jurisdictions:**
  - {jurisdictions}

- **Alert Thresholds:**
  - High risk items trigger immediate escalation.
  - Medium risk items logged for next review cycle.
  - Low risk items ignored unless trend detected.

- **Approval Date:** {date}
- **Review Date:** {date} (Re-approve every 6–12 months)
```

**Rule:** If a run surfaces a finding that falls outside the standing scope or introduces a new sensitive category, pause collection immediately and ask the user for guidance before proceeding.

## Workspace conventions

Monitoring state lives OUTSIDE the skill directory in a private workspace controlled by the user. This ensures data isolation and prevents accidental leakage into model contexts or shared directories.

**Suggested Path:** `~/osint-monitoring/{subject-slug}/`

**Required Files:**
- `standing-scope.md`: The approved scope document.
- `baseline.md`: The reference snapshot from the first full audit.
- `runs/`: Directory containing dated run reports (`{YYYY-MM-DD}.md`).
- `remediation-tracker.md`: Log of actions taken and their status.

**Hard Rules:**
- Never store subject personal data inside the skill directory.
- Never paste subject identifiers into third-party AI models or web tools beyond the approved search engines and sources defined in the standing scope.
- Prefer local processing for analysis of collected data; avoid transmitting raw findings to external services.
- Encrypt workspace storage if possible.

## Baseline run

The first run constitutes a full self-audit per the main skill (SKILL.md), using the self-audit report skeleton in `templates.md`. Its findings establish the reference point for all future delta comparisons.

**Baseline Snapshot Template (`baseline.md`)**

| Finding ID | Category | Source | URL | What is Exposed | Risk | Remediation Status | Date Observed |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| {finding_id} | {broker_listing \| social_profile \| breach_exposure \| search_result \| public_record \| code_domain_exposure} | {source_name} | {url} | {description} | {high/medium/low} | {none/in_progress/completed} | {date} |

## Recurring run procedure

1. Load `standing-scope.md`, `baseline.md`, and the most recent file in `runs/`.
2. Re-run the module checklist defined in the standing scope (typically Modules A, B, F, J, O and any others approved). Do not expand modules without user approval.
3. Classify every observation against the baseline using these states:
   - **NEW:** Finding not present in baseline.
   - **CHANGED:** Existing finding with modified data or risk profile.
   - **REMOVED:** Previously observed finding no longer found.
   - **UNCHANGED:** No material difference from baseline.
4. Report only deltas (NEW, CHANGED, REMOVED) plus a one-line summary of UNCHANGED items. Do not repeat full baseline data in the report.
5. Risk-rate each delta using the risk ratings defined in `templates.md`:
   - **High:** Enables account takeover, stalking/doxxing, identity theft, physical risk, or serious reputational/legal harm.
   - **Medium:** Reveals sensitive associations, stale but meaningful personal history, or aggregated exposure.
   - **Low:** Ordinary public presence or low-impact exposure.
6. Update `baseline.md` to incorporate confirmed NEW and CHANGED findings; mark REMOVED items as verified removed. Append actions to `remediation-tracker.md`.
7. Write the run report file `runs/{YYYY-MM-DD}.md` using the template below.

## Alert thresholds and escalation

Surface immediately at the top of the run summary delivered to the user (not buried in the run file) when any of the following occur:

- **New Contact/Location Exposure:** A new home address, phone number, or precise location appears on a data broker or people-search site.
  - *First Remediation Step:* Initiate opt-out request via the broker's designated removal process; log confirmation details. See `remediation.md`.
- **Active Credential Breach:** A new breach notification exposes credentials for an account currently in use by the subject.
  - *First Remediation Step:* Change password and enable MFA for the affected service immediately. See `remediation.md`.
- **Impersonation or Harassment:** Content appears that suggests impersonation, doxxing, or targeted harassment.
  - *First Remediation Step:* Document evidence; report to platform abuse channels; consider legal consultation. See `remediation.md`.
- **Reappearance of Removed Listing:** A listing previously marked REMOVED in the baseline reappears with unchanged data.
  - *First Remediation Step:* Resubmit opt-out request; verify removal process compliance. See `remediation.md`.

## Cadence

| Activity | Frequency | Notes |
| :--- | :--- | :--- |
| Data-broker recheck | 4–6 weeks after opt-outs, then quarterly | Opt-out processing times vary; initial recheck is critical. |
| Search-engine self-search | Monthly | Use approved search engines only; rotate queries to avoid fingerprinting. |
| Breach notifications | Continuous | Monitor via legitimate notification services (e.g., Have I Been Pwned alerts). |
| Social/professional profile review | Quarterly | Check privacy settings, tagged content, and discoverability options. |
| Full baseline refresh | Annually | Perform a complete re-audit to capture drift and update risk ratings. |

## Run report template

```markdown
# Monitoring Run: {subject} — {YYYY-MM-DD}

## Scope Confirmation
- Standing scope approved: Yes / No (if No, see note)
- Modules run: {list_modules}

## Deltas

| State | Finding ID / Description | Risk | Recommended Action |
| :--- | :--- | :--- | :--- |
| NEW | {description} | {high/medium/low} | {action} |
| CHANGED | {description} | {high/medium/low} | {action} |
| REMOVED | {description} | {high/medium/low} | {verify_and_log} |

## Unchanged Summary
- {count} items remain unchanged; no material drift detected.

## Remediation Actions
- **Taken:** {actions_taken}
- **Queued:** {actions_queued}

## Gaps
- What was not checked and why: {explanation}

## Next Run Date
- {YYYY-MM-DD}
```
