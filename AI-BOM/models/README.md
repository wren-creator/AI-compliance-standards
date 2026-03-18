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
```
## Authoring Checklist

- [ ] **Version folder created:** `models/<name>/<version>/`
- [ ] **Hashes recorded match immutable artifact**
- [ ] **TEVV report attached and passing gates**
- [ ] **SBOM and CVE scan references included**
- [ ] **Risk classification aligns with sector overlays**
- [ ] **Model_Owner + AIMS_Admin approvals required**

---

## Evidence & Logging Requirements

- Include **AI‑BOM ID and version** in all:
  - training logs  
  - promotion logs  
  - deployment logs  
  - inference logs  
- Link all **promotion tickets** and **change requests (CM‑6)**.
