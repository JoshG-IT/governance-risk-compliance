<!--
  Conventions
  Case IDs  GRC-<AZ|AWS|GCP|ONP>-NNN; numbering restarts per platform
  Folders   cases/<CASE-ID>-slug/ holds README + evidence always; docs, artifacts as needed
  Guides    guides/frameworks/ for standards, guides/methodology/ for process
  Table     completed cases only; Key Finding = the result, not the topic
  Type      Assessment, Analysis, or Assessment > Remediation > Reassessment
  Access    Read-only | Contributor | Full control
  Scope     risk, control mapping, policy, audit evidence; technical remediation goes in the discipline repo
-->

# Governance, Risk and Compliance

Security casework covering risk assessment, control mapping, policy, and audit evidence across cloud and on-premises environments: NIST 800-53, NIST CSF, the NIST Risk Management Framework, ISO 27001, CMMC, and CIS Controls.

Each case includes the scope assessed, the standard applied, the evidence gathered, gap analysis, risk rating, and prioritized recommendations.

> **How to read the table.** **Type** shows how far a case went: assessment and recommendation, or the full arc through remediation and reassessment. **Access** shows the permission level held, which determines what the case could cover. **Framework** names the standard the assessment was measured against.

---

## Cases

| Case | Name | Type | Framework | Environment | Access | Key Finding |
|---|---|---|---|---|---|---|
| **GRC-AZ-001** | [Cloud Control Assessment](cases/GRC-AZ-001-cloud-control-assessment/) | Assessment | NIST 800-53 | Azure | Read-only | Pending |

---

## Skills Demonstrated

`NIST 800-53` · `NIST CSF` · `NIST RMF` · `ISO 27001` · `CMMC` · `CIS Controls` · `Risk Assessment` · `Control Mapping` · `Policy Authoring` · `Audit Evidence`

---

## Approach

1. Define scope: which systems, which boundary, which standard, which exclusions and why.
2. Establish inventory before assessing it. An assessment against an incomplete asset list is an assessment of nothing.
3. Select the applicable control set and baseline. Record the version assessed against.
4. Gather evidence per control. Configuration state, documented process, or observed practice.
5. Determine implementation status: implemented, partially implemented, planned, alternative implementation, or not applicable.
6. Rate risk by likelihood and impact in the environment as it exists, not by control severity alone.
7. Recommend remediation with named owners and realistic timelines.
8. Document residual risk, compensating controls, and accepted exceptions.

A control marked not applicable requires a stated reason. An unexplained exclusion is a gap in the assessment, not in the system.

Where write access is held, the case continues: remediate, then reassess to confirm the control status changed and nothing else broke.

---

## Frameworks

| Framework | Purpose | Prescriptive |
|---|---|---|
| **NIST 800-53** | Security and privacy control catalog. Used in federal assessments and RMF | Control objectives, not settings |
| **NIST CSF** | Outcome-based framework across Identify, Protect, Detect, Respond, Recover | Outcomes, program level |
| **NIST RMF** | The process wrapping 800-53: categorize, select, implement, assess, authorize, monitor | Process |
| **ISO 27001** | Information security management system requirements, with Annex A controls | Management system |
| **CMMC** | Defense contractor maturity model, built on NIST 800-171 | Practice level |
| **CIS Controls** | Prioritized safeguards organized into implementation groups | Prescriptive at the safeguard level |

---

## Guides

| Guide | Covers |
|---|---|
| [NIST 800-53 Reference](guides/frameworks/nist-800-53.md) | Control families, baselines, and the controls that recur in identity and configuration findings |
| [Control Assessment Procedure](guides/methodology/control-assessment-procedure.md) | Evidence types per control family, implementation status definitions, assessment objectives |
| [Risk Rating Method](guides/methodology/risk-rating-method.md) | Likelihood and impact scoring, defending a rating, residual risk |

---

## Data Handling

These cases document method and reasoning. Organisation and system names, asset inventories, personnel names and roles, network detail, specific control failures tied to identifiable systems, and audit findings that identify a client are redacted from public evidence.

Where casework originates from authorized client engagements, it is published only with written permission, after an agreed delay, and generalized so the environment is not identifiable from its description.
