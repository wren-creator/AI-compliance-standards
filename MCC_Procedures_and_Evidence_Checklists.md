# Procedures & Evidence Checklists — Master Controls Catalog (MCC)

**Version:** 1.0  
**Last Updated:** 2026-03-18 14:56:53Z


This companion document provides **standard operating procedures (SOPs)** and **evidence checklists** for each control in the Master Controls Catalog. Link each section to your tickets, dashboards, and repositories to operationalize the control set.

---


### MCC‑01: AI Risk Management Lifecycle (AIRM)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑01 Control Guidance**
- Run AIIA/AIRA and document hazards, mitigations, residual risk.
- Link TEVV plan; set review cadence (quarterly).
- For High‑Risk: attach post‑market monitoring plan.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑02: Data Governance & Quality (DGQ)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑02 Control Guidance**
- Catalog datasets; record lineage & licenses.
- Run quality checks & bias tests; store reports.
- Tag PHI/PII; enforce masking/redaction rules in gateway.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑03: Logging, Monitoring & Traceability (LMT)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑03 Control Guidance**
- Implement the AI log schema (who/what/when/where/outcome + object IDs/hashes).
- Create SIEM dashboards & saved searches; schedule quarterly schema review.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑04: Human Oversight & HITL (HO)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑04 Control Guidance**
- Define HITL thresholds; configure workflow to block pending review.
- Capture human rationale; link to decision record.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑05: Transparency & User Information (TXP)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑05 Control Guidance**
- Enable provenance labels/watermarks for outward content.
- Generate explanation references when required and log IDs alongside outputs.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑06: Security, Robustness & TEVV (SRT)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑06 Control Guidance**
- Execute TEVV battery: jailbreak, leakage, toxicity/bias, RAG poisoning, cost‑DoS, regression.
- Define objective acceptance criteria; fail‑close if unmet.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- onfigs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑07: Access Control & RBAC (ARB)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑07 Control Guidance**
- Apply canonical RBAC; implement JIT & short‑lived creds.
- Run Quarterly Access Review; remediate excessive privileges.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑08: Configuration Management & CM‑6 for AI CIs (CMC)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑08 Control Guidance**
- Publish hardened baselines; hash/sign known‑good configs.
- Deny unknown hashes at runtime; alert on drift.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑09: Model & Data Provenance / Integrity (MDP)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑09 Control Guidance**
- Maintain Model Cards; record data/model lineage.
- Require append‑only registry; verify signatures before use.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑10: Signed CI/CD & Artifact Attestation (SCD)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑10 Control Guidance**
- Sign artifacts in CI; verify signatures at deploy & runtime.
- For promotions: require linked approvals and TEVV references.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑11: AI Gateway Enforcement (AGE)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑11 Control Guidance**
- Route all LLM traffic through gateway; maintain allow‑lists.
- Enforce redaction, rate/cost limits, tool scopes; emit provenance.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑12: RAG & Vector Store Governance (RVG)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑12 Control Guidance**
- Separate curation (staging) from promotion (prod via CI).
- Require signed ingestion manifests & index parameter baselines.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑13: Incident Response for AI (IR‑AI)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑13 Control Guidance**
- Maintain AI‑specific IR playbooks & triggers.
- Drill twice a year; perform post‑incident review and update risk files.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑14: Post‑Market Monitoring & Drift (PMD)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑14 Control Guidance**
- Define drift metrics & bounds on Model Card.
- Monitor dashboards; open remediation tickets for excursions.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑15: Supplier & Third‑Party Governance (STG)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑15 Control Guidance**
- Collect vendor model cards/SBOMs/safety evidence.
- Evaluate licenses & data terms; add contractual security clauses.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑16: Sector Overlays (SEC‑OV)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑16 Control Guidance**
- Apply sector overlay pack (Finance/Healthcare/Defense).
- Add sector‑specific tests, logs, retention & approvals.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑17: Transparency Records & Technical Documentation (TRD)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑17 Control Guidance**
- Maintain technical file per system; run internal audits.
- Capture management reviews & KPIs.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑18: Gateway Bypass Prevention & Egress Control (GBE)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑18 Control Guidance**
- Enforce mTLS + egress allow‑lists; block direct public LLM calls.
- Alert on bypass attempts; open IR tickets.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑19: Explainability & Output Governance (XOG)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑19 Control Guidance**
- Configure safety filters & HITL routing by risk.
- Store explanation IDs/hashes alongside outputs.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---


### MCC‑20: Governance Reviews & Continuous Improvement (GRCI)

#### Standard Operating Procedure (SOP)
1. **Trigger & Intake**
   - Capture a change/request using the standard intake form (link to your tracker).
   - Classify the use case/risk tier and assign owners.
2. **Preparation**
   - Gather required inputs, baseline references, and applicable sector overlay (if any).
3. **Execution Steps**
   - Step-by-step activities unique to this control (see *Control-specific Steps* below).
4. **Approvals & SoD**
   - Obtain required sign‑offs (roles defined in MCC Roles & SoD).
5. **Promotion/Activation**
   - Apply the change through signed CI/CD or gateway policy as applicable.
6. **Validation**
   - Confirm guardrails are active; run post‑change checks.
7. **Logging & Evidence**
   - Ensure AU‑2/AU‑3 fields are emitted to SIEM; archive artifacts in the Evidence folder.
8. **Review & Closure**
   - Record outcomes, deviations, lessons learned; schedule re‑evaluation.

#### Control‑specific Steps
**MCC‑20 Control Guidance**
- Hold quarterly governance reviews; track improvement actions.
- Update crosswalks & training when standards change.

- **Key Activities:**
  - See Guidance above; adapt steps to your environment.
- **Automation Hooks:**
  - Reference your CI/CD jobs, IaC modules, gateway policies, and scanners.
- **Failure/Exception Handling:**
  - Define alerts & thresholds; document rollback/kill‑switch; escalate to IR when required.

#### Evidence Checklist (attach to ticket)
- Intake record (ticket ID) & risk tier
- Owner assignments & SoD confirmation
- Configs/policies/baselines referenced (commit SHAs or doc links)
- Screenshots/CLI output of validation checks
- SIEM query results proving AU‑2/AU‑3 logging
- Approvals (names, timestamps)
- Final status & date; next review date

---
