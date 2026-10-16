# MTL-XF-040 — Project brief

This is a simulated confidential-client engagement using public/open data. Stakeholders and commercial/security scenarios are fictional. Do not claim real-client employment, endorsement, operational deployment or realised benefits. This master pack specifies work to be completed; it does not claim the team has executed it.

**Client:** Confidential Commercial SOC · **Sponsor:** Security Operations Centre Manager · **Team:** 6–8 · **Duration:** 8 weeks · **Cycle:** daily suspicious-URL triage review

## Problem and commission

SOC analysts need to prioritise suspicious-URL alerts while controlling false positives and retaining a human escalation route. Historical URL/webpage features can test offline triage, but do not establish live threat status or safe access to listed domains.

> Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules.

## Core scope

All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

Required source: PhiUSIIL_Phishing_URL_Dataset.csv. Model grain: One observed URL/webpage feature record. Use normalised URL grouping and registrable-domain groups for partitioning; record public-suffix-list version offline.

Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

Additional datasets, live integrations, operational deployment and claims of achieved benefits are outside core. Scope/source changes need approval and updated tests.

## Cross-functional roles

| Role | Required evidence |
| --- | --- |
| Business Analyst / Delivery Lead | Eight numbered prioritised requirements for Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules. As-is/to-be workflow, stakeholder map and requirement→D→AC→DT traceability. |
| Data Governance Analyst | S1 rights, byte manifest, field support, approved cohort and lineage for all seven KPIs; review Reversed labels, shared-domain leakage or live browsing of dataset URLs would invalidate or compromise triage. |
| Data Engineer | Reproducible ingestion, curated model, source-row ledger and key/join controls at grain: One observed URL/webpage feature record. Use normalised URL grouping and registrable-domain groups for partitioning; record public-suffix-list version offline. |
| SOC and Threat Intelligence Analyst | Create ten defanged triage cases, including false positives and false negatives, with evidence preservation, analyst action and incident-response escalation. |
| Data Scientist / Decision Modelling Analyst | Baseline/alternative implementation, evaluation manifest, uncertainty and sensitivity. Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats. |
| BI / Decision Product Developer | Four views for the daily suspicious-URL triage review: overview, diagnostics, action/policy comparison, quality/limitations. Five independent KPI reconciliations and static export. |
| Security Model Assurance Analyst | Execute DT1–DT10, three UAT tasks and a distinct-member clean rerun; record expected/actual evidence, defects and retests. |

Assign named owners and review partners at kickoff. Combine roles only when a distinct member reviews critical calculations and performs final clean rerun. Sponsor labels describe simulated roles, separate from actual team identities.

## Evaluation contract

Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.

Record predictor allowlist, target mapping, timing assumptions, partition/resample IDs and train-only transforms. Report partition/class counts and uncertainty. Negative model results can support a manual/baseline recommendation; invented performance cannot.

## Decision contract

Baseline simple lexical rule IsDomainIP=1 or URLLength>100 (project rule); compare validation-selected lexical model with review thresholds. Choose high-risk threshold maximising phishing recall subject to validation legitimate FPR≤1%; if infeasible mark target unmet. Add intermediate review band at score≥0.50 and below high threshold (if high threshold<0.50 choose and document lower review boundary on validation). Never auto-open or automatically block URLs.

## Objectives and gates

Deliver D1–D12, K1–K7, AC1–AC12, ten executed domain tests, three UAT tasks, five reconciliations and an independent rerun. The sponsor must trace one action to source and explain why uncertain cases are deferred.

| Gate | Due | Evidence and accountable reviewers |
| --- | --- | --- |
| G1 scope/source | Week 2 | Security Operations Centre Manager, BA and Governance approve eight requirements, S1 rights/manifest, actual fields and frozen cohort. Unsupported mandatory outputs block dependent work. |
| G2 engineering/metrics | Week 4 | Engineer, SOC and Threat Intelligence Analyst and distinct reviewer approve row accounting, keys/joins, K1–K7, five reconciliations and evaluation manifest. |
| G3 policy | Week 6 | Security Operations Centre Manager reviews baseline/alternative, sensitivity, workload, assumptions and one insufficient-evidence/manual-review case. |
| G4 release | Week 8 | Simulated Mettelo panel and Security Model Assurance Analyst accept D1–D12, AC1–AC12, ten executed tests, three UAT tasks and clean rerun with zero critical/high defects. |

[Deliverables](DELIVERABLES.md), [acceptance](ACCEPTANCE_CRITERIA.md), [data register](../data/SOURCE_REGISTER.md).
