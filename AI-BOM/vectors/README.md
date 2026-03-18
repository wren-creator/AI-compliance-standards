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
