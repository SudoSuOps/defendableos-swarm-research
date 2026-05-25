# 03 Source Ranking and Acquisition Plan

## DefendableOS Research Corpus

**Document Version:** 1.0  
**Date:** May 25, 2026  
**Sources Evaluated:** 172  
**Scoring Dimensions:** 7  
**Composite Formula:** Evidence(25%) + Pain Density(15%) + Fixer Potential(15%) + Safety(15%) + Automation(10%) + Commercial(10%) + Ledger(10%)  

---

## 1. Ranking Methodology

### 1.1 Scoring Dimensions (1-10 Each)

| Dimension | Weight | Description | Criteria for High Scores |
|-----------|--------|-------------|-------------------------|
| **Evidence Strength** | 25% | Source reliability, authority, and evidentiary value | Tier 1 primary authority (government, court, standard body) with confirmed provenance |
| **Pain Density** | 15% | Concentration of documented consumer harm signals | Contains narratives + dollar losses + outcomes; enforcement actions with restitution data |
| **Defense Fixer Potential** | 15% | Actionability for consumer defense pathways | Contains remedies, regulatory actions, defense frameworks, complaint procedures |
| **Corpus Safety** | 15% | Suitability for ingestion without legal or privacy risk | Low PII risk, primary authority, structured access, clear licensing |
| **Automation Potential** | 10% | Ease of automated or semi-automated data collection | API/CSV/JSON formats; regular update cadence; no auth barriers |
| **Commercial Relevance** | 10% | Product relevance for DefendableOS consumer protection platform | Consumer-facing lanes (financial, fraud, property), dollar losses, enforcement outcomes |
| **Ledger Readiness** | 10% | Readiness for structured ledger ingestion with minimal preprocessing | Ledger-ready recommendation, outcomes, dollar data, primary source |

### 1.2 Composite Priority Score Formula

```
Priority Score = (Evidence x 0.25) + (Pain Density x 0.15) + (Fixer Potential x 0.15) 
               + (Corpus Safety x 0.15) + (Automation x 0.10) + (Commercial x 0.10) 
               + (Ledger x 0.10)
```

### 1.3 Score Interpretation

| Score Range | Tier | Action |
|-------------|------|--------|
| 7.0 - 10.0 | **Top Tier** | Ingest first — highest value, lowest risk |
| 5.0 - 6.9 | **Second Tier** | Ingest second — valuable but may need preprocessing |
| 4.0 - 4.9 | **Monitor Tier** | Valuable for ongoing monitoring, lower immediate priority |
| 3.0 - 3.9 | **Manual Review** | Requires human assessment before ingestion |
| < 3.0 | **Quarantine** | Exclude pending further analysis |

### 1.4 Distribution Summary

| Tier | Score Range | Count | Percentage |
|------|-------------|-------|------------|
| Top Tier | 7.0+ | 44 | 25.6% |
| Second Tier | 5.0-6.9 | 97 | 56.4% |
| Monitor Tier | 4.0-4.9 | 31 | 18.0% |
| Manual Review | 3.0-3.9 | 0 | 0.0% |
| Quarantine | < 3.0 | 0 | 0.0% |
| **Total** | | **172** | **100%** |

---

## 2. Top Tier Sources (Ingest First) — Score 7.0+

These 44 sources represent the highest-value, lowest-risk ingestion targets. They combine strong evidence authority, documented consumer harm with dollar amounts, defense fixer pathways, and favorable automation characteristics.

## 2. Top Tier Sources (Ingest First) — Score 7.0+

These 44 sources represent the highest-value, lowest-risk ingestion targets. They combine strong evidence authority, documented consumer harm with dollar amounts, defense fixer pathways, and favorable automation characteristics.

### Top Tier Complete Listing Sources

