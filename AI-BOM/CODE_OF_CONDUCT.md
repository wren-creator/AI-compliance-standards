# Code of Conduct
AI Governance & Compliance Framework Repository

This project is governed by strict security, compliance, and auditability requirements.
All contributors are expected to uphold the highest standards of integrity, transparency,
and accountability when working with AI-related configuration items.

This Code of Conduct applies to:
- Repository contributors
- Reviewers and maintainers
- Automated systems (PR bots, CI/CD pipelines)
- Internal or external stakeholders interacting with the repo

---

# 1. Core Principles

## ✅ 1.1 Integrity & Transparency
Contributors must:
- Provide accurate, complete information in all AI-BOM entries.
- Ensure provenance, lineage, และ evidence reflect the true state of artifacts.
- Never falsify TEVV results, risk assessments, signatures, or audit records.

## ✅ 1.2 Security by Design
Contributors must:
- Follow CM‑6 configuration management requirements.
- Treat models, prompts, datasets, tools, and vector indexes as governed config items.
- Use approved signing keys and CI/CD pipelines.
- Protect sensitive or confidential data.

## ✅ 1.3 Compliance Alignment
Work must align with:
- EU AI Act (2024/1689)
- ISO/IEC 42001:2023
- ISO/IEC 23894:2023
- NIST AI RMF
- NIST SP 800‑53 & 800‑171
- Sector-specific overlays (finance, healthcare, defense)

## ✅ 1.4 Separation of Duties (SoD)
- Authors cannot approve their own changes.
- Governance roles (Model_Owner, AIMS_Admin) cannot be bypassed.
- CI/CD must validate signatures, TEVV results, and schema compliance.

---

# 2. Expected Behavior

Contributors are expected to:
- Follow required branching, versioning, and PR formats.
- Provide complete lineage, provenance, and risk classification.
- Include TEVV results for changes affecting AI systems.
- Respond respectfully to review comments and governance requests.
- Collaborate constructively with the wider governance community.

---

# 3. Unacceptable Behavior

The following are explicitly prohibited:
- Modifying artifacts without updating their version.
- Circumventing governance controls or PR bot enforcement.
- Providing incomplete or misleading metadata.
- Uploading unsigned, unscanned, or untested artifacts.
- Attempting to approve PRs where SoD would be violated.
- Removing required evidence or suppressing TEVV findings.
- Submitting code or data that violates legal or licensing restrictions.

---

# 4. Reporting Violations

To report a violation, contact:
- **AIMS Governance Team:** aims-governance@example.com  
- **Security/Compliance:** sec-ops@example.com  

Reports will be handled confidentially and in accordance with internal compliance procedures.

---

# 5. Enforcement

Violations may result in:
- PR rejections or required remediation
- Removal of contributor/maintainer permissions
- Audit escalation to Compliance or Security teams
- Temporary or permanent contribution bans
- Internal incident reports (if applicable)

All enforcement actions follow SoD and governance protocols.

---

# 6. Acknowledgment

By contributing to this repository, you acknowledge that you:
- Understand the compliance obligations governing AI artifacts
- Agree to follow all governance requirements described here
- Accept the enforcement mechanisms that ensure audit integrity

Thank you for supporting a secure, transparent, and compliant AI governance ecosystem.
