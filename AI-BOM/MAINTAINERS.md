# MAINTAINERS.md
AI Governance & Compliance Framework

This document defines the roles, responsibilities, and governance boundaries
for maintainers of this repository.

All maintainers must follow:
- CM‑6 configuration governance
- RBAC & SoD requirements
- EU AI Act Annex IV documentation standards
- ISO/IEC 42001 AIMS controls
- NIST AI RMF Govern functions
- AU‑2 / AU‑3 logging alignment

---

# 1. Maintainer Roles

## ✅ 1.1 AIMS_Admin (Governance Authority)
**Responsibilities:**
- Approves PRs involving regulated AI assets.
- Ensures compliance with MCC controls and sector overlays.
- Reviews AI‑BOM entries for correctness, completeness, and alignment.
- Confirms TEVV, SBOM, and attestation metadata.
- Enforces SoD and governance policy adherence.

**Cannot:**
- Approve PRs they authored.
- Override failed TEVV, signature, or schema checks.

---

## ✅ 1.2 Model_Owner (Content Authority)
**Responsibilities:**
- Validates correctness of models, prompts, datasets, tools, or vector indexes.
- Ensures lineage, provenance, and versioning accuracy.
- Confirms domain-specific risk classification.
- Attests accuracy of evidence and validation results.

**Cannot:**
- Approve changes to unrelated AI assets.
- Approve PRs without complete evidence attached.

---

## ✅ 1.3 Security_Maintainer (Security Oversight)
**Responsibilities:**
- Verifies SBOM references and CVE scans.
- Confirms signature and artifact integrity.
- Ensures secure handling of sensitive data or credentials.
- Reviews logs for AU‑2/AU‑3 coverage and tamper-evidence.

---

## ✅ 1.4 Repository_Maintainer (Operational Support)
**Responsibilities:**
- Reviews documentation, folder structure, templates, and schemas.
- Ensures CI/CD pipeline stability.
- Maintains PR‑bot validation workflows.
- Supports contributors in following contributing rules.

---

# 2. Approval Rules (Strict SoD)

| Change Type | Required Approvers | Notes |
|-------------|-------------------|-------|
| AI-BOM entries (any type) | Model_Owner + AIMS_Admin | SoD enforced |
| Model changes | Model_Owner + AIMS_Admin + Security_Maintainer | TEVV required |
| Dataset changes | Model_Owner + AIMS_Admin | Lineage required |
| Prompt/Agent updates | Model_Owner + AIMS_Admin | Jailbreak tests required |
| Tools/Plugins | Model_Owner + Security_Maintainer | SBOM/CVE required |
| Vector indexes | Model_Owner + AIMS_Admin | Retrieval TEVV required |
| Policy/SOP/MCC updates | AIMS_Admin | Governance impact review |
| CI/CD & PR-bot updates | Repository_Maintainer + AIMS_Admin | No bypass allowed |

---

# 3. Maintainer Permissions

### ✅ Maintainers *may*:
- Trigger CI/CD & validation workflows
- Merge PRs only after all automated and human checks pass
- Request additional evidence or TEVV reruns
- Flag risky changes for security/audit review

### ❌ Maintainers *may NOT*:
- Merge failing PRs
- Approve their own work
- Bypass signature, TEVV, or schema validation
- Modify historical versions (immutable)

---

# 4. Maintainer Onboarding

New maintainers must:
1. Complete AI governance training (AIMS).
2. Review the MCC + SOPs.
3. Shadow an existing maintainer for 2 PR cycles.
4. Demonstrate ability to verify AI‑BOM compliance.
5. Be approved by:
   - AIMS_Admin
   - Security_Maintainer (if applicable)
   - Repository_Maintainer

---

# 5. Maintainer Offboarding

Maintainer access must be revoked when:
- They change roles
- They violate compliance rules
- They no longer require access
- Directed by compliance/security teams

All access changes must be auditable per AU‑2/AU‑3.

---

# 6. Contact

- **AIMS Admin Team:** aims-admin@example.com  
- **Security Team:** sec-ops@example.com  
- **Model Owners Group:** model-owners@example.com  
- **Repository Maintainers:** repo-maintainers@example.com  

---

Maintainers uphold the security, transparency, and auditability foundations
of the organization’s AI governance program.
