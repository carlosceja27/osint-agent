# OSINT - Open-Source Intelligence Skill

**Created by:** Carlos Ceja

## Overview

The OSINT skill is a comprehensive, lawful, and ethical open-source intelligence workflow designed to guide investigations and privacy audits. It provides a structured approach to finding, verifying, and reporting information from publicly available sources while strictly adhering to ethical boundaries and legal frameworks.

## Purpose and Use Cases

This skill was meticulously designed to serve several critical functions:

1. **Self-Audits and Online Presence Monitoring:** Individuals can conduct self-audits to discover their digital footprint, monitor their online presence over time, and take actionable steps to reduce exposure (e.g., removing data from data brokers, improving privacy settings).
2. **Journalism and Public-Interest Investigations:** Journalists and researchers can utilize this skill to investigate public figures, organizations, claims, or issues using public sources. It helps ensure that investigations are source-grounded, verified, and minimize harm.
3. **Workplace Investigations and HR Functions:** HR professionals and workplace investigators can leverage this tool to conduct lawful investigations that protect employees and safeguard company reputation, ensuring that all findings are properly sourced and evaluated.

## Core Capabilities

The OSINT skill operates in three primary modes—**Self-audit**, **Monitoring**, and **Journalism**—and offers a robust suite of capabilities:

* **Structured Intake and Planning:** Guides the user through a formal intake process to define the scope, requirements, jurisdiction, and stop conditions before any collection begins.
* **Extensive Module Library:** Includes 15 specialized collection modules covering:
  * Baseline web footprints and search engine dorking
  * Social media presence (SOCMINT)
  * Public records, courts, and corporate registries
  * Data broker and people-search exposure
  * Image, video, and synthetic-media verification
  * Geospatial and chronolocation
  * Breach exposure (via legitimate notification services)
  * Mis/disinformation and claim verification
  * Alias and avatar enumeration
* **Verification and Analysis:** Enforces strict sourcing standards (SIFT method), corroboration requirements, and structured analysis (ACH-lite) to prevent bias and ensure intelligence is accurate and decision-useful.
* **Remediation and Monitoring:** Provides actionable guidance for data removal, breach response, and continuous presence monitoring to protect privacy over time.
* **Embedded Ethics and Legal Boundaries:** Ethics are deeply embedded into the skill's core posture. It explicitly refuses social engineering, unauthorized access, handling of raw breach dumps, and unnecessary collection of sensitive data. It heavily emphasizes necessity, proportionality, and the reduction of privacy harm.

## How to Use

The OSINT skill is designed to be highly versatile and can be executed within both agentic environments and web chat interfaces.

### Agentic Settings (CLI & Workspaces)
This skill functions best in environments where the AI agent has direct tool access (e.g., file system reading/writing, web search, URL fetching). Supported agents include **Claude Code, Antigravity, Codex, Hermes, OpenClaw**, and similar tools.

1. **Clone the repository:** Clone this directory into your local workspace.
2. **Invoke the agent:** Point your agent to the `SKILL.md` file.
   * *Example prompt:* "Read the `SKILL.md` file in this directory and help me conduct a privacy self-audit."
3. **Agent Workflow:** The agent will autonomously read the core instructions, templates, and module references. It will then initiate the structured intake process and build a collection plan for you to approve.

### Web Chat Environments
If you are using a standard web interface without direct file system access (e.g., **Claude Web, ChatGPT, Gemini**), you can still leverage the OSINT workflow:

1. **Use the Web Prompt:** Open the `WEB_CHAT_PROMPT.md` file located in this repository.
2. **Copy and Paste:** Copy the contents of that file and paste it into your web chat interface.
3. **Interactive Guidance:** The prompt injects the core guidelines into the AI's context. The AI will act as your offline OSINT guide—managing your intake, generating specific search queries (dorks) for you to run manually, and analyzing the source text or HTML you paste back into the chat.

## License

This project is licensed under the [Apache License 2.0](LICENSE).
