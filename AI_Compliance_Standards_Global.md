# AI Compliance Standards for a Global Landscape
### A Unified Governance, Risk, and Compliance Framework for Enterprise AI

> **Version 1.0 | Confidential**
> Aligned to: NIST AI RMF · ISO/IEC 42001 · EU AI Act · OWASP GenAI · NIST SP 800-53 Rev.5

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [The Global Regulatory Landscape](#2-the-global-regulatory-landscape)
3. [The Policy Stack: A Three-Layer Architecture](#3-the-policy-stack-a-three-layer-architecture)
4. [Technical Guardrails and the Universal Control Architecture](#4-technical-guardrails-and-the-universal-control-architecture)
5. [Role-Based Access Control for AI Systems](#5-role-based-access-control-for-ai-systems)
6. [AI Use-Case Lifecycle: From Idea to Retirement](#6-ai-use-case-lifecycle-from-idea-to-retirement)
7. [Day-Zero Rules: Ten Norms to Establish Immediately](#7-day-zero-rules-ten-norms-to-establish-immediately)
8. [Implementation Roadmap: 30-60-90 Days](#8-implementation-roadmap-30-60-90-days)
9. [Global Compliance Matrix Architecture](#9-global-compliance-matrix-architecture)
10. [Sector-Specific Overlays](#10-sector-specific-overlays)
11. [Governance Artifact Templates](#11-governance-artifact-templates)
12. [Program Tailoring and Open Questions](#12-program-tailoring-and-open-questions)

---

## 1. Executive Summary

Artificial intelligence is no longer a future consideration, it is an active operational reality across every sector. Yet governance for AI remains, for most organizations, fragmented: scattered across ad hoc expectations, vendor usage terms, tribal security knowledge, and undocumented norms that live in people's heads.

This document establishes a coherent, authoritative, and enforceable AI governance framework designed to consolidate that fragmentation into a unified control plane. It is built on three foundational principles:

- **Anchor to established frameworks.** By aligning internal policies and controls to NIST AI RMF, ISO/IEC 42001, the EU AI Act, and OWASP GenAI, governance decisions are defensible, audit-ready, and globally portable.
- **Set precedent proactively.** Rather than reacting to external enforcement timelines or vendor-defined guardrails, this framework establishes internal norms that become the standard others follow, rational controls that enable delivery instead of creating bureaucratic drag.
- **Couple policy to technical enforcement.** Rules are not merely words. Every policy maps to enforceable controls: gateways, logging, redaction, registries, and telemetry that feed directly into SIEM infrastructure.

The framework is organized around four interrelated concerns: the global regulatory landscape and where frameworks converge or diverge; a three-layer policy stack (Policies, Standards, Procedures); technical guardrails and a universal control architecture; and a practical 30-60-90 day implementation roadmap.

> **A note on philosophy:** This framework does not aim for AI bureaucracy. It aims for governance that is risk-proportionate, simple for teams to navigate, and designed to protect without strangling innovation.

---

## 2. The Global Regulatory Landscape

Any enterprise operating, or planning to operate AI systems that touch multiple jurisdictions must assume a multinational regulatory environment from day one. Building governance once, with regional dial settings per jurisdiction, avoids reinventing the wheel for every compliance review cycle.

The major frameworks relevant to a global AI governance program fall into three categories.

### 2.1 Principle-Based Frameworks (Voluntary)

These frameworks are risk-based and lifecycle-focused. They do not carry legal penalties but exert strong influence, particularly in procurement and audit contexts.

| Framework | Description |
|-----------|-------------|
| **NIST AI RMF** | Structured around a Govern → Map → Measure → Manage lifecycle. The 2024 Generative AI Profile offers directly applicable controls and documentation patterns for LLM-based systems. |
| **ISO/IEC 42001 (AIMS)** | The first internationally auditable AI Management System standard — effectively "ISO 27001 for AI." Provides a certifiable program structure. |
| **ISO/IEC 23894** | AI-specific risk management guidance covering the full system lifecycle, including hazards such as model drift and algorithmic bias. |
| **OECD AI Principles** | Internationally recognized principles emphasizing accountability, robustness, and traceability — useful for APAC and multilateral partner alignment. |

### 2.2 Binding Regulatory Law

**EU AI Act (2024/1689):** The most comprehensive and enforceable AI regulation globally. Even for US-centric organizations, its risk tiering (Prohibited / High-Risk / Limited-Risk / Minimal-Risk) and prescriptive obligations, risk management systems, data governance, logging, human oversight, accuracy and robustness requirements provide excellent policy scaffolding. Violations carry multi-million-euro penalties. High-risk systems require ongoing conformity assessment and technical documentation.

### 2.3 Executive Directives and Sector Guidance

| Source | Key Requirements |
|--------|-----------------|
| **US EO 14110 (Oct 2023)** | Red-team testing before deployment, content provenance mechanisms, and safety risk standards. Binding on federal agencies; strong signal to private sector. |
| **NIST SP 800-53 Rev. 5** | IT security control catalog. Controls AU-2 (Event Logging) and AU-3 (Content of Audit Records) apply directly to AI telemetry requirements. |
| **OWASP GenAI / LLM Top 10** | Definitive threat model for AI application security: prompt injection, insecure output handling, data leakage, excessive agency, and RAG poisoning. |

Regional frameworks; including the UK AI Safety Institute guidelines, Singapore's AI Governance Framework, Japan's OECD-aligned guidelines, and Australia's ISO/IEC 42001 adoption path layer additional considerations for multinational deployments. The common principle: **build controls once, tune dials by region.**

### 2.4 Where Global Frameworks Converge and Diverge

All major global frameworks share a **common governance core**:

- Risk management lifecycle
- Data governance and bias control
- Logging and traceability
- Human oversight
- Security and robustness testing
- Documentation and record-keeping

**Key divergences:**

| Dimension | EU AI Act | NIST AI RMF / ISO | US EO 14110 |
|-----------|-----------|-------------------|-------------|
| Legal status | Binding law, enforceable penalties | Voluntary guidance / certifiable standard | Binding for federal agencies; private sector signal |
| Risk tiering | Prescriptive: regulator defines high-risk categories | Contextual: organization defines own thresholds | Not prescriptive |
| Documentation burden | Extremely high: mandatory technical files, QMS, conformity assessment | Moderate (ISO 42001) to flexible (NIST) | Focused on safety testing and provenance records |
| Red-teaming | Implied via cybersecurity / risk management requirements | Recommended, not mandated | Explicitly required before release of powerful models |
| Transparency | Legally mandates disclosure of AI-generated content | General guidance, implementer-defined | Promotes provenance standards; less prescriptive |

> **Practical implication:** A program built to satisfy EU AI Act obligations will generally satisfy the requirements of all other frameworks. NIST AI RMF and ISO/IEC 42001 provide the structural language and audit-readiness; the EU AI Act defines the compliance ceiling.

---

## 3. The Policy Stack: A Three-Layer Architecture

Effective AI governance requires clear separation between durable policy, mappable standards, and enforceable procedures. The mental model is straightforward: **policy text references frameworks; standards implement them; configurations enforce them.**

### Layer A: Policies (Board-Level, Durable)

Policies define principles, scope, and intent. They should be durable and written at a level that executives and auditors can meaningfully review.

| Policy | Description |
|--------|-------------|
| **AI Acceptable Use and Data Boundary Policy** | Defines allowed data classifications and prohibits transfers to external models for sensitive categories (e.g., "No PII or CUI to public endpoints"). The foundational policy, publish this first. |
| **AI Risk Classification Policy** | Maps use cases to Prohibited, High, Limited, or Minimal risk tiers mirroring EU AI Act hierarchy, with required controls per tier. |
| **Third-Party AI Procurement and Model Intake Policy** | Requires model cards, SBOMs, license/terms review, security posture assessment, and test evidence before any external model is onboarded. |
| **AI Logging, Monitoring, and Retention Policy** | Mandates event types, retention periods, and PII minimization requirements. Mapped to NIST SP 800-53 AU-2 and AU-3. |
| **Human-in-the-Loop Policy** | For high-risk decisions: requires pre-deployment TEVV and defines operational thresholds for human review. Mirrors EU AI Act Articles 9–15. |

### Layer B: Standards (Mappable to Controls)

Standards translate policy intent into specific requirements that can be mapped to security controls.

- **Identity and Access Standard**: Least-privileged tool access and token scoping for all AI agent interactions.
- **Data Governance Standard**: Data classification, masking, retrieval filter configuration, and PII/sensitive term deny-lists.
- **Secure SDLC for AI**: Red-team testing, model evaluations for toxicity/bias/jailbreak resistance, and drift monitors. Aligns to NIST AI RMF Measure and Manage functions.
- **Content Provenance Standard**: Hashing, watermarking, or provenance metadata for machine-generated content, per EO 14110 direction.
- **Supply Chain Standard**: Curation of models, datasets, and embeddings; vendor SLA requirements; CVE monitoring for AI libraries; minimum model card requirements per ISO/IEC 42001.

### Layer C: Procedures and Configuration Baselines (Enforceable)

Procedures are the operational layer specific enough to enforce, simple enough to use.

- **AI Use-Case Intake and Impact Assessment (AIIA)**: A streamlined 3-to-5 page impact assessment for high-risk use cases. Mirrors EU AI Act Article 9 without unnecessary bureaucratic burden on lower-risk workloads.
- **Prompt and Output Logging Runbook**: Step-by-step procedures for logging prompts, outputs, tool calls, and decisions while masking secrets and sensitive data. Mapped to AU-2 and AU-3.
- **AI Incident Response Playbooks**: Procedures for AI-specific threat scenarios: prompt injection, data exfiltration, harmful content generation, and model compromise. Aligned to OWASP LLM Top 10.

---

## 4. Technical Guardrails and the Universal Control Architecture

Paper policies without technical enforcement are compliance theater. Every policy in this framework maps to a technical control point. The architecture below is platform-agnostic and equally applicable to on-premises environments (including zLinux and mainframe-adjacent workloads), private cloud, and public cloud deployments.

> **Core principle:** Identical control objectives, implemented with environment-specific mechanisms, producing the same evidence for audit portability.

### 4.1 Data Boundaries and Egress Control

All AI traffic must be routed through a centralized gateway or proxy that:
1. Enforces an allow-list of approved models
2. Strips or redacts sensitive data before it leaves the boundary
3. Attaches policy context — tenant identity, data classification tags, and stated purpose to each request

**For zLinux / mainframe-adjacent workloads specifically:**
- Inference endpoints on dedicated VLANs with mutual TLS using FIPS 140-3 compliant cryptography
- Logs forwarded via journald or syslog to SIEM with tamper-evidence controls
- Model artifact pulls restricted to curated repositories (extend the same Artifactory pattern already in use for managed package distribution)

Every AI system in production must be registered in a **Model Registry** capturing: model name and version, license and training data lineage, evaluation scores, designated owners, and associated risk profile.

### 4.2 Identity, Secrets, and Least Agency

Short-lived, scoped tokens must be used for all tool and plugin interactions. LLM agents must not be able to list capabilities beyond their designated scope or escalate permissions autonomously.

"Excessive agency"; where an AI agent can execute arbitrary shell commands, perform unrestricted network calls, or write to production systems is one of the highest-severity risk categories identified by OWASP. Unless explicitly approved with compensating safeguards, LLMs should operate **without** shell access, arbitrary network access, or production write capabilities.

### 4.3 Prompt and Output Hygiene

- Retrieved content must be treated as **untrusted input**
- System prompts (instructions) must be architecturally separated from user-supplied or retrieved content (data)
- Outputs must be validated before passed to downstream tool execution
- Deny-patterns must be implemented for common injection signatures

This maps to OWASP LLM01 (Prompt Injection) and LLM02 (Insecure Output Handling), the two most frequently exploited vulnerability categories in production AI systems.

### 4.4 Telemetry and Audit

Minimum required events for every AI interaction:

| Event Type | Description |
|-----------|-------------|
| Model identifier and version | Which model processed the request |
| Tool invocations | What tools were called and with what parameters |
| Data classification tags | What sensitivity level was applied |
| Policy decisions | Allowed, blocked, or redacted, and why |
| Redaction actions | What was masked and what rule triggered it |
| Evaluator scores | Safety and quality metrics from any inline evaluators |
| User identity | Who or what initiated the request |

All events must include timestamps, success/failure status, and configuration item references. Retention periods must comply with applicable regulatory clocks.

### 4.5 TEVV and Red-Teaming

Pre-production adversarial testing is required before any model reaches production exposure or external pilots. Minimum test scenario coverage:

- Jailbreak attempts
- Sensitive data leakage scenarios
- Direct and indirect prompt injection
- RAG poisoning attacks
- Cost-denial-of-service (unbounded inference consumption)

This requirement is explicitly grounded in EO 14110 and the NIST AI RMF Measure function, and is strongly implied by EU AI Act cybersecurity and robustness obligations for high-risk systems.

### 4.6 Configuration Management for AI (CM-6 Applied)

A critical and often underestimated risk: **AI system behavior can be changed silently without any code deployment.** A tweak to a prompt template, a modification to retrieval pipeline weights, or a swap of the underlying model artifact changes system behavior as significantly as a software release — but may trigger none of the existing change control gates.

This framework applies NIST SP 800-53 CM-6 configuration hardening principles to AI-specific configuration items (CIs):

| Configuration Item | Baseline Requirements |
|-------------------|----------------------|
| **Model artifacts** | Approved base model list, permitted quantization levels, allowed fine-tune sources, cryptographic hash verification, approved serving parameters |
| **Prompts and agents** | Versioned and read-only in production; tool lists at least privilege; no generic code execution by default |
| **Vector DBs and RAG pipelines** | Schema locked; ingest pipelines curated; production writes restricted to signed CI/CD jobs with change tickets |
| **Gateways** | Model allow-lists, data redaction policies, egress destinations, rate limits, and cost budgets |

Configuration drift, where embeddings change, source documents update, fine-tunes accumulate, or RAG pipeline weights shift without tracking directly affects fairness, safety, accuracy, and compliance exposure. Drift detection, baseline checksums, and behavioral deviation alerts are required components of any production AI governance program.

### 4.7 Threat Model: Seven Attack Surfaces

AI security requires a new threat model paradigm: instead of protecting code, we must **protect behavior-defining configuration.** Behavior = Model + Prompt + Retrieval + Tools + Gateway Policies. If any layer is compromised, the system becomes untrustworthy.

| Threat Surface | Risk | Required Controls |
|---------------|------|------------------|
| **Model artifact tampering** | Replacing/modifying checkpoints changes safety, accuracy, and bias profiles without triggering code review | Signed artifacts, registry immutability, CM-6 baseline enforcement, verification on load |
| **Prompt template tampering** | Editing system prompts weakens guardrails or enables role-swap attacks, no code change required | Prompt versioning as code, approval workflows, runtime hash verification |
| **Vector DB poisoning** | Injecting malicious embeddings or modifying RAG source documents creates controlled misinformation | Curator/Promoter separation, signed ingestion, audit logs, metadata integrity checks |
| **Tool scope escalation** | Expanding agent privileges to filesystem, network, or code execution creates exfiltration pathways | Least-privilege tool binding, sandboxed execution, no admin credentials to generic agents |
| **Gateway egress bypass** | Direct calls to public LLM APIs bypass redaction, logging, and data boundary enforcement | Egress control via gateway only, mTLS, allow-listed endpoints, SIEM alerts for bypass attempts |
| **Retrieval pipeline manipulation** | Changing RAG scoring functions or embedding models silently shifts semantic meaning and factual grounding | Controlled scoring configs, change review, evaluation logs on pipeline modifications |
| **Safety filter bypass** | Disabling toxicity or hallucination detectors removes compliance-mandated output controls | Filter hashing, runtime verification, approval required for threshold changes |

---

## 5. Role-Based Access Control for AI Systems

AI systems have three behavioral determinants: **model parameters**, **prompt and agent logic**, and **the retrieval corpus or vector database**. Each must be governed separately. A single actor with unchecked access to all three can change system behavior completely, and do so in ways that may not be detectable through conventional monitoring.

### Canonical Role Set

| Role | Purpose | Can Do | Cannot Do |
|------|---------|--------|-----------|
| **AIMS_Admin** | Owns governance rules, not systems | Define policies, risk tiering, logging requirements; manage compliance evidence; approve role structures | Deploy models, modify prompts, push embeddings, or write to production |
| **Model_Owner** | Business/technical owner of model behavior | Approve model versions, fine-tunes, quantization profiles, prompt template updates, and safety test results | Modify vector DB contents; deploy artifacts to production directly; alter infrastructure |
| **Data_Curator** | Controls what enters the retrieval pipeline | Curate source documents for RAG; generate embeddings in staging; validate metadata quality; submit promotion requests | Write to production vector DB; modify models or prompts; bypass safety filters |
| **Promoter** | Executes approved production changes via signed CI/CD | Deploy approved model versions; publish approved embeddings; validate artifact signatures; capture promotion events in logs | Approve model or embedding changes; alter behavior logic |
| **Ops_Custodian** | Manages runtime systems but not AI behavior | Maintain compute, networks, storage, secrets, gateways; enforce egress control and mTLS | Change models, embeddings, prompts, or agent logic; publish new vector indexes |
| **Gateway_Admin** | Controls access to external models and enforces redaction | Manage allow-listed endpoints; configure redaction rules; manage rate/cost limits; manage provenance labeling policies | Modify internal LLMs, vector DB, or prompts |
| **Auditor** | Compliance and forensics oversight | Full read-only access to logs, model cards, and configuration baselines | Change anything |

### Why This Structure Is Mandatory

This RBAC model prevents:
- Unauthorized behavioral drift
- Embedding poisoning
- Prompt tampering
- Undocumented model changes
- Excessive agent autonomy
- Misuse of high-risk AI in regulated sectors

It aligns with SP 800-53 CM-6/CM-3/4, NIST AI RMF Govern/Manage, ISO/IEC 42001 operational role definition, EU AI Act Articles 9–15, and OWASP GenAI/LLM Top 10.

---

## 6. AI Use-Case Lifecycle: From Idea to Retirement

The lifecycle below provides teams with a simple, familiar path from initial idea to production operation and eventual decommission. It mirrors change management processes teams already follow but right-sized for AI.

```
Intake → Risk Triage → Controls Assignment → Build & TEVV → Go/No-Go → Operate → Decommission
```

| Stage | Description |
|-------|-------------|
| **1. Intake** | 1-page form: purpose, data classifications involved, user population, integration points, and target model(s). The entry point for everything. |
| **2. Risk Triage** | Auto-classify to Prohibited, High, Limited, or Minimal risk using a decision tree aligned to EU AI Act tiers. High-risk triggers a full AIIA and mandatory human-in-the-loop configuration. |
| **3. Controls Assignment** | Apply the appropriate pre-defined control bundle for the risk tier, covering identity, data handling, TEVV depth, and logging profile. |
| **4. Build and TEVV** | Scenario tests, adversarial red-team testing, and bias/safety metric evaluation. Record all results in the Model Card per NIST AI RMF Measure documentation standards. |
| **5. Go/No-Go (AI Change Advisory)** | Lightweight CAB reviews scope, agency permissions, and rollback procedures. Designed for a 30-minute queue, not a 30-day cycle. |
| **6. Operate** | Continuous drift and safety monitoring, cost guardrails, quarterly access reviews, and incident response rehearsal. |
| **7. Decommission** | Archive model and telemetry, revoke all secrets and credentials, scrub temporary stores. |

> **Key design principle:** Risk-proportionate controls applied automatically. Low-risk use cases move fast. High-risk use cases receive the scrutiny they require. No special cases only predictable lanes.

---

## 7. Day-Zero Rules: Ten Norms to Establish Immediately

Culture shifts happen before documents. These ten rules can be announced and enforced before the full policy stack is published. They establish the organizational tone for AI governance and create immediate risk reduction.

1. **No sensitive data to public LLMs.** If in doubt, route through the AI gateway with redaction enabled.
2. **Register every AI use case** — including experiments in the central intake form. No shadow AI.
3. **Human review is required** for any AI output that affects finance, HR decisions, customer communications, or security controls.
4. **Only models and plugins from the approved, curated registry** may be used in production.
5. **Prompt and output logging is on by default** (with masking) for all non-personal experimentation. Opt-out requires security approval. *(AU-2/AU-3 rationale.)*
6. **No excessive agency.** LLMs cannot execute code, send emails, or modify systems without an explicitly approved tool operating at least privilege. *(OWASP GenAI Top 10.)*
7. **Red-team testing is required** before any production exposure or external pilot. *(EO 14110.)*
8. **Model Cards are mandatory:** purpose, training data, risks, evaluation scores, owners, and rollback procedure. *(ISO 42001 governance and NIST AI RMF documentation requirements.)*
9. **Content provenance is required** for machine-generated customer-facing content. *(EO 14110 direction.)*
10. **Quarterly review** of AI access permissions, logs, and incidents. Publish a short transparency note.

> **Suggestion:** These ten rules work best when published as a single-page reference, something teams can keep accessible without navigating a full policy document. Consider a companion "quick reference card" format in addition to the formal policy publication.

---

## 8. Implementation Roadmap: 30-60-90 Days

### Days 0–30: Bootstrap

Focus: Stop the most immediate risks and establish foundational infrastructure.

- [ ] Stand up the AI Use-Case Intake form and lightweight risk triage decision tree
- [ ] Publish the Day-Zero ten rules
- [ ] Configure an AI gateway (even a basic reverse proxy with redaction policies) to centralize traffic and capture prompts, outputs, and redaction events
- [ ] Draft and publish the **AI Acceptable Use and Data Boundary Policy** and the **AI Logging and Monitoring Policy** (mapped to AU-2/AU-3)
- [ ] Identify and communicate RBAC role owners for AIMS_Admin, Gateway_Admin, and Auditor functions

### Days 31–60: Operationalize

Focus: Build scaffolding for repeatable, consistent governance.

- [ ] Build the Model Registry and Model Card template (mapped to NIST AI RMF and ISO/IEC 42001)
- [ ] Define control bundles by risk tier (Minimal, Limited, High)
- [ ] Pilot TEVV with a red-team playbook covering prompt injection, RAG poisoning, sensitive data leakage, and unbounded consumption *(OWASP GenAI and EO 14110)*
- [ ] Draft the **AI Risk Classification Policy** and **Third-Party AI Procurement and Model Intake Policy**
- [ ] Complete RBAC role assignments across all seven roles

### Days 61–90: Institutionalize

Focus: Make governance self-sustaining and externally defensible.

- [ ] Launch the AI Change Advisory Board (recommended: weekly cadence, 30-minute queue target)
- [ ] Integrate AI telemetry into the SIEM; add drift detection and safety dashboards
- [ ] Run the first quarterly governance review and publish initial transparency notes
- [ ] Complete the **Human-in-the-Loop Policy** and **AI Impact Assessment** procedure
- [ ] Begin the global compliance matrix, mapping internal control statements to EU AI Act, ISO/IEC 42001, and NIST AI RMF requirements

> **Note:** The roadmap above assumes a greenfield governance program. Organizations with existing security or compliance infrastructure may compress the timeline significantly — particularly where SIEM integration, secret management, and egress controls already exist and can be extended to cover AI workloads.

---

## 9. Global Compliance Matrix Architecture

A compliance matrix ensures internal controls satisfy the strictest global requirements, align to certifiable governance frameworks, and produce auditable evidence. It is the **single source of truth**: a record showing auditors and regulators exactly how each internal control maps to each external obligation.

### 9.1 Twelve Universal Control Themes

These themes appear consistently across all major frameworks and serve as the common mapping language:

1. Risk Management Lifecycle
2. Data Governance and Quality
3. Logging, Monitoring, and Traceability
4. Human Oversight
5. Transparency and User Information
6. Technical Documentation and Record-Keeping
7. Security, Robustness, and Adversarial Testing
8. Access Control and RBAC
9. Configuration Management and Change Control
10. Model and Data Provenance and Integrity
11. Incident Response and Post-Market Monitoring
12. Supplier and Third-Party Model Governance

### 9.2 Framework Mapping by Control Theme

| Control Theme | EU AI Act | ISO/IEC 42001 | NIST AI RMF | NIST SP 800-53 / 800-171 |
|--------------|-----------|---------------|-------------|--------------------------|
| Risk Management Lifecycle | Art. 9, 10, 15 | Sect. 6–10 (PDCA) | Govern/Map/Measure/Manage | RA family |
| Data Governance & Quality | Art. 10 | Support/Operations | Map/Manage | SC, MP, PL families |
| Logging & Traceability | Art. 12–13 | Performance & records | Measure/Manage | AU-2, AU-3 |
| Human Oversight | Art. 14 | Roles & competence | Govern/Manage | AT, PM families |
| Transparency | Art. 13, 50 | Operations | Govern | PM family |
| Technical Documentation | Art. 11 | AIMS records | All functions | PM, PL families |
| Security & Robustness | Art. 15 | Operations | Measure/Manage | SI, RA families |
| Access Control & RBAC | Art. 9, 14 | Roles, operations | Govern | AC, IA families |
| Configuration Management | QMS obligations | Policy/operations | Manage | CM-6, CM-2/3/4 |
| Provenance & Integrity | Art. 10, 12 | AIMS governance | Map/Manage | AU, SI families |
| Incident Response | Art. 61, 73 | Corrective action | Manage | IR family |
| Supplier Governance | QMS & suppliers | Supplier management | Govern | SA, SR families (800-171 Rev.3) |

The full compliance matrix with individual control statement mappings, evidence requirements, and responsible roles, is maintained as a living artifact. When standards revision cycles update framework requirements, the matrix should be reviewed and updated within **30 days of publication**.

---

## 10. Sector-Specific Overlays

The core control set described in this document applies universally. For regulated sectors, the following overlays tighten specific controls without replacing the foundation.

### Financial Services

- Strong model explainability and human-in-the-loop requirements for any output affecting credit, fraud, or pricing decisions
- Enhanced immutable audit trails for customer-impacting decisions, with extended retention periods
- Third-party model onboarding requires enhanced due diligence: risk disclosures, SBOM verification, and independent safety test results per EO 14110 standards

### Healthcare

- Strict data minimization and purpose limitation; PII and PHI redaction enforced at the gateway boundary for all external model calls
- Safety evaluations and bias checks are mandatory components of every TEVV cycle; clinical risk boundaries must be documented in Model Cards
- RAG governance requires vetted medical sources only in the vector store; mandatory human promotion gates before any new source is activated in production

### Defense and Government

- NIST SP 800-171 Rev. 3 alignment required for any system handling CUI, including PL, SA, and SR control families
- No public endpoints for sensitive workloads; air-gapped or cross-domain-controlled ingestion required
- Enhanced TEVV including adversarial red-teaming and misuse resistance evaluation per EO 14110; model and version allow-lists maintained at the gateway level

---

## 11. Governance Artifact Templates

The following templates represent the minimum documentation set required to demonstrate a defensible AI governance posture. Each should be version-controlled as organizational records.

| Artifact | Approx. Length | Framework Alignment |
|----------|---------------|---------------------|
| AI Acceptable Use Policy | 5 pages | NIST AI RMF Govern; ISO/IEC 42001 |
| AI Risk Classification Standard (+ decision tree) | 3–4 pages + diagram | EU AI Act risk tiers; NIST AI RMF Map |
| Model Card (owner, scope, data, metrics, risks, rollback) | 1–2 pages per model | ISO/IEC 42001 governance; NIST AI RMF Measure |
| AI Impact Assessment (AIIA) short form | 3–5 pages | EU AI Act Art. 9; NIST AI RMF risk mgmt |
| TEVV / Red-Team Checklist | 2–3 pages | OWASP LLM Top 10 mapped; EO 14110 |
| Logging Profile (AU-2/AU-3 event schema + retention) | 2 pages + schema | NIST SP 800-53 AU-2, AU-3 |
| Third-Party Model Intake Questionnaire | 2–3 pages | EO 14110; ISO/IEC 42001 supplier management |
| AI Incident Response Playbook | 5–8 pages | OWASP GenAI; ISO/IEC 42001; NIST AI RMF Manage |
| Global Compliance Matrix | Living document | All frameworks |

---

## 12. Program Tailoring and Open Questions

Before finalizing this framework for adoption, the following questions should be addressed to right-size controls for the specific organizational context.

**Regulatory regimes in scope**
Which data classifications apply — CUI, HIPAA, PCI, SOX? If CUI is in scope, AI controls must align to NIST SP 800-171 Rev. 3 (including its new PL, SA, and ODP requirements) to ensure future-proofing even where existing contracts reference Rev. 2.

**Infrastructure footprint**
Where will models run, on-premises (zLinux/Ollama), private cloud, public cloud SaaS, or a mixed environment? The answer determines which gateway architecture is most appropriate.

**Governance philosophy**
Where on the spectrum between "restricted by default unless approved" and "permitted by default unless risk threshold is exceeded" does the organization want to operate? This single decision shapes the intake experience more than any other governance design choice.

**Ownership model**
Who owns AI governance long-term — not just approval authority, but the actual lifecycle? Security, Compliance, Architecture, Data Governance, or a combined body? Governance that lacks a clear owner tends to drift toward the very fragmentation this framework is designed to eliminate.

**Existing infrastructure reuse**
What secrets management, allow-listed egress patterns, and SIEM integrations already exist? The fastest path to AI governance maturity runs through infrastructure that is already deployed and trusted, extending existing controls rather than building parallel systems.

---

This framework is designed to be a **living document**. As regulatory guidance evolves, as new threat categories emerge from the OWASP community, and as the organization's own AI footprint grows, the framework should be reviewed and updated on at least an annual cycle with material changes triggering an immediate update to the compliance matrix and affected policy artifacts.

> **Recommendation:** Begin with the Day-Zero rules and the AI Use-Case Intake form. These two actions require no committee approval, create immediate risk reduction, and establish the organizational precedent that AI governance is real, consistent, and here to stay.

---

*AI Compliance Standards for a Global Landscape — Version 1.0 | Confidential*