| ID | Source Name | Lane | E | P | F | S | A | C | L | **Score** | Action |
|----|-------------|------|---|---|---|---|---|---|---|-----------|--------|
| SRC-FIN-001 | CFPB Consumer Complaint Database | FIN | 9 | 10 | 10 | 5 | 10 | 10 | 10 | **9.0** | Ingest |
| SRC-FIN-005 | CFPB Enforcement by the Numbers | FIN | 9 | 7 | 10 | 8 | 8 | 10 | 10 | **8.8** | Ingest |
| SRC-FIN-004 | CFPB Enforcement Actions Database | FIN | 9 | 10 | 10 | 8 | 3 | 10 | 10 | **8.75** | Ingest |
| SRC-PRP-006 | Minnesota DLI Enforcement Actions | PRP | 9 | 10 | 10 | 8 | 4 | 9 | 10 | **8.75** | Ingest |
| SRC-AST-011 | CPSC Recall Record 2025 | AST | 9 | 8 | 7 | 9 | 9 | 9 | 10 | **8.65** | Ingest |
| SRC-PRP-004 | FTC Ygrene Enforcement Action | PRP | 9 | 10 | 10 | 8 | 1 | 9 | 10 | **8.45** | Ingest |
| SRC-AST-001 | DOJ Onur Aksoy Counterfeit Cisco Sentencing | AST | 9 | 10 | 10 | 8 | 1 | 9 | 10 | **8.45** | Ingest |
| SRC-AST-007 | Amazon RBK Refund Fraud Lawsuit | AST | 9 | 8 | 10 | 8 | 4 | 9 | 10 | **8.45** | Ingest |
| SRC-FIN-002 | CFPB Consumer Response Annual Report 2025 | FIN | 8 | 7 | 9 | 8 | 8 | 10 | 10 | **8.4** | Ingest |
| SRC-FRA-001 | FBI IC3 2025 Internet Crime Report | FRA | 8 | 7 | 9 | 8 | 8 | 10 | 10 | **8.4** | Ingest |
| SRC-FRA-002 | FBI IC3 2024 Internet Crime Report | FRA | 8 | 7 | 9 | 8 | 8 | 10 | 10 | **8.4** | Ingest |
| SRC-AST-008 | REKK Refund Fraud Judgment | AST | 9 | 8 | 10 | 8 | 3 | 9 | 10 | **8.35** | Ingest |
| SRC-AIA-003 | OECD AI Incidents Monitor Trends | AIA | 9 | 7 | 6 | 9 | 10 | 8 | 10 | **8.35** | Ingest |
| SRC-PRP-014 | Nevada State Contractors Board | PRP | 8 | 10 | 9 | 8 | 2 | 9 | 10 | **8.15** | Ingest |
| SRC-PRP-015 | North Carolina Licensing Board for General Co... | PRP | 8 | 10 | 9 | 8 | 2 | 9 | 10 | **8.15** | Ingest |
| SRC-FIN-008 | FTC ExploreData Dashboards | FIN | 7 | 7 | 6 | 9 | 10 | 10 | 10 | **8.05** | Ingest |
| SRC-FRA-007 | FTC Annual Report Protecting Older Adults 202... | FRA | 8 | 7 | 9 | 8 | 4 | 10 | 10 | **8.0** | Ingest |
| SRC-FIN-006 | FTC Consumer Sentinel Network Data Book 2024 | FIN | 8 | 7 | 6 | 8 | 8 | 10 | 10 | **7.95** | Ingest |
| SRC-FRA-004 | FTC Consumer Sentinel Network Data Book 2024 | FRA | 8 | 7 | 6 | 8 | 8 | 10 | 10 | **7.95** | Ingest |
| SRC-CYB-001 | CISA KEV Catalog | CYB | 9 | 2 | 9 | 9 | 10 | 7 | 10 | **7.95** | Ingest |
| SRC-FRA-003 | FBI Press Release Crypto and AI Scams | FRA | 8 | 7 | 9 | 8 | 3 | 10 | 10 | **7.9** | Ingest |
| SRC-FRA-005 | SEC Enforcement Results FY2025 | FRA | 8 | 7 | 9 | 8 | 3 | 10 | 10 | **7.9** | Ingest |
| SRC-PRP-002 | California CSLB FY 2024-25 Enforcement Report | PRP | 8 | 7 | 9 | 8 | 4 | 9 | 10 | **7.9** | Ingest |
| SRC-CYB-005 | HHS OCR Breach Portal | CYB | 9 | 7 | 6 | 5 | 10 | 9 | 10 | **7.85** | Ingest |
| SRC-PRP-003 | Tennessee State Board for Licensing Contracto... | PRP | 8 | 7 | 9 | 8 | 3 | 9 | 10 | **7.8** | Ingest |
| SRC-AST-012 | FTC Protecting Older Consumers 2024-2025 | AST | 8 | 7 | 8 | 8 | 4 | 9 | 10 | **7.75** | Ingest |
| SRC-PRP-005 | Illinois AG Top 10 Complaints 2024 | PRP | 8 | 7 | 9 | 8 | 2 | 9 | 10 | **7.7** | Ingest |
| SRC-PRP-009 | Consumer Federation of America 2024 Complaint... | PRP | 6 | 10 | 9 | 7 | 4 | 8 | 10 | **7.6** | Ingest |
| SRC-FIN-003 | CFPB FCRA 611(e) Annual Report | FIN | 8 | 7 | 6 | 8 | 4 | 10 | 10 | **7.55** | Ingest |
| SRC-FIN-007 | FTC IdentityTheft.gov | FIN | 7 | 10 | 5 | 5 | 10 | 10 | 8 | **7.55** | Ingest |
| SRC-FIN-013 | GAO CFPB Financial Audit FY2025 | FIN | 8 | 7 | 6 | 8 | 4 | 10 | 10 | **7.55** | Ingest |
| SRC-FIN-019 | FTC Protecting Older Adults Report 2024-2025 | FIN | 8 | 7 | 6 | 8 | 4 | 10 | 10 | **7.55** | Ingest |
| SRC-FRA-017 | FTC Social Media Scam Losses | FRA | 8 | 7 | 6 | 8 | 4 | 10 | 10 | **7.55** | Ingest |
| SRC-PRP-001 | CFPB Consumer Response Annual Report 2024 | PRP | 8 | 7 | 6 | 8 | 4 | 9 | 10 | **7.45** | Ingest |
| SRC-CYB-003 | MITRE ATT&CK Framework | CYB | 9 | 2 | 6 | 9 | 10 | 7 | 9 | **7.4** | Ingest |
| SRC-PRP-007 | Lex Machina Insurance Litigation Report 2025 | PRP | 8 | 7 | 6 | 8 | 3 | 9 | 10 | **7.35** | Ingest |
| SRC-PRP-008 | NCS Credit Lien Index Q3 2025 | PRP | 6 | 7 | 7 | 7 | 8 | 8 | 10 | **7.25** | Ingest |
| SRC-FIN-009 | CFPB FDCPA Annual Report 2025 | FIN | 8 | 7 | 5 | 8 | 4 | 10 | 8 | **7.2** | Ingest |
| SRC-FIN-010 | Federal Reserve Consumer Complaint Data | FIN | 8 | 7 | 5 | 8 | 4 | 10 | 8 | **7.2** | Ingest |
| SRC-FIN-018 | FTC National Do Not Call Registry Data Book F... | FIN | 8 | 7 | 5 | 8 | 4 | 10 | 8 | **7.2** | Ingest |
| SRC-AST-009 | Singapore Nvidia Chip Smuggling Case | AST | 7 | 6 | 7 | 8 | 4 | 9 | 10 | **7.2** | Ingest |
| SRC-CYB-004 | IBM Cost of Data Breach Report 2025 | CYB | 8 | 7 | 5 | 8 | 3 | 8 | 10 | **7.1** | Ingest |
| SRC-AST-003 | NIST AMD Trust and Provenance Workshop | AST | 8 | 7 | 5 | 8 | 2 | 9 | 10 | **7.1** | Ingest |
| SRC-CYB-007 | AHA Change Healthcare Report | CYB | 8 | 7 | 5 | 8 | 2 | 8 | 10 | **7.0** | Ingest |
---

