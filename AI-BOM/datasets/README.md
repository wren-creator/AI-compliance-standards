
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
```
##Dataset Authoring Checklist

- [ ] **Lineage and collection method documented**  
  - Include source systems, collection tools, and acquisition workflow.

- [ ] **Consent / license / usage constraints recorded**  
  - Note license type, redistribution rules, consent forms, and any usage restrictions.

- [ ] **Data quality (DQ) and bias checks attached**  
  - Provide results of validation, completeness checks, representational bias review, and known limitations.

- [ ] **Sensitive data handling & redaction documented**  
  - Describe masking, tokenization, PII handling, and secure storage requirements.
