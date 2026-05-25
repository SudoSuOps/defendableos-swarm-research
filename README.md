# DefendableOS Deep Research Swarm
## Offense Signals, Pain Receipts & Defense Fixers Corpus v0.1

[![Corpus Version](https://img.shields.io/badge/corpus-v0.1.0-gold)](./deliverables/10_DEFENDABLE_LEDGER_MANIFEST.json)
[![Records](https://img.shields.io/badge/records-255-blue)](./deliverables/05_REAL_SEED_CORPUS.jsonl)
[![Sources](https://img.shields.io/badge/sources-172-green)](./deliverables/02_SOURCE_REGISTRY.csv)
[![Fixers](https://img.shields.io/badge/fixers-115-purple)](./deliverables/06_DEFENSE_FIXER_LIBRARY.jsonl)
[![License](https://img.shields.io/badge/trust-verified-darkgreen)]()

> **No proof, no honey.** A source-grounded, ledger-ready research corpus for training SwarmCurator, testing SwarmJelly, and powering the Defendable Ledger.

---

## What This Is

This repository contains the complete output of the **Defendable Deep Research Swarm** -- a multi-agent, multi-lane research mission that built the foundational corpus for [DefendableOS](https://defendableos.com), a trust-and-proof operating system.

The corpus connects three core concepts:

- **Offense Signal** -- A documented or alleged pattern that may create harm, unfairness, loss, deception, or untrustworthy conduct
- **Pain Receipt** -- Evidence showing how the offense signal affects a person, business, asset, or system
- **Defense Fixer** -- A remedy, control, verification process, or escalation mechanism capable of reducing, proving, resolving, or preventing the pain

Every record is traceable to its source. Every source has a trust tier. Nothing is presented as fact that is only allegation.

---

## Repository Structure

```
defendableos-swarm-research/
|-- README.md                          # This file
|-- deliverables/                      # 13 canonical deliverables
|   |-- 00_EXECUTIVE_MEMO.md           # One-page strategic summary
|   |-- 01_DEFENDABLE_ONTOLOGY.md      # Full vocabulary & taxonomy system
|   |-- 02_SOURCE_REGISTRY.csv         # 172 sources with metadata
|   |-- 03_SOURCE_RANKING_AND_ACQUISITION_PLAN.md  # Source prioritization
|   |-- 04_CORPUS_SCHEMA.json          # JSON Schema for all records
|   |-- 05_REAL_SEED_CORPUS.jsonl      # 255 real, source-grounded records
|   |-- 06_DEFENSE_FIXER_LIBRARY.jsonl # 115 reusable fixer objects
|   |-- 07_SWARMCURATOR_EVAL_PACK.jsonl   # 157 evaluation examples
|   |-- 08_SWARMJELLY_FAILURE_PACK.jsonl  # 151 hard/ambiguous examples
|   |-- 09_STREETCHAT_SIGNAL_POLICY.md    # Community signal ingestion policy
|   |-- 10_DEFENDABLE_LEDGER_MANIFEST.json # Provenance manifest
|   |-- 11_PRODUCT_AND_AGENT_OPPORTUNITY_MAP.md  # Product strategy
|   |-- 12_RESEARCH_GAPS_AND_NEXT_RUN.md # What's next
|
|-- research/                          # Raw research by lane
|   |-- defendable_dim01_consumer_financial.md     # Lane 1: CFPB, FTC, AGs
|   |-- defendable_dim02_fraud_digital.md          # Lane 2: FBI IC3, SEC, crypto
|   |-- defendable_dim03_cyber_ai_risk.md          # Lane 3: CISA, NVD, MITRE
|   |-- defendable_dim04_property_contractor.md    # Lane 4: State boards, courts
|   |-- defendable_dim05_asset_compute.md          # Lane 5: Hardware, valuation
|   |-- defendable_dim06_ai_agent_trust.md         # Lane 6: AI safety, frameworks
|
|-- docs/
|   |-- VERDICT.md                     # Tribunal verdict (HONEY approved)
```

---

## The Numbers

| Metric | Value |
|--------|-------|
| **Research Lanes** | 6 |
| **Sources Cataloged** | 172 |
| **Trust Tier 1 Sources** | 66 (38%) |
| **Trust Tier 2 Sources** | 105 (61%) |
| **Seed Corpus Records** | 255 |
| **Defense Fixers** | 115 |
| **SwarmCurator Eval Examples** | 157 |
| **SwarmJelly Hard Examples** | 151 |
| **Ledger-Ready Records** | 210 (82%) |
| **Total Research Lines** | 8,219+ |

### Corpus Distribution by Lane

| Lane | Records | Primary Source | Key Stat |
|------|---------|---------------|----------|
| Consumer Financial Pain | 52 | CFPB Complaint Database | 6.6M complaints in 2025 |
| Fraud, Impersonation & Digital Loss | 50 | FBI IC3 Annual Report | $20.877B in losses (2025) |
| Cyber & AI System Risk | 50 | CISA KEV Catalog | 1,484 actively exploited vulns |
| Property & Contractor Pain | 28 | State Licensing Boards | 49% home warranty satisfaction |
| Asset, Compute & Proof-of-Value | 35 | FTC/CPSC Enforcement | $44.3B e-commerce fraud |
| AI Agent Trust & Accountability | 40 | NIST AI RMF + EU AI Act | $1.28B deepfake fraud |

---

## Key Discoveries

### Discovery 1: Consumer Financial Pain Is a Data Goldmine
The CFPB Consumer Complaint Database is the single highest-value source for DefendableOS. It contains **6.6 million complaints** (2025), is publicly accessible, includes both narratives and outcomes, and covers the full Offense Signal -> Pain Receipt -> Defense Fixer chain. Credit reporting complaints alone grew **3,000% since 2020**. [Source Registry](./deliverables/02_SOURCE_REGISTRY.csv) | [Research](./research/defendable_dim01_consumer_financial.md)

### Discovery 2: Fraud Losses Exceed $20 Billion and Are Accelerating
The FBI IC3 2025 Annual Report documents **$20.877 billion in total losses** -- a 26% increase year-over-year. Investment fraud ($8.649B), BEC ($3.046B), and crypto fraud ($11.3B via FBI and other agencies) dominate. AI-nexus BEC alone caused **$30+ million in confirmed losses**. This is the largest addressable market for DefendableOS products. [Research](./research/defendable_dim02_fraud_digital.md)

### Discovery 3: CISA KEV Catalog Is Underutilized for Training
CISA's Known Exploited Vulnerabilities catalog contains **1,484 vulnerabilities** with 245 added in 2025 alone (20% growth). **20.5% of KEV vulnerabilities are linked to ransomware**. Yet this authoritative, structured, PII-free source is rarely used for AI training. It represents an immediately ingestible, high-evidence-strength dataset. [Research](./research/defendable_dim03_cyber_ai_risk.md)

### Discovery 4: Property/Contractor Pain Is a Fragmented Wasteland
Unlike consumer financial pain, there is **no central federal database for contractor complaints**. Data is fragmented across 50+ state licensing boards, municipal inspection offices, and court systems. This represents both a research gap and a product opportunity -- DefendableOS could become the first unified record system for this $400B+ industry. [Research](./research/defendable_dim04_property_contractor.md)

### Discovery 5: Counterfeit Hardware Reaches Military Systems
A DOJ-prosecuted counterfeit Cisco scheme generated **$100+ million in revenue** and reached **U.S. military fighter jets (F-15, F-22)**. Counterfeit electronics increased **25% in 2024** (highest since 2015). Singapore saw a **$390 million Nvidia chip smuggling case**. Hardware provenance verification is a critical, underserved market. [Research](./research/defendable_dim05_asset_compute.md)

### Discovery 6: AI Agent Risk Now Has a Standards Body Framework
NIST published the **AI RMF Agentic Profile** (May 2026), covering agent compromise, behavioral hijack, runaway agent, and delegation chain compromise. The Air Canada chatbot case (C$812 tribunal award) established precedent for **AI liability for hallucinated information**. LLM legal hallucination rates are **58-88%** (Stanford study). [Research](./research/defendable_dim06_ai_agent_trust.md)

---

## The 13 Deliverables

### For Founders & Strategists
| # | File | What It Contains |
|---|------|-----------------|
| 00 | [EXECUTIVE_MEMO.md](./deliverables/00_EXECUTIVE_MEMO.md) | One-page summary: opportunity, architecture, top products, risks |
| 11 | [PRODUCT_AND_AGENT_OPPORTUNITY_MAP.md](./deliverables/11_PRODUCT_AND_AGENT_OPPORTUNITY_MAP.md) | 16 scored product opportunities, build order, commercialization paths |
| 12 | [RESEARCH_GAPS_AND_NEXT_RUN.md](./deliverables/12_RESEARCH_GAPS_AND_NEXT_RUN.md) | What's missing, what to research next, 90-day plan |

### For Engineers & Data Scientists
| # | File | What It Contains |
|---|------|-----------------|
| 04 | [CORPUS_SCHEMA.json](./deliverables/04_CORPUS_SCHEMA.json) | Validated JSON Schema 2020-12 for all corpus records |
| 05 | [REAL_SEED_CORPUS.jsonl](./deliverables/05_REAL_SEED_CORPUS.jsonl) | 255 real records, source-grounded, PII-scrubbed |
| 06 | [DEFENSE_FIXER_LIBRARY.jsonl](./deliverables/06_DEFENSE_FIXER_LIBRARY.jsonl) | 115 reusable fixer objects with steps and evidence requirements |
| 07 | [SWARMCURATOR_EVAL_PACK.jsonl](./deliverables/07_SWARMCURATOR_EVAL_PACK.jsonl) | 157 eval examples testing 13 Curator capabilities |
| 08 | [SWARMJELLY_FAILURE_PACK.jsonl](./deliverables/08_SWARMJELLY_FAILURE_PACK.jsonl) | 151 hard/ambiguous examples for failure-mode testing |
| 10 | [DEFENDABLE_LEDGER_MANIFEST.json](./deliverables/10_DEFENDABLE_LEDGER_MANIFEST.json) | Provenance manifest with counts, distributions, SHA-256 placeholders |

### For Researchers & Auditors
| # | File | What It Contains |
|---|------|-----------------|
| 01 | [DEFENDABLE_ONTOLOGY.md](./deliverables/01_DEFENDABLE_ONTOLOGY.md) | Complete vocabulary: 13 top-level labels, 60+ subclasses, severity mappings |
| 02 | [SOURCE_REGISTRY.csv](./deliverables/02_SOURCE_REGISTRY.csv) | 172 sources with 23 metadata columns each |
| 03 | [SOURCE_RANKING_AND_ACQUISITION_PLAN.md](./deliverables/03_SOURCE_RANKING_AND_ACQUISITION_PLAN.md) | 7-dimension scoring, weighted rankings, ingestion pipeline |
| 09 | [STREETCHAT_SIGNAL_POLICY.md](./deliverables/09_STREETCHAT_SIGNAL_POLICY.md) | Community signal ingestion: PII rules, corroboration, promotion pathway |

---

## Severity Classification

This corpus uses the Defendable Tribunal classification system:

| Label | Meaning | Records | Ledger Status |
|-------|---------|---------|---------------|
| **HONEY** | Verified, highest quality, safe to ingest | 12 | Ledger-ready |
| **JELLY** | Messy/ambiguous, valuable for Curator testing | 46 | Context/discovery only |
| **PROPLOLIS** | Critical risk, strict handling required | 98 | Ledger-ready with review |
| **CRITICAL** | Highest risk, immediate attention | 99 | Ledger-ready with review |

**Note:** The mission's 4-tier system maps to the existing Tribunal taxonomy as: `honey -> HONEY`, `jelly -> JELLY` (in training context), `propolis -> JELLY` (in ledger context), `critical -> PROPOLIS`.

---

## Trust Tiers

| Tier | Level | Sources | Use |
|------|-------|---------|-----|
| **1** | Primary / Authoritative | 66 (38%) | Supports ledger-ready records |
| **2** | High-Quality Secondary | 105 (61%) | Contextual records and research hypotheses |
| **3** | Discovery Signal | 1 (<1%) | Emerging-language, pain-signal, investigation-lead only |
| **4** | Reject / Quarantine | 0 | Excluded or placed in rejected-source log |

---

## Top 5 Product Opportunities

| Rank | Product | Score | First Customer |
|------|---------|-------|---------------|
| 1 | Credit Repair Documentation Assistant | 8.46 | 34M Americans with credit errors |
| 2 | Consumer Dispute Assistant | 8.30 | CFPB complainants, billing dispute victims |
| 3 | Documentation & Certified-Letter Workflow | 8.16 | All product lanes (foundational) |
| 4 | Fraud-Defense Assistant | 8.12 | $20.8B annual fraud victims |
| 5 | Identity Theft Recovery Assistant | 8.10 | 1.1M+ annual identity theft victims |

See [full product map](./deliverables/11_PRODUCT_AND_AGENT_OPPORTUNITY_MAP.md) for scoring methodology, commercialization paths, and risk assessment.

---

## How to Use This Corpus

### Quick Start for ML Training
```python
import json

# Load seed corpus
records = []
with open('deliverables/05_REAL_SEED_CORPUS.jsonl', 'r') as f:
    for line in f:
        records.append(json.loads(line))

# Filter ledger-ready records only
ledger_ready = [r for r in records 
                if r['trust']['ledger_status'] == 'ledger_ready']

# Filter by lane
cyber_records = [r for r in records 
                 if r['research_lane'] == 'cyber_ai']

print(f"Total records: {len(records)}")
print(f"Ledger-ready: {len(ledger_ready)}")
print(f"Cyber/AI records: {len(cyber_records)}")
```

### Quick Start for Evaluation
```python
# Load SwarmCurator eval pack
evals = []
with open('deliverables/07_SWARMCURATOR_EVAL_PACK.jsonl', 'r') as f:
    for line in f:
        evals.append(json.loads(line))

# Test a specific capability
refusal_tests = [e for e in evals 
                 if 'refuse_overstate' in e.get('labels_to_test', [])]
print(f"Refusal/overclaiming tests: {len(refusal_tests)}")
```

### Validate Against Schema
```python
import json
from jsonschema import validate, Draft202012Validator

with open('deliverables/04_CORPUS_SCHEMA.json', 'r') as f:
    schema = json.load(f)

# Validate the schema itself
Draft202012Validator.check_schema(schema)

# Validate a record
with open('deliverables/05_REAL_SEED_CORPUS.jsonl', 'r') as f:
    first_record = json.loads(f.readline())
    validate(first_record, schema)
```

---

## Schema Quick Reference

Every corpus record contains these top-level sections:

```json
{
  "record_id": "REC-FIN-0001",
  "corpus_version": "defendable-offense-pain-fixer-v0.1",
  "created_at": "2026-05-25T00:00:00Z",
  "research_lane": "consumer_financial",
  "source": { /* source provenance */ },
  "classification": {
    "offense_signal": { /* what happened */ },
    "pain_receipt": { /* who was harmed, how */ },
    "defense_fixer": { /* what fixer applies */ }
  },
  "severity": { /* severity_label, score, rationale */ },
  "trust": { /* ledger_status, confidence, corroboration */ },
  "curator_training": { /* training/eval suitability flags */ },
  "privacy_and_safety": { /* PII flags, storage safety */ }
}
```

See [full schema](./deliverables/04_CORPUS_SCHEMA.json) for complete field definitions, enums, and validations.

---

## Research Methodology

This corpus was built using a **multi-agent deep research swarm** with the following methodology:

1. **6 parallel research lanes**, each investigated by a specialized agent
2. **60+ independent web searches** across government databases, regulatory filings, enforcement actions, and standards publications
3. **10+ searches per lane**, coarse-to-fine progression
4. **Primary sources prioritized**: government datasets > official reports > investigative journalism > community signal
5. **No synthetic incidents**: every record traces to a verifiable public source
6. **PII scrubbed**: all personal identifiers removed before inclusion
7. **Trust tier assigned**: every source classified by authority level
8. **Cross-verification**: findings validated across multiple independent sources

### Research Lanes

| Lane | Focus | Key Sources | Records |
|------|-------|-------------|---------|
| 1 | Consumer Financial Pain | CFPB, FTC, State AGs | 52 |
| 2 | Fraud & Digital Loss | FBI IC3, SEC, CFTC | 50 |
| 3 | Cyber & AI System Risk | CISA, NVD, MITRE, NIST | 50 |
| 4 | Property & Contractor | State Boards, Courts | 28 |
| 5 | Asset & Compute | FTC, CPSC, DOJ | 35 |
| 6 | AI Agent Trust | NIST, EU AI Act, OECD | 40 |

---

## StreetChat Policy Summary

Community signals (Tier 3) must pass through a **5-stage extraction pipeline** before use:

1. **Intake** -- Raw community post enters system
2. **Pre-Screen** -- Automated spam/malware detection
3. **Redaction** -- PII stripping (16 mandatory categories)
4. **Pattern Extraction** -- Generalized pain patterns extracted, personal narrative discarded
5. **Tribunal Classification** -- SwarmCurator assigns Honey/Jelly/Propolis label

**Promotion rules**: Tier 3 -> Tier 2 requires dual-authorization corroboration. Tier 2 -> Tier 1 requires institutional confirmation. StreetChat-derived patterns **must never** be presented as verified facts without independent Tier 1 evidence.

See [full policy](./deliverables/09_STREETCHAT_SIGNAL_POLICY.md).

---

## Next Steps

### Immediate (Weeks 1-4)
- [ ] Ingest CFPB Consumer Complaint Database via API (5,000+ records)
- [ ] Ingest CISA KEV Catalog (1,484 vulnerabilities)
- [ ] Build production ingestion pipeline
- [ ] Validate SwarmCurator against eval pack (target: >85% accuracy)

### Short-term (Months 2-4)
- [ ] Build Credit Repair Documentation Assistant prototype
- [ ] Second research run: 1,000+ records with API-based ingestion
- [ ] Open Lane 4 (Property/Contractor) with state-by-state manual research
- [ ] Implement StreetChat redaction pipeline

### Medium-term (Months 4-12)
- [ ] Launch Consumer Dispute Assistant (free tier)
- [ ] Build cross-lane entity linking
- [ ] Expand to 10,000+ ledger-ready records
- [ ] Professional service tier for fraud-defense and identity recovery

See [Research Gaps & Next Run](./deliverables/12_RESEARCH_GAPS_AND_NEXT_RUN.md) for full plan.

---

## Legal & Trust

- No private personal information is included in this corpus
- All records are sourced from publicly available materials
- Allegations are clearly distinguished from adjudicated findings
- StreetChat/community signals are Tier 3 by default and marked accordingly
- Synthetic incidents were not created and not presented as real
- Operational instructions facilitating wrongdoing are excluded

See [Source Registry](./deliverables/02_SOURCE_REGISTRY.csv) for source-specific licensing notes and [StreetChat Policy](./deliverables/09_STREETCHAT_SIGNAL_POLICY.md) for data handling rules.

---

## Related DefendableOS Repositories

| Repository | Purpose |
|-----------|---------|
| [defendable-docs](https://github.com/SudoSuOps/defendable-docs) | Documentation site (docs.defendableos.com) |
| [defendableos-swarm-research](https://github.com/SudoSuOps/defendableos-swarm-research) | This repo -- research corpus |
| [defendableos.com](https://defendableos.com) | Main site |
| [OpenDefense](https://defendableos.com/opendefense) | Market intelligence |

---

## Citation

If you use this corpus in research or product development:

```
DefendableOS Deep Research Swarm (2026).
Offense Signals, Pain Receipts & Defense Fixers Corpus v0.1.
https://github.com/SudoSuOps/defendableos-swarm-research
```

---

## License

The corpus data and schemas are provided under the terms documented in the [Source Registry](./deliverables/02_SOURCE_REGISTRY.csv). Individual source licensing varies; see the `terms_or_reuse_notes` column per source. Government data (CFPB, CISA KEV, FBI IC3 reports, NIST publications) is generally public domain. Secondary sources may require attribution.

---

> **Tribunal Verdict: HONEY -- Approved for ingestion and product development.**
>
> *Operator-grade -- books and records -- to the shed.*
>
> See [VERDICT.md](./docs/VERDICT.md) for the full tribunal determination.
