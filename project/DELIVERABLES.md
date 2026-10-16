# MTL-XF-040 — Deliverables and metric contracts

**Decision:** Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules.

Required team outputs follow; this master does not claim they are complete. Each item needs a named author, distinct reviewer, version, evidence link and status.

## D1 — Discovery and requirements

**Due:** Week 2 · **Owner:** Business Analyst / Delivery Lead · **Team location:** docs/01-discovery/

Eight user requirements, prioritised by decision value, each with owner and measurable test; stakeholder map and as-is/to-be workflow for daily suspicious-URL triage review.

**Pass evidence:** All eight link source support, D/AC/DT and Security Operations Centre Manager approval.

## D2 — Governed source and freeze

**Due:** Week 2 · **Owner:** Data Governance Analyst · **Team location:** docs/02-data-governance/

S1 provenance, rights, dictionary, storage/restore path and immutable byte manifest. All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

**Pass evidence:** Every required file/field is verified and approved; unsupported requirements explicitly block G1.

## D3 — Engineering pipeline and model

**Due:** Week 4 · **Owner:** Data Engineer · **Team location:** src/ and docs/03-data-model/

Versioned ingestion/transformation and curated model. Grain: One observed URL/webpage feature record. Use normalised URL grouping and registrable-domain groups for partitioning; record public-suffix-list version offline. Preserve file/sheet/row lineage and all exclusion reasons.

**Pass evidence:** Input=retained+excluded+quarantined exactly; no unexplained join multiplication; clean-run instructions exist.

## D4 — Quality and exceptions

**Due:** Week 4 · **Owner:** Data Engineer + independent reviewer · **Team location:** docs/04-data-quality/

Profile types, nulls, duplicates, sentinels, labels, units and source support. Address Reversed labels, shared-domain leakage or live browsing of dataset URLs would invalidate or compromise triage.

**Pass evidence:** Every treatment has affected count, reason, owner and reviewer; no silent row loss or coercion.

## D5 — Phishing population and feature-availability audit

**Due:** Week 4 · **Owner:** SOC and Threat Intelligence Analyst · **Business reviewer:** Security Operations Centre Manager · **Independent reviewer:** Security Model Assurance Analyst

**Required artefact:** data/curated/phishing-population-and-feature-availability-audit.csv and docs/05-kpi-catalogue/phishing-population-and-feature-availability-audit.md.

235,795 source records, label map, duplicate/conflict/quarantine counts, offline registrable-domain grouping and every predictor classified lexical/webpage/corpus-derived/identifier.

**Mandatory pass condition (SC1):** label=0 becomes phishing_event=1; initial class counts reconcile to 100,945 phishing/134,850 legitimate; zero domain overlap across splits; raw URL/Domain/FILENAME/Title identifiers excluded from core.

**Review evidence:** retain the actual output, source-to-field/code/configuration lineage, expected/actual verification, reviewer and date. A heading, screenshot or unsupported claim alone cannot satisfy this deliverable.


## D6 — Offline lexical detection evaluation

**Due:** Week 6 · **Owner:** Data Scientist / Decision Modelling Analyst · **Business reviewer:** Security Operations Centre Manager · **Independent reviewer:** Security Model Assurance Analyst

**Required artefact:** docs/06-analysis/offline-lexical-detection-evaluation.md plus machine-readable evaluation_results.csv.

Simple lexical baseline versus candidate; domain-disjoint precision/recall, PR-AUC, legitimate FPR and confidence intervals; separate full-feature appendix if used.

**Mandatory pass condition (SC2):** Training-only preprocessing; no live URL access; webpage/unverifiable corpus signals excluded from receipt-time model; report actual test FPR even if target is missed.

**Review evidence:** retain the actual output, source-to-field/code/configuration lineage, expected/actual verification, reviewer and date. A heading, screenshot or unsupported claim alone cannot satisfy this deliverable.


## D7 — Three-band analyst triage policy

**Due:** Week 6 · **Owner:** SOC and Threat Intelligence Analyst · **Business reviewer:** Security Operations Centre Manager · **Independent reviewer:** Security Model Assurance Analyst

**Required artefact:** docs/07-decision-framework/three-band-analyst-triage-policy.csv plus policy.md.

Validation-selected high threshold targeting legitimate FPR≤1%, intermediate boundary and low-priority band; per-1,000 workload, missed phishing and ten defanged case records.

**Mandatory pass condition (SC3):** Nonzero high-band coverage required for a viable threshold; if infeasible mark target unmet; every case has explanation, human owner, action/escalation and evidence hash; no automatic URL blocking.

**Review evidence:** retain the actual output, source-to-field/code/configuration lineage, expected/actual verification, reviewer and date. A heading, screenshot or unsupported claim alone cannot satisfy this deliverable.


## D8 — SOC triage dashboard

