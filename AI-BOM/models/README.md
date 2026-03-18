# AI‑BOM for Models

This folder tracks **base**, **fine‑tuned**, **distilled/quantized**, and **embedding** models as controlled configuration items.

Each version lives at:
models/<model_name>/<version>/ai-bom.json</version>

## Required Fields (Model)

- `id` – globally unique stable ID (e.g., `model:my-model:1.2.0`)
- `type` – `"model"`
- `name` / `version`
- `owner.model_owner` and `owner.aims_admin`
- `provenance` – source, hash, upstream model, license, training data lineage
- `security` – signing key, integrity hash, SBOM reference, CVE results
- `risk` – classification (incl. sector overlays), assessment, controls applied (from MCC)
- `tevv` – last_run, results_url, fairness/robustness/adversarial/regression references
- `signatures[]` – signer, signature, timestamp

## Example `ai-bom.json`

```json
{
  "id": "model:claims-qa:2.1.0",
  "type": "model",
  "name": "claims-qa",
  "version": "2.1.0",
  "owner": {
    "model_owner": "j.smith",
    "aims_admin": "a.khan"
  },
  "provenance": {
    "source": "internal-finetune",
    "hash": "sha256:...model.bin",
    "download_url": "artifact://models/claims-qa/2.1.0/model.bin",
    "license": "Enterprise-internal",
    "upstream_model": "meta/llama-3.1-8b",
    "training_data_lineage": [
      "dataset:claims-labeled:2026-02",
      "dataset:synth-augment:2026-02A"
    ]
  },
  "tevv": {
    "last_run": "2026-03-15T18:22:00Z",
    "results_url": "artifact://tevv/claims-qa/2.1.0/report.html",
    "fairness_eval": "artifact://tevv/claims-qa/2.1.0/fairness.json",
    "robustness_eval": "artifact://tevv/claims-qa/2.1.0/robustness.json",
    "adversarial_eval": "artifact://tevv/claims-qa/2.1.0/redteam.pdf",
    "regression_suite": "artifact://tevv/claims-qa/2.1.0/regression.xml"
  },
  "security": {
    "signing_key": "cosign://keys/models",
    "integrity_hash": "sha256:...model.bin",
    "sbom_reference": "artifact://sbom/claims-qa/2.1.0/sbom.json",
    "cve_scan_results": "artifact://vuln/claims-qa/2.1.0/cve.json"
  },
  "risk": {
    "risk_classification": "High — healthcare overlay",
    "risk_assessment": "artifact://risk/claims-qa/2.1.0/assessment.md",
    "controls_applied": [
      "MCC-01 AI Risk Lifecycle",
      "MCC-06 TEVV",
      "MCC-10 Signed CI/CD",
      "MCC-15 Sector Overlay (Healthcare)"
    ]
  },
  "signatures": [
    {
      "signer": "sigstore/cosign",
      "signature": "MEUCIQD...==",
      "timestamp": "2026-03-15T18:25:10Z"
    }
  ]
}

Authoring Checklist

 Version folder created: models/<name>/<version>/
 Hashes recorded match immutable artifact
 TEVV report attached and passing gates
 SBOM and CVE scan references included
 Risk classification aligns with sector overlays
 Model_Owner + AIMS_Admin approvals required

Evidence & Logging

Include AI‑BOM id and version in all training, promotion, deployment, and inference logs.
Link promotion tickets and change requests (CM‑6).

---

## `AI-BOM/prompts/README.md`

```markdown
# AI‑BOM for Prompts & Agents

Tracks **system prompts**, **agent graphs/workflows**, and **tool bindings** as governed configuration items.

Each version lives at:
prompts/<prompt_or_agent_name>/<version>/ai-bom.json</version>

## Required Fields (Prompt/Agent)

- `type` = `"prompt"`
- Include `tool definitions` or link to tool configs if external
- Record **guardrails**, **safety configs**, and **gateway policy IDs** in `provenance` or `security` as applicable
- TEVV should include **prompt regression**, **instruction‑following**, **refusal‑behavior**, and **jailbreak resistance**

## Example `ai-bom.json`