## 3. Second Tier (Ingest Second) — Score 5.0-6.9

These 97 sources are valuable for the corpus but may require preprocessing, format conversion, or additional legal review before ingestion. Many are Tier 2 secondary sources that provide essential context and trend analysis but lack the direct evidentiary weight of primary sources.

**Recommended approach:** Batch-process these sources after Top Tier ingestion is complete. Prioritize within this tier by automation score.

### Second Tier — Highest-Priority Subset (25 of 97) Sources

| ID | Source Name | Lane | E | P | F | S | A | C | L | **Score** | Action |
|----|-------------|------|---|---|---|---|---|---|---|-----------|--------|
| SRC-AIA-002 | EU AI Act Portal | AIA | 8 | 2 | 10 | 8 | 4 | 6 | 9 | **6.9** | Preprocess |
| SRC-CYB-011 | MIT AI Agent Index 2025 | CYB | 9 | 2 | 5 | 9 | 8 | 7 | 7 | **6.85** | Preprocess |
| SRC-AIA-001 | NIST AI RMF Agentic Profile | AIA | 8 | 2 | 10 | 8 | 3 | 6 | 9 | **6.8** | Preprocess |
| SRC-AST-004 | Tom's Hardware Counterfeit RTX 4090 | AST | 7 | 6 | 4 | 8 | 4 | 9 | 10 | **6.75** | Preprocess |
| SRC-AST-005 | Gamers Nexus Counterfeit AMD 9800X3D | AST | 7 | 6 | 4 | 8 | 4 | 9 | 10 | **6.75** | Preprocess |
| SRC-AST-006 | Tom's Hardware eBay RTX 5090 Component Stripp... | AST | 7 | 6 | 4 | 8 | 4 | 9 | 10 | **6.75** | Preprocess |
| SRC-AIA-018 | OECD Common Reporting Framework for AI Incide... | AIA | 8 | 2 | 7 | 9 | 6 | 6 | 8 | **6.7** | Preprocess |
| SRC-AIA-019 | FourDots AI Hallucination Business Impact | AIA | 6 | 7 | 8 | 7 | 2 | 7 | 10 | **6.7** | Preprocess |
| SRC-FIN-011 | CFA CFPB Enforcement Legacy Report | FIN | 6 | 7 | 6 | 7 | 3 | 9 | 9 | **6.6** | Preprocess |
| SRC-AIA-006 | ISO IEC 42001 Standard | AIA | 8 | 2 | 10 | 8 | 1 | 6 | 9 | **6.6** | Preprocess |
| SRC-AIA-028 | Air Canada Chatbot Case Study | AIA | 6 | 7 | 8 | 7 | 1 | 7 | 10 | **6.6** | Preprocess |
| SRC-PRP-012 | Warranty Week New Home Builder Warranty Repor... | PRP | 6 | 7 | 5 | 7 | 7 | 8 | 7 | **6.55** | Preprocess |
| SRC-AIA-031 | Q2 2025 Deepfake Incident Report | AIA | 6 | 7 | 5 | 7 | 7 | 7 | 8 | **6.55** | Preprocess |
| SRC-AST-002 | State Department OIG Grey Market Cisco Alert | AST | 7 | 6 | 4 | 8 | 1 | 9 | 10 | **6.45** | Preprocess |
| SRC-FRA-008 | AARP FBI Report Analysis 2025 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-009 | CFTC Virtual Currency Enforcement Trends | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-013 | Deepfake Statistics and Trends 2026 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-014 | Synthetic Identity Fraud Statistics 2026 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-015 | Romance Scam Statistics 2025-2026 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-016 | KELA Ransomware Report 2025 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-019 | TransUnion Identity Fraud Trends | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-021 | DeepStrike Ransomware Statistics 2026 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-022 | Nacha BEC Analysis 2024 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-023 | Identity Theft Statistics 2025 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |
| SRC-FRA-024 | Elder Fraud Statistics 2026 | FRA | 6 | 7 | 5 | 7 | 4 | 9 | 7 | **6.35** | Preprocess |