**Due:** Week 7 · **Owner:** BI / Decision Product Developer · **Business reviewer:** Security Operations Centre Manager · **Independent reviewer:** Security Model Assurance Analyst

**Required artefact:** dashboard/README.md, runnable dashboard/prototype and static review export.

Band workload, false-positive/negative review, threshold trade-off and domain/source-quality views.

**Mandatory pass condition (SC4):** Ten flagged legitimate among 1,000 legitimate=1% FPR; reviewer traces a false positive and missed phishing case; no clickable malicious URLs appear in exports.

**Review evidence:** retain the actual output, source-to-field/code/configuration lineage, expected/actual verification, reviewer and date. A heading, screenshot or unsupported claim alone cannot satisfy this deliverable.


## D9 — Independent assurance and UAT

**Due:** Week 7 · **Owner:** Security Model Assurance Analyst · **Team location:** docs/08-assurance-uat/

Execute DT1–DT10 and three stakeholder tasks; record actual results and defects/retests.

**Pass evidence:** All ten tests and three tasks pass; zero unresolved critical/high defects.

## D10 — Technical/operational handover

**Due:** Week 8 · **Owner:** Engineer + Delivery Lead · **Team location:** docs/09-technical-handover/

One documented run entry point, dependency versions, manifest, output checksums/tolerances, refresh, rollback and operational owner.

**Pass evidence:** Second member reproduces all seven KPIs and policy queue from approved bytes; environment, elapsed time and discrepancies recorded.

## D11 — SOC response playbook and tabletop

**Due:** Week 8 · **Owner:** Business Analyst / Delivery Lead with domain specialist · **Business reviewer:** Security Operations Centre Manager · **Independent reviewer:** Security Model Assurance Analyst

**Required artefact:** deliverables/soc-response-playbook-and-tabletop.pdf plus editable slides and supporting cards/runbook.

Ten worked cases including false positives/negatives and uncertain domains; evidence retention, escalation, incident-response handoff, analyst override and monitoring triggers.

**Mandatory pass condition (SC5):** Two tabletop tasks pass: resolve legitimate high-score alert and escalate confirmed-in-fixture phishing; no browsing, DNS resolution, credential collection or claim of current live threat status.

**Review evidence:** retain the actual output, source-to-field/code/configuration lineage, expected/actual verification, reviewer and date. A heading, screenshot or unsupported claim alone cannot satisfy this deliverable.


## D12 — Contribution and final submission

**Due:** Weekly; final week 8 · **Owner:** Delivery Lead · **Team location:** CONTRIBUTIONS.md and submission/FINAL_SUBMISSION.md

Named D owners/reviewers, authored work, issues/PRs/commits, substantive reviews and demo/handover contribution for each member.

**Pass evidence:** All D/AC/DT evidence links resolve at final commit/tag; individual contribution is demonstrated beyond bulk upload or commit count.

## K1–K7 — Authoritative contracts

| ID | Metric | Definition and population | Grain |
| --- | --- | --- | --- |
| K1 | Phishing prevalence | count(label=0)/valid records; label=1 is legitimate. | frozen offline cohort |
| K2 | Phishing recall | TP/(TP+FN) where positive means phishing_event=1. | test |
| K3 | Phishing precision | TP/(TP+FP) in high-risk band. | test |
| K4 | Legitimate false-positive rate | legitimate records in high-risk band / all legitimate records. | test |
| K5 | PR-AUC | precision-recall area with phishing as positive and documented integration method. | domain-disjoint test |
| K6 | Review workload | high + intermediate band records per 1,000 evaluated; also show high band alone. | test |
| K7 | Domain isolation | number of registrable domains shared between train/validation/test; must equal zero. | all partitions |

Extend each contract with actual S1 raw fields and curated columns, code lineage, population/exclusions, numerator/denominator, units/grain, aggregation, missing/zero/undefined policy, owner/reviewer, freeze ID and tests. SOC and Threat Intelligence Analyst owns interpretation; Engineer implements; Security Model Assurance Analyst reviews.

Zero denominators produce unavailable values with reasons. Do not average subgroup rates when compatible summed numerators/denominators are required. Show class/segment counts beside rates and uncertainty. Counts reconcile exactly; arithmetic reconciles unrounded or to a documented tolerance no wider than 0.01 displayed unit. No source field can silently be replaced by an assumption.

## Evaluation and decision policy

Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME, Title and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.

Baseline simple lexical rule IsDomainIP=1 or URLLength>100 (project rule); compare validation-selected lexical model with review thresholds. Choose high-risk threshold maximising phishing recall subject to validation legitimate FPR≤1%; if infeasible mark target unmet. Add intermediate review band at score≥0.50 and below high threshold (if high threshold<0.50 choose and document lower review boundary on validation). Never auto-open or automatically block URLs.

**Interpretation boundary:** Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

See [acceptance](ACCEPTANCE_CRITERIA.md) for tests and [governance](GOVERNANCE.md) for release decisions.
