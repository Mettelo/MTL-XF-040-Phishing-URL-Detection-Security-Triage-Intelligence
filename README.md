# MTL-XF-040 — Phishing URL Detection Security Triage Intelligence

**Track:** Cross-Functional · **Use case:** Information security · **Team:** 6–8 · **Duration:** 8 weeks

This is a simulated confidential-client engagement using public/open data. Stakeholders and commercial/security scenarios are fictional. Do not claim real-client employment, endorsement, operational deployment or realised benefits. This master pack specifies work to be completed; it does not claim the team has executed it.

## Business commission

**Client:** Confidential Commercial SOC. **Decision owner:** Security Operations Centre Manager. **Cadence:** daily suspicious-URL triage review.

SOC analysts need to prioritise suspicious-URL alerts while controlling false positives and retaining a human escalation route. Historical URL/webpage features can test offline triage, but do not establish live threat status or safe access to listed domains.

**Decision:** Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules.

## End-to-end delivery

Deliver business requirements, governed source acquisition, engineering and data quality, seven defined metrics, baseline/alternative policy comparison, decision dashboard, assurance/UAT, executive recommendation and operational handover. A model alone is insufficient.

Baseline simple lexical rule IsDomainIP=1 or URLLength>100 (project rule); compare validation-selected lexical model with review thresholds. Choose high-risk threshold maximising phishing recall subject to validation legitimate FPR≤1%; if infeasible mark target unmet. Add intermediate review band at score≥0.50 and below high threshold (if high threshold<0.50 choose and document lower review boundary on validation). Never auto-open or automatically block URLs.

## Core dataset and frozen cohort

**S1:** [PhiUSIIL Phishing URL (Website)](https://archive.ics.uci.edu/dataset/967). **Input:** PhiUSIIL_Phishing_URL_Dataset.csv. **Source population:** 235,795 URLs: 134,850 legitimate and 100,945 phishing.

All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

Exact official download:

https://archive.ics.uci.edu/static/public/967/phiusiil+phishing+url+dataset.zip

Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

No raw data are uploaded by this update. Teams preserve original bytes outside Git in an approved durable snapshot, with checksums, source metadata and reviewer access. The source register records verification evidence and acquisition rules.

## Pack navigation

- [Project brief](project/PROJECT_BRIEF.md) — scope, roles and milestones.
- [Business context](project/BUSINESS_CONTEXT.md) — stakeholders and decisions.
- [Deliverables](project/DELIVERABLES.md) — D1–D12 and K1–K7.
- [Acceptance criteria](project/ACCEPTANCE_CRITERIA.md) — AC1–AC12 and DT1–DT10.
- [Governance](project/GOVERNANCE.md) — gates, assumptions and changes.
- [Data guidance](data/README.md) and [source register](data/SOURCE_REGISTER.md).
- [Submission pack](submission/README.md) — team repository and final evidence.

## Evaluation and policy boundary

Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.

**Primary risk:** Reversed labels, shared-domain leakage or live browsing of dataset URLs would invalidate or compromise triage.

At G1 (week 2), approve requirements, source rights, actual schema and frozen bytes. At G2 (week 4), approve row accounting, all seven metrics and evaluation design. At G3 (week 6), review baseline/alternative and uncertainty. At G4 (week 8), require all twelve deliverables, ten executed domain tests, three UAT tasks, five reconciliations and a distinct-member clean rerun.

Assign named authors and review partners. Unsupported mandatory outputs remain blocked until an approved source/scope change resolves them. Record actual results in a separate Mettelo team repository; this master defines the work.