**Remaining Second Tier:** 72 additional sources. Full details in 02_SOURCE_REGISTRY.csv.
---

## 4. Monitor Tier — Score 4.0-4.9

These 31 sources are valuable for ongoing monitoring and trend tracking but are lower priority for immediate ingestion. They include tertiary sources, one-time reports, and advisory content that enriches context without providing direct evidentiary value.

**Recommended approach:** Subscribe to updates/feeds. Ingest selectively when they document specific incidents with dollar amounts or enforcement outcomes.

### Monitor Tier Complete Listing Sources

| ID | Source Name | Lane | E | P | F | S | A | C | L | **Score** | Action |
|----|-------------|------|---|---|---|---|---|---|---|-----------|--------|
| SRC-FIN-015 | Morgan Lewis State AG Financial Enforcement A... | FIN | 6 | 1 | 4 | 7 | 4 | 7 | 5 | **4.9** | Monitor |
| SRC-CYB-018 | Cyble KEV Analysis | CYB | 6 | 2 | 4 | 7 | 4 | 5 | 5 | **4.85** | Monitor |
| SRC-CYB-020 | Intruder.io Top Vulnerabilities | CYB | 6 | 2 | 4 | 7 | 4 | 5 | 5 | **4.85** | Monitor |
| SRC-CYB-035 | CyberMagazine CrowdStrike 2026 | CYB | 6 | 2 | 4 | 7 | 4 | 5 | 5 | **4.85** | Monitor |
| SRC-CYB-039 | GovCIO Media Secure by Design | CYB | 6 | 2 | 4 | 7 | 4 | 5 | 5 | **4.85** | Monitor |
| SRC-CYB-041 | NETBankAudit Financial CVEs | CYB | 6 | 2 | 4 | 7 | 4 | 5 | 5 | **4.85** | Monitor |
| SRC-AIA-026 | Simon Willison Agentic Browser Security | AIA | 6 | 2 | 4 | 7 | 4 | 5 | 5 | **4.85** | Monitor |
| SRC-CYB-021 | Guardz Data Breaches 2025 | CYB | 6 | 4 | 4 | 3 | 4 | 6 | 6 | **4.75** | Monitor |
| SRC-CYB-029 | BankInfoSecurity MOVEit Report | CYB | 6 | 4 | 4 | 3 | 4 | 6 | 6 | **4.75** | Monitor |
| SRC-CYB-031 | CyberSecurityIntelligence NHS Attack | CYB | 6 | 4 | 4 | 3 | 4 | 6 | 6 | **4.75** | Monitor |
| SRC-CYB-037 | FireCompass Synnovis Analysis | CYB | 6 | 2 | 4 | 7 | 3 | 5 | 5 | **4.75** | Monitor |
| SRC-AST-022 | OpenFox Blockchain Chain of Custody | AST | 6 | 2 | 4 | 7 | 2 | 6 | 5 | **4.75** | Monitor |
| SRC-AST-026 | SMT Corp Counterfeit Components | AST | 6 | 2 | 4 | 7 | 2 | 6 | 5 | **4.75** | Monitor |
| SRC-CYB-019 | MazeHQ Vulnerability Report | CYB | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-CYB-024 | SentinelOne Jailbreak Guide | CYB | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-CYB-025 | Checkpoint OWASP LLM Poisoning | CYB | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-CYB-026 | Palo Alto Unit 42 Ivanti Brief | CYB | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-CYB-027 | BlackBerry Salt Typhoon Analysis | CYB | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-CYB-032 | Giskard Best-of-N Jailbreaking | CYB | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-010 | Wiz.io Agentic Browser Security Review | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-011 | LayerX CometJacking Research | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-017 | Augment Code Multi-Agent Failures | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-021 | Lasso Security Agentic AI Threats | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-022 | Metamindz AI Auditing Frameworks | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-023 | Mindgard AI Red Teaming Guide | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-024 | PromptFoo DeepSeek R1 Security | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-029 | C2PA Technical Review World Privacy Forum | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-036 | SparkCo AI Audit Trails | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-AIA-037 | Chicago Business Law Review AI Section 230 | AIA | 6 | 2 | 4 | 7 | 2 | 5 | 5 | **4.65** | Monitor |
| SRC-CYB-038 | 311 Institute Secure by Design | CYB | 6 | 2 | 4 | 7 | 1 | 5 | 5 | **4.55** | Monitor |
| SRC-AIA-035 | OnHealthcare AI Data Provenance | AIA | 6 | 2 | 4 | 3 | 2 | 5 | 5 | **4.05** | Monitor |
---

