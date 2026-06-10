# Businesses, Professional Sources, and Tool-Practice Landscape

Date: 2026-06-08

User preference: no pricing/vendor-profile market map. This artifact focuses on practices that credible organizations and businesses publish or embody.

| ID | Source | Org | Jurisdiction | Why it matters |
|---|---|---|---|---|
| PRO-01 | [Bellingcat Online Investigation Toolkit](https://bellingcat.gitbook.io/toolkit) | Bellingcat | global | Curated practical OSINT tool/resource list; use as tool landscape, not sole authority. |
| PRO-02 | [Bellingcat Guides and Resources](https://www.bellingcat.com/category/resources/) | Bellingcat | global | Practice articles on geolocation, verification, archiving, and investigative workflows. |
| PRO-03 | [Online Research Tools](https://gijn.org/resource/online-research-tools/) | Global Investigative Journalism Network (GIJN) | global | Journalism-oriented OSINT tool list and method route. |
| PRO-04 | [The Verification Handbook](https://verificationhandbook.com/) | European Journalism Centre / DataJournalism.com | global | Canonical verification workflow for user-generated content and online claims. |
| PRO-05 | [First Draft Essential Guide to Verifying Online Information](https://firstdraftnews.org/long-form-article/essential-guide-to-verifying-online-information/) | First Draft | global | Strong verification practices; note First Draft is no longer active but resources remain influential. |
| PRO-06 | [OCCRP Aleph](https://aleph.occrp.org/) | Organized Crime and Corruption Reporting Project | global | Investigative public/leaked-record search platform; use with source/context caution. |
| PRO-07 | [ICIJ Offshore Leaks Database](https://offshoreleaks.icij.org/) | International Consortium of Investigative Journalists | global | Public searchable database for offshore leaks; requires careful identity resolution and context. |
| PRO-08 | [Hunchly: OSINT workflow and capture tool resources](https://hunch.ly/) | Hunchly | global | Good for evidence capture and browser-based workflow practices; treat vendor content as practice-oriented, not neutral authority. |
| PRO-09 | [Maltego blog and resources](https://www.maltego.com/blog/) | Maltego | global | Link-analysis and entity-resolution practice examples; vendor caveat applies. |
| PRO-10 | [Shodan Help Center](https://help.shodan.io/) | Shodan | global | Useful for lawful internet-exposure discovery and query syntax; avoid exploit usage. |
| PRO-11 | [SpiderFoot documentation](https://github.com/smicallef/spiderfoot) | SpiderFoot | global | Automation tool docs; useful for describing collection automation, API keys, false positives, and scoping. |
| PRO-12 | [OSINT Framework](https://osintframework.com/) | OSINT Framework community | global | Broad tool map; useful as discovery index, not authority. |
| PRO-13 | [OpenCorporates](https://opencorporates.com/) | OpenCorporates | global | Corporate registry aggregator; verify critical findings against primary registries. |
| PRO-14 | [crt.sh Certificate Search](https://crt.sh/) | Sectigo / Certificate Transparency ecosystem | global | Certificate transparency search for domains/subdomains; useful for public infrastructure OSINT. |
| PRO-15 | [Internet Archive Wayback Machine](https://web.archive.org/) | Internet Archive | global | Core archiving and historical-web source; record snapshot dates and limitations. |
| PRO-16 | [Have I Been Pwned](https://haveibeenpwned.com/) | Have I Been Pwned | global | Lawful breach-exposure checking without raw dump access; mainly self-audit/defensive. |
| PRO-17 | [Recorded Future threat intelligence resources](https://www.recordedfuture.com/resources) | Recorded Future | global | Useful public reports on threat intelligence and OSINT-adjacent practices; vendor caveat. |
| PRO-18 | [Flashpoint resources](https://flashpoint.io/resources/) | Flashpoint | global | Public reports can inform risk framing and collection categories; vendor caveat and avoid dark-web operational detail. |

## Practice categories

### 1. Verification and investigative journalism practice

Bellingcat, GIJN, the Verification Handbook, and First Draft provide practical workflows for verification, geolocation, source discovery, and online evidence interpretation ([PRO-01: Bellingcat Online Investigation Toolkit](https://bellingcat.gitbook.io/toolkit), [PRO-03: Online Research Tools](https://gijn.org/resource/online-research-tools/), [PRO-04: The Verification Handbook](https://verificationhandbook.com/), [PRO-05: First Draft Essential Guide to Verifying Online Information](https://firstdraftnews.org/long-form-article/essential-guide-to-verifying-online-information/)). These sources are especially useful for an LLM skill because they translate broad principles into checklists and repeatable steps.

### 2. Investigative databases and public-interest data platforms

OCCRP Aleph and ICIJ Offshore Leaks are high-value investigative databases, but they should be treated as starting points that require identity resolution and context ([PRO-06: OCCRP Aleph](https://aleph.occrp.org/), [PRO-07: ICIJ Offshore Leaks Database](https://offshoreleaks.icij.org/)). OpenCorporates similarly helps discover corporate records but critical findings should be verified against primary registries ([PRO-13: OpenCorporates](https://opencorporates.com/)).

### 3. Evidence capture and archiving

Hunchly resources and the Internet Archive illustrate the importance of preserving URLs, timestamps, screenshots, and navigation paths ([PRO-08: Hunchly: OSINT workflow and capture tool resources](https://hunch.ly/), [PRO-15: Internet Archive Wayback Machine](https://web.archive.org/)). Vendor content should be used for practice ideas, not as legal authority.

### 4. Link analysis and automation

Maltego and SpiderFoot represent modern automation and entity/link-analysis patterns ([PRO-09: Maltego blog and resources](https://www.maltego.com/blog/), [PRO-11: SpiderFoot documentation](https://github.com/smicallef/spiderfoot)). The skill should describe them as optional accelerators with false-positive controls, not as required tools.

### 5. Lawful technical/cyber OSINT

Shodan, crt.sh, ENISA reports, and public vendor threat-intelligence resources can support public exposure discovery and defensive context ([PRO-10: Shodan Help Center](https://help.shodan.io/), [PRO-14: crt.sh Certificate Search](https://crt.sh/), [GOV-08: ENISA Threat Landscape 2024](https://www.enisa.europa.eu/publications/enisa-threat-landscape-2024), [PRO-17: Recorded Future threat intelligence resources](https://www.recordedfuture.com/resources), [PRO-18: Flashpoint resources](https://flashpoint.io/resources/)). The skill must explicitly stop before exploitation, scanning outside authorization, or credential handling.

### 6. Broad tool indexes

OSINT Framework and GIJN tool collections are useful for discovery but should not define best practice by themselves ([PRO-12: OSINT Framework](https://osintframework.com/), [PRO-03: Online Research Tools](https://gijn.org/resource/online-research-tools/)). A modern skill should pair any tool list with source-tier, validation, privacy, and logging rules.
