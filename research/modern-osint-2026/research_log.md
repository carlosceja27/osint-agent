# Research Log

Date: 2026-06-08

## Inputs

- Existing skill inspected: `skill.md`
- User-approved scope: latest/modern OSINT practices and fundamentals; improve existing OSINT skill; include US, Western Europe, Canada, Australia/New Zealand, NATO/OSCE-adjacent material if relevant; do not draft replacement skill yet; use default Markdown citations; no pricing/vendor profiles; no additional exclusions; report as long as needed.

## Execution notes

- Initial parallel subagent collection failed with API broken-pipe errors, so collection and synthesis were completed directly.
- Sources were selected from known authoritative public agencies, intergovernmental/public-sector bodies, academic/research literature, professional investigative organizations, and business-published practice/tool resources.
- Automated URL checks were run for each source and stored in `source_index.csv`. Some statuses may be HTTP 403, bot-blocked, or check-failed even when a browser can access the page.

## Exclusions enforced

- HUMINT tradecraft excluded except boundary references.
- Social engineering excluded.
- Unauthorized access/exploitation excluded.
- Raw breached databases excluded.
- Doxxing/stalking playbooks excluded.
- Direct dark-web browsing excluded.
- Vendor pricing and market-map profile work excluded.

## Source selection rationale

- Government/public-sector sources establish norms and authoritative registries.
- Academic/research sources inform methodology, misinformation, bias, and automation risks.
- Professional/journalism sources provide practical verification and investigative workflows.
- Business/tool sources are included only for practice patterns or tool-category understanding, with vendor caveats.

## Limitations

- This package is a research synthesis, not a full systematic literature review.
- Some academic entries are search routes for future expansion, clearly labeled as such.
- Some government guidance is OSINT-adjacent rather than explicitly titled OSINT but is included because it governs public-source collection, verification, public records, privacy, or information-environment work.
- Automated URL verification is not equivalent to manual source validation.

## URL verification cleanup

- ODNI IC OSINT Strategy now uses the public report landing page instead of a PDF path that returned 404 to automated curl checks. Browser navigation reached an access-denied page, likely bot protection.
- OHCHR Berkeley Protocol now uses the public landing page; automated checks return 403/bot-blocking, but the source is retained as a canonical public reference.
- Several DOI, Google Scholar, government, and media pages return 403/405/418/000 to automated curl because of bot protection, method restrictions, or TLS/site behavior. These are documented in `source_index.csv` rather than silently treated as source failures.

