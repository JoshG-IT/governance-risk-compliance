# Risk Rating Method

How a finding becomes a rating, and how the rating is defended.

---

## Risk is not severity

A vulnerability score describes a weakness in isolation. Risk describes what that weakness means in
a specific environment.

```text
Severity    "This flaw allows remote code execution"      CVSS, CAT level
Risk        "This flaw is on an internet-facing host
             holding a privileged managed identity,
             and a working exploit is public"             likelihood x impact
```

Reporting severity as risk produces a remediation queue nobody can work, because everything critical
looks equally urgent.

---

## Likelihood

| Rating | Means |
|---|---|
| **High** | Reachable by the relevant threat, a working method exists, and no compensating control blocks it |
| **Moderate** | Reachable but requires conditions, or a compensating control raises the difficulty |
| **Low** | Not reachable without first achieving something else, or a control blocks the path |

Factors:

```text
Exposure        internet-facing, internally reachable, or isolated
Exploitability  public exploit, known technique, or theoretical
Privilege       required to reach it: none, user, or administrative
Detectability   would use be noticed, and would anyone act on it
```

Exposure is the strongest factor. An unreachable weakness is a scheduling problem, not a risk.

---

## Impact

| Rating | Means |
|---|---|
| **High** | Severe or catastrophic effect on operations, assets, or individuals |
| **Moderate** | Serious effect. Significant degradation, damage, or financial loss |
| **Low** | Limited effect. Degradation with primary functions still performed |

Assessed against confidentiality, integrity, and availability. **The highest of the three sets the
rating.** A finding with low confidentiality impact and high availability impact is high impact.

Consider blast radius, not just the asset. A workstation is low impact. A workstation holding cached
domain administrator credentials is not.

---

## The matrix

|  | Low Impact | Moderate Impact | High Impact |
|---|---|---|---|
| **High Likelihood** | Low | Moderate | **High** |
| **Moderate Likelihood** | Low | Moderate | **High** |
| **Low Likelihood** | Low | Low | Moderate |

The matrix produces a starting rating. Adjust it where circumstances justify, and record why. An
unadjusted matrix output is a calculation, not an assessment.

---

## Defending a rating

Every rating needs a sentence supporting each axis and a sentence on why the result is what it is.

**Finding.** Service principal holds Owner at subscription scope with a credential
unrotated for 14 months and no identified owning team.

**Likelihood: High.** The credential is valid, long-lived, and usable through the client
credentials flow without interactive sign-in or MFA. No conditional access applies to
application authentication. Nobody owns the identity, so unusual use would not be questioned.

**Impact: High.** Owner at subscription scope permits creation, modification, and deletion
of every resource in the subscription, including role assignments.

**Risk: High.** Both axes are high and no compensating control reduces either. Rating is
unadjusted from the matrix.

If either axis cannot be supported in a sentence, the rating is not yet defensible.

---

## Adjusting

Adjustments are legitimate. Unrecorded adjustments are not.

| Reason to adjust down | Example |
|---|---|
| Compensating control | Network segmentation prevents the reachability the likelihood assumed |
| Monitoring in place | Use is detected and alerted, reducing the window |
| Scope narrower than assumed | The account exists in a development subscription with no production data |

| Reason to adjust up | Example |
|---|---|
| Aggregation | Three moderate findings combine into a complete attack path |
| Asset criticality | The system is a dependency for several others |
| Regulatory consequence | The finding carries a reporting obligation beyond operational impact |

**Aggregation is the one most often missed.** Individually manageable findings that chain into a path
are higher risk than any of them alone. Rate the chain as its own finding.

---

## Residual risk

Every assessment closes with what remains and who accepted it.

| Finding | Treatment | Residual | Compensating Control | Accepted By | Review |
|---|---|---|---|---|---|
| Legacy OS on SRV-03 | Accepted | Moderate | Isolated VLAN, no internet egress, monitored | [Role] | 2026-06-01 |

Four treatment options: **mitigate**, **transfer**, **avoid**, **accept**. Acceptance requires a named
accepting authority and a review date. Documented acceptance is a mature outcome. A finding quietly
left unfixed is not.

---

## Communicating a rating

Lead with consequence, not with the finding.

```text
WEAK      "AC-6 is not implemented. Service principal has Owner. Risk: High."

BETTER    "An unowned automated account can create, modify, or delete anything in the
           subscription, including granting itself further access. Its credential has
           not changed in over a year and its use would not raise an alert. Replacing
           the role takes an afternoon; the account needs an owner first."
```

Same finding. The second supports a decision.
