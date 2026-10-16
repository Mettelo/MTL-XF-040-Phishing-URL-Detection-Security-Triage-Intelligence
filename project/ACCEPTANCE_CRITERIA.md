# MTL-XF-040 — Acceptance and domain tests

Acceptance requires executed evidence, not headings. Security Model Assurance Analyst records state, actual result, evidence/commit, date, author, reviewer and defect/retest reference. Templates start NOT RUN.

## AC1–AC12

| Criterion | Output | Measurable pass condition |
| --- | --- | --- |
| AC1 | D1 | All eight link source support, D/AC/DT and Security Operations Centre Manager approval. |
| AC2 | D2 | Every required file/field is verified and approved; unsupported requirements explicitly block G1. |
| AC3 | D3 | Input=retained+excluded+quarantined exactly; no unexplained join multiplication; clean-run instructions exist. |
| AC4 | D4 | Every treatment has affected count, reason, owner and reviewer; no silent row loss or coercion. |
| AC5 | D5 / SC1 | label=0 becomes phishing_event=1; initial class counts reconcile to 100,945 phishing/134,850 legitimate; zero domain overlap across splits; raw URL/Domain/FILENAME/Title identifiers excluded from core. |
| AC6 | D6 / SC2 | Training-only preprocessing; no live URL access; webpage/unverifiable corpus signals excluded from receipt-time model; report actual test FPR even if target is missed. |
| AC7 | D7 / SC3 | Nonzero high-band coverage required for a viable threshold; if infeasible mark target unmet; every case has explanation, human owner, action/escalation and evidence hash; no automatic URL blocking. |
| AC8 | D8 / SC4 | Ten flagged legitimate among 1,000 legitimate=1% FPR; reviewer traces a false positive and missed phishing case; no clickable malicious URLs appear in exports. |
| AC9 | D9 | All ten tests and three tasks pass; zero unresolved critical/high defects. |
| AC10 | D10 | Second member reproduces all seven KPIs and policy queue from approved bytes; environment, elapsed time and discrepancies recorded. |
| AC11 | D11 / SC5 | Two tabletop tasks pass: resolve legitimate high-score alert and escalate confirmed-in-fixture phishing; no browsing, DNS resolution, credential collection or claim of current live threat status. |
| AC12 | D12 | All D/AC/DT evidence links resolve at final commit/tag; individual contribution is demonstrated beyond bulk upload or commit count. |

## SC1–SC5 — Business output success contracts

These requirements supplement AC1–AC12 and are mandatory. Record approval at G1, then execute against final outputs. All five require PASS with traceable evidence, or a formally approved scope revision; an unmet model-performance target must be reported as unmet and reflected in the recommendation.

### SC1 / D5 — Phishing population and feature-availability audit

**Accountable delivery role:** SOC and Threat Intelligence Analyst. **Business reviewer:** Security Operations Centre Manager. **Independent assurance:** Security Model Assurance Analyst.

**Required artefact:** data/curated/phishing-population-and-feature-availability-audit.csv and docs/05-kpi-catalogue/phishing-population-and-feature-availability-audit.md.

**Content:** 235,795 source records, label map, duplicate/conflict/quarantine counts, offline registrable-domain grouping and every predictor classified lexical/webpage/corpus-derived/identifier.

**Pass condition:** label=0 becomes phishing_event=1; initial class counts reconcile to 100,945 phishing/134,850 legitimate; zero domain overlap across splits; raw URL/Domain/FILENAME/Title identifiers excluded from core.

**Evidence to retain:** actual output at final commit, source/configuration lineage, executed expected-versus-actual checks, reviewer identity/date and PASS/FAIL/BLOCKED. Do not mark complete from document presence alone.

### SC2 / D6 — Offline lexical detection evaluation

**Accountable delivery role:** Data Scientist / Decision Modelling Analyst. **Business reviewer:** Security Operations Centre Manager. **Independent assurance:** Security Model Assurance Analyst.

**Required artefact:** docs/06-analysis/offline-lexical-detection-evaluation.md plus machine-readable evaluation_results.csv.

**Content:** Simple lexical baseline versus candidate; domain-disjoint precision/recall, PR-AUC, legitimate FPR and confidence intervals; separate full-feature appendix if used.

**Pass condition:** Training-only preprocessing; no live URL access; webpage/unverifiable corpus signals excluded from receipt-time model; report actual test FPR even if target is missed.

**Evidence to retain:** actual output at final commit, source/configuration lineage, executed expected-versus-actual checks, reviewer identity/date and PASS/FAIL/BLOCKED. Do not mark complete from document presence alone.

### SC3 / D7 — Three-band analyst triage policy

**Accountable delivery role:** SOC and Threat Intelligence Analyst. **Business reviewer:** Security Operations Centre Manager. **Independent assurance:** Security Model Assurance Analyst.

**Required artefact:** docs/07-decision-framework/three-band-analyst-triage-policy.csv plus policy.md.

**Content:** Validation-selected high threshold targeting legitimate FPR≤1%, intermediate boundary and low-priority band; per-1,000 workload, missed phishing and ten defanged case records.