## 5. Manual Review Tier — Requires Human Assessment

Sources in this tier require human legal or editorial review before ingestion. As of this evaluation, no sources scored below 4.0 in the composite formula. However, several categories of sources require manual review regardless of score:

### 5.1 PII-Risk Sources Requiring Scrubbing (11 sources)

| Source ID | Source Name | PII Risk | Score | Review Required |
|-----------|-------------|----------|-------|-----------------|
| SRC-FIN-001 | CFPB Consumer Complaint Database | yes | 9.0 | PII scrubbing pipeline |
| SRC-CYB-005 | HHS OCR Breach Portal | yes | 7.85 | PII scrubbing pipeline |
| SRC-FIN-007 | FTC IdentityTheft.gov | yes | 7.55 | PII scrubbing pipeline |
| SRC-AIA-012 | Miami Law Review Mobley v Workday | yes | 6.1 | PII scrubbing pipeline |
| SRC-FIN-016 | Apify CFPB Complaints Scraper | yes | 6.0 | PII scrubbing pipeline |
| SRC-AIA-013 | Databahn AI Agents Security Incidents | yes | 5.95 | PII scrubbing pipeline |
| SRC-CYB-006 | NHS England Synnovis Incident Report | yes | 5.75 | PII scrubbing pipeline |
| SRC-CYB-036 | Synnovis Official Updates | yes | 5.6 | PII scrubbing pipeline |
| SRC-AIA-009 | Blackbird.ai OpenClaw Moltbook Analysis | yes | 5.2 | PII scrubbing pipeline |
| SRC-CYB-030 | HyperProof Change Healthcare Analysis | yes | 5.1 | PII scrubbing pipeline |
| SRC-AIA-038 | Penligent OpenClaw Moltbot Analysis | yes | 5.1 | PII scrubbing pipeline |

### 5.2 Manual Review Criteria

All sources flagged with `contains_pii_risk = yes` must pass through the PII scrubbing pipeline before ingestion, regardless of tier. The scrubbing pipeline:

1. **Removes:** ZIP codes, dates of birth, account numbers, phone numbers, email addresses
2. **Anonymizes:** Consumer narratives by replacing proper names with `[REDACTED]`
3. **Generalizes:** Geographic identifiers to state level only
4. **Quarantines:** Any record where narrative contains suspected PII that cannot be automatically scrubbed
5. **Audits:** 5% random sample human review of scrubbed records

### 5.3 Trust Tier 3 Sources

All Tier 3 (third-party aggregator/scraper) sources require human verification of a sample before batch ingestion:

| Source ID | Source Name | Owner | Verification Sample Size |
|-----------|-------------|-------|-------------------------|
| SRC-FIN-017 | Apify CFPB Complaints Scraper | Apify | 100 records vs. official CFPB API |

---

## 6. Quarantine Tier — Exclude Pending Further Analysis

No sources are currently quarantined. Quarantine criteria include:

| Criterion | Action |
|-----------|--------|
| Unverifiable claims without corroboration | Hold until second source confirms |
| Litigation still in discovery (no adjudication) | Monitor docket; ingest upon resolution |
| Sources behind paywalls with no institutional access | Negotiate access or find alternative |
| Preprints without peer review or replication | Monitor for published version |
| Sources with known factual disputes from opposing party | Flag both claims; ingest with dispute notation |

### Active Quarantine Candidates

| Source ID | Reason | Resolution Trigger |
|-----------|--------|-------------------|
| *(none currently)* | | |

---

## 7. Language Discovery Only — Tier 3 Community Sources

These sources are not suitable for ledger ingestion but provide essential vocabulary, phrasing, and narrative patterns for training the SwarmJelly language model on how consumers describe their pain.

### Language Value Sources

| Category | Examples | Value |
|----------|----------|-------|
| Consumer complaint narratives (CFPB opt-in) | 40% of CFPB complaints include narrative text | Rich consumer language for offense signal detection |
| FTC fraud report descriptions | Individual fraud report summaries | Scam pattern language, emotional indicators |
| Reddit r/personalfinance, r/scams | Community discussion threads | **Not for ingestion** — vocabulary mining only |
| BBB complaint narratives | Consumer business complaint descriptions | Contractor/service failure language patterns |
| Court filing excerpts (public) | Class action complaint language | Formal harm articulation patterns |

