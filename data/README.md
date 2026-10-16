# MTL-XF-040 — Data acquisition and engineering

## Approved S1

[PhiUSIIL Phishing URL (Website)](https://archive.ics.uci.edu/dataset/967); required files: **PhiUSIIL_Phishing_URL_Dataset.csv**. Expected source population: 235,795 URLs: 134,850 legitimate and 100,945 phishing.

Exact official download:

https://archive.ics.uci.edu/static/public/967/phiusiil+phishing+url+dataset.zip

No paid API or temporary dashboard export is required. [Source register](SOURCE_REGISTER.md) records checked byte references and rights.

## Frozen cohort and schema

All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

**Grain:** One observed URL/webpage feature record. Use normalised URL grouping and registrable-domain groups for partitioning; record public-suffix-list version offline.

**Required fields:** label, URL, Domain, FILENAME, URLLength, DomainLength, IsDomainIP, TLD and remaining provided URL/webpage numeric features; maintain availability and derivation classification for every predictor.

## Acquisition and freeze procedure

1. Retrieve original bytes and required documentation into approved durable storage outside Git. Record retrieval UTC, requested/resolved URLs and HTTP result.
2. Verify archive/member integrity, actual sizes and SHA-256 against the checked reference. A mismatch stops processing for publisher-change/corruption review.
3. Inspect schema, encoding, separator, headers/sheets, count, label coding, dates and coverage. Preserve actual header spellings, field types and original row order; distinguish identifiers, predictors and outcomes.
4. Complete source→actual field→KPI→deliverable support matrix for K1–K7 and D1–D12. Missing mandatory fields block dependent work; do not invent substitutes.
5. Approve an immutable S1-v1 byte manifest and exact cohort with retention owner, reviewer access, analyst/reviewer identities and date. Master source verification does not replace team G1 approval.
6. Transform reproducibly into separate curated outputs. Account for every raw row once as retained, excluded or quarantined; preserve lineage and treatment reason.

## Evaluation

Group-based approximately 60/20/20 train/validation/test by registrable domain using seed 40; missing/unparseable domains stay in a quarantine table. Keep duplicate normalised URLs in one group. Fit all learned preprocessing on train. Exclude URL, Domain, FILENAME, Title and label identifiers; core lexical-only model excludes webpage-derived and unverifiable corpus-derived features, including URLSimilarityIndex/TLDLegitimateProb/URLCharProb unless train-only derivation can be reproduced. A full provided-feature offline model may be reported separately with provenance caveats.

## Interpretation and quality

Offline only: no DNS resolution, live URL visits, webpage fetching, exploit testing or credential collection. Existing extracted features may include source population statistics and webpage-only signals. Never present these as all available at initial URL receipt; no proof of current maliciousness.

Profile every actual column. Dictionary includes spelling, type, unit, valid values, sentinel/null policy, meaning and feature/target/ID role plus availability time. Investigate duplicates/label conflicts; no silent deduplication or denominator invention. Validate key uniqueness and joins at the declared grain.

Keep [raw](raw/README.md), [references](reference/README.md) and [metadata](metadata/README.md) separate. Derived outputs belong in team data/curated/ or an approved location. Raw data are not uploaded by this update. Refresh creates a new snapshot while the accepted core stays reproducible.