**Pass condition:** Nonzero high-band coverage required for a viable threshold; if infeasible mark target unmet; every case has explanation, human owner, action/escalation and evidence hash; no automatic URL blocking.

**Evidence to retain:** actual output at final commit, source/configuration lineage, executed expected-versus-actual checks, reviewer identity/date and PASS/FAIL/BLOCKED. Do not mark complete from document presence alone.

### SC4 / D8 — SOC triage dashboard

**Accountable delivery role:** BI / Decision Product Developer. **Business reviewer:** Security Operations Centre Manager. **Independent assurance:** Security Model Assurance Analyst.

**Required artefact:** dashboard/README.md, runnable dashboard/prototype and static review export.

**Content:** Band workload, false-positive/negative review, threshold trade-off and domain/source-quality views.

**Pass condition:** Ten flagged legitimate among 1,000 legitimate=1% FPR; reviewer traces a false positive and missed phishing case; no clickable malicious URLs appear in exports.

**Evidence to retain:** actual output at final commit, source/configuration lineage, executed expected-versus-actual checks, reviewer identity/date and PASS/FAIL/BLOCKED. Do not mark complete from document presence alone.

### SC5 / D11 — SOC response playbook and tabletop

**Accountable delivery role:** Business Analyst / Delivery Lead with domain specialist. **Business reviewer:** Security Operations Centre Manager. **Independent assurance:** Security Model Assurance Analyst.

**Required artefact:** deliverables/soc-response-playbook-and-tabletop.pdf plus editable slides and supporting cards/runbook.

**Content:** Ten worked cases including false positives/negatives and uncertain domains; evidence retention, escalation, incident-response handoff, analyst override and monitoring triggers.

**Pass condition:** Two tabletop tasks pass: resolve legitimate high-score alert and escalate confirmed-in-fixture phishing; no browsing, DNS resolution, credential collection or claim of current live threat status.

**Evidence to retain:** actual output at final commit, source/configuration lineage, executed expected-versus-actual checks, reviewer identity/date and PASS/FAIL/BLOCKED. Do not mark complete from document presence alone.


## DT1–DT10

| Test | Case | Expected result |
| --- | --- | --- |
| DT1 | Label inversion | Original label=0 maps to phishing_event=1 and label=1 maps to zero. |
| DT2 | Domain leakage | Two URLs with the same registrable domain cannot occur in different partitions. |
| DT3 | Defanged evidence | Displayed URL examples use hxxps and [.] or hashes; clickable malicious links fail publication review. |
| DT4 | Feature timing | A webpage-only feature in the lexical receipt-time model fails the availability audit. |
| DT5 | False-positive arithmetic | Ten flagged legitimate URLs among 1,000 legitimate URLs give 1% FPR, regardless of phishing count. |
| DT6 | Infeasible threshold | If no validation threshold meets FPR≤1% with nonzero alert coverage, mark target unmet and route to manual review. |
| DT7 | Source row accounting | One malformed fixture row is quarantined with source ID/reason; retained+excluded+quarantined equals input with no overlap. |
| DT8 | Missing versus zero | A 0/0 rate is unavailable with reason. Missing source evidence never becomes a measured zero or a fabricated result. |
| DT9 | BI reconciliation | K1–K5 match independent calculations on full cohort and one filtered slice. Counts exact; arithmetic unrounded or tolerance at most 0.01 displayed unit. |
| DT10 | Independent rerun | Distinct member reproduces cohort IDs, K1–K7 and policy selections from frozen bytes/configuration. Any stochastic tolerance is declared before running and discrepancies resolved. |

Use small synthetic fixtures for edge cases and frozen-source checks where relevant. Clearly distinguish fixture results from measured source outputs. Retain expected/actual evidence in docs/08-assurance-uat/; automate deterministic calculations where practical and document UI/interpretation reviews.

## Three project-specific UAT tasks

1. **Business review:** At daily SOC review, an analyst inspects high-risk and intermediate bands, reviews defanged examples and false positives/negatives, and follows a documented evidence-preservation and incident-response handoff. No listed URL is opened. The participant must explain the observed baseline, population and decision limitation without assistance from the author; record actual completion and any defect.
2. **Policy challenge:** use the D7 artefact to compare a baseline and alternative case, then record accept/defer/override with evidence and accountable owner. The domain reviewer must independently reproduce the case outcome.
3. **Operational walkthrough:** Ten flagged legitimate among 1,000 legitimate=1% FPR; reviewer traces a false positive and missed phishing case; no clickable malicious URLs appear in exports. Retain the task recording/screenshots, expected/actual values and reviewer outcome.

All three must pass after defect retest. Static exports may support review if interactive access is unavailable. The independent reviewer also checks every SC output against its declared artefact and source/configuration lineage.

## Release

All twelve ACs, ten DTs, UAT and independent rerun require evidence with zero unresolved critical/high defects. Underperformance can justify a baseline/manual policy; wrong labels/units, leakage, unregistered data or unsupported operational claims block acceptance. A scope revision updates affected requirements/tests; it cannot mark an unexecuted check passed.