### Language Discovery Policy

1. **Never ingest** community forum content directly into the evidentiary corpus
2. **Extract vocabulary lists** only — terms, phrases, complaint patterns
3. **Cross-reference** discovered language against primary sources for validation
4. **Maintain separation** between language training data and evidentiary ledger

---
## 8. Recommended First Ingestion Pipeline

### Phase 1: Foundation Layer (Weeks 1-2)
Ingest the 10 highest-scoring sources to establish the core evidentiary corpus:

| Priority | Source ID | Source Name | Automation | Est. Records | Engineering Task |
|----------|-----------|-------------|------------|-------------|-----------------|
| 1 | SRC-FIN-001 | CFPB Consumer Complaint Database | API (no auth) | 13.8M+ | Build CFPB API connector; PII scrubbing pipeline |
| 2 | SRC-FIN-005 | CFPB Enforcement by the Numbers | CSV download | ~500 rows | CSV parser; dollar normalization |
| 3 | SRC-FIN-004 | CFPB Enforcement Actions Database | Scrape/HTML | ~300 actions | Enforcement action scraper; consent order parser |
| 4 | SRC-AST-011 | CPSC Recall Record 2025 | API | ~400 recalls/year | CPSC API connector; product categorization |
| 5 | SRC-AST-001 | DOJ Onur Aksoy Counterfeit Cisco | Manual/PDF | 1 case | Document parser; case study extraction |
| 6 | SRC-PRP-003 | California CSLB FY 2024-25 Report | PDF | 10,399 complaints | PDF table extractor; state normalizer |
| 7 | SRC-FRA-001 | FBI IC3 2025 Internet Crime Report | PDF/CSV | ~1M complaints | IC3 data parser; category mapping |
| 8 | SRC-CYB-001 | CISA KEV Catalog | API | 1,484 CVEs | CISA KEV API connector; CVSS enrichment |
| 9 | SRC-AIA-003 | OECD AI Incidents Monitor | API | 14 themes | OECD.AI API connector; incident taxonomy mapping |
| 10 | SRC-FIN-002 | CFPB Consumer Response Annual Report | PDF | Aggregate | PDF report parser; trend extraction |

### Phase 2: Expansion Layer (Weeks 3-4)
Ingest remaining Top Tier sources (34 additional):

| Batch | Sources | Focus |
|-------|---------|-------|
| 2A | SRC-FIN-00*, SRC-FRA-00* | Financial and fraud enforcement actions |
| 2B | SRC-PRP-00*, SRC-AST-00* | Property contractor and asset/compute |
| 2C | SRC-CYB-00*, SRC-AIA-00* | Cyber/AI risk and AI agent trust |

### Phase 3: Context Layer (Weeks 5-8)
Batch-process Second Tier sources by automation score:

| Batch | Criteria | Count |
|-------|----------|-------|
| 3A | Automation score >= 8 (API/CSV/JSON sources) | ~30 sources |
| 3B | Automation score 5-7 (PDF/download sources) | ~40 sources |
| 3C | Automation score < 5 (manual/scrape sources) | ~27 sources |

### Phase 4: Monitoring Layer (Ongoing)
Establish automated monitoring for:
- Daily: CFPB complaint database API
- Weekly: CISA KEV catalog additions, HHS OCR breach portal
- Monthly: FTC enforcement actions, SEC enforcement releases, State AG newsletters
- Quarterly: FBI IC3 reports, FTC Consumer Sentinel, OECD AI Incidents Monitor

---

## 9. API Collection Requirements

### 9.1 APIs with No Authentication Required

| Source ID | API Endpoint | Rate Limit | Format | Priority |
|-----------|-------------|------------|--------|----------|
| SRC-FIN-001 | consumerfinance.gov/data-research/consumer-complaints/ | 1,000/hour | JSON/CSV | Critical |
| SRC-FIN-008 | ftc.gov/exploredata (Sentinel) | Public | JSON | Critical |
| SRC-CYB-001 | cisa.gov/known-exploited-vulnerabilities-catalog | Unlimited | JSON | Critical |
| SRC-AIA-003 | oecd.ai/en/incidents | Public | JSON/CSV | High |
| SRC-CYB-005 | HHS OCR Breach Portal | Searchable | HTML/JSON | High |

### 9.2 APIs Requiring Registration/Key

| Source ID | API | Registration | Cost | Priority |
|-----------|-----|-------------|------|----------|
| SRC-FIN-001 (bulk) | CFPB S3 bulk download | None | Free | High |
| SRC-CYB-003 | MITRE ATT&CK (STIX) | None | Free | Medium |
| SRC-CYB-006 | NHS England API | Developer account | Free | Low |

### 9.3 APIs Under Evaluation

