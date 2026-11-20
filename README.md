# Eridan Winckler
**Backend and platform engineer: Java 17/21 and Spring Boot services, REST API and ERP integrations, and the infrastructure automation that provisions, deploys, and releases them (Ansible, Docker, GitLab CI/CD, AWS).**

> - **Now:** Software Engineer at Ovitas Inc. (Burlington, MA, fully remote) since June 2024; Junior Software Engineer there from June 2022 to June 2024. Domain: enterprise content management (ECM, ELO Digital Office) integrated with ERP platforms.
> - **Location:** Brazil (UTC-3), remote, overlapping US Eastern business hours. English and Portuguese.
> - **Engagement:** remote contract, international: independent contractor or C2C. Inside Brazil: PJ or CLT.
> - **Contact:** [LinkedIn](https://www.linkedin.com/in/eridan-winckler). Site: [eriwinckler.netlify.app](https://eriwinckler.netlify.app).

I joined Ovitas Inc. in 2022. Four years later, fully remote, I wrote the CI/CD recommendation the company adopted, and the first three pipelines on the new platform are mine. That work lives in private company repositories, so this page is the record rather than the code: every figure below traces to git history, Jira, or Confluence, and I can walk through any of it in an interview.

## Selected work

Customer names are left out on purpose.

- **A Java 17 and Spring Boot sync service.** It replicates ERP-fed SQL Server master data to JSON for an AWS Bedrock knowledge base: read-only against the customer schema, verified crash recovery, roughly 8,000 rows per second measured, 34 integration tests on Testcontainers.

- **ERP and SaaS integrations, kept running and extended.** I maintain and extend the REST API integrations between the ECM platform and Dynamics 365 Business Central (OAuth2, OData incremental sync), QuickBooks Online, SAP Business One, DocuSign, and WordPress publishing. Earlier, as a core contributor to the Java and Spring Boot integration platform itself, I refactored its configuration layer into per-package, unit-tested typed config so ERP and CRM products coexist in one deployment, and added cursor-based stop-and-resume pagination to admin syncs.

- **Environment provisioning as code.** A 13-role Ansible system takes a bare Linux VM to a working ECM plus integration environment in one guided run, replacing a manual procedure the company's own documentation put at roughly 50 steps. It ships as a Docker image so the operator needs no Ansible, Java, or Python installed, and it ends with a read-only verification playbook of about 60 named checks that also runs standalone, as an audit of an environment somebody else built. Guided means guided: a few steps still pause for a human, each arriving with every field value pre-computed.

- **The company's CI/CD direction.** I wrote the recommendation to migrate from Jenkins to GitLab; it was adopted at the May 2026 dev meeting. I then registered the company's first GitLab runner and shipped its first three pipelines (environment configuration sync, sprint-boundary schema sync, and package build and publish with drift detection), with gates that block cleartext secrets from ever being committed. I also own release engineering: Python release automation that generates Confluence release notes from Jira sprints, plus the version, documentation, and security-scan gates.

- **A vendor configuration layer under version control, which the platform itself does not ship.** A source-of-truth repository for the platform's 42 configuration packages and a five-job GitLab pipeline that builds them fully offline, publishes versioned bundles, and detects drift against live environments. The guard logic is mutation tested. The judgment call inside it: the platform's own package export yields an environment that looks correct and is subtly broken, so vendor-authored artifacts are tracked as pinned, checksummed binaries instead of source, a rule enforced in the build rather than by convention.

- **A disposable copy of the whole platform, sole-authored.** One command brings up roughly 11 Docker containers of ECM and integration services behind an Apache reverse proxy with TLS, in about 25 minutes on a laptop, replacing contention over a handful of shared VPN-only VMs. Reproducing a customer's environment becomes a profile file plus a staged content tree, not new code. It ships with recorded design decisions and an onboarding path written so a teammate can pick it up without me.

- **Full lifecycle for one enterprise customer.** The ECM platform installed on a bare VM; a Java OSGi plugin suite for invoice processing that I was primary author of (approver routing, duplicate vendor invoice detection); then production support and incident response, from an outage root-caused and fixed within days, with a written incident record, to a change retrofitted across more than 1,000 in-flight workflows. Install it, build on it, ship it, then answer the phone when it breaks.

- **Classes of problems, not instances.** One shared Java connection wrapper, rolled out across 283 files in every module and plugin, removed a category of concurrency errors (ConcurrentModificationException from multi-threaded SDK connections) instead of patching call sites as they surfaced. The deployment tool I wrote as a junior engineer is still in use today as a phase of the provisioning system above, since rebuilt into a modular, rerunnable phase orchestrator. And Docker became the standard deployment model for the Java integration services after I containerized them and drove adoption.

- **AI tooling, applied rather than collected.** I built the MCP server the team uses for support work: it gives AI assistants controlled access to the ECM platform, with workflow inspection, integration mappings, and a read-only mode for production investigation. Alongside it, Claude Code commands that generate configuration merge reports.

Three of the repositories behind this work did not exist until I created them: environment configuration as code, the local platform stack, and the configuration source of truth.

Two habits run through all of it. Verification ships with the thing: the read-only audit playbook, mutation-tested pipeline guards, integration tests against real databases in containers. And I write the handover while building (runbooks, decision records, onboarding paths; 65 Confluence pages and 22 decision records so far), because on contract work the handover is the deliverable.

## Stack

- **Languages:** Java 21 and 17, Python, Bash, SQL, TypeScript
- **Backend:** Spring Boot, REST APIs, OAuth2, Maven, Gradle, Apache Tomcat, OSGi plugins
- **ECM platform:** ELO Digital Office: Java plugins, workflows, configuration packages
- **Integrations:** Dynamics 365 Business Central (AL extensions, OData incremental sync), QuickBooks Online, SAP Business One, DocuSign, WordPress
- **Cloud and infrastructure:** AWS (EC2, S3, CloudWatch, Lambda, Bedrock knowledge bases), Amazon Linux 2023 and Ubuntu, Apache HTTP Server, TLS and keystore management, Windows Server containers, PostgreSQL, SQL Server
- **DevOps and CI/CD:** Ansible, Docker and Docker Compose, GitLab CI/CD, Jenkins, configuration as code
- **Practice:** JUnit and Testcontainers integration tests, mutation testing, secret encryption and rotation, decision records

The domain is niche. The engineering under it is not: JVM services, integration across several third-party ERP and SaaS APIs, containerized deployment, CI/CD, and the automation that keeps a multi-environment estate reproducible.

## Education and certifications

- B.S. in Software Engineering, Uninter International, Brazil (2022)
- Law studies, Pontifícia Universidade Católica do Paraná (PUCPR), Brazil (2008 - 2013)
- Anthropic Academy, March to April 2026:
  - Model Context Protocol ([verify](https://verify.skilljar.com/c/dxo6ua4davyk))
  - Claude Code in Action ([verify](https://verify.skilljar.com/c/jvr3656mcjmz))
  - Building with the Claude API ([verify](https://verify.skilljar.com/c/tbfctmq6tqe9))
  - Introduction to agent skills ([verify](https://verify.skilljar.com/c/86mxkd2hz57a))

## Contact

Reach me on [LinkedIn](https://www.linkedin.com/in/eridan-winckler), or see [eriwinckler.netlify.app](https://eriwinckler.netlify.app).
