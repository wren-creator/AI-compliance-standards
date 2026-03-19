# AI Compliance Standards for a Global Landscape
### A Unified Governance, Risk, and Compliance Framework for Enterprise AI

> **Version 1.0 | Confidential**
> Aligned to: NIST AI RMF · ISO/IEC 42001 · EU AI Act · OWASP GenAI · NIST SP 800-53 Rev.5

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [The Global Regulatory Landscape: A Unified Strategy](#2-the-global-regulatory-landscape-a-unified-strategy)
3. [The Three-Layer Policy Stack](#3-the-three-layer-policy-stack)
4. [Technical Guardrails and the Universal Control Architecture](#4-technical-guardrails-and-the-universal-control-architecture)
5. [Role-Based Access Control for AI Systems](#5-role-based-access-control-for-ai-systems)
6. [AI Use-Case Lifecycle: From Idea to Retirement](#6-ai-use-case-lifecycle-from-idea-to-retirement)
7. [AI Day-Zero Rules](#7-ai-day-zero-rules)
8. [Implementation Roadmap: 30-60-90 Days](#8-implementation-roadmap-30-60-90-days)
9. [Global AI Compliance Matrix](#9-global-ai-compliance-matrix)
10. [Sector-Specific Overlays](#10-sector-specific-overlays)
11. [Model Card Template](#11-model-card-template)
12. [AI Use-Case Intake and Impact Assessment (AIIA)](#12-ai-use-case-intake-and-impact-assessment-aiia)
13. [AI Incident Response Playbook](#13-ai-incident-response-playbook)
14. [Third-Party AI Model and Vendor Intake Questionnaire](#14-third-party-ai-model-and-vendor-intake-questionnaire)
15. [Quarterly AI Transparency Note](#15-quarterly-ai-transparency-note)

---

## 1. Executive Summary

AI governance is shifting from fragmented, undocumented norms to a unified, enforceable control plane. For most organizations today, AI policies are scattered across ad hoc expectations, vendor usage terms, tribal security knowledge, and shadow rules living in individual teams' heads creating inconsistent risk posture, unpredictable approvals, and policy debt that accumulates like technical debt.

This document establishes a coherent, authoritative, and enforceable AI governance framework built on three foundational principles:

- **Anchor to established frameworks.** By aligning to NIST AI RMF, ISO/IEC 42001, the EU AI Act, and OWASP GenAI, governance decisions are defensible, audit-ready, and globally portable.
- **Set precedent proactively.** Rather than reacting to external enforcement timelines or vendor-defined guardrails, this framework establishes internal norms that become the standard others follow, rational controls that enable delivery instead of creating bureaucratic drag.
- **Couple policy to technical enforcement.** Rules are not merely words. Every policy maps to enforceable controls: gateways, logging, redaction, registries, and telemetry feeding directly into SIEM infrastructure.

The framework is organized around a unified strategy: **follow the strictest rule (the EU AI Act) to simplify global operations.** By anchoring to a common core, risk management, data governance, and logging. We create regional dial settings that allow compliance tuning for specific jurisdictions without reinventing the wheel. Build once, deploy anywhere.

---

## 2. The Global Regulatory Landscape: A Unified Strategy

> **Verbiage Strategy:** Focus on "efficiency through alignment." The goal is to convince stakeholders that following the strictest rule (EU AI Act) simplifies global operations rather than complicating them. A program built to satisfy EU AI Act obligations will generally satisfy all other frameworks by default.

Any enterprise operating AI systems that touch multiple jurisdictions must assume a multinational regulatory environment from day one. The **"Build Once, Deploy Anywhere"** principle means anchoring to a common core of risk management, data governance, and logging, then creating regional dial settings to tune compliance for specific jurisdictions without reinventing the wheel.

### 2.1 Framework Alignment Matrix

| Category | Framework | Key Governance Role |
|----------|-----------|---------------------|
| **Voluntary / Lifecycle** | NIST AI RMF | Provides the Govern → Map → Measure → Manage backbone for all internal processes and artifacts. |
| **Auditable Standard** | ISO/IEC 42001 | Acts as the "ISO 27001 for AI," providing a certifiable AI Management System structure. |
| **Binding Law** | EU AI Act | Defines the **compliance ceiling** with prescriptive risk tiering and multi-million-euro penalty risks. |
| **Risk Guidance** | ISO/IEC 23894 | AI-specific risk management guidance covering the full lifecycle, including drift and bias hazards. |
| **Technical Security** | OWASP GenAI Top 10 | The definitive threat model for preventing prompt injection, data exfiltration, and excessive agency. |
| **Executive Directive** | US EO 14110 | Mandates red-team testing, content provenance, and risk standards; justifies internal test-before-prod gates. |
| **Security Controls** | NIST SP 800-53 Rev.5 | IT control catalog; AU-2/AU-3 (logging) and CM-6 (configuration hardening) apply directly to AI systems. |

### 2.2 Where Global Frameworks Converge and Diverge

Despite significant differences in legal status, all major global frameworks share a **common governance core**: risk management lifecycle, data governance and bias control, logging and traceability, human oversight, security and robustness testing, and documentation and record-keeping.

**Key divergences:**

| Dimension | EU AI Act | NIST AI RMF / ISO | US EO 14110 |
|-----------|-----------|-------------------|-------------|
| Legal status | Binding law, enforceable penalties | Voluntary guidance / certifiable standard | Binding for federal agencies; private sector signal |
| Risk tiering | Prescriptive: regulator defines high-risk categories | Contextual: organization defines thresholds | Not prescriptive |
| Documentation burden | Extremely high: mandatory technical files, QMS, conformity assessment | Moderate (ISO) to flexible (NIST) | Focused on safety testing and provenance records |
| Red-teaming | Implied via cybersecurity obligations | Recommended, not mandated | **Explicitly required** before release |
| Transparency | Legally mandates disclosure of AI-generated content | General guidance, implementer-defined | Promotes provenance standards; less prescriptive |

> **Practical implication:** A program built to satisfy EU AI Act obligations will generally satisfy the requirements of all other frameworks. NIST AI RMF and ISO/IEC 42001 provide the structural language and audit-readiness; the EU AI Act defines the compliance ceiling.

---

## 3. The Three-Layer Policy Stack

> **Verbiage Strategy:** Use a functional hierarchy. **Policy is the What. Standards are the How. Procedures are the Do.**

Conflating these layers creates documents that are simultaneously too abstract to enforce and too detailed to survive organizational change. The mental model: *policy text references frameworks; standards implement them; configurations enforce them.*

### Layer A: Board-Level Policies (The "Durable" Intent)

Policies define principles, scope, and intent. They should be durable, resistant to organizational restructuring, and written at a level executives and auditors can meaningfully review.

| Policy | Description |
|--------|-------------|
| **AI Acceptable Use and Data Boundary Policy** | Establishes the Data Boundary, strictly prohibiting transfer of PII or sensitive data to unapproved public endpoints. **Publish this first.** |
| **AI Risk Classification Policy** | Automatically categorizes every project into one of four tiers: Prohibited, High, Limited, or Minimal mirroring the EU AI Act hierarchy. |
| **Third-Party AI Procurement and Model Intake Policy** | Requires model cards, SBOMs, license/terms review, security posture assessment, and test evidence before any external model is onboarded. |
| **AI Logging, Monitoring, and Retention Policy** | Mandates event types, retention periods, and PII minimization requirements. Mapped to AU-2 and AU-3. |
| **Human-in-the-Loop Policy** | For high-risk decisions: requires pre-deployment TEVV and defines operational thresholds for human review. Mirrors EU AI Act Articles 9–15. |

### Layer B: Mappable Standards (The "Bridge")

Standards translate policy intent into specific requirements that can be mapped directly to security controls.

- **Identity and Access Standard**: Least-privileged tool access and token scoping for all AI agent interactions.
- **Data Governance Standard**: Specific masking, retrieval filtering, and PII/sensitive term deny-lists required for RAG systems.
- **Secure SDLC for AI**: Mandates red-teaming, toxicity evaluations, and jailbreak resistance testing before any production Go-Live. Aligns to NIST AI RMF Measure and Manage functions.
- **Content Provenance Standard**: Hashing, watermarking, or provenance metadata for machine-generated content per EO 14110.
- **Supply Chain Standard**: Governs curation of models, datasets, and embeddings; vendor SLA requirements; CVE monitoring for AI libraries; minimum model card requirements per ISO/IEC 42001.

### Layer C: Enforceable Procedures (The "Runbooks")

Procedures are the operational layer; specific enough to enforce, simple enough to use.

- **AI Intake and Impact Assessment (AIIA)**: A streamlined, 3-to-5 page document required for high-risk use cases to ensure Article 9 compliance, without imposing unnecessary burden on lower-risk workloads.
- **Logging and Output Hygiene Runbook**: Step-by-step technical instructions for capturing telemetry (AU-2/AU-3) while ensuring secrets are masked and sensitive data is redacted.
- **AI Incident Response Playbooks**: Procedures for AI-specific threat scenarios: prompt injection, data exfiltration, harmful content generation, and model compromise. Aligned to OWASP LLM Top 10.

---

## 4. Technical Guardrails and the Universal Control Architecture

> **Paper policies without technical enforcement are compliance theater.** Every policy in this framework maps to a technical control point.

The architecture below is platform-agnostic and equally applicable to on-premises environments (including zLinux and mainframe-adjacent workloads), private cloud, and public cloud deployments.

### 4.1 The Universal Control Plane

Regardless of whether a model runs on-premises (zLinux/Ollama), in a private cloud, or via SaaS, the following controls are **non-negotiable**:

- **Centralized Gateway Egress**: All AI traffic must route through a proxy that enforces allow-lists, strips sensitive data, and attaches policy context (tenant identity, data classification tags, stated purpose) to every request.
- **Identity and "Least Agency"**: AI agents are granted short-lived, scoped tokens. Unless explicitly approved, LLMs operate without shell access or production write capabilities to prevent "Excessive Agency." *(OWASP GenAI Top 10)*
- **Configuration Hardening (CM-6)**: AI behavior is treated as a Configuration Item (CI). Prompt templates, model hashes, and vector DB schemas are versioned and read-only in production. A change to a prompt template changes system behavior as significantly as a code deploy, and must be treated accordingly.
- **Telemetry and Audit**: Minimum required events: model ID/version, tool invocations, data tags, policy decisions (allowed/blocked/redacted), redaction actions, evaluator scores, and user identity. Mapped to AU-2/AU-3; retained per applicable regulatory clocks.
- **TEVV and Red-Teaming**: Pre-production adversarial testing covering jailbreaks, data leakage, prompt injection, RAG poisoning, and cost-denial-of-service (unbounded inference consumption). Required before any production exposure or external pilot.

### 4.2 Deployment Environment Controls

| Environment | Required Controls |
|-------------|------------------|
| **On-Premises (zLinux)** | Inference endpoints on dedicated VLANs; mutual TLS with FIPS 140-3 crypto; forward journald/syslog to SIEM with tamper-evidence; model artifact pulls only from curated repositories (extend the existing Artifactory pattern). |
| **Private Cloud** | Private endpoints for managed LLMs/vector stores; VPC peering-only access; gateway enforces policy and redaction; same RBAC/ABAC from the central control plane. |
| **Public Cloud / SaaS** | Allow-listed foundation models and regions only; KMS-backed secrets; content provenance on generated outputs per EO 14110; identical AU-2/AU-3 logging schema as on-premises. |

### 4.3 Configuration Management for AI (CM-6 Applied)

A tweak to a prompt template, a modification to retrieval pipeline weights, or a swap of the underlying model artifact changes system behavior as significantly as a software release, but may trigger none of existing change control gates.

| Configuration Item | Baseline Requirements |
|-------------------|----------------------|
| **Model artifacts** | Approved base model list, permitted quantization levels, allowed fine-tune sources, cryptographic hash verification, approved serving parameters |
| **Prompts and agents** | Versioned and read-only in production; tool lists at least privilege; no generic code execution by default |
| **Vector DBs / RAG pipelines** | Schema locked; ingest pipelines curated; production writes restricted to signed CI/CD jobs with change tickets |
| **Gateways** | Model allow-lists, data redaction policies, egress destinations, rate limits, and cost budgets |

### 4.4 Threat Model: Seven Attack Surfaces

| Threat Surface | Risk | Required Controls |
|---------------|------|------------------|
| **Model artifact tampering** | Replacing/modifying checkpoints changes safety, accuracy, and bias without triggering code review | Signed artifacts, registry immutability, CM-6 baseline, verification on load |
| **Prompt template tampering** | Editing system prompts weakens guardrails — no code change required | Prompt versioning as code, approval workflows, runtime hash verification |
| **Vector DB poisoning** | Injecting malicious embeddings creates controlled misinformation via RAG | Curator/Promoter separation, signed ingestion, audit logs, metadata integrity |
| **Tool scope escalation** | Expanding agent privileges creates exfiltration pathways | Least-privilege tool binding, sandboxed execution, no admin credentials to agents |
| **Gateway egress bypass** | Direct API calls bypass redaction, logging, and data boundary enforcement | Gateway-only egress, mTLS, allow-listed endpoints, SIEM alerts for bypass |
| **Retrieval pipeline manipulation** | Changing RAG scoring functions silently shifts factual grounding | Controlled scoring configs, change review, evaluation logs |
| **Safety filter bypass** | Disabling toxicity detectors removes compliance-mandated output controls | Filter hashing, runtime verification, approval required for threshold changes |

---

## 5. Role-Based Access Control for AI Systems

AI systems have three behavioral determinants: **model parameters**, **prompt and agent logic**, and **the retrieval corpus or vector database**. Each must be governed separately. A single actor with unchecked access to all three can change system behavior completely.

| Role | Purpose | Can Do | Cannot Do |
|------|---------|--------|-----------|
| **AIMS_Admin** | Owns governance rules, not systems | Define policies, risk tiering, logging requirements; manage compliance evidence | Deploy models, modify prompts, push embeddings, or write to production |
| **Model_Owner** | Business/technical owner of model behavior | Approve model versions, fine-tunes, quantization profiles, prompt template updates, safety test results | Modify vector DB; deploy artifacts to production; alter infrastructure |
| **Data_Curator** | Controls what enters the retrieval pipeline | Curate source documents for RAG; generate embeddings in staging; submit promotion requests | Write to production vector DB; modify models or prompts; bypass safety filters |
| **Promoter** | Executes approved changes via signed CI/CD | Deploy approved model versions; publish approved embeddings; validate artifact signatures | Approve model or embedding changes; alter behavior logic |
| **Ops_Custodian** | Manages runtime systems but not AI behavior | Maintain compute, networks, storage, secrets, gateways; enforce egress and mTLS | Change models, embeddings, prompts, or agent logic; publish new vector indexes |
| **Gateway_Admin** | Controls access to external models; enforces redaction | Manage allow-listed endpoints; configure redaction rules; manage rate/cost limits; manage provenance labeling | Modify internal LLMs, vector DB, or prompts |
| **Auditor** | Compliance and forensics oversight | Full read-only access to logs, model cards, and configuration baselines | Change anything |

This structure prevents: unauthorized behavioral drift, embedding poisoning, prompt tampering, undocumented model changes, excessive agent autonomy, and misuse of high-risk AI in regulated sectors.

---

## 6. AI Use-Case Lifecycle: From Idea to Retirement

The lifecycle is designed to be simple, familiar, and predictable, similar to change management, but quicker and fit-for-purpose for AI.

```
Intake → Risk Triage → Controls Assignment → Build & TEVV → Go/No-Go → Operate → Decommission
```

| Stage | Description |
|-------|-------------|
| **1. Intake** | 1-page form: purpose, data classifications, user population, integration points, and target model(s). The entry point for everything. |
| **2. Risk Triage** | Auto-classify to Prohibited, High, Limited, or Minimal using a decision tree aligned to EU AI Act tiers. High-risk triggers a full AIIA and mandatory HITL configuration. |
| **3. Controls Assignment** | Apply the pre-defined control bundle for the risk tier. No per-case negotiation predictable lanes only. |
| **4. Build and TEVV** | Scenario tests, adversarial red-team testing, bias/safety metric evaluation. Record all results in the Model Card per NIST AI RMF Measure documentation standards. |
| **5. Go/No-Go (Lightweight CAB)** | Review scope, agency permissions, and rollback procedures. Designed for a 30-minute queue, not a 30-day cycle. |
| **6. Operate** | Continuous drift and safety monitoring, cost guardrails, quarterly access reviews, incident response rehearsal. |
| **7. Decommission** | Archive model and telemetry, revoke all secrets and credentials, scrub temporary stores. |

---

## 7. AI Day-Zero Rules

**Effective Immediately: Mandatory Norms for All AI Research, Development, and Operations.**

Culture shifts happen before documents. These ten rules can be announced and enforced before the full policy stack is published.

| # | Rule | Required Action |
|---|------|----------------|
| **1** | **The Data Boundary:** Strict prohibition on sending PII, CUI, or IP to public LLM endpoints. | All external model traffic must route through the approved AI Gateway with redaction enabled. |
| **2** | **Zero Shadow AI:** Every use case — including internal experiments must be registered. | Submit a 1-page intake form before initiating any new model pull or API integration. |
| **3** | **Human-in-the-Loop (HITL):** Human review is mandatory for AI outputs affecting finance, HR, customers, or security. | High-risk systems must trigger a manual approval gate before final execution. |
| **4** | **Curated Model Registry:** Only models and plugins from the authorized internal registry are permitted in production. | Verify the cryptographic hash and license of any model against the Model Registry before deployment. |
| **5** | **Mandatory Logging (AU-2/AU-3):** Prompt and output logging is ON by default for all enterprise AI interactions. | Ensure all telemetry includes user identity, timestamps, and redaction metadata. |
| **6** | **Anti-Agency Guardrails:** LLMs are prohibited from autonomous code execution or system modification. | Agents must operate with Least Privilege tokens and zero shell access by default. *(OWASP GenAI)* |
| **7** | **Pre-Flight Red-Teaming:** No production exposure or external pilots without adversarial testing. | Complete the TEVV checklist covering prompt injection and RAG poisoning scenarios. *(EO 14110)* |
| **8** | **The Model Card Standard:** Every deployed model must have a completed Model Card. | Document purpose, training data lineage, risks, evaluation scores, owners, and rollback procedures. |
| **9** | **Content Provenance:** All machine-generated customer-facing content must be labeled. | Apply watermarking or metadata tags to identify AI-generated assets per EO 14110. |
| **10** | **Continuous Hygiene:** AI access permissions and logs are subject to mandatory quarterly reviews. | Role owners must validate that behavioral drift remains within established safety thresholds. |

> **Note to Teams:** These rules ensure our innovation is defensible, audit-ready, and globally portable. They are grounded in the NIST AI RMF, ISO/IEC 42001, and the EU AI Act. A companion single-page quick-reference card should be published alongside the formal policy.

---

## 8. Implementation Roadmap: 30-60-90 Days

### Days 0–30: Bootstrap

Focus: Stop the most immediate risks and establish foundational infrastructure.

- [ ] Stand up the AI Use-Case Intake form and lightweight risk triage decision tree
- [ ] Publish the Day-Zero ten rules
- [ ] Configure an AI gateway (even a basic reverse proxy with redaction policies) to centralize traffic
- [ ] Draft and publish the **AI Acceptable Use and Data Boundary Policy** and **AI Logging and Monitoring Policy** (mapped to AU-2/AU-3)
- [ ] Identify and communicate RBAC role owners for AIMS_Admin, Gateway_Admin, and Auditor functions

### Days 31–60: Operationalize

Focus: Build scaffolding for repeatable, consistent governance.

- [ ] Build the Model Registry and Model Card template (mapped to NIST AI RMF and ISO/IEC 42001)
- [ ] Define control bundles by risk tier (Minimal, Limited, High)
- [ ] Pilot TEVV with a red-team playbook covering prompt injection, RAG poisoning, sensitive data leakage, and unbounded consumption
- [ ] Draft the **AI Risk Classification Policy** and **Third-Party AI Procurement and Model Intake Policy**
- [ ] Complete RBAC role assignments across all seven roles

### Days 61–90: Institutionalize

Focus: Make governance self-sustaining and externally defensible.

- [ ] Launch the AI Change Advisory Board (recommended: weekly cadence, 30-minute queue target)
- [ ] Integrate AI telemetry into the SIEM; add drift detection and safety dashboards
- [ ] Run the first quarterly governance review and publish the initial **Quarterly Transparency Note**
- [ ] Complete the **Human-in-the-Loop Policy** and **AI Impact Assessment** procedure
- [ ] Begin the global compliance matrix build, mapping internal control statements to EU AI Act, ISO/IEC 42001, and NIST AI RMF

> **Note:** This roadmap assumes a greenfield governance program. Organizations with existing SIEM integration, secret management, and egress controls may compress the timeline significantly by extending those controls to cover AI workloads rather than building parallel systems.

---

## 9. Global AI Compliance Matrix

This matrix connects internal control themes and artifacts to the specific articles and sections of global frameworks. It is the **single source of truth** for audit readiness.

**How to use this matrix:**
- **Audit Readiness:** When an auditor asks how you comply with EU AI Act Article 12 (Logging), point directly to your Logging and Output Hygiene Runbook and the resulting AU-2/AU-3 logs.
- **Regulatory Updates:** When a framework is updated, update only the mapping in this matrix within 30 days; one change, not a full policy rewrite.
- **Evidence Collection:** Each row should link to a folder of evidence (e.g., signed AIIA forms, timestamped red-team reports, configuration baseline records).

| Control Theme | Internal Artifact / Procedure | EU AI Act | NIST AI RMF | ISO/IEC 42001 |
|--------------|-------------------------------|-----------|-------------|---------------|
| Risk Management | AI Intake & Impact Assessment (AIIA) | Art. 9, 10, 15 | Govern / Map | Sect. 6–10 |
| Data Governance | Acceptable Use & Data Boundary Policy | Art. 10 | Map / Manage | Support / Operations |
| Transparency | Model Card Standard | Art. 13, 50 | Govern | Operations |
| Logging & Audit | Prompt & Output Logging Runbook | Art. 12–13 | Measure / Manage | Performance Records |
| Human Oversight | Human-in-the-Loop Policy | Art. 14 | Govern / Manage | Roles & Competence |
| Security & TEVV | TEVV / Red-Team Checklist | Art. 15 | Measure / Manage | Operations |
| Configuration Mgmt | CM-6 AI Baseline Standard | QMS obligations | Manage | Policy / Operations |
| Incident Response | AI Incident Response Playbook | Art. 61, 73 | Manage | Corrective Action |
| Supplier Governance | Third-Party Model Intake Questionnaire | QMS Obligations | Govern | Supplier Mgmt |
| Access Control | RBAC Policy & Role Assignments | Art. 9, 14 | Govern | Roles & Operations |

---

## 10. Sector-Specific Overlays

The core control set applies universally. For regulated sectors, the following overlays tighten specific controls without replacing the foundation.

### Financial Services

- Strong model explainability and human-in-the-loop requirements for any output affecting credit, fraud, or pricing decisions
- Enhanced immutable audit trails for customer-impacting decisions, with extended retention periods
- Third-party model onboarding requires enhanced due diligence: risk disclosures, SBOM verification, and independent safety test results per EO 14110

### Healthcare

- Strict data minimization and purpose limitation; PII and PHI redaction enforced at the gateway boundary for all external model calls
- Safety evaluations and bias checks are mandatory TEVV components; clinical risk boundaries must be documented in Model Cards
- RAG governance requires vetted medical sources only; mandatory human promotion gates before any new source is activated in production

### Defense and Government

- NIST SP 800-171 Rev. 3 alignment required for any system handling CUI, including PL, SA, and SR control families
- No public endpoints for sensitive workloads; air-gapped or cross-domain-controlled ingestion required
- Enhanced TEVV including adversarial red-teaming and misuse resistance evaluation per EO 14110; model and version allow-lists maintained at the gateway level

---

## 11. Model Card Template

Every deployed model must have a completed Model Card registered in the Central Model Registry. This card must be updated within **30 days** of any material change to the model artifact, prompt template, or retrieval pipeline.

---

**Model Card: `[Model Name/Version]`**
**Status:** `[Draft / Pending Review / Approved / Retired]`
**Owner:** `[Model_Owner Role Name]`
**Last Updated:** `[Date]`

---

### 1. General Identification

- **Model Name and Version:** Specific identifier (e.g., `Llama-3-70b-v1.2`).
- **License Type:** Commercial, Open-Source (e.g., Apache 2.0), or Restricted.
- **Base Model Origin:** Training data lineage and original developer.
- **Quantization Level:** Precision level (e.g., 4-bit, FP16) to ensure behavioral consistency across environments.

### 2. Operational Scope and Purpose

- **Intended Use Case:** Primary business function and user population.
- **Out-of-Scope Uses:** Prohibited applications (e.g., "Not for medical diagnosis").
- **Risk Tier:** `[Minimal / Limited / High]` per the AI Risk Classification Policy.
- **Agency Level:** Approved tool and plugin capabilities and access scopes.

### 3. Safety and Performance Metrics (TEVV Results)

- **Evaluator Scores:** Results from toxicity, bias, and accuracy benchmarks.
- **Adversarial Resilience:** Summary of red-team findings for jailbreak and injection resistance.
- **Drift Baselines:** Initial behavioral checksums used for monitoring deviation over time.
- **Data Redaction Profile:** List of PII and sensitive categories filtered at the gateway.

### 4. Technical Governance and Change Control

- **System Prompt Hash:** Versioned reference to the read-only production prompt template.
- **Cryptographic Verification:** SHA-256 hash of the model artifact for tamper detection.
- **Inference Endpoint:** Authorized VLAN/URL with mTLS enforcement.
- **Retention Policy:** Audit log storage duration (e.g., 2 years) per applicable regulatory requirements.

### 5. Rollback and Decommissioning

- **Contingency Plan:** Step-by-step instructions for reverting to a previous approved version or manual fallback process.
- **Decommissioning Procedure:** Requirements for revoking secrets, archiving telemetry, and scrubbing temporary stores.

---

## 12. AI Use-Case Intake and Impact Assessment (AIIA)

Completion of this form is required for **every AI use case, including experiments**, to eliminate Shadow AI. High-risk classifications will automatically trigger a review by the AI Change Advisory Board.

---

**Document ID:** `[AIIA-YYYY-####]`
**Submission Date:** `[Date]`
**Primary Contact:** `[Project Lead Name]`

---

### 1. Project Overview and Intent

- **Use-Case Name:** Descriptive title of the AI application or integration.
- **Business Objective:** A clear description of the purpose and intended user population.
- **Target Model(s):** List of specific models or external APIs intended for use.
- **Integration Points:** Description of how the AI will interface with existing enterprise systems.

### 2. Data Classification and Boundaries

- **Data Types Involved:** Identification of data classifications specifically noting PII, PHI, CUI, or Financial records.
- **Data Residency:** Disclosure of where the data will be processed: On-premises, Private Cloud, or Public SaaS.
- **Egress Path:** Confirmation that all traffic will route through the centralized AI Gateway.

### 3. Risk Triage (Decision Tree)

Based on the inputs above, the system auto-classifies the project into one of the following tiers aligned to the EU AI Act:

| Tier | Label | Definition and Trigger |
|------|-------|------------------------|
| 🔴 | **Prohibited** | Unacceptable risk. Hard stop. Examples: social scoring systems, real-time biometric identification in public spaces. |
| 🟡 | **High-Risk** | Affects critical infrastructure, employment, or legal status. Requires full Model Card, TEVV, AIIA review, and mandatory HITL configuration before Go-Live. |
| 🔵 | **Limited / Minimal** | Lower-stakes internal productivity tools and experiments. Requires baseline Day-Zero compliance, intake registration, and logging. |

### 4. Behavioral and Agency Assessment

- **Decision Authority:** Does this AI make autonomous decisions affecting finance, HR, or security?
- **Tool/Plugin Permissions:** Will the LLM have Excessive Agency — the ability to execute code, send emails, or modify production databases?
- **Human-in-the-Loop (HITL):** Define the mandatory pre-deployment review and operational thresholds for human oversight.

### 5. Deployment and Post-Market Plan

- **TEVV Strategy:** Summary of the adversarial testing plan, including jailbreak and RAG poisoning scenarios.
- **Drift Monitoring:** Proposed method for detecting behavioral changes or accuracy degradation once live.
- **Rollback Procedure:** Description of the kill-switch or manual fallback process if the AI fails or is compromised.

---

## 13. AI Incident Response Playbook

**Scope:** Specific procedures for AI threat scenarios including prompt injection, data exfiltration, unauthorized configuration change, and model compromise.

> **This playbook must be rehearsed quarterly** via incident response drills to ensure Ops_Custodian and AIMS_Admin can execute containment steps within minutes, not hours.

### Phase 1: Detection and Identification

- **Trigger Alerts:** SIEM alerts for gateway bypass attempts, unauthorized model calls, or high-confidence toxicity detections.
- **Behavioral Deviation:** Identification of configuration drift where embeddings or RAG pipeline weights shift without an associated change ticket.
- **Incident Triage:** Categorize by threat surface (e.g., Model Artifact Tampering vs. Vector DB Poisoning vs. Gateway Egress Bypass).

### Phase 2: Containment and Neutralization

- **The Kill-Switch:** Immediate revocation of short-lived scoped tokens to halt excessive agency or unauthorized automated shell commands.
- **Gateway Lockdown:** Update the AI Gateway allow-list to block a specific model version or egress destination.
- **Prompt Isolation:** Revert to the last-known good version-controlled system prompt template, verified by hash.

### Phase 3: Investigation and Forensic Analysis

- **Telemetry Review:** Analysis of AU-2 and AU-3 logs, including user identity, prompt/output hashes, tool invocations, and redaction metadata.
- **Artifact Verification:** Check cryptographic hashes of model artifacts against the Model Registry to detect tampering.
- **Root Cause Analysis:** Determine whether the breach was via direct injection, indirect RAG poisoning, insecure output handling, or supply chain compromise.

### Phase 4: Recovery and Eradication

- **Environment Scrubbing:** Revoke all secrets and credentials; scrub temporary data stores associated with the incident.
- **Vector DB Sanitation:** Identify and remove malicious embeddings or poisoned source documents from the RAG pipeline.
- **TEVV Re-Validation:** Mandatory adversarial red-teaming (jailbreak and leakage tests) before the system is restored to production.

### Phase 5: Post-Incident Activities

- **Transparency Note:** Publish a summary of the incident and corrective actions for the quarterly governance review.
- **Policy Update:** Refine gateway redaction rules or Day-Zero norms to prevent recurrence. Update the Global Compliance Matrix if controls need to be strengthened.
- **Playbook Revision:** Update this playbook based on lessons learned and share with AIMS_Admin, Ops_Custodian, and Gateway_Admin.

---

## 14. Third-Party AI Model and Vendor Intake Questionnaire

**Aligned to:** NIST AI RMF · ISO/IEC 42001 · EO 14110

> This questionnaire must be completed by the vendor and reviewed by the AIMS_Admin and Model_Owner **before any procurement finalization.** Failure to meet Data Boundary or Least Agency requirements will trigger an immediate **No-Go** decision unless compensating technical safeguards are implemented at the AI Gateway.

### 1. Model Identity and Provenance

- **Model Provenance:** Provide training data lineage and specify if any copyrighted or sensitive datasets were used.
- **Artifact Integrity:** Can the vendor provide cryptographic hashes (SHA-256) for model artifacts to prevent tampering during delivery?
- **Licensing and SBOM:** Attach a Software Bill of Materials (SBOM) and full licensing terms for the model and all associated libraries.

### 2. Security and Robustness (TEVV)

- **Adversarial Testing:** Provide evidence of red-team testing for prompt injection, jailbreaking, and data leakage.
- **Vulnerability Management:** Describe the process for monitoring and patching CVEs within AI-specific libraries or dependencies.
- **Safety Filter Disclosures:** Detail built-in toxicity and hallucination detectors and specify if these can be bypassed or modified by operators.

### 3. Data Privacy and Governance

- **Data Minimization:** Does the service support PII/PHI redaction at the boundary before processing?
- **Retention and Logging:** Specify default data retention periods and confirm if administrative logs (AU-2/AU-3 equivalent) are available for export to our SIEM.
- **Training Opt-Out:** Does the vendor contractually guarantee that our prompts and outputs will **NOT** be used to train future model versions?

### 4. Operational Control and Agency

- **Agency Scope:** Does the model require shell access, arbitrary network calls, or production write capabilities to function?
- **Identity Management:** Does the system support short-lived, scoped tokens and least-privileged access for all tool interactions?

### 5. Compliance and Audit

- **Regulatory Tiering:** Does the vendor provide a self-assessment of the model's risk tier under the EU AI Act (Prohibited, High, Limited, Minimal)?
- **Attestations:** Provide any existing ISO/IEC 42001 or SOC2 Type II certifications relevant to the AI management system.

---

## 15. Quarterly AI Transparency Note

The Quarterly Transparency Note is a condensed summary of AI governance activities for stakeholders. Detailed technical logs are available for review by the authorized Auditor role.

---

**Reporting Period:** `[Q# YYYY]`
**Release Date:** `[Date]`
**Prepared By:** AI Governance Body (AIMS_Admin)

---

### 1. Executive Summary of AI Operations

- **Total Registered Use Cases:** `[Number]` active AI systems currently in production or pilot phases.
- **Risk Distribution:** `[%]`% Minimal Risk · `[%]`% Limited Risk · `[%]`% High-Risk.
- **System Uptime and Reliability:** Performance metrics for the centralized AI Gateway and inference endpoints.

### 2. Governance and Compliance Milestones

- **Assessment Volume:** `[Number]` AI Impact Assessments (AIIA) completed this quarter.
- **Model Registry Updates:** `[Number]` new Model Cards published; `[Number]` models retired or decommissioned.
- **Regulatory Alignment:** Successful mapping of all high-risk controls to the EU AI Act and NIST AI RMF via the Global Compliance Matrix.

### 3. Security and Technical Integrity

- **Red-Teaming Activity:** `[Number]` TEVV cycles completed, including jailbreak and RAG poisoning simulations.
- **Data Boundary Enforcement:** `[Number]` sensitive data points successfully redacted at the gateway boundary.
- **Configuration Stability:** Summary of CM-6 hardening activities and behavioral drift monitoring alerts triggered and resolved.

### 4. Incident and Access Review

- **Reported Incidents:** `[Number]` AI-specific security events identified and resolved per the Incident Response Playbook.
- **Access Control:** Completion of quarterly RBAC review; `[Number]` permissions modified to maintain Least Agency.
- **Audit Findings:** Summary of any internal or third-party audit observations and associated corrective actions.

### 5. Looking Ahead: Next Quarter Priorities

- **Roadmap Focus:** Description of which 30-60-90 day phase activities are being advanced.
- **Policy Refinements:** Planned updates to active policies (e.g., Human-in-the-Loop Policy, Third-Party Model Intake Policy).
- **Framework Updates:** Any new regulatory guidance or framework revisions requiring compliance matrix updates within 30 days.

---

> **Recommendation:** Begin with the Day-Zero rules and the AI Use-Case Intake form. These two actions require no committee approval, create immediate risk reduction, and establish the organizational precedent that AI governance is real, consistent, and here to stay.

---

*AI Compliance Standards for a Global Landscape — Version 1.0 | Confidential*
