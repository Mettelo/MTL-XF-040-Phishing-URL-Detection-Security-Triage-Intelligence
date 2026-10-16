# MTL-XF-040 — Project brief

This is a simulated confidential-client engagement using public/open data. Stakeholders and commercial/security scenarios are fictional. Do not claim real-client employment, endorsement, operational deployment or realised benefits. This master pack specifies work to be completed; it does not claim the team has executed it.

**Client:** Confidential Commercial SOC · **Sponsor:** Security Operations Centre Manager · **Team:** 3–5 · **Duration:** 8 weeks · **Cycle:** daily suspicious-URL triage review

## Problem and commission

The SOC manager needs a triage workflow that captures suspicious URLs without overwhelming analysts with legitimate alerts. An apparently strong classifier can be misleading if legitimate and phishing labels are reversed, domains appear in both training and test, or webpage-derived signals are presented as available when the URL first arrives. The team must evaluate an offline receipt-time feature set, quantify review burden and define human escalation for uncertain and missed cases.

> Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules.

## Practical use case and business outputs

At daily SOC review, an analyst inspects high-risk and intermediate bands, reviews defanged examples and false positives/negatives, and follows a documented evidence-preservation and incident-response handoff. No listed URL is opened.

| Deliverable | What the team must hand over | Required contents |
| --- | --- | --- |
| D5 | Phishing population and feature-availability audit | 235,795 source records, label map, duplicate/conflict/quarantine counts, offline registrable-domain grouping and every predictor classified lexical/webpage/corpus-derived/identifier. |
| D6 | Offline lexical detection evaluation | Simple lexical baseline versus candidate; domain-disjoint precision/recall, PR-AUC, legitimate FPR and confidence intervals; separate full-feature appendix if used. |
| D7 | Three-band analyst triage policy | Validation-selected high threshold targeting legitimate FPR≤1%, intermediate boundary and low-priority band; per-1,000 workload, missed phishing and ten defanged case records. |
| D8 | SOC triage dashboard | Band workload, false-positive/negative review, threshold trade-off and domain/source-quality views. |
| D11 | SOC response playbook and tabletop | Ten worked cases including false positives/negatives and uncertain domains; evidence retention, escalation, incident-response handoff, analyst override and monitoring triggers. |

## Required success contract

| Success ID | Required deliverable | Specific pass condition |
| --- | --- | --- |
| SC1 | D5 — Phishing population and feature-availability audit | label=0 becomes phishing_event=1; initial class counts reconcile to 100,945 phishing/134,850 legitimate; zero domain overlap across splits; raw URL/Domain/FILENAME/Title identifiers excluded from core. |
| SC2 | D6 — Offline lexical detection evaluation | Training-only preprocessing; no live URL access; webpage/unverifiable corpus signals excluded from receipt-time model; report actual test FPR even if target is missed. |
| SC3 | D7 — Three-band analyst triage policy | Nonzero high-band coverage required for a viable threshold; if infeasible mark target unmet; every case has explanation, human owner, action/escalation and evidence hash; no automatic URL blocking. |
| SC4 | D8 — SOC triage dashboard | Ten flagged legitimate among 1,000 legitimate=1% FPR; reviewer traces a false positive and missed phishing case; no clickable malicious URLs appear in exports. |
| SC5 | D11 — SOC response playbook and tabletop | Two tabletop tasks pass: resolve legitimate high-score alert and escalate confirmed-in-fixture phishing; no browsing, DNS resolution, credential collection or claim of current live threat status. |

[Detailed acceptance](ACCEPTANCE_CRITERIA.md) defines executed evidence; [deliverables](DELIVERABLES.md) defines exact artefacts and ownership. G1 records simulated sponsor approval, not invented real-client agreement.

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
| Data Scientist / Decision Modelling Analyst | Baseline/alternative implementation, evaluation manifest, uncertainty and sensitivity. Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME, Title and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats. |
| BI / Decision Product Developer | Four views for the daily suspicious-URL triage review: overview, diagnostics, action/policy comparison, quality/limitations. Five independent KPI reconciliations and static export. |
| Security Model Assurance Analyst | Execute DT1–DT10, three UAT tasks and a distinct-member clean rerun; record expected/actual evidence, defects and retests. |

Assign named owners and review partners at kickoff. Combine roles only when a distinct member reviews critical calculations and performs final clean rerun. Sponsor labels describe simulated roles, separate from actual team identities.

## Evaluation contract

Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME, Title and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.

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

## Team organisation

The recommended team size is **3–5 people**. Delivery roles describe responsibilities, not separate positions: members can combine complementary business analysis, governance, engineering, analysis/modelling, BI and domain responsibilities. Assign a named owner to each deliverable and use a different team member to review critical calculations and perform the final clean rerun.