| Source | Status | Blocker |
|--------|--------|---------|
| CFPB complaint narratives (bulk) | Under review | PII scrubbing pipeline dependency |
| FTC Consumer Sentinel (law enforcement) | Restricted | Law enforcement partner access only |
| State AG complaint databases | Fragmented | 50 separate systems; no unified API |
| Lex Machina litigation analytics | Commercial | Subscription cost (~$50K/year) |

### 9.4 API Engineering Checklist

- [ ] CFPB API connector with pagination and retry logic
- [ ] CISA KEV catalog diff-ing for incremental updates
- [ ] HHS OCR breach portal change detection
- [ ] OECD.AI incident feed polling
- [ ] PDF download and parsing pipeline for enforcement actions
- [ ] CSV normalization for cross-source field mapping
- [ ] PII detection and scrubbing service (pre-ingestion gate)
- [ ] Source freshness validation (reject stale data)
- [ ] Deduplication service (cross-source incident matching)
- [ ] Schema validation against DefendableOS ontology

---

## 10. Legal Review Questions

The following questions must be answered by legal counsel before full-scale ingestion:

### 10.1 Government Data Use

1. **CFPB Complaint Database:** Is the public domain status of CFPB data sufficient for commercial use in a consumer protection product, given that narratives may contain third-party claims about named companies?
2. **FTC Consumer Sentinel:** Does the public data book summary data have any reuse restrictions beyond the standard federal public domain status?
3. **HHS OCR Breach Portal:** Are there HIPAA considerations when processing breach report data that identifies covered entities and affected individual counts?

### 10.2 Court and Enforcement Documents

4. **Consent Orders and Settlements:** Are federal court consent orders and administrative enforcement actions free of copyright restrictions for factual data extraction?
5. **State AG Enforcement:** Do any state attorneys general impose terms of use on their enforcement data that would restrict commercial aggregation?
6. **Pending Litigation:** What is the risk profile for ingesting data from litigation that is still active or on appeal?

### 10.3 Third-Party and Industry Data

7. **Vendor-Sponsored Reports (IBM, CrowdStrike, etc.):** Do these reports' terms of use permit factual data extraction and republication in a commercial product?
8. **Academic Preprints (arXiv):** Are arXiv papers' CC licenses compatible with commercial use for factual extraction?
9. **News and Journalism:** What is the fair use boundary for extracting factual data points from news articles?

### 10.4 PII and Privacy

10. **CFPB Consumer Narratives:** What is the legal risk of using consumer-submitted complaint narratives (opt-in) for training an AI system, even with PII scrubbing?
11. **Breach Data:** Are there state breach notification laws that restrict how breach notification data can be aggregated and presented?
12. **Cross-Border:** Does EU AI Act or GDPR apply to the DefendableOS corpus if any EU citizen data is present in sources like OECD AI Incidents Monitor?

### 10.5 Defamation and Liability

13. **Company Naming:** What is the liability risk of aggregating and presenting government allegations against named companies, especially for dismissed or settled cases?
14. **AI-Generated Content:** If SwarmJelly generates content based on these sources, who bears liability for factual errors — DefendableOS, the source, or the end user?
15. **Section 230:** To what extent does Section 230 immunity apply to an AI system that organizes and presents third-party factual data about consumer harm?

---

## 11. Data Licensing Notes

### 11.1 Public Domain Sources (No Restrictions)

The following source categories are public domain and free for factual extraction and commercial use:

| Category | Examples | Legal Basis |
|----------|----------|-------------|
| Federal government databases | CFPB, FTC, FBI IC3, CISA, SEC, HHS OCR | 17 U.S.C. § 105 (federal works) |
| Federal court records | Consent orders, judgments, dockets | Public domain (judicial works) |
| State government reports | CSLB enforcement, AG annual reports | State public records laws |
| International IGO data | OECD.AI, EU AI Act (regulatory text) | IGO open data policies |
| Academic preprints | arXiv papers | Author CC licenses (check per paper) |

### 11.2 Sources Requiring Attribution

| Source Type | Attribution Required | License |
|-------------|---------------------|---------|
| OWASP standards | Yes (OWASP attribution) | CC BY-SA 4.0 |
| MITRE ATT&CK | Yes (ATT&CK attribution) | Custom (free with attribution) |
| NIST publications | Recommended | Public domain |
| ISO standards (summaries) | Yes | Copyright (purchase full text) |

### 11.3 Sources with Use Restrictions

| Source | Restriction | Mitigation |
|--------|-------------|------------|
| FTC Consumer Sentinel granular data | Law enforcement access only | Use public Data Book summaries |
| Lex Machina analytics | Commercial subscription | Purchase license or use public summaries |
| ISO 42001 full text | Purchase required | Rely on publicly available summaries |
| Vendor-sponsored research reports | May prohibit data extraction | Review ToS per report; use press releases |

### 11.4 PII Handling Requirements

