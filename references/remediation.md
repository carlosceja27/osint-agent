# Remediation and Opt-Out Directory

This directory supports self-audit and monitoring modes for privacy remediation. Remediation actions reduce data exposure but rarely eliminate it entirely; data often reappears over time. Log every action in a tracker to maintain accountability and track progress. Schedule periodic rechecks because listings and exposures frequently return or are repopulated by brokers and platforms.

## California DROP (Delete Act)

California's Delete Request and Opt-Out Platform (DROP) went live for consumers on January 1, 2026 at privacy.ca.gov/data-brokers. One request reaches all data brokers registered with the California Privacy Protection Agency. Brokers must begin retrieving and honoring DROP requests by August 1, 2026, checking at least every 45 days, with penalties of $200 per deletion request per day for non-compliance. Available to California residents; others should use per-broker opt-outs. Note: verify current eligibility and process on the official site.

## Search engine removal

Use search engine tools to request deindexing of results containing personal contact information or sensitive data. Tools include the Google "Results about you" tool (requests removal of results containing personal contact info; does not delete the source site), Google outdated-content removal, and Bing content-removal request.

**Rule:** Removal from search ≠ removal from the web; remediate the source too.

## Data broker and people-search opt-outs

Opt-out pages move frequently, so this table gives stable navigation paths instead of direct links: start from the broker's own privacy/opt-out page, or search the quoted query. Both notes apply broadly — most brokers require email confirmation, and most listings can reappear.

| Broker | How to opt out | Notes |
|---|---|---|
| TruePeopleSearch | privacy/opt-out page on the broker's site; search `TruePeopleSearch opt out` | Listing may reappear; recheck periodically. |
| Whitepages | privacy/opt-out page on the broker's site; search `Whitepages opt out` | May require email confirmation. |
| Spokeo | privacy/opt-out page on the broker's site; search `Spokeo opt out` | Listing may reappear; recheck periodically. |
| BeenVerified | privacy/opt-out page on the broker's site; search `BeenVerified opt out` | May require email confirmation. |
| Intelius | privacy/opt-out page on the broker's site; search `Intelius opt out` | Listing may reappear; recheck periodically. |
| PeopleFinders | privacy/opt-out page on the broker's site; search `PeopleFinders opt out` | May require email confirmation. |
| FamilyTreeNow | privacy/opt-out page on the broker's site; search `FamilyTreeNow opt out` | Listing may reappear; recheck periodically. |
| That's Them | privacy/opt-out page on the broker's site; search `That's Them opt out` | May require email confirmation. |
| Nuwber | privacy/opt-out page on the broker's site; search `Nuwber opt out` | Listing may reappear; recheck periodically. |
| Radaris | privacy/opt-out page on the broker's site; search `Radaris opt out` | May require email confirmation. |
| FastPeopleSearch | privacy/opt-out page on the broker's site; search `FastPeopleSearch opt out` | Listing may reappear; recheck periodically. |
| MyLife | privacy/opt-out page on the broker's site; search `MyLife opt out` | May require email confirmation. |

**Opt-out Advice:**
*   Use a dedicated opt-out email address to protect your primary inbox.
*   Do not submit more personal data than the listing already shows; provide only what is necessary to verify identity.
*   Save confirmation numbers and dates for all submissions.
*   Expect processing times of 2–6 weeks.
*   Brokers repopulate data over time; schedule rechecks to ensure listings remain removed.

## Paid removal services

Subscription services exist that automate broker opt-outs and remediation requests. These may be mentioned for awareness but are not endorsed. California residents can access much of this functionality for free via the DROP platform; weigh the cost against available free options before subscribing. Consider the privacy implications of sharing your identity data with another third-party service to manage other third parties' data.

## Breach and credential remediation

For exposures found via legitimate notification services such as haveibeenpwned.com:
*   Change the password on the breached service immediately.
*   Check for password reuse across other accounts and update those as well.
*   Enable Multi-Factor Authentication (MFA); prefer authenticator apps or passkeys over SMS-based codes.
*   Set up ongoing breach alerts for your email addresses and domains.
*   Consider a credit freeze or fraud alert where identity documents, Social Security Numbers, or sensitive PII were exposed; requirements vary by jurisdiction.

## Platform privacy hardening

Review and adjust settings across platforms to minimize exposure:
*   **Profiles:** Audit public profile fields, bio information, and visible connections.
*   **Content:** Remove or archive old posts containing sensitive details; review photo metadata and tags.
*   **Visibility:** Restrict follower-visible data; disable discoverability by email or phone number where possible.
*   **Integrations:** Review third-party app access and revoke unnecessary permissions.
*   **Location:** Disable location history tracking on personal accounts.
*   **Code/Domain:** Remove exposed personal emails from public commits where feasible; rotate accidentally published secrets; enable WHOIS privacy protection on personal domains.

## Remediation tracker template

Maintain a log of all remediation actions to track progress and schedule rechecks. Copy this table into your monitoring workspace for active tracking.

| Item | Source/Broker | Action taken | Date | Confirmation # | Status (submitted/confirmed/removed/reappeared) | Recheck date |
|---|---|---|---|---|---|---|
| [Item name] | [Broker/Platform] | [Opt-out/Removal request] | [YYYY-MM-DD] | [Ref # if provided] | [Status] | [YYYY-MM-DD] |

**Note:** Keep this tracker in your monitoring workspace, not the skill directory.
