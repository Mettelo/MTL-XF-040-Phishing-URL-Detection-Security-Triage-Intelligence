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

## D5 — KPI catalogue and lineage

**Due:** Week 4 · **Owner:** SOC and Threat Intelligence Analyst · **Team location:** docs/05-kpi-catalogue/

Implement K1–K7 below with actual source fields, code, valid population, denominator, units, grain, exclusions, owner and worked examples.

**Pass evidence:** All seven reviewed; K1–K5 reconcile independently and in BI on full cohort and one filtered slice.

## D6 — Analysis and evaluation

**Due:** Week 6 · **Owner:** Data Scientist / Decision Modelling Analyst · **Team location:** docs/06-analysis/

Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.

**Pass evidence:** Baseline and alternative results, population/class counts, uncertainty, negative findings and feature/timing audit retained; no test-driven tuning.

## D7 — Decision policy and action register

**Due:** Week 6 · **Owner:** SOC and Threat Intelligence Analyst · **Team location:** docs/07-decision-framework/

Baseline simple lexical rule IsDomainIP=1 or URLLength>100 (project rule); compare validation-selected lexical model with review thresholds. Choose high-risk threshold maximising phishing recall subject to validation legitimate FPR≤1%; if infeasible mark target unmet. Add intermediate review band at score≥0.50 and below high threshold (if high threshold<0.50 choose and document lower review boundary on validation). Never auto-open or automatically block URLs.

**Pass evidence:** Both policies and sensitivity outputs supplied; every action has evidence, eligibility, owner, next review and uncertainty. Include a defer case.

## D8 — Dashboard / decision prototype

**Due:** Week 7 · **Owner:** BI / Decision Product Developer · **Team location:** dashboard/

Four linked views: K1–K7 executive overview, source-supported diagnostics, policy/action comparison and quality/limitations for Security Operations Centre Manager.

**Pass evidence:** Five metric/filter checks pass; frozen scope and limitations survive export; static copy/user guide require no paid access.

## D9 — Independent assurance and UAT

**Due:** Week 7 · **Owner:** Security Model Assurance Analyst · **Team location:** docs/08-assurance-uat/

Execute DT1–DT10 and three stakeholder tasks; record actual results and defects/retests.

**Pass evidence:** All ten tests and three tasks pass; zero unresolved critical/high defects.

## D10 — Technical/operational handover

**Due:** Week 8 · **Owner:** Engineer + Delivery Lead · **Team location:** docs/09-technical-handover/

One documented run entry point, dependency versions, manifest, output checksums/tolerances, refresh, rollback and operational owner.

**Pass evidence:** Second member reproduces all seven KPIs and policy queue from approved bytes; environment, elapsed time and discrepancies recorded.

## D11 — Executive recommendation

**Due:** Week 8 · **Owner:** Delivery Lead + domain specialist · **Team location:** deliverables/

8–12 slides and a 5–10-minute demo answering Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules. Include five evidence-linked findings, three next actions, comparison and a defer case.

**Pass evidence:** Every numeric claim links tested evidence; costs/benefits and operational targets are labelled assumptions unless measured.

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

Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.

Baseline simple lexical rule IsDomainIP=1 or URLLength>100 (project rule); compare validation-selected lexical model with review thresholds. Choose high-risk threshold maximising phishing recall subject to validation legitimate FPR≤1%; if infeasible mark target unmet. Add intermediate review band at score≥0.50 and below high threshold (if high threshold<0.50 choose and document lower review boundary on validation). Never auto-open or automatically block URLs.

**Interpretation boundary:** Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

See [acceptance](ACCEPTANCE_CRITERIA.md) for tests and [governance](GOVERNANCE.md) for release decisions.
