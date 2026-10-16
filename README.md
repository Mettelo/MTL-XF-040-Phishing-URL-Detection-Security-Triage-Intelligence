# MTL-XF-040 — Phishing URL Detection Security Triage Intelligence

**Track:** Cross-Functional · **Sector:** Commercial enterprise information security · **Team:** 6–8 · **Duration:** 8 weeks

## The business problem

The SOC manager needs a triage workflow that captures suspicious URLs without overwhelming analysts with legitimate alerts. An apparently strong classifier can be misleading if legitimate and phishing labels are reversed, domains appear in both training and test, or webpage-derived signals are presented as available when the URL first arrives. The team must evaluate an offline receipt-time feature set, quantify review burden and define human escalation for uncertain and missed cases.

**Simulated organisation:** Confidential Commercial SOC. **Accountable decision owner:** Security Operations Centre Manager.

## Practical use case

At daily SOC review, an analyst inspects high-risk and intermediate bands, reviews defanged examples and false positives/negatives, and follows a documented evidence-preservation and incident-response handoff. No listed URL is opened.

**Decision the project must enable:** Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules.

**Current approach:** Treat a single accuracy score as sufficient for alert prioritisation without domain isolation or analyst-workload controls.

**Required future approach:** Use domain-disjoint evaluation, a declared false-positive target and governed human triage with offline evidence.

## Specific deliverables

| Deliverable | What the team must hand over | Required contents |
| --- | --- | --- |
| D5 | Phishing population and feature-availability audit | 235,795 source records, label map, duplicate/conflict/quarantine counts, offline registrable-domain grouping and every predictor classified lexical/webpage/corpus-derived/identifier. |
| D6 | Offline lexical detection evaluation | Simple lexical baseline versus candidate; domain-disjoint precision/recall, PR-AUC, legitimate FPR and confidence intervals; separate full-feature appendix if used. |
| D7 | Three-band analyst triage policy | Validation-selected high threshold targeting legitimate FPR≤1%, intermediate boundary and low-priority band; per-1,000 workload, missed phishing and ten defanged case records. |
| D8 | SOC triage dashboard | Band workload, false-positive/negative review, threshold trade-off and domain/source-quality views. |
| D11 | SOC response playbook and tabletop | Ten worked cases including false positives/negatives and uncertain domains; evidence retention, escalation, incident-response handoff, analyst override and monitoring triggers. |

These five business outputs sit inside the full D1–D12 engagement. The team also delivers requirements/process mapping, source governance, engineering and quality evidence, independent UAT, handover and contribution records. [Detailed deliverable specifications](project/DELIVERABLES.md) define owners, artefact paths, fields, calculations and review evidence.

## Required success criteria

| Success ID | Required deliverable | Specific pass condition |
| --- | --- | --- |
| SC1 | D5 — Phishing population and feature-availability audit | label=0 becomes phishing_event=1; initial class counts reconcile to 100,945 phishing/134,850 legitimate; zero domain overlap across splits; raw URL/Domain/FILENAME/Title identifiers excluded from core. |
| SC2 | D6 — Offline lexical detection evaluation | Training-only preprocessing; no live URL access; webpage/unverifiable corpus signals excluded from receipt-time model; report actual test FPR even if target is missed. |
| SC3 | D7 — Three-band analyst triage policy | Nonzero high-band coverage required for a viable threshold; if infeasible mark target unmet; every case has explanation, human owner, action/escalation and evidence hash; no automatic URL blocking. |
| SC4 | D8 — SOC triage dashboard | Ten flagged legitimate among 1,000 legitimate=1% FPR; reviewer traces a false positive and missed phishing case; no clickable malicious URLs appear in exports. |
| SC5 | D11 — SOC response playbook and tabletop | Two tabletop tasks pass: resolve legitimate high-score alert and escalate confirmed-in-fixture phishing; no browsing, DNS resolution, credential collection or claim of current live threat status. |

