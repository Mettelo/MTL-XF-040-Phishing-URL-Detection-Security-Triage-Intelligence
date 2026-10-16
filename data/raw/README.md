# MTL-XF-040 — Raw-data preservation

**No raw data are uploaded by this update.** This directory documents the strategy; it does not assert that input payloads are in Git.

Acquire PhiUSIIL_Phishing_URL_Dataset.csv from [S1 exact URL and checked-byte reference](../SOURCE_REGISTER.md). Retain original archive/members/codebooks outside Git in an immutable S1-v1 snapshot; record retrieval UTC, URL, filename, bytes and SHA-256. Keep a recoverable copy with retention owner and reviewer access.

**Frozen scope:** All 235,795 original records; retain source IDs for lineage and quarantine duplicate/conflicting-label groups. Original label=1 is legitimate and label=0 phishing; create explicit phishing_event=1−label for evaluation.

Preserve actual header spellings, field types and original row order; distinguish identifiers, predictors and outcomes.

Never overwrite, edit, re-encode or deduplicate originals. Extract into a separate working area; transformations, exclusions and parsed labels belong in code and curated outputs with source-row lineage. Check original and extracted byte hashes before analysis. A mismatch or missing approved snapshot blocks processing until resolved.

Team repositories should ignore local raw payloads while tracking this guidance and metadata. Do not remove any previously supplied raw data without explicit approval. Store access instructions without credentials and document restoration from retained bytes if upstream changes.