```json
{
  "id": "prompt:claims-assistant:4.0.0",
  "type": "prompt",
  "name": "claims-assistant",
  "version": "4.0.0",
  "owner": {
    "model_owner": "j.smith",
    "aims_admin": "a.khan"
  },
  "provenance": {
    "source": "internal",
    "hash": "sha256:...prompt.md",
    "download_url": "git://prompts/claims-assistant/4.0.0/prompt.md",
    "license": "Enterprise-internal",
    "training_data_lineage": []
  },
  "tevv": {
    "last_run": "2026-03-14T10:00:00Z",
    "results_url": "artifact://tevv/prompts/claims-assistant/4.0.0/report.html",
    "fairness_eval": "artifact://tevv/.../fairness.json",
    "robustness_eval": "artifact://tevv/.../robustness.json",
    "adversarial_eval": "artifact://tevv/.../jailbreak.pdf",
    "regression_suite": "artifact://tevv/.../prompt-regression.xml"
  },
  "security": {
    "signing_key": "cosign://keys/prompts",
    "integrity_hash": "sha256:...prompt.md",
    "sbom_reference": null,
    "cve_scan_results": null
  },
  "risk": {
    "risk_classification": "Moderate — healthcare overlay",
    "risk_assessment": "artifact://risk/prompts/claims-assistant/4.0.0/assessment.md",
    "controls_applied": [
      "MCC-04 HITL Oversight",
      "MCC-11 AI Gateway Enforcement",
      "MCC-20 Output Governance"
    ]
  },
  "signatures": [
    {
      "signer": "sigstore/cosign",
      "signature": "MEQCICD...==",
      "timestamp": "2026-03-14T10:05:11Z"
    }
  ]
}

Authoring Checklist

 Include guardrails and gateway policy references
 Provide prompt regression and adversarial/jailbreak results
 Update agent graph/tool bindings if changed and cross‑reference in Tools AI‑BOM
 Approvals & signatures captured

Logging

Inference and content moderation logs must include ai_bom.id, prompt version, gateway policy id, and redaction decisions.

---

## `AI-BOM/datasets/README.md`

```markdown
# AI‑BOM for Datasets

Tracks **training**, **fine‑tune**, **evaluation**, and **synthetic** datasets as configuration items with full lineage.

Each version lives at:
datasets/<dataset_name>/<version>/ai-bom.json</version>
## Required Fields (Dataset)

- `type` = `"dataset"`
- Provenance must capture **source systems**, **collection method**, **transform pipelines**, and **consents/licenses**
- Link to **data quality** metrics and **bias analysis** in TEVV or risk
- If PII/PHI, link to **de‑identification** proof and **gateway redaction** rules

## Example `ai-bom.json`

```json
{
  "id": "dataset:claims-labeled:2026-02",
  "type": "dataset",
  "name": "claims-labeled",
  "version": "2026-02",
  "owner": {
    "model_owner": "data.steward",
    "aims_admin": "a.khan"
  },
  "provenance": {
    "source": "EDW export + manual labeling",
    "hash": "sha256:...claims.parquet",
    "download_url": "artifact://datasets/claims-labeled/2026-02/claims.parquet",
    "license": "Enterprise-internal",
    "training_data_lineage": [
      "system:EDW:v14.3",
      "process:labeling:task-9871"
    ]
  },
  "tevv": {
    "last_run": "2026-03-10T09:00:00Z",
    "results_url": "artifact://dq/claims-labeled/2026-02/summary.html",
    "fairness_eval": "artifact://eval/claims-labeled/2026-02/fairness.json",
    "robustness_eval": null,
    "adversarial_eval": null,
    "regression_suite": "artifact://dq/claims-labeled/2026-02/regression.xml"
  },
  "security": {
    "signing_key": "cosign://keys/datasets",
    "integrity_hash": "sha256:...claims.parquet",
    "sbom_reference": null,
    "cve_scan_results": null
  },
  "risk": {
    "risk_classification": "High — contains sensitive health data",
    "risk_assessment": "artifact://risk/datasets/claims-labeled/2026-02/assessment.md",
    "controls_applied": [
      "MCC-02 Data Governance & Quality",
      "MCC-11 AI Gateway Enforcement (PHI redaction)",
      "MCC-13 Incident Response for AI"
    ]
  },
  "signatures": [
    {
      "signer": "sigstore/cosign",
      "signature": "MEUCIE...==",
      "timestamp": "2026-03-10T09:10:11Z"
    }
  ]
}

Authoring Checklist

 Lineage and collection method documented
 Consent/license/usage constraints recorded
 DQ and bias checks attached
 Sensitive data handling & redaction documented

---

## `AI-BOM/vectors/README.md`

```markdown
# AI‑BOM for Vector Indexes

Tracks **vector stores** and **indexes** (per corpus) including build pipelines, chunking, embeddings, and filters.

Each index lives at:
vectors/<store_name>/<index_id>/ai-bom.json

## Required Fields (Vector Index)

- `type` = `"vector_index"`
- Record **embedding model** + version, **chunking params**, **filters**, **index build job hash**
- Include **indexing events** in AU‑2/AU‑3 logs with AI‑BOM IDs

## Example `ai-bom.json`

