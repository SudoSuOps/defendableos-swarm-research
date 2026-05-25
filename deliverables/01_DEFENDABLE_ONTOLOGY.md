# DefendableOS Ontology v1.0

## Canonical Vocabulary System for Offense Signals, Pain Receipts, and Defense Fixers

**Version:** 1.0.0
**Date:** May 25, 2026
**Status:** Canonical
**Classification:** DefendableOS Core Schema

---

## Table of Contents

1. [Ontology Overview](#1-ontology-overview)
2. [Parent Classes](#2-parent-classes)
3. [Subclasses by Domain Lane](#3-subclasses-by-domain-lane)
4. [Severity Classification](#4-severity-classification)
5. [Trust Tier System](#5-trust-tier-system)
6. [Status Taxonomy](#6-status-taxonomy)
7. [Example Fact Patterns](#7-example-fact-patterns)
8. [Example Fixer Pathways](#8-example-fixer-pathways)
9. [Uncertainty, Contradiction & Missing Proof Labels](#9-uncertainty-contradiction--missing-proof-labels)
10. [Schema Field Cross-Reference](#10-schema-field-cross-reference)

---

## 1. Ontology Overview

### 1.1 Purpose

The DefendableOS Ontology provides a canonical vocabulary system for classifying, labeling, and routing harm-related signals through a structured pipeline of detection, documentation, verification, and remediation. It is designed to serve engineers, auditors, researchers, and automated systems operating within the DefendableOS ecosystem.

The ontology harmonizes with the existing Tribunal classification system (HONEY, ROYAL_JELLY, JELLY, PROPOLIS) and extends it with a domain-specific vocabulary grounded in empirical research across six harm domains.

### 1.2 Scope

| Dimension | Coverage |
|-----------|----------|
| **Lane 1: Consumer Financial** | CFPB complaints, credit reporting, debt collection, mortgage servicing, overdraft fees, identity theft |
| **Lane 2: Fraud & Digital Loss** | BEC, crypto fraud, investment scams, romance scams, deepfakes, ransomware, synthetic identity |
| **Lane 3: Cyber & AI System Risk** | Vulnerabilities, ransomware, APT activity, prompt injection, AI agent safety, data breaches |
| **Lane 4: Property & Contractor** | Workmanship failures, contractor nonperformance, unlicensed contracting, warranty disputes, lien abuse |
| **Lane 5: Asset & Compute** | Counterfeit hardware, supply chain fraud, return fraud, chip smuggling, data center risk |
| **Lane 6: AI Agent Trust** | Hallucination, algorithmic bias, agent autonomy failures, deepfake fraud, vendor liability gaps |

### 1.3 Design Principles

| Principle | Description |
|-----------|-------------|
| **Signal-Driven** | Every entry must trace to a documented or plausibly alleged pattern of harm, not theoretical risk |
| **Evidence-Anchored** | Labels require at minimum a SOURCE_RECEIPT; preferred is a VERIFIED_FINDING |
| **Severity-Native** | All signals carry a severity classification at creation, mapping to the Tribunal 4-tier system |
| **Status-Aware** | Every entry progresses through a defined status lifecycle (alleged -> reported -> verified/adjudicated) |
| **Fixer-Mapped** | Every OFFENSE_SIGNAL must have at least one associated DEFENSE_FIXER path |
| **Uncertainty-Explicit** | Gaps, contradictions, and missing proofs are first-class labels, not afterthoughts |
| **Cross-Lane Composable** | Signals may span multiple lanes; composite labels are explicitly supported |
| **Tribunal-Aligned** | The ontology is the canonical vocabulary for the Tribunal system's HONEY/ROYAL_JELLY/JELLY/PROPOLIS classifications |

### 1.4 Core Axioms

1. **An OFFENSE_SIGNAL without a PAIN_RECEIPT is an unverified allegation.**
2. **A PAIN_RECEIPT without a DEFENSE_FIXER is an unresolved harm.**
3. **A DEFENSE_FIXER without a LEDGER_READY proof package is an undocumented claim.**
4. **All labels degrade to JELLY or lower when CONTRADICTION is present.**
5. **HUMAN_REVIEW is required before any signal is promoted to HONEY.**

---

## 2. Parent Classes

### 2.1 Top-Level Taxonomy

```
DEFENDABLE_ENTITY
├── OFFENSE_SIGNAL
├── PAIN_RECEIPT
├── DEFENSE_FIXER
├── SOURCE_RECEIPT
├── PROOF_GAP
├── CONTRADICTION
├── HUMAN_REVIEW
├── QUARANTINED_SIGNAL
├── VERIFIED_FINDING
├── ALLEGED_HARM
├── RESOLUTION_PATH
├── LEDGER_READY
└── NOT_LEDGER_READY
```

### 2.2 Class Definitions

#### OFFENSE_SIGNAL

A documented or alleged pattern that may create harm, unfairness, loss, deception, breach, manipulation, unsafe operation, unverified value, failed duty, exploitability, or untrustworthy conduct.

| Attribute | Type | Description |
|-----------|------|-------------|
| `signal_id` | UUID | Canonical identifier (e.g., `OS-FIN-001-A`) |
| `signal_class` | Enum | Category of offense (see Lane subclasses) |
| `description` | String | Human-readable pattern description |
| `severity` | Enum | HONEY / ROYAL_JELLY / JELLY / PROPOLIS |
| `status` | Enum | alleged / reported / admitted / settled / adjudicated / verified_technical / aggregate_only / unknown |
| `affected_domain` | Enum[] | One or more of Lane 1-6 |
| `evidence_count` | Integer | Number of supporting SOURCE_RECEIPT entries |
| `dollar_magnitude` | Decimal | Estimated or confirmed financial impact |
| `first_observed` | Date | Earliest documented occurrence |
| `last_confirmed` | Date | Most recent confirmed occurrence |
| `repeat_offender` | Boolean | Whether the same actor has been cited before |

#### PAIN_RECEIPT

Evidence showing how the offense signal affects a person, business, property, asset, system, market, or transaction.

| Attribute | Type | Description |
|-----------|------|-------------|
| `receipt_id` | UUID | Canonical identifier (e.g., `PR-FIN-001`) |
| `parent_signal` | FK | Reference to originating OFFENSE_SIGNAL |
| `receipt_type` | Enum | Monetary / Operational / Reputational / Physical / Psychological / Regulatory |
| `affected_party` | String | Who experienced the pain (consumer, business, system) |
| `evidence_source` | FK | Reference to SOURCE_RECEIPT |
| `quantified_impact` | Decimal | Measured or estimated harm amount |
| `impact_units` | String | USD, records, days, percent, etc. |
| `attribution_confidence` | Enum | confirmed / probable / possible / unverified |

#### DEFENSE_FIXER

A remedy, control, verification process, evidence package, operating procedure, legal/regulatory path, technical mitigation, monitoring workflow, appraisal method, or escalation mechanism.

| Attribute | Type | Description |
|-----------|------|-------------|
| `fixer_id` | UUID | Canonical identifier (e.g., `DF-FIN-001`) |
| `fixer_class` | Enum | Prevention / Detection / Response / Recovery / Policy / Governance / Technical |
| `applicable_signals` | FK[] | Array of OFFENSE_SIGNAL references |
| `effectiveness_evidence` | String | Documentation of proven or estimated effectiveness |
| `implementation_cost` | String | Low / Medium / High / Variable |
| `time_to_effect` | String | Immediate / Hours / Days / Weeks / Months |
| `requires_human` | Boolean | Whether human intervention is required |
| `automation_level` | Enum | Fully_Automated / Semi_Automated / Manual |

#### SOURCE_RECEIPT

An evidentiary artifact documenting the origin, provenance, and trustworthiness of a claim.

| Attribute | Type | Description |
|-----------|------|-------------|
| `source_id` | UUID | Canonical identifier |
| `source_tier` | Integer | 1 (Primary) / 2 (Secondary) / 3 (Tertiary) |
| `source_type` | Enum | Government_DB / Court_Record / Regulatory_Action / Academic_Paper / Industry_Report / News_Media / Consumer_Report / Technical_Analysis / whistleblower |
| `url` | String | Permanent URL or archive link |
| `access_date` | Date | When the source was last verified |
| `corpus_score` | Integer | 0-10 fitness score for DefendableOS corpus inclusion |

#### PROOF_GAP

An explicitly identified missing piece of evidence that, if obtained, would strengthen or change the classification of a signal.

| Attribute | Type | Description |
|-----------|------|-------------|
| `gap_id` | UUID | Canonical identifier |
| `parent_signal` | FK | Reference to the signal with the gap |
| `missing_evidence` | String | Description of what is missing |
| `gap_severity` | Enum | blocks_promotion / weakens_claim / nice_to_have |
| `estimated_obtainable` | Boolean | Whether the evidence is realistically obtainable |

#### CONTRADICTION

An explicit conflict between two or more sources, claims, or findings related to the same signal.

| Attribute | Type | Description |
|-----------|------|-------------|
| `contradiction_id` | UUID | Canonical identifier |
| `signal_a` | FK | First conflicting signal or source |
| `signal_b` | FK | Second conflicting signal or source |
| `contradiction_type` | Enum | source_conflict / stakeholder_dispute / temporal_drift / jurisdictional_split |
| `resolution_status` | Enum | unresolved / partially_resolved / resolved |
| `severity_impact` | Enum | demotes_to_jelly / demotes_to_propolis / no_change |

#### HUMAN_REVIEW

A structured human evaluation required before promotion of a signal to higher trust tiers.

| Attribute | Type | Description |
|-----------|------|-------------|
| `review_id` | UUID | Canonical identifier |
| `subject_signal` | FK | Signal under review |
| `reviewer_role` | Enum | auditor / engineer / domain_expert / legal / tribunal |
| `review_type` | Enum | promotion_review / contradiction_resolution / gap_assessment / de_escalation |
| `outcome` | Enum | promote / demote / hold / quarantine |

#### QUARANTINED_SIGNAL

A signal placed in a restricted state pending further evidence, review, or contradiction resolution.

| Attribute | Type | Description |
|-----------|------|-------------|
| `quarantine_id` | UUID | Canonical identifier |
| `subject_signal` | FK | Signal in quarantine |
| `quarantine_reason` | Enum | insufficient_evidence / active_contradiction / pending_litigation / source_unverified / pii_risk |
| `review_date` | Date | Scheduled review date |
| `auto_expire` | Date | Automatic expiration of quarantine |

#### VERIFIED_FINDING

A signal that has been independently confirmed through primary authority sources, adjudication, or technical verification.

| Attribute | Type | Description |
|-----------|------|-------------|
| `finding_id` | UUID | Canonical identifier |
| `parent_signal` | FK | Signal being verified |
| `verification_method` | Enum | court_order / regulatory_action / technical_exploit / independent_audit / replicated_research |
| `verifying_authority` | String | Who performed the verification |
| `verification_date` | Date | When verification occurred |

#### ALLEGED_HARM

A preliminary classification for harm patterns reported by affected parties but not yet supported by independent evidence.

| Attribute | Type | Description |
|-----------|------|-------------|
| `allegation_id` | UUID | Canonical identifier |
| `reporter_type` | Enum | consumer / whistleblower / journalist / researcher / automated_system |
| `report_date` | Date | When the allegation was made |
| `escalation_trigger` | String | Condition that would elevate from ALLEGED_HARM to OFFENSE_SIGNAL |

#### RESOLUTION_PATH

A documented sequence from signal detection through fixer application to outcome.

| Attribute | Type | Description |
|-----------|------|-------------|
| `path_id` | UUID | Canonical identifier |
| `start_signal` | FK | Origin signal |
| `fixer_chain` | FK[] | Ordered array of DEFENSE_FIXER references |
| `actual_outcome` | String | What actually happened |
| `outcome_status` | Enum | resolved / partial / failed / ongoing |

#### LEDGER_READY

A status indicating a signal and its associated receipts, fixers, and evidence are complete enough for Tribunal ledger inclusion.

| Attribute | Type | Description |
|-----------|------|-------------|
| `ledger_id` | UUID | Canonical identifier |
| `completeness_score` | Integer | 0-100 percent complete |
| `required_fields` | String[] | List of fields that must be populated |

#### NOT_LEDGER_READY

A status indicating a signal cannot be included in the Tribunal ledger due to missing required fields, unresolved contradictions, or insufficient evidence.

| Attribute | Type | Description |
|-----------|------|-------------|
| `blocker_id` | UUID | Canonical identifier |
| `blocker_reason` | Enum | missing_fields / proof_gap_open / contradiction_active / below_threshold / pii_unresolved |
| `unblock_conditions` | String[] | Specific conditions required to reach LEDGER_READY |

---

## 3. Subclasses by Domain Lane

### 3.1 Lane 1: Consumer Financial Pain

**Scope:** Banking, credit reporting, debt collection, mortgage servicing, payment networks, student loans, investment fraud

#### Lane 1 OFFENSE_SIGNAL Subclasses

| Signal ID | Signal Name | Description | Key Magnitude |
|-----------|-------------|-------------|---------------|
| `OS-FIN-001` | Credit Reporting Errors | Inaccurate, incomplete, or unverified info on credit reports; dispute investigation failures | 5.8M complaints (2025) |
| `OS-FIN-002` | Surprise Overdraft Fees | Overdraft fees on transactions with sufficient funds at authorization; NSF double-dipping | $141M (Regions); $80M (Navy Fed) |
| `OS-FIN-003` | Debt Collection Abuses | Phantom debt, threats, harassment, attempts to collect debts not owed | 387,400 complaints (2025) |
| `OS-FIN-004` | Mortgage Servicing Violations | Foreclosure protection failures, kickbacks, redlining, PACE loan abuse | $3M+ redress per case |
| `OS-FIN-005` | Account Mishandling | Unauthorized account opening, account freezing, reward withholding | $3.7B (Wells Fargo) |
| `OS-FIN-006` | Interest Rate Manipulation | Freezing rates on legacy accounts while offering higher rates on new products | $2B alleged (Capital One) |
| `OS-FIN-007` | Payment Network Fraud | Failure to protect consumers from fraud on P2P networks; inadequate reimbursement | "Hundreds of millions" (Zelle) |
| `OS-FIN-008` | Student Loan Servicing Abuse | Misleading repayment info, botched processing, cosigner release deception | $120M (Navient) |
| `OS-FIN-009` | Investment/Imposter Scams | Investment scams, imposter scams targeting consumers via social media/phone | $5.7B + $2.95B (FTC 2024) |
| `OS-FIN-010` | Identity Theft | Misuse of personal information to open accounts, make fraudulent purchases | 1.1M reports (FTC 2024) |

#### Lane 1 PAIN_RECEIPT Subclasses

| Receipt ID | Receipt Type | Evidence Form |
|------------|-------------|---------------|
| `PR-FIN-001` | Direct Monetary Loss — Fees | Consent order dollar amounts, refund totals |
| `PR-FIN-002` | Direct Monetary Loss — Fraud/Theft | FTC Sentinel loss data, IC3 complaint losses |
| `PR-FIN-003` | Credit Score Damage | Denied applications, FICO score changes, dispute records |
| `PR-FIN-004` | Account Freezing/Access Denial | Consumer narratives, bank response data |
| `PR-FIN-005` | Home Loss (Foreclosure) | Foreclosure filings, RESPA violations, redress amounts |
| `PR-FIN-006` | Vehicle Loss (Repossession) | Repossession records, CFPB complaint volume (+124% 2025) |
| `PR-FIN-007` | Time and Administrative Burden | Resolution timelines, dispute attempt counts |
| `PR-FIN-008` | Psychological Stress | Consumer narrative text, employee testimony |
| `PR-FIN-009` | Identity Compromise | Identity theft reports, breach notification letters |
| `PR-FIN-010` | Lost Opportunities | Missed refinancing, employment denials, home sales blocked |

#### Lane 1 DEFENSE_FIXER Subclasses

| Fixer ID | Fixer Name | When It Applies |
|----------|-----------|-----------------|
| `DF-FIN-001` | CFPB Complaint Filing | Consumer has dispute with financial company; direct resolution failed |
| `DF-FIN-002` | CRA Direct Dispute (FCRA 611) | Consumer finds inaccurate info on credit report |
| `DF-FIN-003` | IdentityTheft.gov Reporting | Identity stolen; need recovery plan and credit freeze |
| `DF-FIN-004` | FTC Fraud Reporting | Consumer lost money to scam |
| `DF-FIN-005` | Civil Penalty Fund Redress | Harmed by company subject to CFPB enforcement |
| `DF-FIN-006` | FTC Redress/Refund Programs | Harmed by company subject to FTC settlement |
| `DF-FIN-007` | NSF Fee Elimination | Consumer charged NSF fees; bank policy change |
| `DF-FIN-008` | Credit Freeze/Lock | Consumer suspects identity theft |
| `DF-FIN-009` | MLA Protections | Active-duty military and dependents; 36% rate cap |
| `DF-FIN-010` | FBI Financial Fraud Kill Chain | High-dollar fraud losses; IC3 Recovery Asset Team |

---

### 3.2 Lane 2: Fraud, Impersonation & Digital Loss

**Scope:** Business email compromise, cryptocurrency fraud, investment scams, deepfake fraud, romance scams, ransomware, synthetic identity, account takeover

#### Lane 2 OFFENSE_SIGNAL Subclasses

| Signal ID | Signal Name | Description | Key Magnitude |
|-----------|-------------|-------------|---------------|
| `OS-FRD-001` | Investment Fraud | Cryptocurrency, social media, pig butchering, Ponzi schemes | $8.649B (IC3 2025) |
| `OS-FRD-002` | Impersonation & BEC | Business email compromise, CEO fraud, vendor compromise, government impersonation | $3.046B (IC3 2025) |
| `OS-FRD-003` | AI-Enabled Fraud | Deepfake video, voice clone, AI-nexus BEC, synthetic media identity bypass | $893M + $1.1B deepfake |
| `OS-FRD-004` | Identity Fraud | Synthetic identity, account takeover, identity theft, credential stuffing | $2.9B ATO; 80%+ new account fraud |
| `OS-FRD-005` | Extortion & Ransomware | Ransomware attacks, double extortion, critical infrastructure targeting | $32.32M (+259%); 3,611 reports |
| `OS-FRD-006` | Social Engineering | Romance scams, social media fraud platforms, elder-targeted scams, phishing | $1.2B romance; $7.7B elder |

#### Lane 2 PAIN_RECEIPT Subclasses

| Receipt ID | Receipt Type | Evidence Form |
|------------|-------------|---------------|
| `PR-FRD-001` | Aggregate Financial Damage | IC3 annual totals, FTC Sentinel aggregates |
| `PR-FRD-002` | Enterprise Financial Loss | Single-incident BEC amounts, wire fraud totals |
| `PR-FRD-003` | Operational + Business Disruption | Ransomware downtime, system unavailability |
| `PR-FRD-004` | Massive Individual Losses | Per-victim pig butchering amounts ($100K+ avg) |
| `PR-FRD-005` | Psychological + Financial Devastation | Victim testimony, romance scam reports |
| `PR-FRD-006` | Multi-Modal Deception | Deepfake incident reports, detection failures |
| `PR-FRD-007` | National Security Risk | Critical infrastructure attacks, Salt Typhoon |
| `PR-FRD-008` | Elder Financial Exploitation | Age-disproportionate losses, FTC elder reports |
| `PR-FRD-009` | Platform-Facilitated Mass Victimization | Social media scam volume, platform inaction |
| `PR-FRD-010` | Detection Failure | Sophisticated fraud rates, bypass metrics |
| `PR-FRD-011` | Enforcement Gap | DOJ prosecutions vs. reported losses ratio |
| `PR-FRD-012` | Cross-Sector Identity Abuse | Identity fraud in telecom, insurance, gambling |

#### Lane 2 DEFENSE_FIXER Subclasses

| Fixer ID | Fixer Name | When It Applies |
|----------|-----------|-----------------|
| `DF-FRD-P01` | Multi-Factor Authentication | All email, financial, admin accounts |
| `DF-FRD-P02` | Email Authentication (DMARC/SPF/DKIM) | Prevent email spoofing and domain impersonation |
| `DF-FRD-P03` | Vendor Verification Protocols | Out-of-band verification for payment changes |
| `DF-FRD-P04` | Deepfake Detection Software | Video/voice call verification |
| `DF-FRD-P05` | Credit Freezes | Prevent synthetic identity creation |
| `DF-FRD-D01` | BEC Email Analysis Tools | AI-powered email content/sender analysis |
| `DF-FRD-D02` | Account Anomaly Detection | Behavioral analytics for ATO patterns |
| `DF-FRD-D03` | Dark Web Monitoring | Monitor for exposed credentials |
| `DF-FRD-R01` | Financial Fraud Kill Chain | IC3 Recovery Asset Team rapid freeze |
| `DF-FRD-R02` | FBI IC3 Reporting | File complaint at ic3.gov |
| `DF-FRD-R03` | Operation Level Up | FBI proactive victim notification for crypto fraud |
| `DF-FRD-R04` | Incident Response Plan | Documented ransomware response procedures |
| `DF-FRD-R05` | Decryption Key Distribution | FBI-provided ransomware decryption keys |
| `DF-FRD-C01` | FTC Consumer Refunds | Government-mandated scam restitution |
| `DF-FRD-C02` | Cyber Insurance | Financial protection against ransomware |
| `DF-FRD-POL01` | SEC Cyber & Emerging Technologies Unit | Crypto/AI fraud enforcement |
| `DF-FRD-POL02` | FTC Pass It On Campaign | Elder fraud prevention education |
| `DF-FRD-POL03` | Nacha Rules Updates | BEC prevention rules taking effect 2026 |

---

### 3.3 Lane 3: Cyber & AI System Risk

**Scope:** Known exploited vulnerabilities, critical RCEs, ransomware ecosystems, AI prompt injection, nation-state APTs, data poisoning, vishing, AI agent safety

#### Lane 3 OFFENSE_SIGNAL Subclasses

| Signal ID | Signal Name | Description | Key Magnitude |
|-----------|-------------|-------------|---------------|
| `OS-CYB-001` | Known Exploited Vulnerability Growth | CISA KEV catalog accumulation; weaponized CVEs | 1,484 KEV entries; ~50K CVEs/yr |
| `OS-CYB-002` | Critical RCE Vulnerabilities | Weaponized remote code execution pre-patch | Multiple CVSS 10.0 (2025) |
| `OS-CYB-003` | Ransomware Ecosystem Evolution | RaaS, targeted social engineering, double extortion | $32.32M losses (+259%) |
| `OS-CYB-004` | AI Prompt Injection & Jailbreaking | Direct/indirect prompt injection; universal attacks | ASR 0.5%-8.5% across models |
| `OS-CYB-005` | Nation-State APT Escalation | China-nexus espionage; telecom/infrastructure targeting | 150% increase across sectors |
| `OS-CYB-006` | AI Data & Model Poisoning | Training data corruption; sleeper agents; RAG poisoning | 0.001% token poisoning effective |
| `OS-CYB-007` | Vishing & Social Engineering | Voice phishing; help desk impersonation; AI-enhanced | 442% increase H1-H2 2024 |
| `OS-CYB-008` | AI Agent Safety Gap | L4-L5 autonomy without safety evaluations | 63% orgs lack AI governance |

#### Lane 3 PAIN_RECEIPT Subclasses

| Receipt ID | Receipt Type | Evidence Form |
|------------|-------------|---------------|
| `PR-CYB-001` | Mass Records Exposure | Breach notification letters, HHS OCR data |
| `PR-CYB-002` | Healthcare System Disruption | Hospital delays, appointment cancellations |
| `PR-CYB-003` | Ransom Payment + Recovery Costs | Coveware data, incident response costs |
| `PR-CYB-004` | National Security Compromise | Classified access, surveillance data theft |
| `PR-CYB-005` | Supply Chain Cascade Impact | Downstream victim counts, vendor breach cascades |
| `PR-CYB-006` | Regulatory/Legal Liability | HIPAA fines, state AG actions |
| `PR-CYB-007` | AI System Compromise | Data exfiltration via prompt injection |
| `PR-CYB-008` | Reputational + Market Value Loss | Stock price impact, customer churn |
| `PR-CYB-009` | Operational Downtime | Measured in hours/days of service unavailability |
| `PR-CYB-010` | Patient Safety Impact | Deaths attributed to system unavailability |
| `PR-CYB-011` | Shadow AI Breach Premium | +$670K average breach cost |
| `PR-CYB-012` | Credential Mass Exposure | API keys, plaintext passwords in agent systems |

#### Lane 3 DEFENSE_FIXER Subclasses

| Fixer ID | Fixer Name | When It Applies |
|----------|-----------|-----------------|
| `DF-CYB-001` | CISA KEV Catalog Prioritization | Federal remediation requirements |
| `DF-CYB-002` | Secure by Design Pledge | Manufacturer security commitments |
| `DF-CYB-003` | Rapid Patch Management | Negative-one-day exploitation timelines |
| `DF-CYB-004` | Ransomware Defense Suite | Immutable backups, network segmentation, offline backups |
| `DF-CYB-005` | AI Governance Framework | NIST AI RMF + Agentic Profile |
| `DF-CYB-006` | OWASP LLM Top 10 Controls | LLM application security framework |
| `DF-CYB-007` | Prompt Injection Defenses | Architectural isolation, sandboxing |
| `DF-CYB-008` | MITRE ATT&CK Framework | Threat-informed defense |
| `DF-CYB-009` | Behavior-Based EDR | Malware-free attack detection |
| `DF-CYB-010` | AI Agent Safety Architecture | Privilege separation, approval gates |
| `DF-CYB-011` | Data-Centric Protection | Tokenization, P2PE encryption |
| `DF-CYB-012` | Healthcare-Specific Hardening | Third-party monitoring, PHI encryption |

---

### 3.4 Lane 4: Property & Contractor

**Scope:** Contractor nonperformance, workmanship failures, unlicensed contracting, warranty disputes, mechanics lien abuse, post-disaster fraud, inspection failures

#### Lane 4 OFFENSE_SIGNAL Subclasses

| Signal ID | Signal Name | Description | Key Magnitude |
|-----------|-------------|-------------|---------------|
| `OS-PRP-001` | Improper/Substandard Workmanship | Work below contractual or code standards; defective materials | $10.1M avg commercial claim (TX) |
| `OS-PRP-002` | Contractor Nonperformance/Abandonment | Payment taken, work not performed or abandoned | #1 complaint category (IL AG) |
| `OS-PRP-003` | Unlicensed Contracting | Work performed without required licenses; no insurance/bond | 100+ arrests (FL post-hurricane) |
| `OS-PRP-004` | Deceptive Financing/Predatory Lending | High-pressure tactics, forged liens, deceptive loan terms | $2.9M refunds (Ygrene) |
| `OS-PRP-005` | Home Warranty Claim Denials | Systematic denial of legitimate claims; fine-print exclusions | 49% claim satisfaction |
| `OS-PRP-006` | Mechanics Lien Abuse | Improper lien filings; retaliatory liens; payment disputes | Elevated in TX, FL, CA, GA, NV |
| `OS-PRP-007` | Failed Inspections/Permit Violations | Work without permits; code violations; "rented qualifiers" | 106 stop orders (CSLB sweeps) |
| `OS-PRP-008` | Post-Disaster Fraud | Exploitation after natural disasters; emergency repair scams | 100+ arrests, 150+ charges (FL) |

#### Lane 4 PAIN_RECEIPT Subclasses

| Receipt ID | Receipt Type | Evidence Form |
|------------|-------------|---------------|
| `PR-PRP-001` | Direct Financial Loss — Excess Payments | Deposit losses, overcharges, refund amounts |
| `PR-PRP-002` | Repair and Remediation Costs | Cost to fix defective work; replacement expenses |
| `PR-PRP-003` | Legal Fees and Dispute Costs | Litigation expenses; attorney fees |
| `PR-PRP-004` | Property Damage and Diminished Value | Physical damage; reduced property value |
| `PR-PRP-005` | Time and Opportunity Costs | Project delays; backlog (5,375 CSLB complaints) |

#### Lane 4 DEFENSE_FIXER Subclasses

| Fixer ID | Fixer Name | When It Applies |
|----------|-----------|-----------------|
| `DF-PRP-001` | Pre-Hiring Verification Protocol | License, insurance, bonding, reference checks |
| `DF-PRP-002` | Contract Documentation & Compliance | Written contracts meeting statutory requirements |
| `DF-PRP-003` | Payment Protection and Escrow | Milestone-based payments; credit card deposits |
| `DF-PRP-004` | Evidence Preservation Package | Photo/video documentation; correspondence records |
| `DF-PRP-005` | Regulatory Complaint Pathways | CSLB, AG, FTC, CFPB, BBB complaint hierarchy |
| `DF-PRP-006` | Post-Disaster Specific Protections | Heightened vigilance; multi-agency sting models |
| `DF-PRP-007` | Lien Dispute Resolution | Lien waivers; attorney consultation; payment proof |
| `DF-PRP-008` | Insurance Claim Documentation | Damage photos; independent estimates; policy review |

---

### 3.5 Lane 5: Asset & Compute

**Scope:** Counterfeit hardware, supply chain infiltration, return fraud, chip smuggling, data center risk, proof-of-value verification

#### Lane 5 OFFENSE_SIGNAL Subclasses

| Signal ID | Signal Name | Description | Key Magnitude |
|-----------|-------------|-------------|---------------|
| `OS-AST-001` | Counterfeit/Re-marked Dies | Authentic-looking products with re-marked chips | RTX 4090 w/ RTX 3080 Ti die |
| `OS-AST-002` | Shell/Empty Product Fraud | Genuine packaging with no functional silicon | Fake AMD 9800X3D, no die |
| `OS-AST-003` | Component Stripping/Return Fraud | Working products stripped of valuable components, then returned | $4,000 RTX 5090 stripped |
| `OS-AST-004` | Fake Specifications/Misrepresentation | Products marketed with misleading specs/capabilities | Counterfeit Cisco in military |
| `OS-AST-005` | Franken-hardware Assembly | Devices assembled from broken/mismatched components | Fried RTX 4080 as RTX 4090 |
| `OS-AST-006` | Supply Chain Return Fraud Poisoning | Fraudulent returns re-entering supply chain as "new" | Amazon fake CPU resold |
| `OS-AST-007` | Organized Refund Fraud | Criminal rings obtaining fraudulent refunds while keeping items | REKK: $2.4M judgment |
| `OS-AST-008` | Grey Market/Unauthorized Channel Infiltration | Counterfeit products through unauthorized resellers | State Dept OIG fraud alert |
| `OS-AST-009` | Relabeling Older Hardware as New | Older devices modified to appear as newer models | Pro Network $100M Cisco fraud |
| `OS-AST-010` | eBay Shipping Address Scam | Scammers intercepting shipments via forwarding addresses | GPU shipping scams |
| `OS-AST-011` | Fake Benchmark/Test Results | Falsified performance data supporting inflated claims | Marketplace listing fraud |
| `OS-AST-012` | Chip Smuggling/Export Control Evasion | Large-scale diversion of controlled semiconductors | $390M Nvidia chip smuggling |

#### Lane 5 PAIN_RECEIPT Subclasses

| Receipt ID | Receipt Type | Evidence Form |
|------------|-------------|---------------|
| `PR-AST-001` | Direct Financial Loss from Bad Purchases | Purchase price, dispute resolution costs |
| `PR-AST-002` | Data Center Outage Costs | $100K-$1M+ per outage; 54% exceed $100K |
| `PR-AST-003` | Operational Downtime/Reputational Damage | Service disruption; business continuity loss |
| `PR-AST-004` | Chargeback and Fraud Management Costs | $35 per $100 in disputes; $100B chargebacks (2025) |
| `PR-AST-005` | Network Security Compromise from Counterfeit HW | Firmware vulnerabilities; backdoors |
| `PR-AST-006` | National Security Supply Chain Compromise | Military systems compromised |
| `PR-AST-007` | Return Fraud and Abuse Losses | $103B fraudulent returns (US) |
| `PR-AST-008` | Time and Resource Waste on Dispute Resolution | Weeks resolving refund claims |
| `PR-AST-009` | Warranty/Support Denial for Counterfeit Goods | Excluded from manufacturer support |
| `PR-AST-010` | Legal and Compliance Exposure | CMMC/NDAA compliance issues |

#### Lane 5 DEFENSE_FIXER Subclasses

| Fixer ID | Fixer Name | When It Applies |
|----------|-----------|-----------------|
| `DF-AST-001` | Physical Inspection & Delidding | GPU/CPU die verification |
| `DF-AST-002` | Benchmark Validation & Stress Testing | Performance verification against specs |
| `DF-AST-003` | Serial Number & Warranty Verification | Manufacturer database checks |
| `DF-AST-004` | Authorized Distributor Procurement | Manufacturer-authorized channels only |
| `DF-AST-005` | AS6081/AS6171 Counterfeit Avoidance Testing | Industry-standard electronic component testing |
| `DF-AST-006` | Blockchain/Immutable Chain-of-Custody | Cryptographic provenance tracking |
| `DF-AST-007` | Cryptographic Hardware Attestation | Silicon-level authenticity verification |
| `DF-AST-008` | Return Inspection Workflows | Mandatory physical inspection before refund |
| `DF-AST-009` | Proof-of-Value Appraisal Packets | Independent third-party appraisal |
| `DF-AST-010` | Fraud Detection ML/AI Systems | Pattern analysis for fraudulent listings |
| `DF-AST-011` | eBay Seller Protection Compliance | Verified addresses; tracked/insured shipping |
| `DF-AST-012` | SBOM/HBOM Documentation | Component-level supply chain transparency |
| `DF-AST-013` | Visual AI Component Inspection | Automated PCBA authenticity verification |
| `DF-AST-014` | Independent Escrow & Inspection | Third-party holding for P2P transactions |

---

### 3.6 Lane 6: AI Agent Trust

**Scope:** AI hallucination, algorithmic bias, agent autonomy failures, deepfake fraud, vendor liability gaps, agent security vulnerabilities

#### Lane 6 OFFENSE_SIGNAL Subclasses

| Signal ID | Signal Name | Description | Key Magnitude |
|-----------|-------------|-------------|---------------|
| `OS-AIT-001` | Unsupported Action | Agent takes action without authorization or proper scope | Air Canada chatbot; Workday auto-reject |
| `OS-AIT-002` | Fabrication (Hallucination) | AI generates false information presented as factual | 58-88% on legal queries (Stanford) |
| `OS-AIT-003` | Record Alteration/Memory Poisoning | Agent memory corrupted with harmful persistent instructions | OpenAI Atlas CSRF; cascade degradation |
| `OS-AIT-004` | Improper Data Handling | Mishandling of sensitive data, credentials, PII | OpenClaw plaintext keys; Moltbook exposure |
| `OS-AIT-005` | Missing Receipts/Accountability Gaps | Inability to trace AI decisions to responsible parties | 88% vendors cap liability |
| `OS-AIT-006` | Unsafe Advice | AI recommendations that could cause harm if followed | Comet clicked phishing links |
| `OS-AIT-007` | Unprovenanced Output | AI-generated content without verifiable origin | Deepfakes without C2PA |

#### Lane 6 PAIN_RECEIPT Subclasses

| Receipt ID | Receipt Type | Evidence Form |
|------------|-------------|---------------|
| `PR-AIT-001` | Bad Decisions Based on AI Output | Wrongful denials, incorrect actions, faulty purchases |
| `PR-AIT-002` | Compliance Failures | Regulatory suspension, sanctions, security standard violations |
| `PR-AIT-003` | Reputational Damage | Brand erosion, media impressions (296.4B from deepfakes 2025) |
| `PR-AIT-004` | Financial Loss | Direct losses, runaway cloud costs, fraud losses ($1.28B deepfake) |
| `PR-AIT-005` | Regulatory/Legal Liability | Class actions, defamation suits, court sanctions |

#### Lane 6 DEFENSE_FIXER Subclasses

| Fixer ID | Fixer Name | When It Applies |
|----------|-----------|-----------------|
| `DF-AIT-001` | Audit Logging | All agent actions, decisions, tool invocations logged |
| `DF-AIT-002` | Human-in-the-Loop (HITL) | Tiered approval gates for consequential decisions |
| `DF-AIT-003` | Output Verification | Citation validation, RAG verification, expert review |
| `DF-AIT-004` | Agent Decommissioning | Formal authority revocation and removal procedures |
| `DF-AIT-005` | Behavioral Telemetry | Runtime anomaly detection: action velocity, escalation rate |
| `DF-AIT-006` | Provenance Tracking | C2PA content credentials, cryptographic chain of custody |
| `DF-AIT-007` | Red Teaming & Safety Evaluation | NIST ARIA, systematic adversarial testing |
| `DF-AIT-008` | Autonomy Tier Governance | NIST 4-tier classification with proportional governance |
| `DF-AIT-009` | Tool-Use Risk Management | Tool inventory by consequence scope, reversibility |
| `DF-AIT-010` | Accountability Lineage | Every agent action traced to responsible human officer |

---

## 4. Severity Classification

### 4.1 Tribunal 4-Tier System

The DefendableOS Tribunal system classifies all signals into four quality/risk tiers. These are canonical and immutable within the ontology.

| Tier | Label | Color Code | Definition | Inclusion Criteria | Exclusion Criteria |
|------|-------|-----------|------------|-------------------|-------------------|
| **T1** | `HONEY` | Amber/Gold | Verified, highest quality, court-adjudicated or regulator-confirmed | Consent order filed; judgment entered; regulatory enforcement action completed; independent audit confirmed; replicated technical exploit | Open contradiction; unresolved proof gap; source tier > 1 only |
| **T2** | `ROYAL_JELLY` | Cream/Pale | High value, strong evidence, likely valid but not fully adjudicated | Active litigation with credible evidence; government investigation confirmed; multiple independent Tier-1 sources; technical vulnerability with CVE and PoC | Single-source allegation; contested by primary authority; older than 5 years without reconfirmation |
| **T3** | `JELLY` | Amber/Translucent | Messy, ambiguous, incomplete, or contradictory | Reported by credible source but unverified; active stakeholder dispute; mixed evidence; aggregate-only data | Demonstrably false; contradicted by Tier-1 evidence; retracted by source |
| **T4** | `PROPOLIS` | Dark Brown/Red | Critical risk, requires immediate attention; includes all `critical` severity | Confirmed imminent harm; active exploitation; repeat offender pattern; national security impact; regulatory enforcement with >$100M redress | Unsubstantiated fear; theoretical risk without evidence; speculative projection |

### 4.2 Dual-Axis Severity Model

Every OFFENSE_SIGNAL carries **two severity dimensions**:

#### Axis A: Tribunal Quality Tier (HONEY -> PROPOLIS)
Measures the **trustworthiness and completeness of the evidence** supporting the signal.

#### Axis B: Harm Severity Level (1 -> 4)
Measures the **magnitude of potential or actual harm** if the signal is valid.

| Level | Label | Description | Dollar Threshold | Record Threshold | Systemic Threshold |
|-------|-------|-------------|-----------------|------------------|-------------------|
| 1 | `informational` | Low individual impact; useful for pattern detection | <$1K | <10 records | Single consumer |
| 2 | `significant` | Moderate impact; actionable for affected parties | $1K-$100K | 10-10K records | Localized group |
| 3 | `severe` | High impact; affects populations or critical systems | $100K-$100M | 10K-1M records | Multi-jurisdictional |
| 4 | `critical` | Catastrophic impact; national security, mass harm, or market failure | >$100M | >1M records | Systemic/cross-sector |

### 4.3 Cross-Matrix: Tribunal Tier x Harm Severity

```
                    Harm Severity
                   L1    L2    L3    L4
                 +-----+-----+-----+-----+
T1 HONEY         |  A  |  B  |  C  |  D* |
T2 ROYAL_JELLY   |  E  |  F  |  G  |  H* |
T3 JELLY         |  I  |  J  |  K  |  L* |
T4 PROPOLIS      |  M  |  N  |  O  |  P* |
                 +-----+-----+-----+-----+
                 * = HUMAN_REVIEW required for all L4 signals regardless of tier
```

**Interpretation:**
- **Cell D** (HONEY + Critical harm): The rarest and most valuable classification. Confirmed catastrophic harm with complete evidence. Automatic Tribunal priority.
- **Cell P** (PROPOLIS + Critical harm): Critical-risk signal that requires immediate HUMAN_REVIEW. May be demoted to ROYAL_JELLY or promoted to HONEY after review.
- **Cell L** (JELLY + Critical harm): High-stakes but messy signal. Quarantined until proof gaps resolved.
- **All L4 cells**: Require mandatory HUMAN_REVIEW before any ledger action.

### 4.4 Tribunal Classification Mapping

| Mission 4-Tier | Tribunal Label | Mapping Notes |
|----------------|---------------|---------------|
| `honey` | `HONEY` | Direct 1:1 equivalence |
| `jelly` | `ROYAL_JELLY` | Mission "jelly" maps to Tribunal T2; mission T3 is also called `jelly` but is distinct |
| `propolis` | `JELLY` | Mission "propolis" is T3; Tribunal "PROPOLIS" is T4-critical |
| `critical` | `PROPOLIS` | Mission "critical" = Tribunal "PROPOLIS" (T4); highest risk tier |

> **IMPORTANT NOTE ON NAMING:** The mission uses a 4-tier system (honey/jelly/propolis/critical) that maps to the Tribunal system as follows:
> - Mission `honey` = Tribunal `HONEY`
> - Mission `jelly` = Tribunal `ROYAL_JELLY`
> - Mission `propolis` = Tribunal `JELLY`
> - Mission `critical` = Tribunal `PROPOLIS`
>
> This is an intentional inversion: Tribunal `PROPOLIS` represents the highest-risk, most-critical classification, while mission "critical" maps directly to it. Engineers should always use Tribunal labels in internal systems and map at the API boundary.

### 4.5 Severity Escalation Rules

| Rule ID | Trigger | Action |
|---------|---------|--------|
| `SEV-R01` | Signal crosses $100M threshold | Auto-escalate to L4; trigger HUMAN_REVIEW |
| `SEV-R02` | Signal affects >1M records | Auto-escalate to L4; trigger HUMAN_REVIEW |
| `SEV-R03` | Repeat offender detected (>1 prior enforcement) | Escalate tier by 1 level (max T4) |
| `SEV-R04` | Nation-state attribution confirmed | Minimum L3; escalate to L4 if critical infrastructure |
| `SEV-R05` | Active exploitation confirmed (CISA KEV or equivalent) | Minimum L3; auto-T4 for ransomware/APT |
| `SEV-R06` | CONTRADICTION present | Cap at T3 (JELLY) until resolved |
| `SEV-R07` | PROOF_GAP blocks_promotion | Cap at T3 (JELLY) until gap closed |
| `SEV-R08` | Source tier = 3 only | Cap at T3 (JELLY) regardless of other indicators |

---

## 5. Trust Tier System

### 5.1 Tier Definitions

The Trust Tier System classifies the **reliability and authority of evidence sources**, independent of the Tribunal quality tier.

#### Tier 1: Primary Authority

| Criterion | Description |
|-----------|-------------|
| **Definition** | Government databases, court records, regulatory actions, official agency reports, peer-reviewed research |
| **Examples** | CFPB Consumer Complaint Database, FBI IC3 Annual Report, CISA KEV Catalog, SEC Enforcement Actions, FTC Consumer Sentinel, HHS OCR Breach Portal, DOJ Press Releases, Federal Court Filings, ISO/IEC Standards |
| **Corpus Score Range** | 8-10 |
| **Verification** | Self-authenticating or cryptographically verifiable |
| **Bias Profile** | Institutional; may have regulatory or political constraints |
| **Reuse Rights** | Federal data: public domain. Court records: public domain. Standards: licensed. |

#### Tier 2: High-Quality Secondary

| Criterion | Description |
|-----------|-------------|
| **Definition** | Industry reports from reputable firms, academic legal analysis, investigative journalism from established outlets, recognized expert analysis |
| **Examples** | Lex Machina litigation analytics, CrowdStrike Threat Reports, Coveware Ransomware Data, Stanford HAI Research, ProPublica Investigations, AARP Policy Analysis, IBM Security Reports |
| **Corpus Score Range** | 5-9 |
| **Verification** | Methodology-documented; citation chains available; author credibility established |
| **Bias Profile** | Commercial or institutional; potential sponsor influence on industry reports |
| **Reuse Rights** | Varies; factual data generally extractable; analysis requires attribution |

#### Tier 3: Tertiary / Aggregated

| Criterion | Description |
|-----------|-------------|
| **Definition** | Aggregated data compilations, legal news blogs, specialized forums, third-party scrapers/wrappers, advocacy organization summaries |
| **Examples** | Apify CFPB scraper documentation, JD Supra legal tracking, NCLC advocacy fact sheets, industry blog compilations, BBB complaint summaries |
| **Corpus Score Range** | 3-6 |
| **Verification** | Source citations should be checked; methodology may be opaque |
| **Bias Profile** | Advocacy-influenced; commercial interest in traffic/volume |
| **Reuse Rights** | Highly variable; treat as pointers to primary sources |

#### Tier 4: Unverified / Disputed

| Criterion | Description |
|-----------|-------------|
| **Definition** | Social media posts, forum threads, self-published content, retracted claims, actively disputed allegations |
| **Examples** | Reddit complaint threads, unverified X/Twitter posts, individual blog posts, class action solicitation sites |
| **Corpus Score Range** | 0-4 |
| **Verification** | Requires independent verification; not admissible as primary evidence |
| **Bias Profile** | Highly variable; individual emotional stake; potential manipulation |
| **Reuse Rights** | Personal data protected; factual claims may be reused with caution |

### 5.2 Tier Elevation Rules

| Condition | Tier Adjustment |
|-----------|----------------|
| Multiple Tier 2 sources independently confirm | Elevate to equivalent of Tier 1 for factual claims |
| Tier 1 source contradicts Tier 2 source | Defer to Tier 1; flag CONTRADICTION |
| Source older than 5 years without reconfirmation | Degrade by 1 tier |
| Source methodology challenged by peer institution | Degrade by 1 tier pending resolution |
| Whistleblower with documentary evidence | Treat as Tier 1 for specific claims if documents verified |
| Industry report sponsored by affected party | Degrade by 1 tier for bias risk |

### 5.3 Source Receipt Requirements by Tribunal Tier

| Tribunal Tier | Minimum Source Tier | Minimum Source Count |
|---------------|-------------------|---------------------|
| HONEY | Tier 1 | 2+ independent Tier 1 sources |
| ROYAL_JELLY | Tier 1 or Tier 2 | 2+ sources with consistent findings |
| JELLY | Tier 2 or Tier 3 | 1+ credible source |
| PROPOLIS | Tier 1 (if available) | 1+ confirmed finding; HUMAN_REVIEW mandatory |

---

## 6. Status Taxonomy

### 6.1 Status Lifecycle

Every signal progresses through a defined status lifecycle. Status transitions are logged immutably.

```
ALLEGED_HARM
    |
    v (reporter provides details; meets minimum filing requirements)
OFFENSE_SIGNAL [status=alleged]
    |
    +---> QUARANTINED_SIGNAL (insufficient_evidence / pii_risk)
    |         |
    |         v (evidence obtained / pii resolved)
    |     OFFENSE_SIGNAL [status=reported]
    |         |
    |         v (source receipt attached)
    |     OFFENSE_SIGNAL [status=reported] ---+---> VERIFIED_FINDING
    |                                         |       (technical verification / independent audit)
    |                                         |
    |                                         +---> [status=admitted]
    |                                         |       (respondent acknowledges)
    |                                         |
    |                                         +---> [status=settled]
    |                                         |       (consent order / settlement agreement)
    |                                         |
    |                                         +---> [status=adjudicated]
    |                                         |       (judgment entered / final order)
    |                                         |
    |                                         +---> [status=verified_technical]
    |                                         |       (PoC demonstrated / CVE confirmed)
    |                                         |
    |                                         +---> [status=aggregate_only]
    |                                         |       (pattern confirmed but individual cases not verified)
    |                                         |
    |                                         +---> [status=unknown]
    |                                                 (insufficient information to classify)
    |
    +---> RESOLUTION_PATH (fixer chain activated)
              |
              v (outcome documented)
          LEDGER_READY or NOT_LEDGER_READY
```

### 6.2 Status Definitions

| Status | Definition | Requirements to Enter | Auto-Exit Conditions |
|--------|-----------|----------------------|---------------------|
| `alleged` | Claim made but not independently verified | Reporter identity recorded; basic signal description provided | Escalates to `reported` when source receipt attached; quarantines if no receipt within 30 days |
| `reported` | Claim supported by at least one source receipt | One SOURCE_RECEIPT of Tier 2+ | Escalates to `admitted`, `settled`, or `verified_technical` when evidence obtained; remains `reported` if stalled 180 days |
| `admitted` | Respondent acknowledges the pattern | Written or public acknowledgment by responsible party | Auto-escalates to `settled` or `adjudicated` if formal action follows; degrades if admission retracted |
| `settled` | Resolved through settlement or consent order | Signed settlement agreement or consent order filed | Terminal status; may be updated with redress amounts |
| `adjudicated` | Resolved through court judgment or final administrative order | Judgment entered; appeal period expired or resolved | Terminal status; most authoritative for Tribunal classification |
| `verified_technical` | Technically confirmed through exploit, PoC, or independent technical analysis | CVE assigned; PoC demonstrated; independent security audit confirms | Terminal status for technical signals |
| `aggregate_only` | Pattern confirmed at population level; individual cases not independently verified | Multiple consistent reports; statistical significance; no contradictory evidence | May be promoted to `verified_technical` if specific case confirmed; demotes if contradictory evidence emerges |
| `unknown` | Insufficient information to classify | Signal received but critical fields missing | Auto-quarantine after 14 days; expires if no update within 90 days |

### 6.3 Status Transitions Table

| From Status | To Status | Trigger | Authority |
|-------------|-----------|---------|-----------|
| `alleged` | `reported` | Source receipt attached | Automated |
| `alleged` | QUARANTINED | No receipt within 30 days | Automated |
| `reported` | `admitted` | Respondent acknowledgment | HUMAN_REVIEW |
| `reported` | `settled` | Settlement/Consent order filed | Automated + HUMAN_REVIEW |
| `reported` | `adjudicated` | Judgment entered | Automated |
| `reported` | `verified_technical` | CVE/PoC/audit confirmed | Automated + HUMAN_REVIEW |
| `reported` | `aggregate_only` | Population pattern confirmed; individual cases unverified | HUMAN_REVIEW |
| Any active | QUARANTINED | CONTRADICTION detected or PROOF_GAP opened | Automated |
| QUARANTINED | Previous status | CONTRADICTION resolved or PROOF_GAP closed | HUMAN_REVIEW |
| Any | `unknown` | Critical data loss or source retraction | Automated |

---

## 7. Example Fact Patterns

### 7.1 Lane 1: Consumer Financial — 6 Example Patterns

#### Pattern CF-001: Surprise Overdraft Fee Scheme

```json
{
  "signal_id": "OS-FIN-002-REGIONS",
  "signal_class": "surprise_overdraft_fees",
  "description": "Bank charges overdraft fees on transactions where consumer had sufficient funds at time of authorization",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L3"
  },
  "status": "settled",
  "affected_domain": ["Lane_1"],
  "primary_source": {
    "source_id": "SRC-001",
    "source_tier": 1,
    "source_type": "Regulatory_Action",
    "citation": "CFPB Consent Order against Regions Bank, September 28, 2022"
  },
  "dollar_magnitude": 141000000,
  "affected_party": "Consumers with checking accounts at Regions Bank",
  "pain_receipts": [
    {
      "receipt_id": "PR-FIN-001",
      "type": "Direct Monetary Loss",
      "quantified_impact": 141000000,
      "impact_units": "USD in surprise overdraft fees"
    },
    {
      "receipt_id": "PR-FIN-008",
      "type": "Psychological Stress",
      "evidence": "Bank employees could not explain fee structure to consumers"
    }
  ],
  "fixers_available": ["DF-FIN-001", "DF-FIN-005", "DF-FIN-007"],
  "resolution": {
    "outcome": "Consent order; $141M in refunds; $15M civil penalty",
    "status": "settled"
  },
  "tribunal_classification": "HONEY",
  "ledger_ready": true
}
```

#### Pattern CF-002: Credit Reporting Dispute Failure

```json
{
  "signal_id": "OS-FIN-001-EQUIFAX",
  "signal_class": "credit_reporting_errors",
  "description": "Equifax failed to properly investigate consumer disputes; relied on faulty creditor information",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L3"
  },
  "status": "settled",
  "affected_domain": ["Lane_1"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Regulatory_Action",
    "citation": "CFPB Consent Order against Equifax, January 2025"
  },
  "dollar_magnitude": 15000000,
  "key_evidence": "Equifax confirmed only ~37% of consumer-reported prior disputes vs Experian exceeding 90%",
  "pain_receipts": ["PR-FIN-003", "PR-FIN-007"],
  "tribunal_classification": "HONEY",
  "ledger_ready": true
}
```

#### Pattern CF-003: Savings Account Interest Manipulation

```json
{
  "signal_id": "OS-FIN-006-CAPONE",
  "signal_class": "interest_rate_manipulation",
  "description": "Capital One froze 360 Savings APY at 0.3% while newer product reached 4.25%; barred employees from informing customers",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L3"
  },
  "status": "settled",
  "affected_domain": ["Lane_1"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Court_Record",
    "citation": "CFPB v. Capital One (dismissed Feb 27, 2025); Private litigation settled $425M"
  },
  "dollar_magnitude": 425000000,
  "controversy": {
    "contradiction_id": "CONTR-001",
    "description": "CFPB dismissed case after leadership change; private settlement approved separately",
    "contradiction_type": "stakeholder_dispute",
    "resolution_status": "partially_resolved"
  },
  "pain_receipts": ["PR-FIN-001", "PR-FIN-010"],
  "tribunal_classification": "ROYAL_JELLY"
}
```

#### Pattern CF-004: Phantom Debt Collection

```json
{
  "signal_id": "OS-FIN-003-GLOBALCIRC",
  "signal_class": "debt_collection_abuses",
  "description": "Debt collector used threats of arrest, lawsuits, wage garnishment to coerce payment of non-existent debts",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L2"
  },
  "status": "settled",
  "affected_domain": ["Lane_1"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Regulatory_Action",
    "citation": "FTC Final Order against Global Circulation Inc., May 2025"
  },
  "dollar_magnitude": 9600000,
  "pain_receipts": ["PR-FIN-001", "PR-FIN-008"],
  "fixers_available": ["DF-FIN-001", "DF-FIN-004"]
}
```

#### Pattern CF-005: Zelle Payment Network Fraud

```json
{
  "signal_id": "OS-FIN-007-ZELLE",
  "signal_class": "payment_network_fraud",
  "description": "Major banks failed to prevent fraud on Zelle network; inadequate safeguards caused hundreds of millions in losses",
  "severity": {
    "tribunal_tier": "JELLY",
    "harm_level": "L4"
  },
  "status": "reported",
  "affected_domain": ["Lane_1", "Lane_2"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Regulatory_Action",
    "citation": "CFPB lawsuit filed Dec 2024; dismissed March 4, 2025"
  },
  "controversy": {
    "contradiction_id": "CONTR-002",
    "description": "CFPB sued for $870M+; case dismissed after leadership change; true harm scope disputed",
    "contradiction_type": "stakeholder_dispute",
    "resolution_status": "unresolved"
  },
  "proof_gaps": [
    {
      "gap_id": "GAP-001",
      "missing_evidence": "Exact number of defrauded consumers and total verified losses",
      "gap_severity": "weakens_claim"
    }
  ],
  "pain_receipts": ["PR-FIN-001", "PR-FIN-004"],
  "tribunal_classification": "JELLY"
}
```

#### Pattern CF-006: Student Loan Servicing Abuse

```json
{
  "signal_id": "OS-FIN-008-NAVIENT",
  "signal_class": "student_loan_servicing_abuse",
  "description": "Navient misled borrowers about income-driven repayment; harmed disabled veterans credit; deceived about cosigner release",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L3"
  },
  "status": "settled",
  "affected_domain": ["Lane_1"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Regulatory_Action",
    "citation": "CFPB v. Navient settlement, September 2024"
  },
  "dollar_magnitude": 120000000,
  "affected_party": "12 million borrowers; disabled veterans",
  "pain_receipts": ["PR-FIN-001", "PR-FIN-003", "PR-FIN-007"],
  "tribunal_classification": "HONEY",
  "ledger_ready": true
}
```

---

### 7.2 Lane 2: Fraud & Digital Loss — 6 Example Patterns

#### Pattern FD-001: Business Email Compromise

```json
{
  "signal_id": "OS-FRD-002-BEC-50M",
  "signal_class": "business_email_compromise",
  "description": "Construction entity in New York lost $50M to BEC attack targeting critical infrastructure",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L4"
  },
  "status": "reported",
  "affected_domain": ["Lane_2"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Government_DB",
    "citation": "FBI IC3 2024 Annual Report"
  },
  "dollar_magnitude": 50000000,
  "pain_receipts": ["PR-FRD-002", "PR-FRD-003"],
  "fixers_available": ["DF-FRD-D01", "DF-FRD-R01", "DF-FRD-P03"]
}
```

#### Pattern FD-002: Cryptocurrency Investment Fraud

```json
{
  "signal_id": "OS-FRD-001-CRYPTO-11B",
  "signal_class": "investment_fraud_cryptocurrency",
  "description": "181,565 IC3 complaints involving cryptocurrency totaling $11.3B in losses; single largest loss vector",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L4"
  },
  "status": "aggregate_only",
  "affected_domain": ["Lane_2"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Government_DB",
    "citation": "FBI IC3 2025 Annual Report; FBI Press Release April 2026"
  },
  "dollar_magnitude": 11300000000,
  "pain_receipts": ["PR-FRD-001", "PR-FRD-004"],
  "fixers_available": ["DF-FRD-R02", "DF-FRD-R03"]
}
```

#### Pattern FD-003: Deepfake Video Conference Fraud

```json
{
  "signal_id": "OS-FRD-003-DEEPFAKE-ARUP",
  "signal_class": "ai_enabled_fraud_deepfake",
  "description": "Finance worker at Arup tricked into wiring $25M via deepfake video conference call with fake CFO",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L3"
  },
  "status": "reported",
  "affected_domain": ["Lane_2", "Lane_6"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "News_Media",
    "citation": "Keepnet Labs Deepfake Statistics 2026"
  },
  "dollar_magnitude": 25000000,
  "pain_receipts": ["PR-FRD-002", "PR-FRD-006"],
  "fixers_available": ["DF-FRD-P04", "DF-FRD-P03"]
}
```

#### Pattern FD-004: Pig Butchering Romance Scam

```json
{
  "signal_id": "OS-FRD-006-PIGBUTCHER",
  "signal_class": "social_engineering_romance_investment",
  "description": "Romance scams converged with investment fraud; victims lured via fake relationships into crypto investment schemes",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L4"
  },
  "status": "aggregate_only",
  "affected_domain": ["Lane_2"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Government_DB",
    "citation": "FBI IC3 2024; FTC Data Book 2024"
  },
  "dollar_magnitude": 3900000000,
  "key_metrics": "Average loss $100K+ per victim; operated from SE Asia compounds using trafficked labor",
  "pain_receipts": ["PR-FRD-005", "PR-FRD-004"],
  "fixers_available": ["DF-FRD-P04", "DF-FRD-D02"]
}
```

#### Pattern FD-005: Ransomware Critical Infrastructure Attack

```json
{
  "signal_id": "OS-FRD-005-RANSOMWARE-NHS",
  "signal_class": "ransomware_critical_infrastructure",
  "description": "Synnovis/NHS London ransomware attack delayed 11,000+ appointments; at least one confirmed patient death",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L4"
  },
  "status": "adjudicated",
  "affected_domain": ["Lane_2", "Lane_3"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Government_DB",
    "citation": "NHS England; Synnovis Official Updates; CyberSecurityIntelligence"
  },
  "key_metrics": "800+ operations cancelled; 60+ IT systems rebuilt; 6-month recovery",
  "pain_receipts": ["PR-FRD-003", "PR-FRD-007"]
}
```

#### Pattern FD-006: Synthetic Identity Fraud Surge

```json
{
  "signal_id": "OS-FRD-004-SYNTHID",
  "signal_class": "synthetic_identity_fraud",
  "description": "Synthetic identities account for 80%+ of new account fraud; $3.3B lender exposure in H1 2025",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L3"
  },
  "status": "aggregate_only",
  "affected_domain": ["Lane_2"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "Industry_Report",
    "citation": "TransUnion Identity Fraud Trends for Government, 2025; BIIA Synthetic Identity Statistics 2026"
  },
  "dollar_magnitude": 3300000000,
  "pain_receipts": ["PR-FRD-009", "PR-FRD-010"],
  "fixers_available": ["DF-FRD-P05", "DF-FRD-D02"]
}
```

---

### 7.3 Lane 3: Cyber & AI System Risk — 6 Example Patterns

#### Pattern CY-001: Change Healthcare Ransomware

```json
{
  "signal_id": "OS-CYB-003-CHANGEHC",
  "signal_class": "ransomware_ecosystem",
  "description": "ALPHV/BlackCat ransomware attack on Change Healthcare; largest healthcare breach in history",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L4"
  },
  "status": "adjudicated",
  "affected_domain": ["Lane_3"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Government_DB",
    "citation": "HHS OCR Breach Portal; AHA Report; HyperProof Analysis"
  },
  "dollar_magnitude": 22000000,
  "key_metrics": "192.7M individuals affected; $22M ransom; 74% of hospitals reported patient care impact",
  "pain_receipts": ["PR-CYB-001", "PR-CYB-002", "PR-CYB-005", "PR-CYB-010"]
}
```

#### Pattern CY-002: AI Prompt Injection Universal Vulnerability

```json
{
  "signal_id": "OS-CYB-004-PROMPTINJECT",
  "signal_class": "ai_prompt_injection",
  "description": "All evaluated frontier models vulnerable to indirect prompt injection; ASR 0.5%-8.5%",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L3"
  },
  "status": "verified_technical",
  "affected_domain": ["Lane_3", "Lane_6"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Academic_Paper",
    "citation": "arXiv:2603.15714; OWASP Top 10 for LLMs 2025"
  },
  "key_metrics": "Attack success rate 0.5% (Claude Opus 4.5) to 8.5% (Gemini 2.5 Pro); tool use scenarios most vulnerable at 4.82%",
  "pain_receipts": ["PR-CYB-006", "PR-CYB-007"],
  "fixers_available": ["DF-CYB-006", "DF-CYB-007"]
}
```

#### Pattern CY-003: Salt Typhoon Telecom Espionage

```json
{
  "signal_id": "OS-CYB-005-SALTTYPHOON",
  "signal_class": "nation_state_apt",
  "description": "China MSS Salt Typhoon breached 8+ US telecom providers; stole call records and surveillance request data",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L4"
  },
  "status": "reported",
  "affected_domain": ["Lane_3"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Government_DB",
    "citation": "CrowdStrike Global Threat Report 2025; BlackBerry Analysis"
  },
  "key_metrics": "Customer call records stolen; law enforcement surveillance data accessed; custom backdoors deployed",
  "pain_receipts": ["PR-CYB-004", "PR-CYB-001"],
  "fixers_available": ["DF-CYB-008", "DF-CYB-009"]
}
```

#### Pattern CY-004: AI Agent Safety Gap

```json
{
  "signal_id": "OS-CYB-008-AIAGENT",
  "signal_class": "ai_agent_safety_gap",
  "description": "AI agents deployed at L4-L5 autonomy without documented safety evaluations; 63% of organizations lack AI governance",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L3"
  },
  "status": "aggregate_only",
  "affected_domain": ["Lane_3", "Lane_6"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Academic_Paper",
    "citation": "MIT AI Agent Index 2025; NIST AI RMF Agentic Profile May 2026; IBM Cost of Breach 2025"
  },
  "key_metrics": "88% of organizations using AI; 62% experimenting with AI agents; 97% of AI breaches involved systems lacking access controls",
  "pain_receipts": ["PR-CYB-011", "PR-CYB-012"],
  "fixers_available": ["DF-CYB-005", "DF-CYB-010"]
}
```

#### Pattern CY-005: Critical RCE (React2Shell)

```json
{
  "signal_id": "OS-CYB-002-REACT2SHELL",
  "signal_class": "critical_rce",
  "description": "CVE-2025-55182: Unauthenticated RCE in React Server Components via insecure deserialization; CVSS 10.0",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L3"
  },
  "status": "verified_technical",
  "affected_domain": ["Lane_3"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Technical_Analysis",
    "citation": "CISA KEV; Shadowserver detection data"
  },
  "key_metrics": "28,964 vulnerable IPs detected; exploitation by Chinese APT UNC5174",
  "pain_receipts": ["PR-CYB-001"],
  "fixers_available": ["DF-CYB-001", "DF-CYB-003"]
}
```

#### Pattern CY-006: AI Data Poisoning

```json
{
  "signal_id": "OS-CYB-006-POISONING",
  "signal_class": "ai_data_poisoning",
  "description": "Data poisoning corrupts AI training data; 0.001% token poisoning produces harmful models matching clean benchmarks",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L2"
  },
  "status": "verified_technical",
  "affected_domain": ["Lane_3", "Lane_6"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Academic_Paper",
    "citation": "Nature Medicine study; Anthropic Sleeper Agents research"
  },
  "key_metrics": "250 malicious documents sufficient to backdoor LLMs 600M-13B parameters; 100 poisoned models discovered on Hugging Face",
  "pain_receipts": ["PR-CYB-007"],
  "fixers_available": ["DF-CYB-006"]
}
```

---

### 7.4 Lane 4: Property & Contractor — 6 Example Patterns

#### Pattern PR-001: Contractor Nonperformance (Cabinet Company)

```json
{
  "signal_id": "OS-PRP-002-CABINET",
  "signal_class": "contractor_nonperformance",
  "description": "Consumer paid $10,237 deposit; never received final contract; company refused full refund",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L1"
  },
  "status": "settled",
  "affected_domain": ["Lane_4"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Regulatory_Action",
    "citation": "CFA 2024 Consumer Complaint Survey Report; Hillsborough County mediation"
  },
  "dollar_magnitude": 5119,
  "pain_receipts": ["PR-PRP-001"],
  "fixers_available": ["DF-PRP-003", "DF-PRP-005"]
}
```

#### Pattern PR-002: Post-Hurricane Unlicensed Contracting

```json
{
  "signal_id": "OS-PRP-003-HURRICANE",
  "signal_class": "unlicensed_contracting",
  "description": "Post-hurricane unlicensed contractor sting in Pinellas County, FL; 100+ arrests, 150+ charges",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L2"
  },
  "status": "adjudicated",
  "affected_domain": ["Lane_4"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Government_DB",
    "citation": "CFA 2024; Pinellas County law enforcement records"
  },
  "key_metrics": "100+ arrests; 150+ criminal charges; felony enhancement during state of emergency",
  "pain_receipts": ["PR-PRP-001", "PR-PRP-004"],
  "fixers_available": ["DF-PRP-006"]
}
```

#### Pattern PR-003: Home Warranty Systematic Denials

```json
{
  "signal_id": "OS-PRP-005-WARRANTY",
  "signal_class": "home_warranty_claim_denials",
  "description": "Home warranty companies deny legitimate claims citing pre-existing conditions or fine-print exclusions",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L2"
  },
  "status": "aggregate_only",
  "affected_domain": ["Lane_4"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "Industry_Report",
    "citation": "Reviews.com/Home Warranty Survey 2024 (YouGov); FTC action against Choice Home Warranty"
  },
  "key_metrics": "Only 49% claim satisfaction; thousands of BBB complaints; American Home Shield NBC News investigation",
  "pain_receipts": ["PR-PRP-001", "PR-PRP-005"],
  "fixers_available": ["DF-PRP-008"]
}
```

#### Pattern PR-004: Solar Installation Fraud

```json
{
  "signal_id": "OS-PRP-002-SOLAR",
  "signal_class": "contractor_nonperformance",
  "description": "Solar company left 140+ Utah consumers without functional systems; used fake Google reviews",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L2"
  },
  "status": "settled",
  "affected_domain": ["Lane_4"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "Industry_Report",
    "citation": "CFA 2024; Utah AG cease & desist"
  },
  "dollar_magnitude": 240000,
  "pain_receipts": ["PR-PRP-001", "PR-PRP-004", "PR-PRP-005"]
}
```

#### Pattern PR-005: Deceptive Home Improvement Financing

```json
{
  "signal_id": "OS-PRP-004-YGRENE",
  "signal_class": "deceptive_financing",
  "description": "Home improvement financing company made false claims; contractors used forgery; liens recorded without consent",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L2"
  },
  "status": "settled",
  "affected_domain": ["Lane_4"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Regulatory_Action",
    "citation": "FTC v. Ygrene Energy Fund; July 2025"
  },
  "dollar_magnitude": 2900000,
  "pain_receipts": ["PR-PRP-001"],
  "fixers_available": ["DF-PRP-005"]
}
```

#### Pattern PR-006: Construction Defect Litigation Surge

```json
{
  "signal_id": "OS-PRP-001-DEFECTS",
  "signal_class": "improper_workmanship",
  "description": "Construction defect claims increasing due to labor shortages; 500,000 worker shortfall since 2023",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L3"
  },
  "status": "aggregate_only",
  "affected_domain": ["Lane_4"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "Industry_Report",
    "citation": "Seyfarth Shaw 2025 Commercial Litigation Outlook; Texas Lawbook"
  },
  "key_metrics": "3,500+ homeowner policy lawsuits in federal courts (2024); $10.1M average commercial defect claim (TX)",
  "pain_receipts": ["PR-PRP-002", "PR-PRP-003"]
}
```

---

### 7.5 Lane 5: Asset & Compute — 6 Example Patterns

#### Pattern AS-001: Counterfeit GPU with Re-marked Die

```json
{
  "signal_id": "OS-AST-001-RTX4090",
  "signal_class": "counterfeit_remarked_dies",
  "description": "Counterfeit RTX 4090 used re-marked RTX 3080 Ti die with counterfeit memory; visually indistinguishable",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L1"
  },
  "status": "verified_technical",
  "affected_domain": ["Lane_5"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "News_Media",
    "citation": "Tom's Hardware, July 6, 2024; NorthWest Repair analysis"
  },
  "dollar_magnitude": 1500,
  "pain_receipts": ["PR-AST-001"],
  "fixers_available": ["DF-AST-001", "DF-AST-002"]
}
```

#### Pattern AS-002: Fake CPU Empty Shell

```json
{
  "signal_id": "OS-AST-002-9800X3D",
  "signal_class": "shell_empty_product_fraud",
  "description": "Fake AMD Ryzen 7 9800X3D purchased from Amazon as 'new' — empty shell with no silicon die inside",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L1"
  },
  "status": "verified_technical",
  "affected_domain": ["Lane_5"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "News_Media",
    "citation": "NotebookCheck/Gamers Nexus, June 2025; Amazon.de direct sale"
  },
  "dollar_magnitude": 450,
  "pain_receipts": ["PR-AST-001", "PR-AST-008"],
  "fixers_available": ["DF-AST-001", "DF-AST-003"]
}
```

#### Pattern AS-003: $100M Counterfeit Cisco in Military Systems

```json
{
  "signal_id": "OS-AST-004-CISCO-100M",
  "signal_class": "fake_specifications",
  "description": "Onur Aksoy/Pro Network imported counterfeit Cisco via 19 companies; discovered in F-15, F-22, AH-64, B-52 systems",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L4"
  },
  "status": "adjudicated",
  "affected_domain": ["Lane_5"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Government_DB",
    "citation": "DOJ Press Release, May 2, 2024; 6.5 year prison sentence; $100M restitution"
  },
  "dollar_magnitude": 100000000,
  "pain_receipts": ["PR-AST-005", "PR-AST-006"],
  "fixers_available": ["DF-AST-003", "DF-AST-005", "DF-AST-009"]
}
```

#### Pattern AS-004: Organized GPU Return Fraud Ring

```json
{
  "signal_id": "OS-AST-007-REKK",
  "signal_class": "organized_refund_fraud",
  "description": "REKK criminal ring stole millions through systematic abuse of retailer return policies targeting GPUs and laptops",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L2"
  },
  "status": "adjudicated",
  "affected_domain": ["Lane_5"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Court_Record",
    "citation": "Courthouse News, February 2025; $2.4M default judgment"
  },
  "dollar_magnitude": 2400000,
  "pain_receipts": ["PR-AST-007"],
  "fixers_available": ["DF-AST-008", "DF-AST-010"]
}
```

#### Pattern AS-005: Chip Smuggling National Security

```json
{
  "signal_id": "OS-AST-012-CHIPSMUGGLE",
  "signal_class": "chip_smuggling_export_control",
  "description": "$390M Nvidia chip smuggling through Singapore; AI chips diverted through shell companies",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L4"
  },
  "status": "adjudicated",
  "affected_domain": ["Lane_5"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "News_Media",
    "citation": "TechCrunch, March 2025; Singapore court case; CNAS report"
  },
  "dollar_magnitude": 390000000,
  "pain_receipts": ["PR-AST-006"],
  "fixers_available": ["DF-AST-006", "DF-AST-012"]
}
```

#### Pattern AS-006: eBay GPU Component Stripping

```json
{
  "signal_id": "OS-AST-003-EBAY5090",
  "signal_class": "component_stripping_return_fraud",
  "description": "eBay buyer returned RTX 5090 with GPU die and memory modules carefully removed",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L1"
  },
  "status": "reported",
  "affected_domain": ["Lane_5"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "News_Media",
    "citation": "Tom's Hardware, March 2026"
  },
  "dollar_magnitude": 4000,
  "pain_receipts": ["PR-AST-001", "PR-AST-008"],
  "fixers_available": ["DF-AST-008", "DF-AST-011"]
}
```

---

### 7.6 Lane 6: AI Agent Trust — 6 Example Patterns

#### Pattern AI-001: Air Canada Chatbot Hallucination

```json
{
  "signal_id": "OS-AIT-002-AIRCANADA",
  "signal_class": "fabrication_hallucination",
  "description": "Air Canada chatbot incorrectly told passenger bereavement fare discount could be applied retroactively; denied claim",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L1"
  },
  "status": "adjudicated",
  "affected_domain": ["Lane_6"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "Industry_Report",
    "citation": "British Columbia Civil Resolution Tribunal ruling; Envive.ai case study"
  },
  "dollar_magnitude": 812,
  "key_metrics": "Tribunal rejected Air Canada's defense that chatbot was 'separate legal entity'",
  "pain_receipts": ["PR-AIT-001", "PR-AIT-005"],
  "fixers_available": ["DF-AIT-002", "DF-AIT-003"]
}
```

#### Pattern AI-002: AI Discrimination in Hiring (Mobley v. Workday)

```json
{
  "signal_id": "OS-AIT-001-WORKDAY",
  "signal_class": "unsupported_action",
  "description": "Workday AI auto-rejected Black disabled applicant 100+ times in minutes; nationwide class action certified",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L3"
  },
  "status": "adjudicated",
  "affected_domain": ["Lane_6"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "Academic_Paper",
    "citation": "Miami Law Review; Seyfarth Shaw; CDF Labor Law; Mobley v. Workday class certification May 2025"
  },
  "key_metrics": "1.1 billion applications rejected using Workday tools; class covers potentially millions of applicants",
  "pain_receipts": ["PR-AIT-001", "PR-AIT-005"],
  "fixers_available": ["DF-AIT-002", "DF-AIT-010"]
}
```

#### Pattern AI-003: Deepfake Romance Scam

```json
{
  "signal_id": "OS-AIT-007-BRADPITT",
  "signal_class": "unprovenanced_output",
  "description": "French interior designer lost $850K to Brad Pitt deepfake romance scam over 18 months",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L2"
  },
  "status": "reported",
  "affected_domain": ["Lane_6", "Lane_2"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "News_Media",
    "citation": "Q2 2025 Deepfake Incident Report"
  },
  "dollar_magnitude": 850000,
  "pain_receipts": ["PR-AIT-004", "PR-AIT-003"],
  "fixers_available": ["DF-AIT-006"]
}
```

#### Pattern AI-004: LLM Legal Hallucination Crisis

```json
{
  "signal_id": "OS-AIT-002-LEGALHALL",
  "signal_class": "fabrication_hallucination",
  "description": "LLMs hallucinate 58-88% on legal queries; court cases involving AI hallucinations accelerated 10->37->73+",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L3"
  },
  "status": "aggregate_only",
  "affected_domain": ["Lane_6"],
  "primary_source": {
    "source_tier": 1,
    "source_type": "Academic_Paper",
    "citation": "Stanford HAI Large Legal Fictions Study 2024-2025; FourDots AI Hallucination Impact Analysis"
  },
  "key_metrics": "10 cases (2023) -> 37 (2024) -> 73+ (Jan-May 2025); Lexis+ AI 17% hallucination, Westlaw AI 34%",
  "pain_receipts": ["PR-AIT-001", "PR-AIT-002"],
  "fixers_available": ["DF-AIT-003", "DF-AIT-007"]
}
```

#### Pattern AI-005: OpenClaw Agent Security Crisis

```json
{
  "signal_id": "OS-AIT-004-OPENCLAW",
  "signal_class": "improper_data_handling",
  "description": "Open-source AI assistant with 100K+ installations had plaintext API keys, no authentication; CVE-2025-53773 CVSS 9.6",
  "severity": {
    "tribunal_tier": "HONEY",
    "harm_level": "L2"
  },
  "status": "verified_technical",
  "affected_domain": ["Lane_6", "Lane_3"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "Security_Research",
    "citation": "Blackbird.ai OpenClaw/Moltbook Security Analysis; Penligent.ai analysis"
  },
  "key_metrics": "100K+ installations; 22% of enterprises had employees using as shadow AI; active crypto theft campaigns",
  "pain_receipts": ["PR-AIT-002", "PR-AIT-004"],
  "fixers_available": ["DF-AIT-001", "DF-AIT-004", "DF-AIT-005"]
}
```

#### Pattern AI-006: AI Vendor Liability Caps

```json
{
  "signal_id": "OS-AIT-005-VENDORCAP",
  "signal_class": "missing_receipts_accountability",
  "description": "88% of AI vendors impose liability caps; only 17% provide regulatory compliance warranties",
  "severity": {
    "tribunal_tier": "ROYAL_JELLY",
    "harm_level": "L2"
  },
  "status": "aggregate_only",
  "affected_domain": ["Lane_6"],
  "primary_source": {
    "source_tier": 2,
    "source_type": "Legal_Practice",
    "citation": "Jones Walker AI Vendor Liability Analysis, September 2025"
  },
  "pain_receipts": ["PR-AIT-005"],
  "fixers_available": ["DF-AIT-010"]
}
```

---

## 8. Example Fixer Pathways

### 8.1 Lane 1: Consumer Financial — 4 Pathways

#### Pathway CF-F01: Credit Reporting Error Resolution

```
Trigger: Consumer finds inaccurate information on credit report

Step 1: DF-FIN-002  CRA Direct Dispute (FCRA 611)
   |     File dispute with Equifax, Experian, and/or TransUnion
   |     Required: 45-day wait; new 2026 policy requires CRA first
   |
   +-- [Dispute resolved] ---> LEDGER_READY
   |
   +-- [Dispute unresolved] --->
        |
        v
Step 2: DF-FIN-001  CFPB Complaint Filing
        File complaint at consumerfinance.gov
        Required: Evidence of CRA dispute attempt
        |
        +-- [CFPB mediates successfully] ---> LEDGER_READY
        |
        +-- [Pattern affects many consumers] --->
             |
             v
Step 3: DF-FIN-006  Class Action or Regulatory Enforcement
             Potential CFPB enforcement action or class litigation
             |
             +-- [Settlement/order obtained] ---> LEDGER_READY
             |
             +-- [Pattern persists] ---> DF-FIN-005 Civil Penalty Fund Redress
                  |
                  v
             LEDGER_READY
```

**Example:** Equifax $15M settlement (2025) — consumer disputes failed, CFPB investigation, consent order.

#### Pathway CF-F02: Surprise Overdraft Fee Recovery

```
Trigger: Consumer charged overdraft fee despite sufficient funds at authorization

Step 1: DF-FIN-001  CFPB Complaint Filing
   |     Document transaction: date, amount, balance at authorization
   |     
   +-- [Bank voluntarily refunds] ---> LEDGER_READY
   |
   +-- [Bank refuses] --->
        |
        v
Step 2: DF-FIN-007  NSF Fee Elimination Claim
        If bank eliminated NSF fees after CFPB pressure (99% of large banks)
        Cite CFPB analysis showing $6.1B annual consumer savings
        |
        +-- [Bank refunds under pressure] ---> LEDGER_READY
        |
        +-- [Pattern at specific bank] --->
             |
             v
Step 3: DF-FIN-010  FBI Financial Fraud Kill Chain
             If high-dollar losses across multiple accounts
             IC3 Recovery Asset Team may freeze funds
             |
             v
         LEDGER_READY or NOT_LEDGER_READY (if below threshold)
```

**Example:** Regions Bank $141M refund, $15M penalty (2022) — CFPB consent order.

#### Pathway CF-F03: Identity Theft Recovery

```
Trigger: Consumer discovers identity theft

Step 1: DF-FIN-003  IdentityTheft.gov Reporting
   |     File report; receive recovery plan; place credit freeze
   |     
Step 2: DF-FIN-008  Credit Freeze/Lock
   |     Freeze credit at all three NCRAs simultaneously
   |     
Step 3: DF-FIN-004  FTC Fraud Reporting (if financial loss)
   |     Report at ReportFraud.ftc.gov
   |     
   +-- [Single incident] ---> LEDGER_READY
   |
   +-- [Pattern linked to data breach] --->
        |
        v
Step 4: DF-FIN-001  CFPB Complaint Filing
        If financial institution failed to protect data
        |
        v
    LEDGER_READY
```

**Example:** 1.1M identity theft reports to FTC (2024); credit freeze most effective fixer.

#### Pathway CF-F04: Investment Scam Response

```
Trigger: Consumer loses money to investment scam

Step 1: DF-FIN-004  FTC Fraud Reporting
   |     File at ReportFraud.ftc.gov; provide all documentation
   |
Step 2: DF-FIN-010  FBI IC3 Reporting (if cyber-enabled)
   |     File at ic3.gov; Recovery Asset Team for wire fraud
   |
   +-- [Within 24 hours] ---> 66% freeze success rate
   |
   +-- [Crypto-related] --->
        |
        v
Step 3: DF-FIN-004 + FBI Operation Level Up
        Proactive victim notification for crypto fraud
        8,000+ victims notified; $500M+ losses prevented
        |
        v
    LEDGER_READY
```

**Example:** $5.7B investment scam losses (FTC 2024); early reporting critical for recovery.

---

### 8.2 Lane 2: Fraud & Digital Loss — 4 Pathways

#### Pathway FD-F01: BEC Incident Response

```
Trigger: Business discovers BEC wire transfer fraud

Step 1: DF-FRD-R01  Financial Fraud Kill Chain (IMMEDIATE)
   |     Contact bank; request wire recall; file IC3 complaint
   |     CRITICAL: Must be within 24 hours for 66% freeze rate
   |
Step 2: DF-FRD-R02  FBI IC3 Reporting
   |     File detailed complaint at ic3.gov
   |     Include: email headers, wire instructions, timeline
   |
Step 3: DF-FRD-P03  Vendor Verification Protocol (PREVENTION)
   |     Implement out-of-band verification for all payment changes
   |     Phone verification required; no email-only changes
   |
   +-- [Funds recovered] ---> LEDGER_READY
   |
   +-- [Funds unrecoverable] --->
        |
        v
Step 4: DF-FRD-C02  Cyber Insurance Claim
        File claim for uncovered losses
        |
        v
    LEDGER_READY
```

**Example:** $4.9M real estate wire fraud recovered through FBI quick intervention (2024).

#### Pathway FD-F02: Ransomware Defense

```
Trigger: Ransomware attack detected

Step 1: DF-FRD-R04  Incident Response Plan
   |     Activate documented IR procedures
   |     Isolate affected systems; preserve evidence
   |
Step 2: DF-FRD-R05  Law Enforcement Engagement
   |     Report to FBI IC3; check for decryption keys available
   |     FBI distributed 7,000+ LockBit decryption keys
   |
   +-- [Decryption key available] ---> DF-FRD-R05 Restore
   |
   +-- [No key available] --->
        |
        +-- [Pay ransom?] NOT RECOMMENDED
        |    64% refused to pay (2025); 80% re-attacked within 12 months
        |    Only 4% recovered ALL data after paying
        |
        v
Step 3: DF-FRD-P09  Immutable Backup Restoration
        Restore from offline immutable backups
        53% of organizations fully recovered within one week (2025)
        |
        v
Step 4: DF-FRD-C02  Cyber Insurance Claim + DF-FRD-P01 EDR Hardening
        |
        v
    LEDGER_READY
```

**Example:** Change Healthcare paid $22M ransom but still faced secondary extortion.

#### Pathway FD-F03: Deepfake Fraud Prevention

```
Trigger: Organization detects or suspects deepfake fraud attempt

Step 1: DF-FRD-P04  Deepfake Detection Software
   |     Deploy AI-based detection for video/voice calls
   |     Human detection rates under 25% without tools
   |
Step 2: DF-FRD-P03  Out-of-Band Verification
   |     Phone callback to known number for any financial request
   |     Establish verification protocol before transaction
   |
Step 3: DF-FRD-P01  Multi-Factor Authentication
   |     Enforce MFA on all email, financial, admin accounts
   |     Prevents 99%+ of credential-based account takeover
   |
   +-- [Attempt prevented] ---> LEDGER_READY
   |
   +-- [Fraud successful] --->
        |
        v
Step 4: DF-FRD-R02  FBI IC3 Reporting
        File complaint; provide deepfake samples if available
        |
        v
    LEDGER_READY
```

**Example:** Arup $25M deepfake prevented by verification protocol; Ferrari CEO scam thwarted by knowledge question.

#### Pathway FD-F04: Romance/Pig Butchering Scam Response

```
Trigger: Victim or family member suspects romance investment scam

Step 1: DF-FRD-P04  Deepfake Detection (if video/voice involved)
   |     Analyze communications for AI-generated content
   |
Step 2: DF-FRD-R02  FBI IC3 Reporting + Local Law Enforcement
   |     File IC3 complaint; contact local FBI field office
   |     Document all financial transfers, communications
   |
Step 3: DF-FRD-C01  FTC Consumer Refunds (if settlement exists)
   |     Check for restitution programs
   |     Most victims never recover funds
   |
   +-- [Funds recoverable via Kill Chain] --->
        |
        v
Step 4: DF-FRD-R01  Financial Fraud Kill Chain
        If wire transfer within 24 hours
        |
        v
    LEDGER_READY
```

**Example:** Average pig butchering loss $100K+; recovery rate extremely low; prevention is primary fixer.

---

### 8.3 Lane 3: Cyber & AI System Risk — 4 Pathways

#### Pathway CY-F01: KEV Vulnerability Response

```
Trigger: CISA adds vulnerability to KEV catalog

Step 1: DF-CYB-001  CISA KEV Catalog Prioritization
   |     Check CISA BOD 22-01 requirements
   |     Federal agencies: remediate by specified due date
   |
Step 2: DF-CYB-003  Rapid Patch Management
   |     Prioritize patching based on exploitation timeline
   |     Average exploitation: negative one day from patch release
   |
   +-- [Patch available and deployable] --->
        |
        v
Step 3: DF-CYB-009  Behavior-Based EDR
        Deploy compensating controls during patch window
        Monitor for exploitation indicators
        |
        v
    LEDGER_READY
```

**Example:** CVE-2025-0282 (Ivanti): CISA KEV added Jan 8, 2025; deadline Jan 15, 2025.

#### Pathway CY-F02: AI Prompt Injection Defense

```
Trigger: AI application deployed or prompt injection suspected

Step 1: DF-CYB-007  Prompt Injection Defenses
   |     Architectural isolation: separate user instructions from untrusted content
   |     Implement privilege separation, constrained tool access
   |
Step 2: DF-CYB-006  OWASP LLM Top 10 Controls
   |     Apply LLM01-LLM10 controls based on risk assessment
   |     Input validation, parameterized prompts, output filtering
   |
Step 3: DF-CYB-010  AI Agent Safety Architecture
   |     Sandboxing, approval gates, action scope limits
   |     Runtime monitoring for anomalous behavior
   |
   +-- [Production deployment] --->
        |
        v
Step 4: DF-AIT-007  Red Teaming & Safety Evaluation (cross-lane)
        NIST ARIA program; systematic adversarial testing
        Target: ASR <5%, coverage >90%
        |
        v
    LEDGER_READY
```

**Example:** Microsoft 365 Copilot data exfiltration via prompt injection (Johann Rehberger, 2024).

#### Pathway CY-F03: Healthcare Data Breach Response

```
Trigger: Healthcare data breach detected

Step 1: DF-CYB-012  Healthcare-Specific Hardening
   |     Continuous third-party monitoring
   |     80%+ of healthcare breaches involve third parties
   |
Step 2: DF-CYB-011  Data-Centric Protection
   |     PHI encryption; tokenization of patient data
   |     Limits usefulness of exfiltrated data
   |
Step 3: DF-CYB-004  Ransomware Defense Suite
   |     Immutable offline backups; network segmentation
   |     53% recovered within one week with immutable backups (2025)
   |
Step 4: DF-CYB-003  Rapid Patch Management
   |     Critical: average healthcare breach containment 279 days
   |   (5 weeks longer than global average)
   |
   +-- [Breach contained] ---> LEDGER_READY
   |
   +-- [Regulatory notification required] --->
        |
        v
Step 5: HHS OCR Breach Notification
        742 breaches reported (2024); 289M+ individuals affected
        |
        v
    LEDGER_READY
```

**Example:** Change Healthcare (192.7M records); Synnovis/NHS London (one confirmed death).

#### Pathway CY-F04: AI Agent Governance Implementation

```
Trigger: Organization deploying AI agents at Tier 2+ autonomy

Step 1: DF-CYB-005  AI Governance Framework (NIST AI RMF)
   |     Apply GOVERN, MAP, MEASURE, MANAGE functions
   |     Agentic Profile extensions for autonomous systems
   |
Step 2: DF-AIT-008  Autonomy Tier Governance (cross-lane)
   |     Classify by tier: L1 (Fully Supervised) through L4 (Full Autonomy)
   |     Tier 4: oversight board review required
   |
Step 3: DF-AIT-010  Accountability Lineage (cross-lane)
   |     Agent accountability register
   |     Every action traceable to responsible human officer
   |
Step 4: DF-AIT-005  Behavioral Telemetry (cross-lane)
   |     Runtime monitoring: action velocity, escalation rate
   |     Cost tracking, exception rates, delegation depth
   |
   v
LEDGER_READY (when all controls documented and active)
```

**Example:** Perplexity Comet (L4-L5) had no safety evaluations; multiple prompt injection CVEs discovered.

---

### 8.4 Lane 4: Property & Contractor — 4 Pathways

#### Pathway PR-F01: Pre-Hiring Contractor Protection

```
Trigger: Consumer planning home improvement project

Step 1: DF-PRP-001  Pre-Hiring Verification Protocol
   |     Verify license through state licensing board
   |     Check disciplinary history; confirm insurance/bonding
   |     Contact 3+ recent references
   |
Step 2: DF-PRP-002  Contract Documentation
   |     Obtain written contract with: scope, materials, timeline
   |     California requires: payment schedule, 3-day right to cancel
   |     Florida: verify registration status
   |
Step 3: DF-PRP-003  Payment Protection
   |     Maximum 10-20% deposit (or $1,000, whichever is less)
   |     Tie payments to completion milestones
   |     Withhold 10-15% final payment until inspection pass
   |     Use credit card (not cash) for deposit dispute rights
   |
Step 4: DF-PRP-004  Evidence Preservation
   |     Before/during/after photos; save all correspondence
   |     Record license plates; note all workers on-site
   |
   v
LEDGER_READY (preventive pathway; no offense signal triggered)
```

**Example:** CFA recommends 3+ written estimates; never pay full amount upfront.

#### Pathway PR-F02: Contractor Nonperformance Recovery

```
Trigger: Contractor takes deposit and fails to perform

Step 1: DF-PRP-005  Regulatory Complaint — State Licensing Board
   |     File complaint with CSLB (CA), TNSBLC (TN), NSCB (NV)
   |     Primary channel: can issue citations, suspend/revoke license
   |
Step 2: DF-PRP-005  Regulatory Complaint — State Attorney General
   |     If deceptive practices involved
   |     IL AG saved $12M via mediation + $48M via enforcement (2024)
   |
   +-- [Licensed contractor] --->
        |
        v
Step 3: DF-PRP-005  Regulatory Complaint — CFPB (if financed)
        If home improvement financing involved
        |
        +-- [Unlicensed contractor] --->
             |
             v
Step 4: DF-PRP-006  Criminal Prosecution Pathway
             District Attorney referral; CSLB referred 1,066 cases (FY2024-25)
             Felony enhancement during state of emergency (FL)
             |
             v
         LEDGER_READY
```

**Example:** Cabinet company $10,237 deposit (FL) -> Hillsborough County mediation -> 50% refund.

#### Pathway PR-F03: Home Warranty Dispute Resolution

```
Trigger: Home warranty company denies legitimate claim

Step 1: DF-PRP-004  Evidence Preservation
   |     Document all maintenance records, service calls
   |     Preserve claim denial in writing with specific reason cited
   |
Step 2: DF-PRP-005  BBB Complaint + State DOI Complaint
   |     BBB tracks complaint patterns; may issue alerts
   |     State Department of Insurance for regulatory oversight
   |
Step 3: DF-PRP-008  Independent Repair + Insurance Claim
   |     Obtain independent estimate (not just warranty company's)
   |     If home insurance may cover: file homeowner claim
   |
   +-- [Pattern of denials documented] --->
        |
        v
Step 4: DF-PRP-005  FTC/CPSC Complaint
        For systematic deceptive practices
        FTC v. Choice Home Warranty precedent
        |
        v
    LEDGER_READY
```

**Example:** 49% claim satisfaction; FTC action against Choice Home Warranty for deceptive denials.

#### Pathway PR-F04: Post-Disaster Contractor Fraud Prevention

```
Trigger: Natural disaster declared; homeowners need emergency repairs

Step 1: DF-PRP-006  Post-Disaster Specific Protections
   |     Do NOT accept unsolicited repair offers
   |     Contact insurance company before hiring contractors
   |     Get multiple estimates; verify post-disaster licenses
   |
Step 2: DF-PRP-001  Accelerated Verification
   |     Check contractor has proper post-disaster authorization
   |     FL: unlicensed contracting is felony during emergency
   |
Step 3: DF-PRP-003  Enhanced Payment Protection
   |     Never pay full amount upfront (even for emergency work)
   |     Document all emergency repairs with photos
   |     Keep receipts for insurance reimbursement
   |
Step 4: DF-PRP-005  Multi-Agency Reporting
   |     Pinellas County model: multi-agency sting operations
   |     Report suspected unlicensed activity to law enforcement
   |
   v
LEDGER_READY
```

**Example:** FL post-hurricane: 100+ arrests, 150+ charges in multi-agency sting operations.

---

### 8.5 Lane 5: Asset & Compute — 4 Pathways

#### Pathway AS-F01: Counterfeit Hardware Detection

```
Trigger: Purchased high-value electronics; suspect counterfeit

Step 1: DF-AST-002  Benchmark Validation
   |     Run standardized benchmarks; compare to known-good results
   |     Significant deviation indicates counterfeit
   |
Step 2: DF-AST-001  Physical Inspection
   |     GPU/CPU: inspect PCB markings, component placement
   |     Delid if necessary to verify die markings (expert only)
   |
   +-- [Confirmed counterfeit] --->
        |
        v
Step 3: DF-AST-003  Serial Number & Warranty Verification
        Check manufacturer database for validity
        Counterfeit products excluded from warranty
        |
        v
Step 4: DF-AST-011  eBay/Platform Seller Protection
        Report counterfeit; file refund claim
        Ship only to verified addresses in future
        |
        v
    LEDGER_READY
```

**Example:** Fake AMD 9800X3D on Amazon.de; weight difference 7-8g; mismatched PCB numbers.

#### Pathway AS-F02: Enterprise Supply Chain Protection

```
Trigger: Enterprise procurement of networking/ compute equipment

Step 1: DF-AST-004  Authorized Distributor Procurement
   |     Source exclusively from manufacturer-authorized channels
   |     State Dept OIG fraud alert on grey market Cisco
   |
Step 2: DF-AST-005  AS6081/AS6171 Counterfeit Avoidance Testing
   |     Industry-standard testing for electronic components
   |     25% increase in counterfeit parts reported by ERAI
   |
Step 3: DF-AST-007  Cryptographic Hardware Attestation
   |     Silicon-level attestation for high-security environments
   |     Verify device authenticity via cryptographic signatures
   |
Step 4: DF-AST-012  SBOM/HBOM Documentation
   |     Software and Hardware Bill of Materials
   |     Component-level supply chain transparency
   |
   v
LEDGER_READY
```

**Example:** Pro Network $100M counterfeit Cisco reached F-15, F-22 fighter jet platforms.

#### Pathway AS-F03: Return Fraud Prevention for Sellers

```
Trigger: Seller of high-value electronics on marketplace platform

Step 1: DF-AST-011  eBay/Platform Seller Protection
   |     Ship only to verified PayPal/registered addresses
   |     Require signature confirmation for items >$750
   |
Step 2: DF-AST-008  Return Inspection Workflow
   |     Mandatory physical inspection before refund processing
   |     Photograph serial numbers before shipping
   |
Step 3: DF-AST-010  Fraud Detection Systems
   |     ML models to detect suspicious buyer patterns
   |     Amazon lawsuit against RBK refund fraud group
   |
   +-- [Return fraud detected] --->
        |
        v
Step 4: DF-AST-014  Independent Escrow & Inspection
        For high-value P2P transactions
        Third-party holding and verification services
        |
        v
    LEDGER_READY
```

**Example:** eBay RTX 5090 stripped of GPU die ($4,000 loss); Amazon v. REKK ($2.4M judgment).

#### Pathway AS-F04: Data Center Outage Prevention

```
Trigger: Data center planning reliability improvements

Step 1: DF-AST-009  Proof-of-Value Appraisal Packets
   |     Independent third-party appraisal of all equipment
   |     Document condition, specs, market value
   |
Step 2: DF-AST-006  Blockchain/Immutable Chain-of-Custody
   |     Cryptographic provenance tracking from manufacturer
   |     Ensures authentic components in supply chain
   |
Step 3: DF-AST-013  Visual AI Component Inspection
   |     Automated PCBA component inspection during assembly
   |     Detects counterfeit components before deployment
   |
   v
LEDGER_READY
```

**Example:** 54% of organizations report outage costs exceeding $100,000; power root cause of 54%.

---

### 8.6 Lane 6: AI Agent Trust — 4 Pathways

#### Pathway AI-F01: AI Hallucination Prevention

```
Trigger: Organization deploying AI for high-stakes information tasks

Step 1: DF-AIT-003  Output Verification
   |     Citation validation against authoritative sources
   |     Cross-reference with known databases
   |     RAG verification for grounded responses
   |
Step 2: DF-AIT-002  Human-in-the-Loop Gates
   |     Human review for all consequential outputs
   |     Structured escalation protocols
   |
Step 3: DF-AIT-007  Red Teaming & Safety Evaluation
   |     NIST ARIA program participation
   |     Target: ASR <5%, MTTC >100 hours
   |
   +-- [Legal setting] --->
        |
        v
Step 4: DF-AIT-006  Provenance Tracking
        C2PA content credentials for AI-generated content
        Tamper-proof chain of custody
        |
        v
    LEDGER_READY
```

**Example:** Stanford study: Lexis+ AI 17% hallucination, Westlaw AI 34%, GPT-4 43%.

#### Pathway AI-F02: Algorithmic Bias Mitigation

```
Trigger: AI used for hiring, lending, or other consequential decisions

Step 1: DF-AIT-007  Red Teaming & Safety Evaluation
   |     Adversarial testing across demographic groups
   |     Measure disparate impact metrics
   |
Step 2: DF-AIT-010  Accountability Lineage
   |     Register: business owner, technical owner, delegation authority
   |   (Required by NIST AG-GV.2, EU AI Act)
   |
Step 3: DF-AIT-002  Human-in-the-Loop for Decisions
   |     Mandatory human review before adverse action
   |   (Air Canada lesson: hybrid models outperform autonomous)
   |
   +-- [Disparate impact detected] --->
        |
        v
Step 4: Algorithmic Audit + Remediation
        Independent third-party algorithmic audit
        Remediation plan with measurable outcomes
        |
        v
    LEDGER_READY
```

**Example:** Mobley v. Workday: 1.1B applications rejected; class action certified May 2025.

#### Pathway AI-F03: AI Agent Security Hardening

```
Trigger: Deploying autonomous AI agents with tool access

Step 1: DF-AIT-008  Autonomy Tier Governance
   |     Classify by NIST 4-tier system
   |     Tier 1: human approval before any action
   |     Tier 4: oversight board review required
   |
Step 2: DF-AIT-009  Tool-Use Risk Management
   |     Inventory all tools by: consequence scope, reversibility
   |     Authentication requirements, compositional risk
   |
Step 3: DF-AIT-005  Behavioral Telemetry
   |     Runtime monitoring: action velocity, escalation rate
   |     Cost tracking, loop detection, exception rates
   |
Step 4: DF-AIT-004  Agent Decommissioning
   |     Documented triggers and procedures
   |   (Required for Tier 4 agents per NIST AG-GV.3)
   |
   v
LEDGER_READY
```

**Example:** OpenClaw: 100K+ installations, no authentication, CVE-2025-53773 CVSS 9.6.

#### Pathway AI-F04: Deepfake Fraud Defense

```
Trigger: Organization at risk of deepfake-enabled fraud

Step 1: DF-AIT-006  Content Provenance (C2PA)
   |     Implement C2PA content credentials
   |     Cryptographic chain of custody for media
   |
Step 2: DF-FRD-P04  Deepfake Detection Software
   |     Cross-lane fixer: AI-based video/voice detection
   |     Deploy at points of financial authorization
   |
Step 3: DF-FRD-P03  Out-of-Band Verification
   |     Cross-lane fixer: phone callback protocol
   |     Knowledge-based challenge questions
   |
   +-- [Suspected deepfake detected] --->
        |
        v
Step 4: DF-FRD-R02  FBI IC3 Reporting
        Document incident; preserve deepfake samples
        Contributes to pattern detection database
        |
        v
    LEDGER_READY
```

**Example:** $1.28B deepfake fraud losses (2025); Ferrari CEO thwarted via knowledge question.

---

## 9. Uncertainty, Contradiction & Missing Proof Labels

### 9.1 Uncertainty Framework

The ontology treats uncertainty as a first-class citizen. Every signal carries uncertainty metadata that affects its Tribunal classification and routing behavior.

#### Uncertainty Dimensions

| Dimension | Label | Description | Impact on Tier |
|-----------|-------|-------------|---------------|
| **Evidence Strength** | `evidence_strong` | Multiple independent Tier-1 sources confirm | No impact |
| | `evidence_moderate` | Single Tier-1 or multiple Tier-2 sources | Cap at ROYAL_JELLY |
| | `evidence_weak` | Tier-2 only; limited corroboration | Cap at JELLY |
| | `evidence_anecdotal` | Single report; no independent verification | Cap at JELLY; require HUMAN_REVIEW |
| **Attribution Confidence** | `attribution_confirmed` | Technical or legal confirmation of actor | No impact |
| | `attribution_probable` | Strong indicators but not definitive | Note in metadata |
| | `attribution_possible` | Some indicators; could be other actors | Degrade by 1 tier |
| | `attribution_unknown` | No meaningful attribution possible | No impact; flag gap |
| **Temporal Certainty** | `date_exact` | Precise date known | No impact |
| | `date_approximate` | Month or quarter known | Note in metadata |
| | `date_unknown` | No reliable date information | Cap at JELLY |
| **Financial Certainty** | `amount_confirmed` | Court order, settlement, or audit confirmed | No impact |
| | `amount_alleged` | Plaintiff/regulator allegation | Cap at ROYAL_JELLY |
| | `amount_estimated` | Third-party estimate | Note methodology |
| | `amount_unknown` | No reliable estimate available | Flag PROOF_GAP |

### 9.2 Contradiction Handling Protocol

When a CONTRADICTION is detected, the following protocol is executed:

#### Step 1: Contradiction Classification

| Contradiction Type | Definition | Example |
|-------------------|-----------|---------|
| `source_conflict` | Two credible sources report different facts | CFPB says $2B lost interest; Capital One says allegations unfounded |
| `stakeholder_dispute` | Affected parties disagree on harm scope | Industry groups say complaints "spurious"; consumer advocates say "massive issues" |
| `temporal_drift` | Same source reports different facts at different times | Equifax dispute confirmation rate changed dramatically over years |
| `jurisdictional_split` | Different legal/regulatory bodies reach different conclusions | CFPB dismissed Zelle case; NY AG pursuing EFTA claim |

#### Step 2: Automatic Actions

```
CONTRADICTION DETECTED
    |
    v
Step 1: Flag signal with CONTRADICTION label
    |
    v
Step 2: IMMEDIATE: Cap Tribunal tier at JELLY
    |     HONEY and ROYAL_JELLY signals demoted
    |
    v
Step 3: QUARANTINE if contradiction is source_conflict or stakeholder_dispute
    |     Prevent ledger inclusion until resolved
    |
    v
Step 4: SCHEDULE HUMAN_REVIEW within 72 hours
    |     Assign to domain expert or Tribunal auditor
    |
    v
Step 5: HUMAN_REVIEW determines:
         (a) Promote to previous tier + resolution notes
         (b) Maintain JELLY + document reasoning
         (c) Demote to PROPOLIS if risk warrants priority review
         (d) Maintain QUARANTINE with expiration date
```

#### Step 3: Contradiction Resolution Criteria

| Resolution | Requirements | Outcome |
|------------|-------------|---------|
| `resolved` | New primary evidence settles the dispute | Signal promoted; contradiction archived |
| `partially_resolved` | Partial clarification; remaining ambiguity documented | Signal remains JELLY; notes explain limits |
| `unresolved` | No new evidence; dispute persists | Signal remains quarantined or JELLY; auto-review in 90 days |

### 9.3 PROOF_GAP Taxonomy

PROOF_GAP labels are attached to signals where specific evidence is known to be missing.

#### Gap Severity Levels

| Level | Label | Description | Ledger Impact |
|-------|-------|-------------|---------------|
| 1 | `blocks_promotion` | Missing evidence prevents promotion to next tier | Signal cannot advance past current tier |
| 2 | `weakens_claim` | Missing evidence weakens but does not invalidate | Signal tier capped; notes explain limitation |
| 3 | `nice_to_have` | Additional evidence would strengthen but not change | No impact; documented for future research |

#### Common Proof Gap Patterns by Lane

| Lane | Common Gap | Gap ID Pattern | Obtainable? |
|------|-----------|---------------|-------------|
| L1 | Exact number of consumers affected by a specific fee scheme | `GAP-FIN-AFFECTED-N` | Often obtainable from consent orders |
| L1 | Individual dollar losses per consumer | `GAP-FIN-INDIVIDUAL-LOSS` | Sometimes; class action discovery |
| L1 | Recovery rate (what consumers actually received) | `GAP-FIN-RECOVERY-RATE` | Rarely; CFPB redress tracking |
| L2 | Scammer identity/location | `GAP-FRD-ACTOR-ID` | Rarely; law enforcement only |
| L2 | True fraud losses (accounting for underreporting) | `GAP-FRD-TRUE-LOSSES` | Estimated only (FTC: $195.9B vs $12.5B reported) |
| L2 | Deepfake detection without consumer knowledge | `GAP-FRD-DEEPFAKE-DETECT` | Emerging technology; limited |
| L3 | Exploitability of specific CVE in target environment | `GAP-CYB-EXPLOIT-CONFIRMED` | Sometimes; penetration testing |
| L3 | Full scope of data breach exfiltration | `GAP-CYB-BREACH-SCOPE` | Often limited by investigation quality |
| L3 | Nation-state attribution confidence | `GAP-CYB-APT-ATTRIBUTION` | Rarely public; classified |
| L4 | Municipal inspection failure rates (nationwide) | `GAP-PRP-INSPECTION-DATA` | Fragmented; not standardized |
| L4 | Contractor complaint volumes (all 50 states) | `GAP-PRP-COMPLAINT-VOLUME` | Partial; 41 of 200+ agencies surveyed |
| L4 | Home warranty claim denial rates by company | `GAP-PRP-DENIAL-RATES` | Fragmented across state DOIs |
| L5 | Counterfeit product origin and supply chain path | `GAP-AST-ORIGIN-TRACE` | Difficult; requires customs/law enforcement |
| L5 | Actual performance of counterfeit hardware (failure rate) | `GAP-AST-FAILURE-RATE` | Limited data; case-by-case |
| L6 | AI model decision rationale (explainability) | `GAP-AIT-EXPLAINABILITY` | Active research area; limited |
| L6 | Causal link between AI decision and specific harm | `GAP-AIT-CAUSAL-HARM` | Difficult; often correlation only |
| L6 | Prevalence of shadow AI in enterprise environments | `GAP-AIT-SHADOW-PREVALENCE` | Estimated; surveys indicate 22%+ |

### 9.4 Missing Proof Flag Lifecycle

```
PROOF_GAP Opened
    |
    v
Step 1: Attach to signal; set gap_severity level
    |
    v
Step 2: If gap_severity = blocks_promotion:
    |     Cap signal at current tier
    |     Add to research backlog
    |
Step 3: If gap_severity = weakens_claim:
    |     Add qualifier to signal description
    |     Include uncertainty language in all outputs
    |
Step 4: Monitor for gap-closing evidence
    |
    +-- [Evidence obtained] --->
    |        |
    |        v
    |    Update signal; remove or downgrade PROOF_GAP
    |    Recalculate Tribunal tier
    |
    +-- [Evidence unobtainable after 180 days] --->
             |
             v
         PROOF_GAP expires
         Signal retains limitation notes
         May be downgraded to aggregate_only
```

### 9.5 Handling Underreporting and Dark Figures

Many harm domains have massive underreporting. The ontology handles this explicitly:

| Lane | Reported vs. Estimated | Handling |
|------|----------------------|----------|
| L1 | CFPB complaints vs. actual harmed consumers | Report both figures; label as aggregate_only when using estimates |
| L2 | IC3 $20.877B vs. FTC-estimated $195.9B true losses | Signal status = aggregate_only; note estimation methodology |
| L3 | Reported breaches vs. unreported/unobserved | Use HHS OCR minimums; flag PROOF_GAP for unreported |
| L4 | Surveyed agency complaints vs. actual nationwide | Report coverage limits (41 of 200+ agencies) |
| L5 | Detected counterfeits vs. actual circulation | Use seizure data minimums; flag as lower bound |
| L6 | Documented court cases vs. actual AI failures | Report documented minimums; note accelerating trend |

**Rule:** When both reported and estimated figures exist, the ontology stores both. The Tribunal uses reported figures for HONEY classification and estimated figures for PROPOLIS risk assessment.

---

## 10. Schema Field Cross-Reference

### 10.1 Ontology Labels to JSON Schema Fields

The following table maps each ontology label to its corresponding field in the DefendableOS JSON schema.

#### Core Entity Fields

| Ontology Label | JSON Path | Type | Required | Description |
|----------------|-----------|------|----------|-------------|
| `signal_id` | `$.offense_signal.id` | string (UUID) | Yes | Canonical signal identifier |
| `signal_class` | `$.offense_signal.class` | string (enum) | Yes | Lane-specific signal subclass |
| `OFFENSE_SIGNAL` | `$.offense_signal` | object | Yes | Root object for offense data |
| `description` | `$.offense_signal.description` | string | Yes | Human-readable pattern description |
| `severity.tribunal_tier` | `$.offense_signal.tribunal_tier` | string (enum) | Yes | HONEY / ROYAL_JELLY / JELLY / PROPOLIS |
| `severity.harm_level` | `$.offense_signal.harm_level` | integer (1-4) | Yes | 1=informational, 4=critical |
| `status` | `$.offense_signal.status` | string (enum) | Yes | alleged / reported / admitted / settled / adjudicated / verified_technical / aggregate_only / unknown |
| `affected_domain` | `$.offense_signal.lanes[]` | string[] | Yes | Lane_1 through Lane_6 |
| `dollar_magnitude` | `$.offense_signal.dollar_magnitude` | decimal | No | Estimated or confirmed financial impact |
| `first_observed` | `$.offense_signal.first_observed` | date | No | Earliest documented occurrence |
| `last_confirmed` | `$.offense_signal.last_confirmed` | date | No | Most recent confirmed occurrence |
| `repeat_offender` | `$.offense_signal.repeat_offender` | boolean | No | Whether actor has prior enforcement |

#### Pain Receipt Fields

| Ontology Label | JSON Path | Type | Required | Description |
|----------------|-----------|------|----------|-------------|
| `PAIN_RECEIPT` | `$.pain_receipts[]` | array | No | Array of pain receipt objects |
| `receipt_id` | `$.pain_receipts[].id` | string (UUID) | Yes* | Canonical receipt identifier |
| `parent_signal` | `$.pain_receipts[].signal_id` | string (UUID) | Yes* | Reference to parent signal |
| `receipt_type` | `$.pain_receipts[].type` | string (enum) | Yes* | monetary / operational / reputational / physical / psychological / regulatory |
| `affected_party` | `$.pain_receipts[].affected_party` | string | No | Who experienced the pain |
| `quantified_impact` | `$.pain_receipts[].quantified_impact` | decimal | No | Measured harm amount |
| `impact_units` | `$.pain_receipts[].impact_units` | string | No | USD, records, days, percent |
| `attribution_confidence` | `$.pain_receipts[].attribution_confidence` | string (enum) | No | confirmed / probable / possible / unverified |

*Required when pain_receipts array is non-empty.

#### Defense Fixer Fields

| Ontology Label | JSON Path | Type | Required | Description |
|----------------|-----------|------|----------|-------------|
| `DEFENSE_FIXER` | `$.defense_fixers[]` | array | No | Array of fixer objects |
| `fixer_id` | `$.defense_fixers[].id` | string (UUID) | Yes* | Canonical fixer identifier |
| `fixer_class` | `$.defense_fixers[].class` | string (enum) | Yes* | prevention / detection / response / recovery / policy / governance / technical |
| `applicable_signals` | `$.defense_fixers[].applicable_signals[]` | string[] | No | Signal IDs this fixer addresses |
| `effectiveness_evidence` | `$.defense_fixers[].effectiveness` | string | No | Documentation of effectiveness |
| `implementation_cost` | `$.defense_fixers[].cost` | string (enum) | No | Low / Medium / High / Variable |
| `time_to_effect` | `$.defense_fixers[].time_to_effect` | string (enum) | No | Immediate / Hours / Days / Weeks / Months |
| `requires_human` | `$.defense_fixers[].requires_human` | boolean | No | Whether human intervention needed |
| `automation_level` | `$.defense_fixers[].automation` | string (enum) | No | fully_automated / semi_automated / manual |

*Required when defense_fixers array is non-empty.

#### Source Receipt Fields

| Ontology Label | JSON Path | Type | Required | Description |
|----------------|-----------|------|----------|-------------|
| `SOURCE_RECEIPT` | `$.sources[]` | array | Yes | Array of source objects |
| `source_id` | `$.sources[].id` | string (UUID) | Yes | Canonical source identifier |
| `source_tier` | `$.sources[].tier` | integer (1-4) | Yes | 1=Primary, 2=Secondary, 3=Tertiary, 4=Unverified |
| `source_type` | `$.sources[].type` | string (enum) | Yes | Type of source (see Section 5) |
| `url` | `$.sources[].url` | string (URL) | No | Permanent or archive URL |
| `access_date` | `$.sources[].access_date` | date | No | Last verification date |
| `corpus_score` | `$.sources[].corpus_score` | integer (0-10) | No | Corpus inclusion fitness score |

#### Quality Control Fields

| Ontology Label | JSON Path | Type | Required | Description |
|----------------|-----------|------|----------|-------------|
| `PROOF_GAP` | `$.proof_gaps[]` | array | No | Open proof gaps |
| `gap_id` | `$.proof_gaps[].id` | string (UUID) | Yes* | Gap identifier |
| `missing_evidence` | `$.proof_gaps[].description` | string | Yes* | What's missing |
| `gap_severity` | `$.proof_gaps[].severity` | string (enum) | Yes* | blocks_promotion / weakens_claim / nice_to_have |
| `CONTRADICTION` | `$.contradictions[]` | array | No | Active contradictions |
| `contradiction_id` | `$.contradictions[].id` | string (UUID) | Yes* | Contradiction identifier |
| `contradiction_type` | `$.contradictions[].type` | string (enum) | Yes* | source_conflict / stakeholder_dispute / temporal_drift / jurisdictional_split |
| `resolution_status` | `$.contradictions[].resolution` | string (enum) | Yes* | unresolved / partially_resolved / resolved |
| `HUMAN_REVIEW` | `$.human_reviews[]` | array | No | Human review records |
| `QUARANTINED_SIGNAL` | `$.quarantine` | object | No | Quarantine status if applicable |
| `VERIFIED_FINDING` | `$.verified_finding` | object | No | Verification record if applicable |

*Required when parent array/object is present.

#### Tribunal & Ledger Fields

| Ontology Label | JSON Path | Type | Required | Description |
|----------------|-----------|------|----------|-------------|
| `ALLEGED_HARM` | `$.offense_signal.harm_type` | string (enum) | No | alleged / documented / verified |
| `RESOLUTION_PATH` | `$.resolution_path` | object | No | Fixer chain and outcome |
| `LEDGER_READY` | `$.ledger.ready` | boolean | Yes | Whether signal is ledger-ready |
| `LEDGER_READY.completeness_score` | `$.ledger.completeness_score` | integer (0-100) | No | Completeness percentage |
| `NOT_LEDGER_READY` | `$.ledger.blockers[]` | array | No | Reasons not ledger-ready |

### 10.2 Schema Validation Rules

| Rule | Condition | Validation |
|------|-----------|------------|
| `VAL-R01` | `tribunal_tier = HONEY` | Requires `status` in (settled, adjudicated, verified_technical); Requires >=2 Tier-1 sources; Requires HUMAN_REVIEW record |
| `VAL-R02` | `tribunal_tier = ROYAL_JELLY` | Requires `status` in (reported, admitted, settled); Requires >=1 Tier-1 source or >=2 Tier-2 sources |
| `VAL-R03` | `tribunal_tier = JELLY` | No minimum source tier; Requires at least one credible source; CONTRADICTION present auto-caps at JELLY |
| `VAL-R04` | `tribunal_tier = PROPOLIS` | Requires HUMAN_REVIEW record; harm_level must be 3 or 4 |
| `VAL-R05` | `harm_level = 4` | Requires HUMAN_REVIEW record regardless of tier; Auto-flags for Tribunal priority |
| `VAL-R06` | `status = alleged` | Must have ALLEGED_HARM record; Must have reporter_type |
| `VAL-R07` | `repeat_offender = true` | Must document prior enforcement actions; Auto-escalates tier by 1 |
| `VAL-R08` | `CONTRADICTION` present | `tribunal_tier` cannot be HONEY; If unresolved, cap at JELLY |
| `VAL-R09` | `PROOF_GAP.severity = blocks_promotion` | `tribunal_tier` cannot be promoted until gap closed |
| `VAL-R10` | `ledger.ready = true` | All required fields populated; No unresolved CONTRADICTION; No blocks_promotion gaps; completeness_score >= 80 |

### 10.3 Example Complete JSON Object

```json
{
  "schema_version": "1.0.0",
  "record_id": "defendable-os-rec-001",
  "created_at": "2026-05-25T00:00:00Z",
  "updated_at": "2026-05-25T00:00:00Z",
  "offense_signal": {
    "id": "OS-FIN-002-REGIONS",
    "class": "surprise_overdraft_fees",
    "parent_label": "OFFENSE_SIGNAL",
    "description": "Regions Bank charged consumers overdraft fees on debit card and ATM transactions even when consumers had sufficient funds at the time of authorization",
    "tribunal_tier": "HONEY",
    "harm_level": 3,
    "status": "settled",
    "lanes": ["Lane_1"],
    "dollar_magnitude": 141000000,
    "dollar_currency": "USD",
    "first_observed": "2018-08-01",
    "last_confirmed": "2021-07-31",
    "repeat_offender": false,
    "harm_type": "documented"
  },
  "pain_receipts": [
    {
      "id": "PR-FIN-001-REGIONS",
      "parent_label": "PAIN_RECEIPT",
      "signal_id": "OS-FIN-002-REGIONS",
      "type": "monetary",
      "description": "Consumers paid $141 million in surprise overdraft fees",
      "affected_party": "Consumers with checking accounts at Regions Bank (Alabama-based, 16 states)",
      "quantified_impact": 141000000,
      "impact_units": "USD",
      "attribution_confidence": "confirmed"
    },
    {
      "id": "PR-FIN-008-REGIONS",
      "parent_label": "PAIN_RECEIPT",
      "signal_id": "OS-FIN-002-REGIONS",
      "type": "psychological",
      "description": "Consumers unable to understand fee structures; bank employees could not explain fees",
      "attribution_confidence": "confirmed"
    }
  ],
  "defense_fixers": [
    {
      "id": "DF-FIN-001",
      "parent_label": "DEFENSE_FIXER",
      "class": "response",
      "name": "CFPB Complaint Filing",
      "description": "Consumer files complaint with CFPB after direct resolution failed",
      "applicable_signals": ["OS-FIN-002"],
      "effectiveness": "CFPB forwards to company; company responds; 99.6% timely response rate",
      "cost": "Low",
      "time_to_effect": "Days",
      "requires_human": true,
      "automation": "semi_automated"
    },
    {
      "id": "DF-FIN-005",
      "parent_label": "DEFENSE_FIXER",
      "class": "recovery",
      "name": "Civil Penalty Fund Redress",
      "description": "Consumer harmed by company subject to CFPB enforcement may receive redress from Civil Penalty Fund",
      "applicable_signals": ["OS-FIN-002"],
      "cost": "Low",
      "time_to_effect": "Months",
      "requires_human": false,
      "automation": "manual"
    },
    {
      "id": "DF-FIN-007",
      "parent_label": "DEFENSE_FIXER",
      "class": "prevention",
      "name": "NSF Fee Elimination",
      "description": "99% of large banks eliminated NSF fees after CFPB pressure; $6.1B annual consumer savings",
      "applicable_signals": ["OS-FIN-002"],
      "cost": "Low",
      "time_to_effect": "Immediate",
      "requires_human": false,
      "automation": "fully_automated"
    }
  ],
  "sources": [
    {
      "id": "SRC-001",
      "parent_label": "SOURCE_RECEIPT",
      "tier": 1,
      "type": "Regulatory_Action",
      "citation": "CFPB Consent Order against Regions Bank, September 28, 2022",
      "url": "https://files.consumerfinance.gov/f/documents/cfpb_Regions_Bank-_Consent-Order_2022-09.pdf",
      "access_date": "2026-05-25",
      "corpus_score": 10
    }
  ],
  "proof_gaps": [],
  "contradictions": [],
  "human_reviews": [
    {
      "id": "HR-001",
      "parent_label": "HUMAN_REVIEW",
      "subject_signal": "OS-FIN-002-REGIONS",
      "reviewer_role": "auditor",
      "review_type": "promotion_review",
      "outcome": "promote",
      "review_date": "2026-05-25",
      "notes": "Consent order is self-authenticating. Primary source. Meets HONEY criteria."
    }
  ],
  "quarantine": null,
  "verified_finding": {
    "id": "VF-001",
    "parent_label": "VERIFIED_FINDING",
    "verification_method": "regulatory_action",
    "verifying_authority": "Consumer Financial Protection Bureau",
    "verification_date": "2022-09-28"
  },
  "resolution_path": {
    "id": "RP-001",
    "parent_label": "RESOLUTION_PATH",
    "start_signal": "OS-FIN-002-REGIONS",
    "fixer_chain": ["DF-FIN-001", "DF-FIN-005"],
    "actual_outcome": "CFPB consent order: $141M consumer refunds, $15M civil penalty, $50M in additional penalties",
    "outcome_status": "resolved"
  },
  "ledger": {
    "ready": true,
    "completeness_score": 95,
    "ingested_at": "2026-05-25T00:00:00Z",
    "ledger_id": "LEDGER-001"
  }
}
```

### 10.4 Index of Required Top-Level Labels

All 12 required top-level labels appear in the ontology as follows:

| Required Label | Section | JSON Path |
|----------------|---------|-----------|
| `OFFENSE_SIGNAL` | 2.2 | `$.offense_signal` |
| `PAIN_RECEIPT` | 2.2 | `$.pain_receipts[]` |
| `DEFENSE_FIXER` | 2.2 | `$.defense_fixers[]` |
| `SOURCE_RECEIPT` | 2.2 | `$.sources[]` |
| `PROOF_GAP` | 2.2, 9.3 | `$.proof_gaps[]` |
| `CONTRADICTION` | 2.2, 9.2 | `$.contradictions[]` |
| `HUMAN_REVIEW` | 2.2, 9.2 | `$.human_reviews[]` |
| `QUARANTINED_SIGNAL` | 2.2 | `$.quarantine` |
| `VERIFIED_FINDING` | 2.2 | `$.verified_finding` |
| `ALLEGED_HARM` | 2.2 | `$.offense_signal.harm_type` |
| `RESOLUTION_PATH` | 2.2 | `$.resolution_path` |
| `LEDGER_READY` | 2.2 | `$.ledger.ready` |
| `NOT_LEDGER_READY` | 2.2 | `$.ledger.blockers[]` |

---

## Appendix A: Cross-Lane Composite Signals

Some signals span multiple lanes. The ontology handles these through multi-lane classification.

| Composite Signal ID | Lanes | Description | Example |
|--------------------|-------|-------------|---------|
| `COMP-001` | L1 + L2 | Financial fraud using synthetic identity | Synthetic identity opens bank account, then applies for loans |
| `COMP-002` | L2 + L3 | Deepfake-enabled credential theft | Deepfake voice passes bank biometric, enabling account takeover |
| `COMP-003` | L3 + L6 | AI agent vulnerability exploited for data breach | Prompt injection exfiltrates PHI from healthcare AI system |
| `COMP-004` | L4 + L1 | Home improvement financing fraud | Contractor partners with predatory lender; deceptive PACE liens |
| `COMP-005` | L5 + L3 | Counterfeit networking equipment in critical infrastructure | Fake Cisco switches in hospital network, creating vulnerability |
| `COMP-006` | L6 + L2 | AI-generated content used for investment scam | LLM creates fake whitepaper for crypto Ponzi scheme |

---

## Appendix B: Tribunal Classification Quick Reference

| Classification | Quality Tier | Harm Level | Auto-Promote | Auto-Quarantine | Human Review Required |
|---------------|-------------|-----------|-------------|----------------|----------------------|
| HONEY | T1 | Any | No | No | Yes (for promotion) |
| ROYAL_JELLY | T2 | L2-L3 | No | No | No (but recommended for L3) |
| JELLY | T3 | L1-L2 | No | If contradiction | No |
| PROPOLIS | T4 | L3-L4 | No | No (already reviewed) | Yes |

---

## Appendix C: Change Log

| Version | Date | Changes |
|---------|------|---------|
| 1.0.0 | 2026-05-25 | Initial canonical release. Covers 6 lanes, 12 parent classes, 60+ offense signals, 60+ pain receipts, 50+ defense fixers. |

---

*This document is canonical for the DefendableOS ecosystem. All engineers, auditors, and automated systems must conform to the vocabulary, classifications, and validation rules specified herein. Updates require Tribunal approval and version increment.*

*Document compiled: May 25, 2026*
*Sources: 200+ Tier 1 and Tier 2 authoritative sources across 6 research lanes*
*Signals documented: 60+ offense signals, 60+ pain receipts, 50+ defense fixers*
*Incidents cataloged: 200+ specific real-world patterns*
