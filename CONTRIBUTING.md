# Contributing to the AI Governance & Compliance Standards Repository

Thank you for contributing to our AI Governance & Compliance Framework.  
This repository is subject to **strict configuration governance**, including CM‑6‑aligned controls, RBAC/SoD approvals, TEVV requirements, artifact signing, and continuous audit readiness per AU‑2/AU‑3.

Please follow this guide when submitting changes.

---

# 1. Scope of Contributions

This repository contains governed artifacts related to:

- AI-BOM (AI Bill of Materials)
- Models, prompts/agents, datasets, tools, vector indexes
- SOPs, MCC controls, evidence templates
- PR‑bot automation and CI/CD governance
- Schema definitions and compliance mappings

**All AI-related artifacts are configuration items**  
and must follow the rules in this document.

---

# 2. Branching & Naming Requirements

All contributions must use the following structure:

### Branch name format

Examples:
ai-bom/model/claims-qa/2.1.0
ai-bom/prompt/claims-assistant/4.0.0
ai-bom/vector/policies-kb/2026-03-17

---

# 3. PR Title & Description Requirements

### Required PR title format

Examples:
[AI-BOM] model:claims-qa@2.1.0 – updated training lineage
[AI-BOM] prompt:claims-assistant@4.0.0 – jailbreak regression improvements

###  Required PR body fields

Your PR description **must include**:

- AI‑BOM `id` and `version`
- Link(s) to:
  - TEVV results
  - SBOM (if applicable)
  - Signature/attestation references
  - Risk assessment document
  - Associated evidence files
- Summary of changes
- Impact assessment (breaking, minor, or documentation-only)
- List of MCC controls touched (if any)

---

# 4. Approvals & Separation of Duties (SoD)

All AI‑BOM contributions must be approved by:

-  **Model_Owner** (content authority)
-  **AIMS_Admin** (governance authority)

###  Authors cannot approve their own PRs  
This maintains **Separation of Duties** required by CM‑6, AC/IA, and 42001.

---

# 5. Required Files for AI‑BOM Changes

Each new or modified AI‑BOM entry **must include** a file:


<type>/<name>/<version>/ai-bom.json</version></name></type>

This file **must**:

- Conform to the schema in `AI-BOM/schema/ai-bom.schema.json`
- Include valid signatures and hashes
- Reference TEVV artifacts
- Include provenance and lineage metadata
- Contain a risk classification + controls applied mapping
- Include SBOM + CVE scans for tools or binaries

---

# 6. Schema Validation (CI/CD)

All PRs modifying AI‑BOM content trigger:

JSON Schema validation  
Required field checks  
Signature & hash verification  
Evidence presence checks  
Risk classification constraints  
Governance approvals (Model_Owner + AIMS_Admin)  
SoD restriction enforcement  
TEVV pass/fail gating  

A PR **will be blocked** if any validation fails.

---

# 7. TEVV Requirements

Any change that affects:

- Models  
- Prompts/agents  
- Tools/plugins  
- Vector stores  
- Datasets used for training or evaluation  

must include **updated TEVV results**, including:

- Functional regression tests  
- Adversarial & robustness tests  
- Fairness/bias evaluations (if applicable)  
- Retrieval/precision regression (for RAG/vector stores)

**No TEVV = No Merge.**

---

# 8. Artifact Signing & Attestation

All governed items must be signed using:

- **cosign** (preferred)  
- Or enterprise-approved equivalent signing pipeline

Required in AI‑BOM:

- `signing_key`
- `integrity_hash`
- `signatures[]`
- SBOM reference (for binaries/tools)
- CVE scan results (for binaries/tools)

Unsigned artifacts will automatically block the PR.

---

# 9. Evidence & Audit Requirements

Contributors must ensure:

- All required evidence artifacts exist
- Links resolve correctly (artifact URLs, internal paths)
- Logs include the correct `ai_bom.id` and `version`
- Change tickets or CM‑6 baselines are referenced

This enables full AU‑2/AU‑3 traceability.

---

# 10. Versioning Rules

**You may not modify an existing version.**

For any change, you must:

Create a new version folder  
Update the AI‑BOM entry with a new version number  
Perform full TEVV  
Re-sign artifacts

Old versions remain immutable for audit history.

---

# 11. Documentation Changes (Non‑AI-BOM)

Updates to:

- SOPs
- MCC controls
- Evidence templates
- Policy documents
- Architecture diagrams

should use branches like:
docs/<area>/<description></description>

And PR titles like:
[Docs] Updated TEVV guidance for dataset lineage

---

# 12. Contact & Support

For questions or approval routing:

- **AIMS Admin Team:** aims-admin@example.com  
- **Model Owners Group:** model-owners@example.com  
- **Security/Compliance:** security-gov@example.com  
- **Repository Maintainers:** repo-maintainers@example.com  

---

# 13. Summary Checklist (Copy Into PR)
AI-BOM file added/updated
Schema validation passed
TEVV results attached
Artifacts signed
SBOM/CVE scan (if applicable)
Risk classification updated
Lineage & provenance documented
Required approvals added (Model_Owner + AIMS_Admin)
SoD maintained
Evidence links validated


Thank you for helping maintain a secure, transparent, and fully compliant AI governance ecosystem.
