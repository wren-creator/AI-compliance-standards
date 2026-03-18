
# Master Controls Catalog (MCC) — AI Governance, Security & Compliance

**Version:** 1.0  
**Last Updated:** 2026-03-18 14:52:32Z  

This Master Controls Catalog (MCC) defines a unified, globally aligned control set for governing, securing, and operating AI systems across on‑prem, private cloud, and public cloud environments. It is designed to satisfy the common core of global frameworks (e.g., NIST AI RMF, ISO/IEC 42001, ISO/IEC 23894) while meeting binding regulatory obligations (e.g., EU AI Act) and mapping to technical security controls (e.g., NIST SP 800‑53, and where applicable, NIST SP 800‑171 Rev.3 for CUI).

> **How to use this catalog**
> - Treat these as your “gold” internal controls.
> - Link each control to concrete standards/procedures (gateway configs, CI/CD jobs, registries, RBAC policies, SIEM schemas).
> - The **Evidence** sections specify what to log/retain for audits.
> - The **Authoritative Mappings** list the frameworks and control families each control supports.

---

## Roles & Separation of Duties (SoD)

- **AIMS_Admin** — Owns governance program, policies, risk lifecycle, audits. No direct ability to deploy or modify production artifacts.
- **Model_Owner** — Approves model/prompt/agent logic and evaluation criteria. Cannot deploy to production or modify vector DB contents.
- **Data_Curator** — Curates sources, prepares embeddings in *staging only*. No production write permissions.
- **Promoter** — Machine/service identity that executes *signed* promotions to production. Cannot approve changes.
- **Ops_Custodian** — Manages infrastructure (clusters, networks, storage, secrets). No ability to change model/prompt/index content.
- **Gateway_Admin** — Manages AI gateway policies (allow‑lists, redaction, rate/cost limits, provenance). No ability to alter models or vectors.
- **Auditor** — Read‑only access to configurations, logs, and documentation.

---

## Table of Contents

