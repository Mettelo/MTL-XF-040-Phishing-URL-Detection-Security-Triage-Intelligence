# MTL-XF-040 — Final submission template

> Replace bracketed fields with actual evidence. Unexecuted items remain NOT RUN or BLOCKED; do not invent results or approvals.

## Identity

Team repository/members: [complete]

Master: https://github.com/Mettelo/MTL-XF-040-Phishing-URL-Detection-Security-Triage-Intelligence

Reviewed master commit; final team commit/tag/date; delivery lead; independent reviewer: [complete]

Simulated sponsor: Security Operations Centre Manager.

This is a simulated confidential-client engagement using public/open data. Stakeholders and commercial/security scenarios are fictional. Do not claim real-client employment, endorsement, operational deployment or realised benefits. This master pack specifies work to be completed; it does not claim the team has executed it.

## Decision and approved scope

Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules.

All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

Actual source freeze/manifest, storage access and approved deviations: [complete]

Retain limitation: Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

## Findings and actions

| Finding | Measured result and denominator | Evidence at final commit | Implication and limit |
| --- | --- | --- | --- |
| F1 | [complete] | [link] | [complete] |
| F2 | [complete] | [link] | [complete] |
| F3 | [complete] | [link] | [complete] |
| F4 | [complete] | [link] | [complete] |
| F5 | [complete] | [link] | [complete] |

Baseline/alternative results, selection changes, sensitivity, partition/stability evidence, assumptions and unmeasured benefits: [complete]

Three next actions with evidence, accountable owner, review date and pilot measurement; one defer/manual-review case: [complete]

Risk control evidence for Reversed labels, shared-domain leakage or live browsing of dataset URLs would invalidate or compromise triage. [complete]

## KPI results

| KPI | Result and population | Source/code lineage | Independent review |
| --- | --- | --- | --- |
| K1 Phishing prevalence | [complete] | [link] | [complete] |
| K2 Phishing recall | [complete] | [link] | [complete] |
| K3 Phishing precision | [complete] | [link] | [complete] |
| K4 Legitimate false-positive rate | [complete] | [link] | [complete] |
| K5 PR-AUC | [complete] | [link] | [complete] |
| K6 Review workload | [complete] | [link] | [complete] |
| K7 Domain isolation | [complete] | [link] | [complete] |

## Deliverable/acceptance evidence

| Deliverable | AC | Artefact/commit | Author/reviewer | State |
| --- | --- | --- | --- | --- |
| D1 Discovery and requirements | AC1 | [link] | [names] | NOT RUN |
| D2 Governed source and freeze | AC2 | [link] | [names] | NOT RUN |
| D3 Engineering pipeline and model | AC3 | [link] | [names] | NOT RUN |
| D4 Quality and exceptions | AC4 | [link] | [names] | NOT RUN |
| D5 KPI catalogue and lineage | AC5 | [link] | [names] | NOT RUN |
| D6 Analysis and evaluation | AC6 | [link] | [names] | NOT RUN |
| D7 Decision policy and action register | AC7 | [link] | [names] | NOT RUN |
| D8 Dashboard / decision prototype | AC8 | [link] | [names] | NOT RUN |
| D9 Independent assurance and UAT | AC9 | [link] | [names] | NOT RUN |
| D10 Technical/operational handover | AC10 | [link] | [names] | NOT RUN |
| D11 Executive recommendation | AC11 | [link] | [names] | NOT RUN |
| D12 Contribution and final submission | AC12 | [link] | [names] | NOT RUN |

## Test execution

| Test | Case | Actual/expected evidence | Reviewer | State |
| --- | --- | --- | --- | --- |
| DT1 | Label inversion | [complete] | [name] | NOT RUN |
| DT2 | Domain leakage | [complete] | [name] | NOT RUN |
| DT3 | Defanged evidence | [complete] | [name] | NOT RUN |
| DT4 | Feature timing | [complete] | [name] | NOT RUN |
| DT5 | False-positive arithmetic | [complete] | [name] | NOT RUN |
| DT6 | Infeasible threshold | [complete] | [name] | NOT RUN |
| DT7 | Source row accounting | [complete] | [name] | NOT RUN |
| DT8 | Missing versus zero | [complete] | [name] | NOT RUN |
| DT9 | BI reconciliation | [complete] | [name] | NOT RUN |
| DT10 | Independent rerun | [complete] | [name] | NOT RUN |

Three UAT task records, defects/retests, unresolved low issues: [complete]

## Independent rerun and handover

Approved input manifest/access (no credentials), environment/dependencies, entry point, elapsed time, cohort/output hashes, K1–K7/policy comparisons, discrepancies, named operator/date: [complete]

Dashboard/static export, slides/demo, operational runbook and contribution record links: [complete]

## Release decision

Blockers/limitations, owners and due dates: [complete]

Actual reviewer/date, simulated sponsor role and ACCEPTED / REWORK / BLOCKED decision: [complete only after evidence review]
