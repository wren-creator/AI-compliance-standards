**AI‑BOM Guidance Document**<br><br>
*1. Purpose of This Document*<br><br>
The AI‑BOM provides a unified, auditable inventory of all AI system components, ensuring full traceability, provenance verification, and governance enforcement across your AI pipeline. It is the AI‑equivalent of an SBOM and is required for compliance with global AI governance standards including:

EU AI Act Annex IV: technical documentation, provenance, model lineage<br>
ISO/IEC 42001 (AIMS): model documentation + governance integration<br>
ISO/IEC 23894: AI risk management evidence<br>
NIST AI RMF: transparency + continuous monitoring<br>
NIST SP 800‑53 (CM‑6): configuration governance<br>
NIST SP 800‑171 (3.4.x): configuration baselines for controlled environments<br>

Your current architecture (signed artifacts, model registry, gateway policy, CI/CD enforcement, provenance hashing) already treats AI as configuration. Therefore, the AI‑BOM becomes the single authoritative compliance artifact for every AI component in your ecosystem.

*2. Scope of an AI‑BOM*<br><br>
An AI‑BOM covers all configuration items used in AI development, training, deployment, and evaluation.<br><br>
*2.1 Models*<br>

Base models (open‑source, licensed, internal)<br>
Fine‑tuned models (supervised, RLHF, domain‑specific)<br>
Distilled / quantized / pruned variants<br>
Embedding models<br>
Versioned TEVV results<br>
Cryptographic signatures and integrity hashes<br>

*2.2 Prompts & Agent Systems*<br>

System prompts
Skill/tool definitions<br>
Multi‑agent graphs, planners, and workflows<br>
Guardrails and policy‑enforced prompt structures<br>

*2.3 Data Assets*<br>

Training datasets (raw, curated, filtered)<br>
Synthetic data pipelines (generation processes + parameters)<br>
Vector stores (index metadata, embedding model, hash)<br>
Data lineage references and transformations<br>

*2.4 Tools / Plugins*<br>

Retrieval tools<br>
Action agents<br>
Internal/external APIs<br>
MCP servers<br>

*2.5 Runtime Controls & Gateway Configuration*<br>

Redaction rules<br>
Allow‑lists / deny‑lists<br>
Safety guard levels<br>
Inference policies and rate‑limits<br>

All these artifacts are already CM‑6 governed in your environment; the AI‑BOM formalizes them into a standard, audit‑friendly structure.<br>

*3. Repository Structure*<br><br>
Place the AI‑BOM hierarchy within your governance repository:<br><br>
/AI-BOM/<br>
    &nbsp;&nbsp;&nbsp;README.md<br>
    &nbsp;&nbsp;&nbsp;schema/<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ai-bom.schema.json<br>
    &nbsp;&nbsp;&nbsp;models/<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<model_name>/<version>/ai-bom.json<br>
    &nbsp;&nbsp;&nbsp;prompts/<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<prompt_name>/<version>/ai-bom.json<br>
    &nbsp;&nbsp;&nbsp;datasets/<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<dataset_name>/<version>/ai-bom.json<br>
    &nbsp;&nbsp;&nbsp;vectors/<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<store_name>/<index_id>/ai-bom.json<br>
    &nbsp;&nbsp;&nbsp;tools/<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<tool_name>/<version>/ai-bom.json<br>

This structure is optimized for:<br>

GitHub PR validation<br>
CI/CD enforcement<br>
Versioned lineage<br>
Artifact signing workflows<br>
Compliance auditability<br>


*4. AI‑BOM Master Schema (JSON)*<br><br>
The Master Schema can be found here. [Master Schema](./schema/ai-bom.schema.json)<br><br>
*5. Governance & Enforcement Rules*<br><br>
These rules are intended to be automated via a GitHub PR workflow:<br>

| **Requirement**                                                     | **Enforcement**     |
|---------------------------------------------------------------------|----------------------|
| Every model/prompt/dataset/tool change must include an updated AI‑BOM | ❌ Block merge        |
| All AI‑BOM files must pass JSON‑schema validation                    | ❌ Block merge        |
| TEVV results must be included and referenced                         | ❌ Block merge        |
| All artifacts must be cryptographically signed                       | ❌ Block merge        |
| Model Owner + AIMS Admin approvals required                          | ❌ Block merge        |
| SBOM reference required for any executable/library                   | ❌ Block merge        |

Workflow lives in:<br>
/.github/workflows/ai-bom-validation.yml<br>

*6. Integration With Existing Controls*<br><br>
Your governance stack is already AI‑BOM‑ready:<br>

AI Risk Lifecycle → risk_classification + controls_applied are encoded<br>
CM‑6 Configuration Governance → all artifacts treated as configuration items<br>
Provenance & Model Cards → captured under provenance + tevv<br>
Signed CI/CD Pipeline → signing_key + signatures<br>
Audit Logging (AU‑2/AU‑3) → ai_bom.id included in all logs<br>
TEVV → versioned results linked explicitly<br>
Industry‑specific Overlays → risk classifications map to sector standards<br>

The AI‑BOM becomes the compliance nucleus for everything downstream.<br>

*7. Authoring Checklist*<br><br>
A contributor must ensure:<br>

Guardrails and gateway policy references are included<br>
Prompt regression tests + adversarial/jailbreak results attached<br>
Agent graph changes are updated and cross‑referenced in the Tools AI‑BOM<br>
Required approvals and signatures are included<br>
Version increments follow your governance rules<br>


*8. Logging Requirements*<br><br>
All inference‑time and content‑moderation logs must contain:<br>

ai_bom.id<br>
Prompt version<br>
Model version<br>
Gateway policy ID<br>
Redaction decisions<br>
Tool invocations (if applicable)<br>

This ensures full lineage reconstruction during audits or incidents.
