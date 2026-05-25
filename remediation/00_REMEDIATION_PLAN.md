# 00_REMEDIATION_PLAN.md · DefendableOS Swarm Research Corpus v0.1 → v0.2

> Branch: `remediation/corpus-v0.2-source-receipts`
> Parent commit: `f8be185` (v0.1 initial)
> README correction commit: `0daa50d`
> Audit basis: `audit/00_RECEIPT_AUDIT_VERDICT.md`
> Verdict at start: **MIXED · NOT LEDGER-READY** (94/210 ledger_ready claims pass)

## Why we did the work
The v0.1 audit found a non-zero count of `source.source_id` values inside
`05_REAL_SEED_CORPUS.jsonl` that were not present in
`02_SOURCE_REGISTRY.csv` (147 affected seed records). That broke the
books-and-records doctrine: a record claiming `ledger_ready` must cite a
source that itself can be opened, read, and verified. Without explicit
trust-tier policy, the `ledger_ready` claim was not defensible.

## What we changed (in this branch)
1. **R1 source receipts**
   - 70 orphan source_ids remapped to existing canonical registry entries via URL_EXACT match (`02_SOURCE_ID_RECONCILIATION_MAP.csv`).
   - 34 new registry entries added under the Path A criteria of `03_TRUST_TIER_POLICY.md` (22 government, 12 non-govt authoritative held at Tier 2 pending human review).
   - 43 seed records downgraded to `context_only` because their orphan source's owner is not on the recognized authoritative lists (Path C). Each record's `trust.fact_vs_inference_notes` carries the `[v0.2 audit]` reason.
   - 0 records rejected (Path D).
2. **R3 trust-tier policy** · published as `03_TRUST_TIER_POLICY.md` · §3 lists the mandatory ledger_ready checks; §5–§8 define the path criteria; §10 defines pedagogical PII markers; §11 defines the manifest field split.
3. **R4 manifest field split** · `10_DEFENDABLE_LEDGER_MANIFEST.json` now has `trust_tier_counts_sources` and `trust_tier_counts_seed_records` instead of the ambiguous `trust_tier_counts`.
4. **R6 pedagogical PII markers** · synthetic PII fixtures in `09_STREETCHAT_SIGNAL_POLICY.md` are wrapped in the explicit `BEGIN/END PEDAGOGICAL_PII_TEST_FIXTURE` HTML comments.
5. **R5 status** · already closed on main via commit `0daa50d` (README pair-count fix).
6. **Ledger requalification** · every record that claimed `ledger_ready` in v0.1 was re-evaluated against `03_TRUST_TIER_POLICY.md` §3. Audit per record is in `04_LEDGER_READY_PROMOTION_REPORT.csv`.

## What we did not change
- `audit/` artifacts are immutable books-and-records of the v0.1 state and were not edited.
- No seed record was deleted. Every seed retains its training/eval value · the conservative downgrade preserves the corpus without claiming more than is defensible.

## What is still open
- 12 non-govt registry entries added in v0.2 are marked `primary_source_confirmed_yes_no = 'no_pending_human_review'`. A human reviewer must audit those rows and promote them in v0.3 if they pass. Until then their citing seeds remain `context_only`.
- The Phase-7 re-audit lives in `audit-v0.2/` and is not pushed to public main until verdict labels the corpus `LEDGER_READY_APPROVED`.

## Final verdict label
See `audit-v0.2/00_RECEIPT_AUDIT_VERDICT.md`.