```json
{
  "id": "vector_index:policies-kb:2026-03-17",
  "type": "vector_index",
  "name": "policies-kb",
  "version": "2026-03-17",
  "owner": {
    "model_owner": "kb.owner",
    "aims_admin": "a.khan"
  },
  "provenance": {
    "source": "SharePoint: /Policies/",
    "hash": "sha256:...index.faiss",
    "download_url": "artifact://vectors/policies-kb/2026-03-17/index.faiss",
    "license": "Enterprise-internal",
    "upstream_model": "text-embedding-3-large@1.0.5",
    "training_data_lineage": [
      "crawler:sp-collector@2.4",
      "parser:pdf-sanitizer@1.1"
    ]
  },
  "tevv": {
    "last_run": "2026-03-17T22:00:00Z",
    "results_url": "artifact://tevv/vectors/policies-kb/2026-03-17/report.html",
    "fairness_eval": null,
    "robustness_eval": "artifact://tevv/.../poisoning-scan.json",
    "adversarial_eval": "artifact://tevv/.../prompt-injection-tests.json",
    "regression_suite": "artifact://tevv/.../retrieval-regression.xml"
  },
  "security": {
    "signing_key": "cosign://keys/vectors",
    "integrity_hash": "sha256:...index.faiss",
    "sbom_reference": "artifact://sbom/vector-tools/1.3.0/sbom.json",
    "cve_scan_results": "artifact://vuln/vector-tools/1.3.0/cve.json"
  },
  "risk": {
    "risk_classification": "Moderate",
    "risk_assessment": "artifact://risk/vectors/policies-kb/2026-03-17/assessment.md",
    "controls_applied": [
      "MCC-12 RAG/Vector Store Governance",
      "MCC-18 Egress Control"
    ]
  },
  "signatures": [
    {
      "signer": "sigstore/cosign",
      "signature": "MEQCIH...==",
      "timestamp": "2026-03-17T22:05:00Z"
    }
  ]
}

Authoring Checklist

 Embedding model + version documented
 Chunking and filtering parameters captured
 Poisoning and prompt‑injection tests attached
 Index build job hash and artifacts recorded

---

## `AI-BOM/tools/README.md`

```markdown
# AI‑BOM for Tools & Plugins

Tracks **retrieval tools**, **action agents**, **plugins**, and **API adapters** that the AI system can invoke.

Each version lives at:
tools/<tool_name>/<version>/ai-bom.json</version>

## Required Fields (Tool)

- `type` = `"tool"`
- Capture **API endpoints**, **auth scopes**, **rate limits**, and **egress controls**
- Link to **SBOM** and **CVE scans** for any binaries or containers
- Include **allow‑list** entries or gateway **policy IDs**

## Example `ai-bom.json`

```json
{
  "id": "tool:claims-api-adapter:3.2.1",
  "type": "tool",
  "name": "claims-api-adapter",
  "version": "3.2.1",
  "owner": {
    "model_owner": "platform.tools",
    "aims_admin": "a.khan"
  },
  "provenance": {
    "source": "internal",
    "hash": "sha256:...adapter.tar.gz",
    "download_url": "artifact://tools/claims-api-adapter/3.2.1/adapter.tar.gz",
    "license": "Enterprise-internal",
    "training_data_lineage": []
  },
  "tevv": {
    "last_run": "2026-03-12T14:00:00Z",
    "results_url": "artifact://tevv/tools/claims-api-adapter/3.2.1/report.html",
    "fairness_eval": null,
    "robustness_eval": "artifact://tevv/.../fault-injection.json",
    "adversarial_eval": "artifact://tevv/.../abuse-cases.pdf",
    "regression_suite": "artifact://tevv/.../integration.xml"
  },
  "security": {
    "signing_key": "cosign://keys/tools",
    "integrity_hash": "sha256:...adapter.tar.gz",
    "sbom_reference": "artifact://sbom/claims-api-adapter/3.2.1/sbom.json",
    "cve_scan_results": "artifact://vuln/claims-api-adapter/3.2.1/cve.json"
  },
  "risk": {
    "risk_classification": "Moderate — egress-sensitive",
    "risk_assessment": "artifact://risk/tools/claims-api-adapter/3.2.1/assessment.md",
    "controls_applied": [
      "MCC-11 AI Gateway Enforcement",
      "MCC-18 Egress Control",
      "MCC-08 RBAC & SoD"
    ]
  },
  "signatures": [
    {
      "signer": "sigstore/cosign",
      "signature": "MEQCID...==",
      "timestamp": "2026-03-12T14:05:13Z"
    }
  ]
}

Authoring Checklist

 API scopes and egress rules documented
 SBOM and CVE scans linked
 Fault/adversarial tests attached
 RBAC/SoD enforced through approvals

---

### Optional: Add a short `CONTRIBUTING.md` (repo root or `AI-BOM/CONTRIBUTING.md`)

```markdown
# Contributing to AI‑BOM

1. Use the per‑type README templates to create `ai-bom.json`.
2. Keep artifacts immutable; update **version** for changes.
3. Ensure PR includes:
   - Schema‑valid AI‑BOM file(s)
   - TEVV results, SBOMs, signatures
   - Risk classification & controls applied
   - Required approvals (Model_Owner + AIMS_Admin)
4. Do not commit secrets or private keys; use references to secure stores.

