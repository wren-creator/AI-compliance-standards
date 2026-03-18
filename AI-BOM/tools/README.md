
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
```

## Authoring Checklist

- [ ] **API scopes and egress rules documented**
- [ ] **SBOM and CVE scans linked**
- [ ] **Fault / adversarial tests attached**
- [ ] **RBAC / Segregation of Duties (SoD) enforced through approvals**