- [MCC‑01 — AI Risk Management Lifecycle (AIRM)](#mcc-01--ai-risk-management-lifecycle-airm)
- [MCC‑02 — Data Governance & Quality (DGQ)](#mcc-02--data-governance--quality-dgq)
- [MCC‑03 — Logging, Monitoring & Traceability (LMT)](#mcc-03--logging-monitoring--traceability-lmt)
- [MCC‑04 — Human Oversight & HITL (HO)](#mcc-04--human-oversight--hitl-ho)
- [MCC‑05 — Transparency & User Information (TXP)](#mcc-05--transparency--user-information-txp)
- [MCC‑06 — Security, Robustness & TEVV (SRT)](#mcc-06--security-robustness--tevv-srt)
- [MCC‑07 — Access Control & RBAC (ARB)](#mcc-07--access-control--rbac-arb)
- [MCC‑08 — Configuration Management & CM‑6 for AI CIs (CMC)](#mcc-08--configuration-management--cm6-for-ai-cis-cmc)
- [MCC‑09 — Model & Data Provenance / Integrity (MDP)](#mcc-09--model--data-provenance--integrity-mdp)
- [MCC‑10 — Signed CI/CD & Artifact Attestation (SCD)](#mcc-10--signed-cicd--artifact-attestation-scd)
- [MCC‑11 — AI Gateway Enforcement (AGE)](#mcc-11--ai-gateway-enforcement-age)
- [MCC‑12 — RAG & Vector Store Governance (RVG)](#mcc-12--rag--vector-store-governance-rvg)
- [MCC‑13 — Incident Response for AI (IR‑AI)](#mcc-13--incident-response-for-ai-irai)
- [MCC‑14 — Post‑Market Monitoring & Drift (PMD)](#mcc-14--postmarket-monitoring--drift-pmd)
- [MCC‑15 — Supplier & Third‑Party Governance (STG)](#mcc-15--supplier--thirdparty-governance-stg)
- [MCC‑16 — Sector Overlays (SEC‑OV)](#mcc-16--sector-overlays-sec-ov)
- [MCC‑17 — Transparency Records & Technical Documentation (TRD)](#mcc-17--transparency-records--technical-documentation-trd)
- [MCC‑18 — Gateway Bypass Prevention & Egress Control (GBE)](#mcc-18--gateway-bypass-prevention--egress-control-gbe)
- [MCC‑19 — Explainability & Output Governance (XOG)](#mcc-19--explainability--output-governance-xog)
- [MCC‑20 — Governance Reviews & Continuous Improvement (GRCI)](#mcc-20--governance-reviews--continuous-improvement-grci)

---

## MCC‑01 — AI Risk Management Lifecycle (AIRM)
**Purpose**: Ensure every AI use case follows a documented, repeatable risk process across the lifecycle.  
**Scope**: All AI systems (on‑prem, private, public), prototypes → production.

**Control Statements**:
1. All use cases must undergo a risk lifecycle (**Govern → Map → Measure → Manage**) before promotion to production and periodically thereafter.
2. High‑risk systems must maintain a living risk file including hazards, mitigations, and post‑market monitoring.

**Implementation Procedures**: Intake → Risk triage (tiering) → AIIA/AIRA → TEVV plan → residual risk sign‑off → quarterly re‑evaluation.

**Roles & SoD**: AIMS_Admin (process owner); Model_Owner (risk file maintainer); Auditor (independent review).

**Evidence & Telemetry**: Risk register, AIIA, TEVV reports, re‑evaluation minutes.

**Authoritative Mappings**: EU AI Act Arts. 9–15; ISO/IEC 42001 (AIMS PDCA); ISO/IEC 23894 (AI lifecycle risk); NIST AI RMF; NIST SP 800‑53 (RA); NIST SP 800‑171 Rev.3 (PL/SR).

---

## MCC‑02 — Data Governance & Quality (DGQ)
**Purpose**: Assure lawful, high‑quality data for training, evaluation, and inference (RAG).  
**Scope**: Training corpora, evaluation datasets, retrieved content, embeddings.

**Control Statements**:
1. Data must be cataloged, classified, quality‑checked, and documented for representativeness and bias controls (esp. high‑risk).
2. RAG sources must be vetted and tagged; PHI/PII handled per data class.

**Implementation Procedures**: Source vetting → lineage → quality gates → bias checks → retention/purpose limits.

**Roles & SoD**: Data_Curator (curation), AIMS_Admin (standards), Model_Owner (usage approval).

**Evidence & Telemetry**: Data lineage, quality/bias reports, RAG allow‑list.

**Authoritative Mappings**: EU AI Act Art.10; ISO/IEC 42001 (operational data mgmt); ISO/IEC 23894 (data risks); NIST AI RMF (MAP/MEASURE); NIST SP 800‑53 (SC/MP).

---

## MCC‑03 — Logging, Monitoring & Traceability (LMT)
**Purpose**: Provide complete, consistent evidence for security, safety, and compliance.  
**Scope**: Inference, tool calls, promotions, config changes, gateway events.

**Control Statements**:
1. Log **event types** covering inference, model/prompt changes, vector store events, gateway actions, TEVV runs, and incidents; include **record content** for who/what/when/where/outcome plus object IDs & hashes.
2. Review/refresh the event set at least quarterly.

**Implementation Procedures**: Adopt standard AI event schema in SIEM; periodic completeness checks.

**Roles & SoD**: Ops_Custodian & Gateway_Admin (emit); Auditor (validate).

**Evidence & Telemetry**: SIEM dashboards, sampling reports, retention attestations.

**Authoritative Mappings**: EU AI Act Art.12; ISO/IEC 42001 (monitoring); NIST AI RMF (traceability); NIST SP 800‑53 (AU‑2/AU‑3); NIST SP 800‑171 Rev.3 (evidence alignment).

---

## MCC‑04 — Human Oversight & HITL (HO)
**Purpose**: Ensure meaningful human control over consequential AI actions.  
**Scope**: High‑impact decisions (finance, medical, defense, HR, safety).

**Control Statements**:
1. Define **HITL thresholds**; block actions until human review when thresholds are triggered.
2. Capture human decisions and rationale in the audit trail.

**Implementation Procedures**: Configure gateway/workflows to route for approval; maintain approver rosters & SLAs.

**Roles & SoD**: Model_Owner (thresholds), Gateway_Admin (enforcement), Approvers (review), Auditor (oversight).

**Evidence & Telemetry**: HITL logs, approver decisions, exception reports.

**Authoritative Mappings**: EU AI Act Art.14; ISO/IEC 42001 (roles/competence); NIST AI RMF (Govern/Manage); NIST SP 800‑53 (AT/PM).

---

## MCC‑05 — Transparency & User Information (TXP)
**Purpose**: Provide users with appropriate disclosures and explanations.  
**Scope**: Customer‑facing content; employee‑facing tools with material impact.

**Control Statements**:
1. Disclose AI‑generated content where required; attach provenance labels/watermarks via the gateway.
2. For explainability‑required use cases, generate and store explanation references linked to outputs.

**Implementation Procedures**: Gateway stamping; explanation services produce reason codes.

**Roles & SoD**: Gateway_Admin (configure); Model_Owner (explainability scope).

**Evidence & Telemetry**: Headers/watermarks, explanation IDs in logs.

**Authoritative Mappings**: EU AI Act (transparency); US EO 14110 (provenance); ISO/IEC 42001 (communications); NIST AI RMF (transparency).

---

## MCC‑06 — Security, Robustness & TEVV (SRT)
**Purpose**: Validate model/system safety, robustness, and performance before release.  
**Scope**: All prod‑bound models/prompts/vectors and major changes.

**Control Statements**:
1. Perform **TEVV** including red‑team tests (jailbreaks, leakage), bias/toxicity, RAG poisoning, cost‑DoS, and regression benchmarks.
2. For powerful models, conduct pre‑release safety testing per executive guidance where applicable.

**Implementation Procedures**: CI pipeline test battery; store signed reports; establish objective acceptance criteria.

**Roles & SoD**: Model_Owner (criteria), AIMS_Admin (high‑risk approval), Promoter (deploy only when passed).

**Evidence & Telemetry**: TEVV artifacts, red‑team results, sign‑offs.

**Authoritative Mappings**: EU AI Act Art.15; ISO/IEC 42001 (performance); ISO/IEC 23894 (robustness); NIST AI RMF (Measure/Manage); NIST SP 800‑53 (SI/SC).

---

## MCC‑07 — Access Control & RBAC (ARB)
**Purpose**: Enforce least privilege & separation of duties across AI components.  
**Scope**: Artifacts (models/prompts/indexes), gateways, clusters, CI/CD.

**Control Statements**:
1. Apply the canonical RBAC: AIMS_Admin, Model_Owner, Data_Curator, Promoter, Ops_Custodian, Gateway_Admin, Auditor.
2. No single role can alter **logic + content + deployment** end‑to‑end.

**Implementation Procedures**: IAM policy sets; scoped tokens; JIT elevation; short‑lived credentials; quarterly access reviews.

**Roles & SoD**: As above.

**Evidence & Telemetry**: IAM policies, access review records, SoD attestations.

**Authoritative Mappings**: EU AI Act (QMS role separation); ISO/IEC 42001 (leadership); NIST AI RMF (Govern); NIST SP 800‑53 (AC/IA); NIST SP 800‑171 Rev.3 (AC).

---

## MCC‑08 — Configuration Management & CM‑6 for AI CIs (CMC)
**Purpose**: Treat models, prompts, vector indexes, tools, and gateway policies as **configuration items** with hardened baselines.  
**Scope**: All AI behavior‑defining assets.

**Control Statements**:
1. Define baselines; require approvals for changes; monitor for drift; block unknown hashes.
2. Apply least functionality (disable unused tools; no shell/network by default).

**Implementation Procedures**: Baseline catalogs; drift scanners; deny‑by‑default tool scopes; runtime hash/signature validation.

**Roles & SoD**: Model_Owner (logic baseline), Ops_Custodian (infra enforcement), Promoter (non‑interactive deployment).

**Evidence & Telemetry**: Baseline manifests, drift alerts, denied changes.

**Authoritative Mappings**: EU AI Act (conformity/QMS); ISO/IEC 42001 (change mgmt); ISO/IEC 23894 (lifecycle); NIST AI RMF (Manage); NIST SP 800‑53 (CM‑2/3/4/6).

---

## MCC‑09 — Model & Data Provenance / Integrity (MDP)
**Purpose**: Guarantee provenance and integrity of all AI artifacts and data lineages.  
**Scope**: Model weights, tokenizers, prompts, datasets, vector indices, safety filters.

**Control Statements**:
1. Maintain **Model Cards** (purpose, data lineage, evals, risks, rollback).
2. Retain immutable lineage for datasets and RAG sources.

**Implementation Procedures**: Registry stores signed artifacts and lineage; updates are append‑only with versioning.

**Roles & SoD**: Model_Owner (model card), Data_Curator (source lineage).

**Evidence & Telemetry**: Model cards, signed manifests, registry proofs.

**Authoritative Mappings**: EU AI Act (technical docs/records); ISO/IEC 42001 (integrity); ISO/IEC 23894 (lineage); NIST AI RMF (traceability); NIST SP 800‑53 (SC/CM/AU).

---

## MCC‑10 — Signed CI/CD & Artifact Attestation (SCD)
**Purpose**: Prevent tampering; ensure only approved artifacts reach production.  
**Scope**: All production deployments (models, prompts, indexes, filters).

**Control Statements**:
1. CI/CD must **sign** artifacts; production must **verify** signatures/hashes at deploy and runtime; reject unknown keys.
2. Maintain promotion approvals and linkage to risk file/TEVV results.

**Implementation Procedures**: HSM/KMS signing keys; verification keys on inference/gateway; periodic re‑verification; non‑interactive promotion jobs.

**Roles & SoD**: Promoter (machine identity) deploys; Model_Owner (approves); Auditor (evidence review).

**Evidence & Telemetry**: CI logs, signatures, verification logs, promotion records.

**Authoritative Mappings**: EU AI Act (robustness & record‑keeping); ISO/IEC 42001 (auditability); NIST AI RMF (Measure/Manage); NIST SP 800‑53 (CM‑3/4/6, AU‑2/3); NIST SP 800‑171 Rev.3 (supply‑chain).

---

## MCC‑11 — AI Gateway Enforcement (AGE)
**Purpose**: Centralize data controls, model allow‑listing, redaction, and provenance.  
**Scope**: All LLM traffic (internal/external) and tools/plugins.

**Control Statements**:
1. All AI calls traverse the gateway; external endpoints must be allow‑listed; PII/PHI redaction on ingress; provenance on egress.
2. Tool scopes are least‑privileged; unsafe actions blocked by default.

**Implementation Procedures**: mTLS; egress rules; DPI/redaction; provenance headers/watermarks; SIEM integration.

**Roles & SoD**: Gateway_Admin (configure), Ops_Custodian (network paths).

**Evidence & Telemetry**: Gateway policy snapshots; redaction/provenance logs; blocked egress events.

**Authoritative Mappings**: EU AI Act (logging, cybersecurity, transparency); NIST AI RMF; OWASP GenAI (Excessive Agency).

---

## MCC‑12 — RAG & Vector Store Governance (RVG)
**Purpose**: Prevent poisoning and undocumented behavioral drift from retrieval.  
**Scope**: Ingestion pipelines, embeddings, indexes, metadata, filters.

**Control Statements**:
1. Separate **curation** (staging writes) from **promotion** (prod writes via signed CI jobs).
2. Curate sources; require signed ingestion manifests and index parameter baselines with approvals.

**Implementation Procedures**: Staging‑only writes by Data_Curator; Promoter publishes to prod; periodic relevance re‑evaluation.

**Roles & SoD**: Data_Curator, Promoter, Model_Owner.

**Evidence & Telemetry**: Source allow‑lists, ingestion manifests, index promotion logs.

**Authoritative Mappings**: EU AI Act (data governance); ISO/IEC 23894 (data risks); NIST AI RMF (Measure/Manage); NIST SP 800‑53 (CM/AU).

---

## MCC‑13 — Incident Response for AI (IR‑AI)
**Purpose**: Rapidly contain and learn from AI‑specific incidents.  
**Scope**: Prompt injection, data leakage, poisoning, excessive agency, gateway bypass.

**Control Statements**:
1. Maintain AI IR playbooks; define triggers from safety/telemetry; rehearse at least semiannually.
2. Post‑incident reviews update risk files, baselines, and training.

**Implementation Procedures**: SIEM rules; gateway kill‑switch; rollback; update model cards; corrective actions tracking.

**Roles & SoD**: IR Lead (SecOps), Model_Owner, Gateway_Admin, AIMS_Admin.

**Evidence & Telemetry**: IR tickets, timelines, corrective actions, lessons‑learned.

**Authoritative Mappings**: EU AI Act (post‑market monitoring); ISO/IEC 42001 (corrective action); NIST AI RMF (Manage); NIST SP 800‑53 (IR family).

---

## MCC‑14 — Post‑Market Monitoring & Drift (PMD)
**Purpose**: Detect performance/safety drift and manage model lifecycle health.  
**Scope**: All production AI systems.

**Control Statements**:
1. Define drift metrics and alert thresholds in Model Cards; investigate out‑of‑bounds events; update mitigations.
2. For high‑risk systems, maintain a post‑market monitoring plan and periodic reporting.

**Implementation Procedures**: Shadow/canary tests; dashboards; quarterly reviews; issue tracking.

**Roles & SoD**: Model_Owner (monitoring), AIMS_Admin (program review).

**Evidence & Telemetry**: Drift dashboards, periodic reports, remediation tickets.

**Authoritative Mappings**: EU AI Act (Art.61); ISO/IEC 42001 (performance); ISO/IEC 23894 (lifecycle); NIST AI RMF (Manage).

---

## MCC‑15 — Supplier & Third‑Party Governance (STG)
**Purpose**: Control risk from external models, datasets, and tools.  
**Scope**: Foundation models, SaaS LLMs, libraries, datasets, plugins.

**Control Statements**:
1. Require model cards/SBOMs/safety test evidence and license/data terms compliance from third‑party components.
2. For CUI/regulated contexts, apply enhanced supply‑chain requirements.

**Implementation Procedures**: Vendor questionnaire; risk scoring; contractual clauses; periodic re‑assessments.

**Roles & SoD**: Procurement, AIMS_Admin, Security, Legal.

**Evidence & Telemetry**: Diligence packets, contracts, re‑assessment logs.

**Authoritative Mappings**: EU AI Act (supplier/QMS); ISO/IEC 42001 (supplier mgmt); ISO/IEC 23894 (supply chain risks); NIST AI RMF (Govern); NIST SP 800‑53 (SA); NIST SP 800‑171 Rev.3 (SR).

---

## MCC‑16 — Sector Overlays (SEC‑OV)
**Purpose**: Apply additional requirements for Finance, Healthcare, Defense/Gov.  
**Scope**: Any AI use case in those sectors.

**Control Statements**:
1. **Finance**: HITL on credit/fraud decisions; long‑term retention; explainability.
2. **Healthcare**: PHI redaction; vetted clinical sources; clinical oversight.
3. **Defense/Gov**: CUI alignment; no public endpoints for sensitive workloads; signed/attested artifacts.

**Implementation Procedures**: Sector standards; additional TEVV; documentation per regulator; approvals by sector SMEs.

**Roles & SoD**: Sector SMEs, AIMS_Admin.

**Evidence & Telemetry**: Overlay checklists, approvals, compliance reports.

**Authoritative Mappings**: EU AI Act (risk tiering & oversight); ISO/IEC 42001; NIST AI RMF; NIST SP 800‑53/171.

---

## MCC‑17 — Transparency Records & Technical Documentation (TRD)
**Purpose**: Maintain audit‑ready documentation for conformity and certification.  
**Scope**: All high‑risk AI; any system subject to audit.

**Control Statements**:
1. Maintain a **technical file** per system: model cards, TEVV evidence, risk assessments, HITL design, logging schema, promotion history.
2. Keep AIMS artifacts for ISO/IEC 42001 audits (policies, roles, KPIs, internal audits).

**Implementation Procedures**: Documentation portal; version control; internal audits; management review.

**Roles & SoD**: AIMS_Admin (owner); Model_Owner (contributor); Auditor (assurance).

**Evidence & Telemetry**: Technical files, internal audit reports, management review minutes.

**Authoritative Mappings**: EU AI Act (Art.11); ISO/IEC 42001; NIST AI RMF; NIST SP 800‑53 (PM/PL families).

---

## MCC‑18 — Gateway Bypass Prevention & Egress Control (GBE)
**Purpose**: Stop shadow AI traffic and ensure policy application to all LLM calls.  
**Scope**: All networks and compute where AI is used.

**Control Statements**:
1. Force LLM egress via the AI Gateway; block direct calls to unapproved endpoints; enforce mTLS and allow‑lists.
2. Log all bypass attempts and alert IR.

**Implementation Procedures**: Network policies; egress firewall rules; DNS controls; CASB/DLP integration.

**Roles & SoD**: Ops_Custodian, Gateway_Admin, SecOps.

**Evidence & Telemetry**: Firewall/Proxy logs; gateway deny events; IR tickets.

**Authoritative Mappings**: EU AI Act (cybersecurity & logging); NIST SP 800‑53 (AU‑2/3); NIST AI RMF (Manage).

---

## MCC‑19 — Explainability & Output Governance (XOG)
**Purpose**: Ensure outputs are appropriate, reviewable, and—when required—explainable.  
**Scope**: Any decision‑impacting output; customer‑facing content.

**Control Statements**:
1. Validate outputs with safety filters; route to HITL based on risk; attach explanations where mandated.
2. Store hashes/IDs of explanations with outputs for traceability.

**Implementation Procedures**: Safety layer integration; explanation services; linkage in logs.

**Roles & SoD**: Model_Owner (policy), Gateway_Admin (enforcement).

**Evidence & Telemetry**: Output logs with explanation IDs; HITL outcomes.

**Authoritative Mappings**: EU AI Act (transparency & oversight); ISO/IEC 42001; NIST AI RMF.

---

## MCC‑20 — Governance Reviews & Continuous Improvement (GRCI)
**Purpose**: Keep the AIMS effective and aligned with evolving laws/risks.  
**Scope**: Program‑wide.

**Control Statements**:
1. Conduct quarterly governance reviews; track KPIs; action improvements.
2. Update crosswalk mappings when standards or laws revise; update training and controls accordingly.

**Implementation Procedures**: Steering committee; change log; training updates; external horizon scanning.

**Roles & SoD**: AIMS_Admin (chair), with Security, Legal, Compliance, SRE, Data Governance.

**Evidence & Telemetry**: Review minutes; KPI dashboards; training records.

**Authoritative Mappings**: ISO/IEC 42001 (PDCA); NIST AI RMF (Govern); EU AI Act (post‑market monitoring).

---

## Appendix A — Abbreviations
- **AIIA/AIRA** — AI Impact/Risk Assessment
- **AIMS** — AI Management System
- **ARB** — Access Control & RBAC
- **AU** — Audit and Accountability
- **CI/CD** — Continuous Integration/Continuous Delivery
- **CM** — Configuration Management
- **CUI** — Controlled Unclassified Information
- **DGQ** — Data Governance & Quality
- **EO** — Executive Order
- **EU AI Act** — Regulation (EU) 2024/1689
- **HITL** — Human‑in‑the‑Loop
- **KMS/HSM** — Key Management Service / Hardware Security Module
- **LMT** — Logging, Monitoring & Traceability
- **MDP** — Model & Data Provenance
- **MCC** — Master Controls Catalog
- **OWASP GenAI** — OWASP Generative AI Security Project
- **PMD** — Post‑Market Monitoring & Drift
- **RAG** — Retrieval‑Augmented Generation
- **RBAC** — Role‑Based Access Control
- **RVG** — RAG & Vector Store Governance
- **SCD** — Signed CI/CD & Attestation
- **SRT** — Security, Robustness & TEVV
- **TEVV** — Testing, Evaluation, Verification & Validation
- **TRD** — Transparency Records & Technical Documentation
- **TXP** — Transparency & User Information

---

## Appendix B — Notes on Evidence Patterns
For each control, maintain a folder or wiki page containing:
- Control owner and SMEs
- Related procedures and configuration references
- Log sampling queries (SIEM)
- Screenshots/dashboards (where relevant)
- Last audit date and findings
- Open action items and target dates