| Data Element | Handling | Legal Basis |
|-------------|----------|-------------|
| Consumer narrative text | Scrub PII; anonymize proper names | FCRA, state privacy laws |
| ZIP codes | Generalize to state | Re-identification risk |
| Company names in allegations | Retain (public record) | First Amendment, public domain |
| Individual names in court filings | Redact unless public figure | Privacy torts |
| Dates of complaints/events | Month/year granularity | Minimization principle |
| Dollar amounts | Retain verbatim | Factual data, no privacy risk |

### 11.5 Recommended Licensing for DefendableOS Output

Given the source mix, DefendableOS output should be licensed as follows:

- **Factual data extracted from public domain sources:** Unrestricted commercial use
- **Aggregated statistics and analytics:** DefendableOS proprietary (or CC BY 4.0 if open)
- **Consumer-facing narratives (scrubbed):** CC BY-SA 4.0 with attribution chain
- **AI-generated guidance:** Disclaimer required — "based on public records, not legal advice"
- **Source provenance metadata:** Always retained and accessible

---

## Appendix A: Scoring Dimension Definitions

### Evidence Strength Score (1-10)

| Score | Criteria |
|-------|----------|
| 9-10 | Primary government authority; court-adjudicated; independent audit |
| 7-8 | Secondary authoritative; reputable industry/academic; data-backed |
| 5-6 | Tertiary analysis; vendor-sponsored; single-source |
| 3-4 | Advocacy perspective; methodology unclear |
| 1-2 | Unverified claims; no methodology; anonymous |

### Pain Density Score (1-10)

| Score | Criteria |
|-------|----------|
| 9-10 | Multiple harm signals (narratives + dollar losses + outcomes + remedies) |
| 7-8 | Two harm signals (e.g., dollar losses + outcomes) |
| 5-6 | One harm signal (dollar losses or outcomes) |
| 3-4 | Contextual/indirect harm documentation |
| 1-2 | No harm documentation; background only |

### Defense Fixer Potential Score (1-10)

| Score | Criteria |
|-------|----------|
| 9-10 | Specific remedies documented; complaint procedures; restitution pathways |
| 7-8 | Enforcement actions with consumer relief; regulatory frameworks |
| 5-6 | Standards or guidance; general protective measures |
| 3-4 | Awareness/education; no specific action pathway |
| 1-2 | No fixer documentation |

### Corpus Safety Score (1-10)

| Score | Criteria |
|-------|----------|
| 9-10 | No PII; primary authority; clear public domain status |
| 7-8 | Minimal PII risk; secondary authority; known licensing |
| 5-6 | Some PII risk; requires scrubbing; third-party source |
| 3-4 | Significant PII risk; unclear licensing; manual review required |
| 1-2 | High PII risk; legal uncertainty; quarantine recommended |

### Automation Potential Score (1-10)

| Score | Criteria |
|-------|----------|
| 9-10 | REST API with no auth; JSON/CSV; daily updates; documentation |
| 7-8 | API with key; downloadable CSV; regular updates |
| 5-6 | Scrapable HTML; PDF with structured tables; periodic updates |
| 3-4 | Manual download; PDF extraction required; infrequent updates |
| 1-2 | Manual only; no digital format; one-time publication |

### Commercial Relevance Score (1-10)

| Score | Criteria |
|-------|----------|
| 9-10 | Directly addresses DefendableOS consumer protection mission; dollar losses; enforcement outcomes |
| 7-8 | Strongly relevant lane; quantitative harm data |
| 5-6 | Moderately relevant; contextual value |
| 3-4 | Indirectly relevant; emerging area |
| 1-2 | Minimal product relevance |

### Ledger Readiness Score (1-10)

| Score | Criteria |
|-------|----------|
| 9-10 | Maps directly to offense signal / pain receipt / defense fixer schema; minimal preprocessing |
| 7-8 | Requires field mapping; structure is regular |
| 5-6 | Requires extraction from prose; semi-structured |
| 3-4 | Requires significant NLP extraction; unstructured |
| 1-2 | Not suitable for ledger; discovery/context only |

---

## Appendix B: Source Count by Lane

| Lane | Code | Sources | Top Tier (7+) | Second Tier (5-6.9) | Monitor (4-4.9) |
|------|------|---------|---------------|----------------------|-----------------|
| Consumer Financial | FIN | 19 | 8 | 10 | 1 |
| Fraud, Digital Loss | FRA | 26 | 4 | 19 | 3 |
| Cyber / AI Risk | CYB | 46 | 10 | 30 | 6 |
| Property / Contractor | PRP | 16 | 7 | 7 | 2 |
| Asset / Compute | AST | 27 | 8 | 15 | 4 |
| AI Agent Trust | AIA | 38 | 7 | 16 | 15 |
| **Total** | | **172** | **44** | **97** | **31** |

---

*Document generated: May 25, 2026*  
*Source data: 02_SOURCE_REGISTRY.csv (172 sources across 6 research lanes)*  
*Scoring formula: Evidence(25%) + Pain Density(15%) + Fixer Potential(15%) + Safety(15%) + Automation(10%) + Commercial(10%) + Ledger(10%)*
