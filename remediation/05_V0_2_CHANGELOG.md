# v0.2 Changelog · defendable-offense-pain-fixer

Tag target: `defendable-offense-pain-fixer-v0.2`
Branch: `remediation/corpus-v0.2-source-receipts`
Parent: `f8be185` · README-fix: `0daa50d` · Audit basis: `audit/00_RECEIPT_AUDIT_VERDICT.md`

## What's in v0.2
- **Source receipts (R1)** — every `source.source_id` cited by a seed
  either resolves to an entry in `02_SOURCE_REGISTRY.csv` OR the citing
  seed is `context_only` with the reason recorded in
  `trust.fact_vs_inference_notes`.
- **Trust-tier policy (R3)** — `remediation/03_TRUST_TIER_POLICY.md` now
  defines the mandatory checks for `ledger_ready`. Every previously-claimed
  ledger_ready record was requalified against this policy.
- **Manifest field split (R4)** — `10_DEFENDABLE_LEDGER_MANIFEST.json` now
  has separate `trust_tier_counts_sources` and `trust_tier_counts_seed_records`.
- **Pedagogical PII markers (R6)** — synthetic PII test fixtures in
  `09_STREETCHAT_SIGNAL_POLICY.md` are wrapped in the explicit
  `BEGIN/END PEDAGOGICAL_PII_TEST_FIXTURE` markers defined in §10 of the trust-tier policy.

## Counts · v0.1 vs v0.2

| Measure                                | v0.1  | v0.2  | Delta  |
| -------------------------------------- | ----- | ----- | ------ |
| Sources in registry                    | 172   | 206   | +34    |
| Seed records                           | 255   | 255   | 0      |
| Orphan source_ids resolved (Path A+B)  | —     | 104   | new    |
| Orphan source_ids retained (Path C)    | 147   | 43    | -104   |
| Seeds claiming `ledger_ready`          | 210   | 79    | -131   |
| Seeds at `context_only`                | 41    | 175   | +134   |
| Seeds at `discovery_signal`            | 4     | 1     | -3     |
| Pedagogical PII fixtures unmarked      | 6     | 0     | -6     |

`A lower but truthful ledger_ready count is stronger than an inflated count.`

## What is intentionally not in v0.2
- **No new training data was added.** v0.2 is a remediation tag · its
  purpose is to bring the v0.1 corpus into ledger-ready discipline, not
  to expand it.
- **No retroactive edits to `audit/`.** The v0.1 audit receipts remain
  immutable in their original form.
- **No promotion of the 12 Tier-2 non-govt sources** that were added in
  this pass. Those wait for human review in v0.3.

## Anchor point
This tag is the books-and-records baseline for every subsequent corpus
release. v0.3 may only promote · it may not silently drop or rewrite the
v0.2 verdicts.
