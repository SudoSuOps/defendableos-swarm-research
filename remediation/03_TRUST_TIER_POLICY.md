# Trust-Tier Policy · DefendableOS Swarm Research Corpus v0.2

> "Trust layers compound. Hype cycles rotate."
> Mr. Defendable doctrine · 2026-05-24

This policy is the **explicit qualification gate** for the
`trust.ledger_status = ledger_ready` claim on every seed record in
`05_REAL_SEED_CORPUS.jsonl`. It is named in `audit/04_SCHEMA_GAP_REPORT.md`
remediation item **R3** and is now the binding standard for the corpus.

The policy is conservative on purpose. **A lower but truthful
ledger_ready count is stronger than an inflated count.** No record is
ledger-ready unless every one of the mandatory checks below evaluates
to PASS against the live `02_SOURCE_REGISTRY.csv` and the seed
metadata itself.

---

## 1 · Scope

Applies to every record where `trust.ledger_status ∈ {ledger_ready, context_only, discovery_signal}`.

Applies to every entry in `02_SOURCE_REGISTRY.csv` that other records
cite via `source.source_id`.

Does **not** retroactively rewrite audit receipts in `audit/` · those
are immutable books-and-records of the v0.1 state.

## 2 · Trust-tier definitions

| Tier | Label                  | Definition                                                                                                                | Examples                              |
| ---- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------- |
| 1    | Government / Statutory | First-party publication of a federal, state, or supra-national government body or court of record.                        | CFPB, FTC, SEC, DOJ, IC3, NIST, GAO   |
| 2    | Authoritative non-govt | Standards body, peer-reviewed academic publisher, vendor security advisory for its own product, or recognized CSIRT/CERT. | ISO, MITRE, OWASP, arXiv, CERT/CC, vendor PSIRT |
| 3    | Industry / Trade       | Recognized industry trade group, regulator-adjacent body, or established news outlet of record.                           | AICPA, ABA, Reuters, Bloomberg, FT    |
| 4    | Operational            | Internal operator field notes, blog posts from named experts, smaller publications, secondary aggregators.                | Brian Krebs, Bleeping Computer        |
| 5    | Unverified             | No primary source, unknown owner, anonymous post, or no resolvable URL.                                                   | Reddit threads, forum posts           |

## 3 · Mandatory ledger_ready checks · ALL must PASS

A record is **ledger_ready** if and only if **every** check below
evaluates to PASS. Failing any single check downgrades the record to
`context_only` (or `discovery_signal` if the source itself is unknown).

1. **REGISTRY_PRESENCE** — `source.source_id` exists in `02_SOURCE_REGISTRY.csv`.
2. **TIER_FLOOR** — registry entry `trust_tier ≤ 2` (Tier 1 govt or Tier 2 authoritative non-govt).
3. **PRIMARY_CONFIRMED** — registry entry `primary_source_confirmed_yes_no == 'yes'`.
4. **REFERENCE_RESOLVABLE** — `source.reference` matches `^https?://` and resolves to a stable public URL or filed court/regulatory document.
5. **NON_EMPTY_EXCERPT_OR_RECORD_ID** — at least one of `source.quoted_excerpt_under_250_chars` (≤250 chars) or `source.source_record_identifier` is non-empty.
6. **FACT_VS_INFERENCE_NOTED** — `trust.fact_vs_inference_notes` is non-empty and ≥ 40 characters · names what is documented fact vs analytic inference.
7. **CONFIDENCE_FLOOR** — `trust.confidence_score_0_to_1 ≥ 0.6`.
8. **CLASSIFICATION_PRESENT** — at least one of `classification.offense_signal`, `classification.pain_receipt`, or `classification.defense_fixer` is non-empty.
9. **NO_RAW_PII** — no live unredacted personal data · pedagogical PII test fixtures must carry the explicit markers defined in §10.

## 4 · Tier-2 (authoritative non-govt) additional gate

Sources promoted to the registry as **Tier 2 authoritative non-govt** during v0.2
remediation are flagged `primary_source_confirmed_yes_no = 'no_pending_human_review'`
until a named human reviewer audits the metadata, then promotes to `'yes'`. Any
seed citing such a source is held at `context_only` until the gate is cleared.

## 5 · Path A · adding a new registry entry

