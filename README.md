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

> **How to read the table.** **Type** shows how far a case went: assessment and recommendation, or the full arc through remediation and reassessment. **Access** shows the permission level held, which determines what the case could cover. **Framework** names the standard the assessment was measured against. All three are stated in full in each case README.

---

## Cases

| Case | Name | Type | Framework | Environment | Access | Key Finding |
|---|---|---|---|---|---|---|

*No completed cases yet.*

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

Standards used across these cases, and what each is for.

| Framework | Purpose | Prescriptive |
|---|---|---|
| **NIST 800-53** | Security and privacy control catalog. Used in federal assessments and RMF | Control objectives, not settings |
| **NIST CSF** | Outcome-based framework across Identify, Protect, Detect, Respond, Recover | Outcomes, program level |
| **NIST RMF** | The process wrapping 800-53: categorize, select, implement, assess, authorize, monitor | Process |
| **ISO 27001** | Information security management system requirements, with Annex A controls | Management system |
| **CMMC** | Defense contractor maturity model, built on NIST 800-171 | Practice level |
| **CIS Controls** | Prioritized safeguards organized into implementation groups | Prescriptive at the safeguard level |

```text
What am I producing?
        |
        +-- A technical configuration baseline for a specific platform
        |       --> CIS Benchmarks or DISA STIG (see vulnerability-management)
        |
        +-- A control assessment for a federal system
        |       --> NIST 800-53, within the RMF process
        |
        +-- A defense contractor readiness assessment
        |       --> CMMC, mapped to NIST 800-171
        |
        +-- A management system certification effort
        |       --> ISO 27001
        |
        +-- Program coverage reporting for leadership
                --> NIST CSF
```

Detailed comparison and control mapping method: [Compliance Frameworks](guides/frameworks/compliance-frameworks.md)

---

## Relationship to the Other Repositories

Technical findings live in the repository matching their discipline. This repository holds the assessment, the control mapping, and the risk decision that follows from them.

| Work | Repository |
|---|---|
| A CIS Benchmark scan of a Windows estate | [vulnerability-management](https://github.com/JoshG-IT/vulnerability-management) |
| A privileged access review | [identity-security](https://github.com/JoshG-IT/identity-security) |
| A detection coverage gap analysis | [security-operations](https://github.com/JoshG-IT/security-operations) |
| Mapping any of the above to 800-53 controls, rating the residual risk, and writing the remediation plan | here |

---

## Data Handling

These cases document method and reasoning. Organisation and system names, asset inventories, personnel names and roles, network detail, specific control failures tied to identifiable systems, and audit findings that identify a client are redacted from public evidence.

Where casework originates from authorized client engagements, it is published only with written permission, after an agreed delay, and generalized so the environment is not identifiable from its description.
