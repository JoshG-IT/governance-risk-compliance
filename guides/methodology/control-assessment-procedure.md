# Control Assessment Procedure

How a control is assessed, what counts as evidence, and how implementation status is determined.

---

## Assessment methods

Three, and most controls need more than one.

| Method | What it is | Answers |
|---|---|---|
| **Examine** | Review documents, configurations, records | Does a control exist on paper or in configuration? |
| **Interview** | Ask the people who operate it | Is it understood and followed? |
| **Test** | Exercise the control and observe the result | Does it actually work? |

Examine alone establishes intent. Test establishes effectiveness. A control assessed by examine only
should be recorded as such, because the difference matters when it fails.

---

## Implementation status

Five values. Use these and no others.

| Status | Means |
|---|---|
| **Implemented** | The control is in place and operating as intended across the assessed scope |
| **Partially implemented** | In place for some of the scope, or in place but not operating as intended |
| **Planned** | Not in place. A documented plan with a date exists |
| **Alternative implementation** | A different control achieves the objective. The alternative and its rationale are documented |
| **Not applicable** | The condition the control addresses does not exist in this system. The reason is documented |

**Partially implemented is the most common real answer and the most often avoided.** A control that
applies to 40 of 50 servers is partial, not implemented. Recording it as implemented is the single
most common way an assessment becomes useless.

**Not applicable requires a reason every time.** "The system does not process PII, so PT family
controls do not apply" is a reason. A blank cell is a gap in the assessment.

---

## Evidence by control family

What to gather, and what is not sufficient on its own.

| Family | Sufficient evidence | Not sufficient alone |
|---|---|---|
| **AC** Access Control | Role assignments exported, group membership, access review records, effective permissions | A policy stating least privilege is required |
| **AU** Audit | Log configuration, retention settings, sample records, review records | A statement that logging is enabled |
| **CM** Configuration | Baseline document, configuration export, drift detection output, change tickets | A baseline with no evidence it is applied |
| **IA** Identification | MFA enrollment report, password policy configuration, credential age report | A policy requiring MFA |
| **RA** Risk Assessment | Scan configuration, scan results, credential verification, remediation tracking | A scan summary with no evidence credentials succeeded |
| **SI** Integrity | Patch status per host, flaw remediation timeline, monitoring configuration | A patch management policy |
| **IR** Incident Response | The plan, exercise records, actual incident records, after-action reports | The plan alone |
| **CP** Contingency | Backup configuration, restore test records, recovery time measured | A backup schedule |

The pattern: a document describing what should happen is evidence of a policy control. It is not
evidence of a technical control. Technical controls need configuration state or observed behaviour.

---

## Evidence quality

```text
Strongest    Output from the system itself, timestamped, with the query that produced it
             Observed test result with before and after state
             Screenshot of configuration with scope visible

Adequate     Export from a management console
             Records of a process being followed, with dates

Weak         A policy document alone
             A statement from an interview with no corroboration
             A screenshot with no scope visible
```

Record how each piece of evidence was obtained. An assessment that cannot be reproduced cannot be
defended.

---

## Sampling

Full population is preferable. Where it is not feasible, state the sample.

Population: 312 domain-joined Windows servers
Sample:     30, selected across all four OUs and both datacenters
Method:     random within stratum
Rationale:  full-population configuration export was unavailable during the window

An unstated sample makes a finding unquantifiable. "Several servers lacked the setting" is not a
finding. "7 of 30 sampled, projecting to approximately 73 of 312" is.

---

## Per-control record

### CM-6 Configuration Settings

**Objective.** The organisation establishes and documents configuration settings, implements them,
and identifies and documents deviations.

**Method.** Examine, Test

**Evidence.**
- Azure Policy definition export showing the naming rule and its permitted effects
- Policy assignment showing the effect parameter in force at subscription scope
- Policy state output showing evaluation results across the scope

**Result.** Settings are defined and evaluation occurs. The assignment supplies an Audit effect, so
non-compliant resources are recorded rather than prevented.

**Status.** Partially implemented

**Gap.** CM-6(1) requires automated enforcement. Detection without prevention does not satisfy it.

**Recommendation.** Move the assignment to Deny after testing against existing workloads.

Objective, method, evidence, result, status, gap, recommendation. Every control, same shape.

---

## Assessment report structure

1. Scope and boundary        what was assessed, what was excluded, why
2. Standard and revision     which catalog, which baseline, which version
3. Method summary            examine, interview, test, and sampling approach
4. Results summary           status counts by family
5. Findings                  per-control records for anything not fully implemented
6. Risk ratings              likelihood and impact per finding
7. Recommendations           owner, timeline, priority
8. Residual risk             what remains, accepted by whom, review date

---

## What invalidates an assessment

| Problem | Why it matters |
|---|---|
| Scope not stated | Nobody knows what the result applies to |
| Revision not stated | Cannot be reproduced or compared |
| Sample not stated | Findings cannot be quantified |
| Status assigned without evidence | An opinion, not an assessment |
| Not applicable without reason | A gap in the assessment |
| Policy used as evidence of a technical control | Documented intent recorded as implementation |
| No reassessment after remediation | The fix is unverified |
