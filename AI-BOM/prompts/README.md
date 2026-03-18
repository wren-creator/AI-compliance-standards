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