These are assessment requirements, not claims that results have already been achieved. At G1 the team records simulated stakeholder approval of scope, policy assumptions and criteria; later changes require a decision log. Financial benefit, causal uplift, production safety and operational adoption need separate pilot evidence. [Acceptance and worked tests](project/ACCEPTANCE_CRITERIA.md) control pass/fail.

## Data and fixed analytical boundary

**Official source:** [PhiUSIIL Phishing URL (Website)](https://archive.ics.uci.edu/dataset/967). **Required input:** PhiUSIIL_Phishing_URL_Dataset.csv. **Expected source population:** 235,795 URLs: 134,850 legitimate and 100,945 phishing.

All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

**Download:** https://archive.ics.uci.edu/static/public/967/phiusiil+phishing+url+dataset.zip

Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

The [source register](data/SOURCE_REGISTER.md) records checked hashes, exact acquisition and snapshot rules. No raw data are uploaded; teams retain immutable originals outside Git with a manifest and reviewer access.

## Analysis and decision rules

Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME, Title and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.

Baseline simple lexical rule IsDomainIP=1 or URLLength>100 (project rule); compare validation-selected lexical model with review thresholds. Choose high-risk threshold maximising phishing recall subject to validation legitimate FPR≤1%; if infeasible mark target unmet. Add intermediate review band at score≥0.50 and below high threshold (if high threshold<0.50 choose and document lower review boundary on validation). Never auto-open or automatically block URLs.

Report measured baselines and alternatives, sample sizes, uncertainty and failure cases. A weaker model does not justify disguising results: the final recommendation must say whether to retain the baseline, improve the prototype or run a controlled pilot, and cite the evidence.

## Who does what

- Business Analyst / Delivery Lead: eight testable user requirements, process map and decision-to-evidence traceability.
- Data Governance Analyst: source rights, frozen cohort, field support and seven-KPI lineage.
- Data Engineer: reproducible model/pipeline, exact row accounting and key/join checks.
- SOC and Threat Intelligence Analyst: Create ten defanged triage cases, including false positives and false negatives, with evidence preservation, analyst action and incident-response escalation.
- Data Scientist / Decision Modelling Analyst: baseline/alternative, feature timing, validation and sensitivity.
- BI / Decision Product Developer: the specified decision views, filter reconciliation and static export.
- Security Model Assurance Analyst: independent checks, three stakeholder walkthroughs and clean rerun.

Assign named authors and distinct reviewers; combining roles cannot remove independent review.

## Delivery and review

| Gate | Due | Evidence and accountable reviewers |
| --- | --- | --- |
| G1 scope/source | Week 2 | Security Operations Centre Manager, BA and Governance approve eight requirements, S1 rights/manifest, actual fields and frozen cohort. Unsupported mandatory outputs block dependent work. |
| G2 engineering/metrics | Week 4 | Engineer, SOC and Threat Intelligence Analyst and distinct reviewer approve row accounting, keys/joins, K1–K7, five reconciliations and evaluation manifest. |
| G3 policy | Week 6 | Security Operations Centre Manager reviews baseline/alternative, sensitivity, workload, assumptions and one insufficient-evidence/manual-review case. |
| G4 release | Week 8 | Simulated Mettelo panel and Security Model Assurance Analyst accept D1–D12, AC1–AC12, ten executed tests, three UAT tasks and clean rerun with zero critical/high defects. |

## Full master pack

[Project brief](project/PROJECT_BRIEF.md) · [Business context](project/BUSINESS_CONTEXT.md) · [Deliverables](project/DELIVERABLES.md) · [Success criteria and tests](project/ACCEPTANCE_CRITERIA.md) · [Governance](project/GOVERNANCE.md) · [Data guidance](data/README.md) · [Submission](submission/README.md).

This is a simulated confidential-client engagement using public/open data. Stakeholders and commercial/security scenarios are fictional. Do not claim real-client employment, endorsement, operational deployment or realised benefits. This master pack specifies work to be completed; it does not claim the team has executed it.