Permitted only when **all** are true:
- Owner is on the recognized government list (Tier 1) OR the recognized non-govt authoritative list (Tier 2).
- `reference` is a valid public URL.
- `source_type` is one of: `report`, `database`, `complaint_record`, `court_filing`, `advisory`, `standard`, `peer_reviewed_paper`, `regulatory_filing`, `enforcement_action`.
- Seed metadata provides the minimum fields for a row in `02_SOURCE_REGISTRY.csv`.

Adding under any other circumstance is forbidden. **Never invent a registry entry.**

## 6 · Path B · remapping to a canonical source_id

Permitted only on **URL_EXACT** match of the seed's `source.reference` to an
existing registry entry's `citation_or_reference`. Name similarity, owner
similarity, or topical similarity alone do **not** qualify. The original
`source_id` is preserved in `source._v0_2_audit.original_source_id_v0_1` for
provenance.

## 7 · Path C · downgrade to context_only

Default for orphan sources whose owner is not on a recognized list, or whose
URL does not resolve, or whose metadata is too thin to qualify under Path A.
The seed is retained for training/eval value · `trust.ledger_status` becomes
`context_only` · `trust.corroboration_required = true` · the reason is
appended to `trust.fact_vs_inference_notes` with the `[v0.2 audit]` prefix.

## 8 · Path D · quarantine or reject

Reserved for records that cannot be defended even as `context_only`:
- Source asserts a verifiable fact that contradicts a Tier 1 primary source.
- Source is anonymous, undated, and the claim is consequential.
- Source is not retrievable and the claim is unique to that source.

Currently **0 records** met this bar in the v0.2 remediation pass.

## 9 · Promotion under v0.3+

Records held at `context_only` because of Tier-2 nongovt human review may be
promoted to `ledger_ready` in v0.3 once the human reviewer signs the registry
row's `primary_source_confirmed_yes_no` flag to `'yes'` and timestamps the
review in the registry. Until then they remain `context_only`.

## 10 · Pedagogical PII markers (R6)

`09_STREETCHAT_SIGNAL_POLICY.md` contains deliberate teaching examples that
include synthetic name/SSN/phone/account fragments. These are not live
personal data · they exist solely to train the operator on what to redact.
Every such example is enclosed in the explicit markers below:

```
<!-- BEGIN PEDAGOGICAL_PII_TEST_FIXTURE: NOT LIVE PERSONAL DATA -->
... example text ...
<!-- END PEDAGOGICAL_PII_TEST_FIXTURE -->
```

These markers are the **only** acceptable container for synthetic PII in any
document in this corpus. A scanner finding raw PII outside these markers
must downgrade the containing artifact to `context_only` and open a remediation
ticket.

**Operational-contact allow-list.** The following are not personal PII and
are permitted outside the markers because they are first-party organizational
endpoints, not natural-person identifiers:

- Email addresses on `*.internal`, `defendableos.com`, `defendable*.com`, and `mrdefendable.com` domains used as operational reporting channels.
- Generic role addresses (`ethics@`, `security@`, `abuse@`, `support@`, `legal@`, `noreply@`).

These exclusions apply to scanners only · the operator-grade rule remains:
never publish a real natural person's email outside the markers.

## 11 · Manifest field discipline (R4)

`10_DEFENDABLE_LEDGER_MANIFEST.json` must split tier counts into two distinct
fields because sources and seed records are different cardinalities:

- `trust_tier_counts_sources` — counts over `02_SOURCE_REGISTRY.csv` (one row per source).
- `trust_tier_counts_seed_records` — counts over `05_REAL_SEED_CORPUS.jsonl` resolved through each seed's `source.source_id`.

A field named simply `trust_tier_counts` is forbidden going forward.

## 12 · Enforcement

Every release tag (`v0.X`) must include:
- `audit-vX_X/` directory with the eleven receipts named in
  `audit/00_RECEIPT_AUDIT_VERDICT.md`.
- A re-run of the source-grounding check producing **0 orphan source_ids**.
- A re-run of the PII scanner producing **0 hits outside §10 markers**.
- Manifest matching observed counts to within ±0.

A tag failing any of these is **not** ledger-ready and must carry the
`HONEY_PENDING_REMEDIATION` or `PROPOLIS_REMAINS` verdict label.

---

`Books and records. No proof, no honey. Validate the validator.`
