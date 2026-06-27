# Remediation and Opt-Out Directory

This directory supports self-audit and monitoring modes for privacy remediation. Remediation actions reduce data exposure but rarely eliminate it entirely; data often reappears over time. Log every action in a tracker to maintain accountability and track progress. Schedule periodic rechecks because listings and exposures frequently return or are repopulated by brokers and platforms.

## California DROP (Delete Act)

California's Delete Request and Opt-Out Platform (DROP) went live for consumers on January 1, 2026 at privacy.ca.gov/data-brokers. One request reaches all data brokers registered with the California Privacy Protection Agency. Brokers must begin retrieving and honoring DROP requests by August 1, 2026, checking at least every 45 days, with penalties of $200 per deletion request per day for non-compliance. Available to California residents; others should use per-broker opt-outs. Note: verify current eligibility and process on the official site.

## Search engine removal

Use search engine tools to request deindexing of results containing personal contact information or sensitive data. Tools include the Google "Results about you" tool (requests removal of results containing personal contact info; does not delete the source site), Google outdated-content removal, and Bing content-removal request.

**Rule:** Removal from search ≠ removal from the web; remediate the source too.

## Arrest & booking records / mugshot sites

When a public arrest or booking record appears on a mugshot or booking-log aggregator (e.g., localcrimenews.com), start with the source site's own free removal/correction process where one exists.

- **Arrest ≠ conviction.** Durable relief largely follows the criminal case outcome.
- **Do not pay "removal" fees.** Several states (including California) restrict commercial pay-to-remove practices [verify current law]; paying often invites re-listing. Treat any paid-removal offer as a red flag.
- If the source page is outdated or the case resolves favorably, also use search-engine removal/de-indexing tools to cut visibility — but removal from search ≠ removal from the source.
- **The court order is the lever:** uncooperative aggregators often ignore standard requests but will act when sent the official **sealing (CA Penal Code §851.91, when there is no conviction)** or **expungement (§1203.4 — eligibility is limited and excludes some offenses, e.g., certain felony DUI-with-injury cases) [verify]** order. Obtain it via a criminal-defense / record-relief attorney, then submit it to the site's webmaster/legal contact.
- This is general information, not legal advice.

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

## Platform exposure self-audit (what your public profile reveals)

The goal is to see your own profile exactly as a stranger sees it — not to guess, but to confirm. Use a logged-out incognito browser window or the platform's built-in "View as public / visitor" feature to inventory what leaks. Use only native platform tools — never third-party scrapers, credential-sharing, or another person's account. Audit only your own presence or that of a consenting, documented subject.

### General logged-out audit procedure

1. Open an incognito / private browser window (or a second browser with no active session).
2. Navigate directly to your profile URL.
3. If the platform offers a native "View as public" / "View as visitor" mode (see table), use it — it reflects current rendering logic more accurately than a cold incognito hit.
4. Inventory every field visible without logging in: full name (does a maiden/middle name appear?); profile photo (identifiable? reverse-image-searchable?); location/hometown; employer/school; contact info (email, phone, WhatsApp link, website); followers/following/connections visibility (can a stranger enumerate your network?); tagged content others posted; post-history reach; "about"/bio fields (birthday, relationship status, views); and photo metadata (GPS/device/timestamp — check separately with `exiftool` or an EXIF viewer, since platforms strip inconsistently).

### Per-platform exposure defaults

| Platform | What's public by default | Native privacy / checkup tool | Key things to lock down |
|---|---|---|---|
| Instagram | Username, bio, follower/following counts, post grid; professional/business accounts **expose email and phone** via the Contact button | Settings → Privacy → Account Privacy (toggle Private); logged-out incognito shows the public state | Switch to personal account to remove the Contact button; remove phone/email; restrict tagged-photo review |
| Facebook | Name, profile/cover photo, and often friends list, tagged photos, and check-ins (audience varies by account age/setup) | Settings → Privacy → Privacy Checkup; Profile → ⋯ → View As (shows public view) | Lock friends list to "Only me"; audit "Photos of You"; set past-posts audience to Friends; hide birthday year |
| X / Twitter | All posts, likes, following/followers, replies, and media are **public by default** unless protected | Settings → Privacy and Safety → Audience and Tagging; incognito view is accurate | Enable protected posts if warranted; remove phone/email from discoverability; check location-on-posts setting |
| LinkedIn | Public profile (name, headline, photo, current role, education, skills, often past roles) is **search-engine indexed by default** | Settings → Visibility → Edit your public profile (exact search-engine preview) | Limit public profile to name + headline; turn off "Viewers also viewed"; manage activity broadcasts |
| TikTok | Accounts are **public by default for users 16+** — videos, likes (if enabled), following/followers | Profile → ⋯ → Privacy (toggle Private); Settings → Privacy → Discoverability | Set to Private; hide liked videos; disable "Suggest your account"; remove phone/email from discoverability |
| YouTube | Channel name, subscriber count, public videos, public playlists, and About page (incl. linked socials) | YouTube Studio → Settings → Channel; incognito on your channel URL | Remove linked socials from About; set non-public playlists to Unlisted; audit location tags on older uploads |
| Reddit | Username, post/comment history, public upvoted/saved content, active communities | Settings → Privacy → Manage privacy; incognito profile URL shows public state | Hide active communities; disable "Allow people to follow you"; audit old comments for PII |
| Snapchat | Profile is private by default, but **Snap Map** can expose location; public Stories and Spotlight submissions are public | Profile → ⚙ → See My Location → Ghost Mode; Who Can… → View My Story / Contact Me / See My Location | Enable Ghost Mode; set Story visibility to Friends; audit linked phone contacts |

### What aggregators do with this

Each field above looks trivial in isolation. Combined, they form a mosaic: full name + employer + neighborhood + photo is enough for most data brokers to build and sell a dossier, and enough for a motivated bad actor to launch a social-engineering or doxxing campaign. This is the exact mechanism exploited when public-profile data is harvested at scale — which is why minimizing each field matters. After this audit, run the data-broker opt-outs (above) to claw back what's already aggregated, then apply the Platform privacy hardening steps (above) to reduce future exposure.

Log findings — fields exposed, platforms audited, changes made, and any opt-outs submitted — in the remediation tracker below.

## Remediation tracker template

Maintain a log of all remediation actions to track progress and schedule rechecks. Copy this table into your monitoring workspace for active tracking.

| Item | Source/Broker | Action taken | Date | Confirmation # | Status (submitted/confirmed/removed/reappeared) | Recheck date |
|---|---|---|---|---|---|---|
| [Item name] | [Broker/Platform] | [Opt-out/Removal request] | [YYYY-MM-DD] | [Ref # if provided] | [Status] | [YYYY-MM-DD] |

**Note:** Keep this tracker in your monitoring workspace, not the skill directory.
