**Backend and platform engineer: enterprise content management (ELO Digital Office) and ERP integration, in Java, plus the infrastructure automation that installs, deploys, and reproduces those platforms.**

> - **Engagement:** remote contract, international: independent contractor or C2C. Inside Brazil: PJ or CLT.
> - Full working-day overlap with US Eastern hours.
> - **Contact:** [LinkedIn](https://www.linkedin.com/in/eridan-winckler-449798169/). English and Portuguese.

My first weeks at Ovitas Inc. (Burlington, MA) in 2022 were spent fixing date formats in a Business Central sync. Four years later, fully remote from Brazil the entire time, the company's CI/CD platform call was mine and the first three pipelines on it are mine. That work lives in private company repositories, so this page is the record rather than the code: every figure below traces to git history, Jira, or Confluence, and I can walk through any of it in an interview.

## Selected work

Customer names are left out on purpose.

- **Environment provisioning as code.** A 13-role Ansible system, about 4,400 lines, takes a bare Linux VM to a working ECM plus integration environment in one guided run, replacing a manual procedure the company's own documentation put at roughly 50 steps. It ships as a Docker image so the operator needs no Ansible, Java, or Python installed, and it ends with a 609-line read-only verification playbook of about 60 named checks that also runs standalone, as an audit of an environment somebody else built. Guided means guided: eight points still pause for a human, each arriving with every field value pre-computed.

- **The company's CI/CD direction.** I wrote the recommendation to migrate from Jenkins to GitLab; it was adopted at the May 2026 dev meeting. I then delivered the company's first GitLab runner and its first three pipelines, and designed the security model under the first of them: a dedicated read-only service account, an SSH forced-command wrapper as the trust boundary, and encryption gates that block cleartext secrets from ever being committed.

- **A vendor configuration layer under version control, which the platform itself does not ship.** A source-of-truth repository (42 packages, 6,320 tracked files) and a CI pipeline that builds fully offline, publishes versioned bundles, detects drift against a live environment, and opens a merge request for it. The guard logic is mutation tested, and the pipeline is proven against live infrastructure as of July 2026, not only on paper. The judgment call inside it: the platform's own package export yields an environment that looks correct and is subtly broken, so vendor-authored artifacts are tracked as pinned, checksummed binaries instead of source, a rule enforced at three points in the build rather than by convention.

- **A disposable copy of the whole platform, sole-authored.** One command brings up roughly 11 containers of ECM and integration services behind a TLS front door, in about 25 minutes on a laptop, replacing contention over a handful of shared VPN-only VMs. Reproducing a customer's environment becomes a profile file plus a staged content tree, not new code. It ships with 22 recorded design decisions and an onboarding path written so a teammate can pick it up without me.

- **Full lifecycle for one enterprise customer.** ELO 25 installed on bare infrastructure; a custom accounts-payable plugin suite I was primary author of (invoice approver routing, duplicate vendor invoice detection, due dates from payment terms, permission-filtered lookups made fast with batching, caching, and background refresh); then production support, including an outage root-caused and fixed within days with a written incident record, and an attachment publisher that pushes documents natively into Business Central so ERP users no longer need ECM licenses, injected retroactively across more than 1,000 in-flight workflows. Install it, build on it, ship it, then answer the phone when it breaks.

- **Classes of problems, not instances.** One connection wrapper rolled out across 283 files removed a category of concurrency errors from the platform's client layer, instead of patching call sites as they surfaced. The deployment tool I wrote in year two is still the deployment tool in year four, now one phase inside the provisioning system above.

- **AI tooling, applied rather than collected.** I built the MCP tooling the team uses for support work: AI assistants operate the ECM platform safely, with workflow inspection, object-map read and write, and a read-only mode for production investigation. I am also building a Java 17 and Spring Boot service that replicates ERP-fed SQL Server master data for a downstream extractor and an AWS Bedrock knowledge base: read-only against the customer schema, roughly 8,000 rows per second measured, 34 integration tests on Testcontainers.

Three of the repositories behind this work did not exist until I created them: environment configuration as code (2024), the local platform stack (2026), and the configuration source of truth (2026).

Two habits run through all of it. Verification ships with the thing: the 609-line audit playbook, mutation-tested pipeline guards, a regression test that replays two real captured stall transcripts. And I write the handover while building, runbooks, decision records, onboarding paths, because on contract work the handover is the deliverable.

## Stack

- **Languages:** Java 21 and 17, Python, Bash, SQL
- **ECM platform:** ELO Digital Office (ELO 23 and 25): IX API, OSGi plugins, workflows, document masks, Business Solutions packages, Automation Services rules
- **Integrations:** Dynamics 365 Business Central (AL extensions, OData incremental sync), SAP Business One, QuickBooks, DocuSign, OAuth2
- **Infrastructure:** Ansible, Docker and Docker Compose, GitLab CI/CD, Jenkins, Apache httpd, TLS and keystore management, PostgreSQL, SQL Server, Amazon Linux, Windows Server containers, AWS Bedrock
- **Practice:** Spring Boot services, Testcontainers integration tests, mutation testing, secret encryption and rotation, configuration as code, decision records

The domain is niche. The engineering under it is not: JVM services, integration across half a dozen third-party APIs, containerized deployment, CI/CD, and the automation that keeps a multi-environment estate reproducible.

## Certifications

- Model Context Protocol, Anthropic Academy, April 2026 ([verify](https://verify.skilljar.com/c/dxo6ua4davyk))
- Claude Code in Action, Anthropic Academy, April 2026 ([verify](https://verify.skilljar.com/c/jvr3656mcjmz))
- Building with the Claude API, Anthropic Academy, April 2026 ([verify](https://verify.skilljar.com/c/tbfctmq6tqe9))
- Introduction to agent skills, Anthropic Academy, March 2026 ([verify](https://verify.skilljar.com/c/86mxkd2hz57a))

## Contact

Reach me on [LinkedIn](https://www.linkedin.com/in/eridan-winckler-449798169/).
