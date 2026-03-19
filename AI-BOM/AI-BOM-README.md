# AI‑BOM (AI Bill of Materials)

**Purpose:** The AI‑BOM is the *single authoritative inventory* of configuration items in AI systems—**models**, **prompts/agents**, **datasets**, **vector indexes**, and **tools/plugins**—managed under CM‑6‑style configuration governance. It powers provenance, approvals, TEVV gating, artifact signing/attestation, and AU‑2/AU‑3 logging.

This directory contains:
- A **schema** for AI‑BOM entries
- Per‑type folders and **versioned instances** (one `ai-bom.json` per item version)
- PR‑bot enforcement (schema validation, TEVV, signatures, approvals)
- Evidence linkage and audit‑ready metadata (Annex IV, ISO/IEC 42001, ISO/IEC 23894, NIST AI RMF, 800‑53/171)

> **Scope:** Treat models, prompts, vector DBs, datasets, tools, and gateway configs as **configuration items** requiring **change control**, **attestation**, and **traceability**.

---

## Folder Layout

AI-BOM/<br>
├── README.md<br>
├── schema/<br>
│ &nbsp;&nbsp;  └── ai-bom.schema.json<br>
├── models/<br>
│ &nbsp;&nbsp; └── <model_name>/<version>/ai-bom.json<br>
├── prompts/<br>
│ &nbsp;&nbsp;  └── <prompt_name>/<version>/ai-bom.json<br>
├── datasets/<br>
│ &nbsp;&nbsp;  └── <dataset_name>/<version>/ai-bom.json<br>
├── vectors/<br>
│ &nbsp;&nbsp;  └── <store_name>/<index_id>/ai-bom.json<br>
└── tools/<br>
 &nbsp;&nbsp;   └── <tool_name>/<version>/ai-bom.json<br>

- **Versioning:** Each version gets its own folder (immutable once released).
- **IDs in Logs:** AI‑BOM `id` and `version` must appear in AU‑2/AU‑3 logs for all inference, training, indexing, and gateway enforcement events.

---

## Governance & RBAC

- **Required Approvals:** `Model_Owner` **and** `AIMS_Admin` must approve changes to AI‑BOM entries.
- **Separation of Duties:** Creators cannot approve their own submissions (SoD enforced via PR rules).
- **Signing:** All artifacts referenced must have **cryptographic signatures** and **attestation** captured in AI‑BOM.
- **TEVV:** Link TEVV results per version. PR merges are blocked without passing TEVV.

---

## Compliance Alignment

- **EU AI Act (2024/1689) – Annex IV**: Technical documentation, training data provenance, version history, risk controls.
- **ISO/IEC 42001 (AIMS)**: Documented AI asset inventory, roles, approvals, monitoring.
- **ISO/IEC 23894**: Risk management artifacts and controls applied.
- **NIST AI RMF** (Govern/Map/Measure/Manage): Transparency, measurement, and continuous monitoring evidence.
- **NIST SP 800‑53 (CM‑6, AU‑2, AU‑3, AC/IA, SI/SC)**: Baselines, logging, access control, security/robustness.
- **NIST SP 800‑171 Rev. 3** (CUI): Config baselines and traceability for systems processing CUI.

---

## PR Bot Enforcement (Overview)

PRs that touch `AI-BOM/**` must:
1. Include a valid `ai-bom.json` conforming to `schema/ai-bom.schema.json`.
2. Reference **TEVV results** (URLs or artifact paths) and pass status checks.
3. Include **signed artifacts** (sig/attestation metadata).
4. Obtain approvals from **Model_Owner** and **AIMS_Admin**.
5. Include an **SBOM link** for any executable/library components referenced.

> See: `.github/workflows/ai-bom-validation.yml` and repo policy docs.

---

## Authoring Workflow

1. **Create a new versioned directory** under the correct type (e.g., `models/my-model/1.2.0/`).
2. **Add `ai-bom.json`** using the type‑specific README template.
3. **Attach evidence** links: TEVV reports, risk assessments, SBOMs, signatures, lineage docs.
4. **Update CHANGELOG** (if applicable) and include the AI‑BOM `id` in PR title.
5. **Open PR**; the bot validates schema, signatures, TEVV, and approvals.
6. **Merge only after all checks pass** and SoD approvals are complete.

---

## Commit & PR Conventions

- **Branch name:** `ai-bom/<type>/<name>/<version>`
- **PR title:** `[AI-BOM] <type>:<name>@<version> – short change summary`
- **PR body:** Must include:
  - AI‑BOM `id` and `version`
  - Links to TEVV, SBOM, signatures
  - Risk classification and applied controls list
  - Any sector overlays (finance/healthcare/defense)

---

## Logging & SIEM

All runtime events **must include**:
- `ai_bom.id`, `ai_bom.type`, `ai_bom.version`
- `model_id`, `prompt_id`, `vector_index_id`, etc., as applicable
- `commit_sha`, `signature_ref`, `gateway_policy_id`

This enables AU‑2/AU‑3 queries for inference events, prompt/agent changes, model promotions, drift alerts, gateway redactions, and vector indexing.

---

## See Also

- `models/README.md` – Model AI‑BOM template & examples
- `prompts/README.md` – Prompt/Agent AI‑BOM template & examples
- `datasets/README.md` – Dataset AI‑BOM template & examples
- `vectors/README.md` – Vector Index AI‑BOM template & examples
- `tools/README.md` – Tool/Plugin AI‑BOM template & examples
- `schema/ai-bom.schema.json` – Master schema used by PR bot


![Open Source](https://badgen.net/badge/open/source/)
