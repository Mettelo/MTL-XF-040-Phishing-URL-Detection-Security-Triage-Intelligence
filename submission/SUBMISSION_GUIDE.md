# MTL-XF-040 — Submission guide

## Release sequence

1. Finish D1–D12 and link eight user requirements to D/AC/DT evidence.
2. Confirm S1 frozen manifest, rights/attribution, exact cohort and reviewer storage access.
3. Independently review K1–K7; reconcile K1–K5 in full cohort and one filtered slice against dashboard.
4. Lock policy/evaluation configuration and retain baseline, alternative and sensitivity outputs. Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME, Title and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.
5. Execute ten domain tests and three UAT tasks with expected/actual results, reviewer, defects and retests. Resolve all critical/high defects.
6. A distinct member performs a clean run from approved bytes. Record environment, dependency versions, entry point, elapsed time, K1–K7 and policy membership comparison.
7. Produce 8–12 slides and a 5–10-minute demo with five findings, three next actions and a defer case for Security Operations Centre Manager.
8. Complete FINAL_SUBMISSION.md, contribution evidence and immutable final commit/tag. Check reviewer access without paid-only dependencies.

## Walkthrough

Answer Choose an offline URL-risk triage threshold, analyst review bands and incident-response handoff rules. Demonstrate headline-to-source lineage, one policy change, one edge case and one unsupported/deferred action. Explain Reversed labels, shared-domain leakage or live browsing of dataset URLs would invalidate or compromise triage.

Keep assumptions, frozen scope and limitations in exports. No raw upload required; supply verified input access and restoration instructions. Security work remains offline and published examples defanged.

Reviewer records accepted/rework/blocked, date, actual reviewer and simulated sponsor role, unresolved low-severity issues with owners/dates and immutable evidence. A filled template without executed checks is not acceptance; formal scope revisions update affected tests before sign-off.

## Specific business acceptance walkthrough

At daily SOC review, an analyst inspects high-risk and intermediate bands, reviews defanged examples and false positives/negatives, and follows a documented evidence-preservation and incident-response handoff. No listed URL is opened.

Supply all five named output artefacts in [deliverables](../project/DELIVERABLES.md), execute SC1–SC5 in [acceptance](../project/ACCEPTANCE_CRITERIA.md), and complete their final-submission evidence table. Show actual values/cases, not only screenshots or report headings. Include the G1 simulated-approval record and a final retain-baseline/revise/pilot recommendation tied to measured evidence.
