# 12. Research Gaps and Next Run Plan

> **Document Version:** 1.0  
> **Project:** DefendableOS Corpus Build  
> **Status:** Gap analysis following initial 6-lane research run (250+ seed records)  
> **Classification:** Internal Planning / Pre-Legal Review  

---

## Executive Summary

The initial research run across six evidence lanes produced **250+ seed records** with uneven lane strength: Lanes 1 (Financial), 2 (Fraud), and 3 (Cyber) yielded strong, authoritative data from federal sources. Lanes 4 (Property), 5 (Assets), and 6 (AI Trust) remain significantly underdeveloped. This document identifies **ten major gaps**, assigns priority ratings, and defines the scope, sources, and success metrics for a recommended second research run and first production ingestion pipeline.

**Top 5 Critical Gaps at a Glance:**

| Rank | Gap | Impact | Remediation Cost |
|------|-----|--------|-----------------|
| 1 | No PACER / federal court case data | Blocks legal-precedent evidence type | High (paywall + manual review) |
| 2 | Lane 4 (Property) lacks any central database | Entire lane is fragmentary | High (50-state manual research) |
| 3 | PII in complaint narratives unresolved | Blocks safe ingestion / training use | Medium (legal review required) |
| 4 | Cross-lane pattern discovery not started | Limits ontology relationship richness | Medium (analyst time) |
| 5 | No production ingestion pipeline defined | Research cannot convert to product | Medium (engineering sprint) |

---

## 1. Missing Authoritative Sources

The following primary sources were identified during planning but **not accessed or fully exploited** during the initial research run. Each entry includes the reason for omission and a priority rating for the next run.

### 1.1 Federal Court Data (PACER)
- **Source:** Public Access to Court Electronic Records (PACER), uscourts.gov
- **Coverage:** Federal civil and criminal case filings, dockets, opinions
- **Why Missing:** Paywall ($0.10/page); no bulk download mechanism; account registration required
- **Relevance:** High. Contains fraud, breach liability, class-action, and negligence precedents that bridge Lanes 1, 2, 3, and 5
- **Priority:** P1

### 1.2 State-Level Contractor Complaint Databases
- **Source:** State contractor licensing boards (e.g., CSLB in California, NY DOS)
- **Coverage:** Licensed contractor complaint histories, disciplinary actions, bond claims
- **Why Missing:** 50+ separate state systems; no federal aggregator; many require state residency or licensed-user accounts
- **Relevance:** High for Lane 4 (Property). Contractor fraud is a major sub-category of property-related financial harm
- **Priority:** P2

### 1.3 Municipal Inspection Records
- **Source:** City and county building / code enforcement departments
- **Coverage:** Failed inspections, code violations, stop-work orders, habitability findings
- **Why Missing:** Hyper-local systems (3,000+ municipalities); often not digitized; FOIA may be required
- **Relevance:** Medium-High. Bridges Lane 4 (Property) and Lane 5 (Asset condition)
- **Priority:** P3

### 1.4 Insurance Claim Dispute Data
- **Source:** State insurance commissioner complaint databases, NAIC
- **Coverage:** Denied claims, bad-faith allegations, premium disputes, coverage gaps
- **Why Missing:** Private-sector primary data; state databases vary in accessibility; NAIC data is aggregated but coarse
- **Relevance:** High for Lane 4 and Lane 5 cross-over
- **Priority:** P2

### 1.5 Corporate Breach Disclosure Details (Beyond Notifications)
- **Source:** SEC 8-K filings, investor letters, post-breach forensic reports
- **Coverage:** Root cause, financial impact, remediation cost, class-action settlements
- **Why Missing:** SEC EDGAR requires API knowledge; forensic reports are often confidential; 8-K filings are event-triggered and require active monitoring
- **Relevance:** High for Lane 3 enrichment
- **Priority:** P1

### 1.6 SEC EDGAR Filings (Fraud-Related)
- **Source:** SEC EDGAR, sec.gov/edgar
- **Coverage:** 10-K risk disclosures, 8-K material events, litigation disclosures
- **Why Missing:** Not yet queried for fraud-specific disclosures; EDGAR full-text search requires tooling
- **Relevance:** Medium-High. Public companies disclose fraud losses and cyber incidents in periodic filings
- **Priority:** P1

### 1.7 State Bar Disciplinary Records
- **Source:** State bar associations (e.g., State Bar of California)
- **Coverage:** Attorney discipline, client trust account violations, fee disputes
- **Why Missing:** State-by-state fragmentation; some records are behind member-login walls
- **Relevance:** Medium. Professional-services fraud is a distinct sub-type in Lane 2
- **Priority:** P3

### 1.8 FDA MAUDE (Medical Device Adverse Events)
- **Source:** FDA Manufacturer and User Facility Device Experience (MAUDE) database
- **Coverage:** Medical device malfunctions, injuries, deaths reported to FDA
- **Why Missing:** Not scoped in initial run; data is event-level but requires medical-domain parsing
- **Relevance:** Medium. Health-sector trust and safety data that connects to Lane 3 (breach/disclosure) and Lane 6 (AI trust in regulated domains)
- **Priority:** P3

### 1.9 Consumer Product Safety Commission (CPSC) Data
- **Source:** CPSC SaferProducts.gov, recalls, NEISS injury data
- **Coverage:** Product recalls, consumer injury reports, manufacturer complaints
- **Why Missing:** API is public but rate-limited; recall data overlaps partially with Lane 5 (asset/product failure)
- **Relevance:** Medium
- **Priority:** P3

### 1.10 Better Business Bureau (BBB) Complaint Data
- **Source:** BBB Scam Tracker, BBB Complaint Portal
- **Coverage:** Business complaint patterns, scam reports, business ratings
- **Why Missing:** BBB data is not bulk-downloadable; web scraping terms of service restrict automated collection
- **Relevance:** Medium. Consumer-level pattern data complements CFPB and FTC sources
- **Priority:** P3

### Missing Sources Summary Table

| Source | Lane | Priority | Barrier | Est. Records |
|--------|------|----------|---------|-------------|
| PACER | 1, 2, 5 | P1 | Paywall / manual | 1,000s (case-level) |
| State Contractor DBs | 4 | P2 | 50-state fragmentation | 10,000s |
| Municipal Inspections | 4, 5 | P3 | Hyper-local / FOIA | Unknown |
| Insurance Disputes | 4, 5 | P2 | Private / state-limited | 1,000s |
| SEC EDGAR (8-K / 10-K) | 1, 3 | P1 | API / tooling | 100s/year |
| State Bar Disciplinary | 2 | P3 | Fragmentation | 100s/year |
| FDA MAUDE | 3, 6 | P3 | Domain parsing | 100,000s |
| CPSC Recalls / NEISS | 5 | P3 | Rate limits | 10,000s |
| BBB Complaints | 1, 2 | P3 | ToS restrictions | 100,000s |

---

## 2. Weak Evidence Lanes

### 2.1 Lane 4: Property / Real Estate / Contractor Fraud

**Current State:** Fragmentary. No single federal database captures property-related financial harm. The lane depends on:
- Scattered state AG enforcement press releases
- News reporting of high-dollar cases
- OCC complaint data (subset)
- Community posts (unverified)

**Required Strengthening:**
- **Manual state-by-state research** for the top 10 states by population / complaint volume
- **FOIA requests** to HUD (Office of Inspector General reports) and state housing agencies
- **Aggregation of state contractor board** complaint histories where publicly searchable
- **Integration of insurance commissioner data** for property-insurance bad-faith cases

**Target:** Move Lane 4 from "Weak" to "Medium" strength in the second run by adding **150+ verified records**.

### 2.2 Lane 5: Asset / Product / Transaction-Level Failures

**Current State:** Medium. Incident data exists (CPSC recalls, breach notifications, product lawsuits) but is scattered across multiple federal agencies with no unified index.

**Required Strengthening:**
- **Add transaction-level granularity** by ingesting SEC EDGAR fraud-loss disclosures
- **Add CPSC recall data** with product-category tagging
- **Add insurance claim patterns** by state (where available)
- **Cross-reference** Lane 5 asset failures with Lane 3 cyber events (e.g., ransomware disabling physical assets)

**Target:** Add **200+ records** with transaction-level financial detail.

### 2.3 Cross-Lane Pattern Discovery

**Current State:** Not started. Each lane was researched independently.

**Required Work:**
- Identify entities that appear in multiple lanes (e.g., a company with CFPB complaints, a breach disclosure, and an SEC 8-K filing)
- Build relationship edges in the ontology: `BreachEvent -> FinancialLoss -> RegulatoryAction`
- Detect temporal patterns: does a cyber event typically precede a financial complaint by N months?

**Target:** Produce **50+ cross-lane relationship assertions** in the second run.

---

## 3. Data Licensing and Reuse Questions

### 3.1 CFPB Consumer Complaint Database
- **Access:** Public download available at consumerfinance.gov/data-research/consumer-complaints
- **License Status:** U.S. government work; presumptively public domain under 17 U.S.C. 105
- **Open Question:** Are complaint *narratives* (free-text descriptions) subject to the same public-domain status as the structured fields? The CFPB publishes them after consumer consent and PII scrubbing, but the scrubbing process is not perfect.
- **Action Required:** Confirm CFPB Terms of Use; document date of download for license snapshot

### 3.2 FBI Internet Crime Complaint Center (IC3)
- **Access:** Annual reports (PDF) published at ic3.gov; no bulk complaint database available to the public
- **License Status:** Public reports are federal government work product
- **Open Question:** Aggregate statistics derived from IC3 reports -- does FBI assert any restriction on downstream use? Can annual report tables be extracted and republished?
- **Action Required:** Review IC3 publication terms; confirm fair use of statistical tables

### 3.3 CISA Known Exploited Vulnerabilities (KEV) Catalog
- **Access:** JSON and XML feeds available at cisagov/known-exploited-vulnerabilities
- **License Status:** Explicitly CC0 1.0 Universal (Public Domain Dedication)
- **Open Question:** None. This is the cleanest source from a licensing perspective.
- **Action Required:** None. Safe for unrestricted production ingestion.

### 3.4 Federal Trade Commission (FTC) Data
- **Access:** FTC Consumer Sentinel Network data is available to approved entities (law enforcement, academia); public reports are available at ftc.gov
- **License Status:** Public reports are federal government work product; Sentinel Network data has access agreements
- **Open Question:** Can data extracted from public FTC enforcement actions and press releases be used for commercial AI training? Are there attribution requirements?
- **Action Required:** Review FTC.gov Terms of Use; document acceptable use for extracted data

### 3.5 Court Filings (PACER)
- **Access:** Pay-per-page; case files are public records
- **License Status:** Public records, but PACER access is a service, not a dataset license
- **Open Question:** Does PACER's Terms of Service restrict bulk extraction or redistribution of downloaded case content? (Historical note: PACER has previously challenged bulk access projects.)
- **Action Required:** Legal review of PACER ToS; consider CourtListener / RECAP as alternative source

### 3.6 CourtListener / Free Law Project (RECAP)
- **Access:** Free API and bulk data at courtlistener.com
- **License Status:** Data is crowdsourced from PACER users via RECAP extension; Free Law Project asserts no copyright in public court records
- **Open Question:** Is RECAP-derived data safe from PACER ToS claims for downstream commercial use?
- **Action Required:** Review Free Law Project data policy; preferred over direct PACER if legally equivalent

### Licensing Summary Matrix

| Source | Public Domain? | Attribution Required? | Commercial Use OK? | Legal Review Needed? |
|--------|---------------|----------------------|-------------------|---------------------|
| CFPB (structured) | Likely Yes | No | Probably | Moderate |
| CFPB (narratives) | Unclear | No | Unknown | **Yes** |
| IC3 Reports | Likely Yes | No | Probably | Low |
| CISA KEV | **Yes (CC0)** | No | **Yes** | None |
| FTC Public Reports | Likely Yes | Unknown | Probably | Moderate |
| PACER | Public record | N/A | Restricted by ToS | **Yes** |
| CourtListener | Public record | Varies | Probably | Moderate |
| SEC EDGAR | **Yes** | No | **Yes** | Low |
| State Databases | Varies by state | Varies | Varies | **Yes** |

---

## 4. PII and Sensitive Data Concerns

The following data types require special handling before ingestion into any production system or AI training pipeline. These concerns are **blockers** until a formal PII handling policy is in place.

### 4.1 CFPB Complaint Narratives
- **Risk:** Free-text consumer complaints may contain residual PII (names, account numbers, addresses) despite CFPB scrubbing. Scrubbing failures have been documented in academic literature.
- **Mitigation:** Run supplemental PII detection (Presidio, AWS Comprehend PII, or spaCy NER) on all narrative text before ingestion. Flag records with >0 PII hits for human review or exclusion.
- **Policy Needed:** Define threshold for exclusion vs. redaction vs. retention with label.

### 4.2 Breach Disclosure Notification Letters
- **Risk:** Breach notices often describe the types of PII exposed (SSN, DOB, medical records, financial account numbers) for real individuals. The notices themselves do not contain the PII, but they confirm its exposure.
- **Mitigation:** The notices are legally required public documents. Risk is low if only the *fact* of breach is recorded, not individual victim data. Ensure no victim lists are scraped.
- **Policy Needed:** Prohibit ingestion of any document containing enumerated victim identifiers.

### 4.3 StreetChat / Community Posts and Forums
- **Risk:** Community-generated content frequently contains self-disclosed PII: property addresses, phone numbers, business names, transaction amounts, legal case numbers.
- **Mitigation:** Apply the same PII detection pipeline as for CFPB narratives. Treat community posts as "unverified" evidence tier regardless of PII status.
- **Policy Needed:** Community posts require explicit labeling: `evidence_tier: unverified`, `source_type: community_report`, `pii_risk: high`.

### 4.4 Health-Related Breach Data (HIPAA)
- **Risk:** HHS Breach Portal ("Wall of Shame") lists covered entities and breach summaries. OCR breach reports describe the nature of protected health information (PHI) exposed.
- **Mitigation:** HHS data is a federal public record. No individual PHI is published. Safe for ingestion as structured event data.
- **Policy Needed:** Confirm no scraping of attached investigation letters that may contain case details.

### 4.5 Court Filings
- **Risk:** Court filings may contain plaintiff/defendant names, addresses, financial details, SSNs (sometimes redacted poorly), and minor identifiers.
- **Mitigation:** If PACER/CourtListener data is ingested, apply automated redaction detection. Flag filings with visible PII for exclusion or manual redaction.
- **Policy Needed:** Define which case types are in scope (e.g., class actions OK, individual small-claims excluded).

### PII Risk Heatmap

| Data Source | PII Density | Sensitivity Class | Ingestion Blocker? | Mitigation Effort |
|------------|-------------|-------------------|-------------------|-------------------|
| CFPB structured fields | None | Low | No | None |
| CFPB narratives | Medium | Medium | **Yes** | Moderate (scan + redact) |
| IC3 reports | None | Low | No | None |
| CISA KEV | None | Low | No | None |
| NVD | None | Low | No | None |
| HHS breach portal | None | **High (PHI context)** | No | Low (structured only) |
| Breach notification letters | Low | **High** | No | Low (aggregate only) |
| Community posts | **High** | Medium | **Yes** | Moderate (scan + tier label) |
| Court filings | Medium-High | Medium | **Yes** | High (case-type filter + scan) |
| SEC EDGAR | None | Low | No | None |

---

## 5. Sources Requiring API Collection

The following sources should be ingested via programmatic APIs in the production pipeline. Each includes API status and estimated integration effort.

### 5.1 CFPB Complaint Database API
- **Endpoint:** `https://www.consumerfinance.gov/data-research/consumer-complaints/search/api/v1/`
- **Status:** Public REST API; no authentication required for search
- **Format:** JSON
- **Rate Limits:** Reasonable; bulk download also available as CSV/JSON
- **Integration Effort:** Low (1-2 days)
- **Recommended Approach:** Use bulk download for initial seed; API for incremental updates

### 5.2 CISA KEV Catalog
- **Endpoint:** `https://www.cisa.gov/sites/default/files/feeds/known_exploited_vulnerabilities.json`
- **Status:** Public JSON feed; no authentication
- **Format:** JSON
- **Rate Limits:** None apparent
- **Integration Effort:** Low (<1 day)
- **Recommended Approach:** Direct HTTP fetch; parse into vulnerability ontology nodes

### 5.3 NIST National Vulnerability Database (NVD) API 2.0
- **Endpoint:** `https://services.nvd.nist.gov/rest/json/cves/2.0`
- **Status:** Public REST API; API key recommended for higher rate limits (free registration)
- **Format:** JSON
- **Rate Limits:** 5 requests/second without key; 50/second with key
- **Integration Effort:** Low-Medium (2-3 days including pagination handling)
- **Recommended Approach:** API key registration required; paginated CVE retrieval with last-modified filter for incremental sync

### 5.4 SEC EDGAR API (Full-Text Search + Submissions)
- **Endpoint:** `https://www.sec.gov/cgi-bin/browse-edgar?action=getcompany` (browse); `https://efts.sec.gov/LATEST/search-index` (full-text)
- **Status:** Public; User-Agent header required (identify requester per SEC fair access policy)
- **Format:** HTML (browse); JSON (full-text search)
- **Rate Limits:** 10 requests/second maximum; SEC actively monitors and blocks abusers
- **Integration Effort:** Medium (3-5 days; requires filing-type parsing)
- **Recommended Approach:** Full-text search for keywords ("cybersecurity incident", "fraud", "data breach"); parse 8-K and 10-K extracts

### 5.5 CourtListener API (Free Law Project)
- **Endpoint:** `https://www.courtlistener.com/api/rest/v3/`
- **Status:** Public REST API; API key available for higher rate limits
- **Format:** JSON
- **Rate Limits:** 5,000 requests/hour with key
- **Integration Effort:** Medium (3-5 days; requires docket and opinion parsing)
- **Recommended Approach:** Search by case type (civil, class action) and keyword ("data breach", "fraud", "negligence"); extract docket entries and opinions

### 5.6 HHS Breach Portal (OCR)
- **Endpoint:** No official API; data available as downloadable archive or scrapable HTML table
- **Status:** Public data; machine-readable JSON has been observed in third-party mirrors
- **Format:** HTML table / JSON mirror
- **Rate Limits:** N/A
- **Integration Effort:** Low-Medium (2-3 days; requires HTML parsing or third-party mirror)
- **Recommended Approach:** Scrape the breach report table; map columns to ontology fields

### 5.7 State-Level APIs (Future)
- Many state databases (contractor boards, insurance commissioners) offer no API
- Where APIs exist, they are typically SOAP-based or require state-issued credentials
- **Effort:** High and variable; defer to Phase 3

### API Integration Priority Queue

| Priority | Source | Effort | Dependencies | Production Ready? |
|----------|--------|--------|-------------|-------------------|
| P0 | CISA KEV | <1 day | None | **Yes** |
| P0 | NVD API | 2-3 days | API key | **Yes** |
| P0 | CFPB API / Bulk | 1-2 days | None | **Yes** |
| P1 | SEC EDGAR | 3-5 days | Filing parser | After legal review |
| P1 | CourtListener | 3-5 days | Case parser | After legal review |
| P2 | HHS Breach Portal | 2-3 days | HTML parser | **Yes** (structured only) |
| P3 | State APIs | Variable | Credentials | Phase 3 |

---

## 6. Sources Requiring Manual Review

These sources cannot be reliably ingested via API and require human analyst judgment for each record.

### 6.1 Court Filings and Dockets
- **Why Manual:** Case relevance must be judged; docket noise is high; extraction of key facts requires legal literacy
- **Review Task:** Read complaint and/or opinion; extract: parties, claims, damages, disposition, precedent value
- **Time Estimate:** 15-30 minutes per case
- **Throughput:** 10-20 cases per analyst per day
- **Quality Control:** Second analyst spot-checks 10% of extractions

### 6.2 State Attorney General Enforcement Actions
- **Why Manual:** Press releases vary widely in detail; some link to full complaints, others do not; multi-state actions require consolidation
- **Review Task:** Read press release and linked complaint (if available); extract: defendant, allegations, remedy, states involved
- **Time Estimate:** 10-20 minutes per action
- **Throughput:** 20-40 actions per analyst per day

### 6.3 Breach Notification Letters
- **Why Manual:** Letters are PDFs or images; OCR quality varies; content must be mapped to standardized fields
- **Review Task:** Extract: entity name, breach date, discovery date, types of PII exposed, affected count, notification date
- **Time Estimate:** 5-10 minutes per letter
- **Throughput:** 40-80 letters per analyst per day
- **Note:** This can be partially automated with OCR + LLM extraction, but human validation is required

### 6.4 Community Posts and Forums (StreetChat, Reddit, etc.)
- **Why Manual:** Unverified source; requires triage for relevance, authenticity, and PII scrubbing
- **Review Task:** Read post; extract: harm type, financial loss estimate, entity involved, date; flag for PII; assign evidence tier
- **Time Estimate:** 5-10 minutes per post
- **Throughput:** 40-80 posts per analyst per day
- **Quality Control:** Supervisor review of all `unverified` tier assignments

### 6.5 News Reporting and Investigative Journalism
- **Why Manual:** High variance in reliability; requires source credibility assessment
- **Review Task:** Extract key facts with attribution; record publication source and date; flag as `evidence_tier: journalistic`
- **Time Estimate:** 10-15 minutes per article
- **Throughput:** 30-50 articles per analyst per day

### Manual Review Resource Estimate (Second Run)

| Source Type | Records Target | Min/Record | Analyst-Days | Cost Band |
|------------|---------------|------------|-------------|-----------|
| Court cases | 100 | 20 min | 34 days | High |
| State AG actions | 200 | 15 min | 50 days | High |
| Breach letters | 300 | 7 min | 35 days | Medium |
| Community posts | 200 | 7 min | 23 days | Medium |
| News articles | 200 | 12 min | 40 days | Medium |
| **Total** | **1,000** | **~11 min avg** | **182 days** | **High** |

> **Note:** 182 analyst-days = approximately 1 full-time analyst for 9 months, or 3 analysts for 3 months. This is a significant investment and should be staged across multiple runs.

---

## 7. Legal Review Questions

The following questions require input from qualified legal counsel before production ingestion or model training can proceed. These are **documented as blockers** with assigned owners.

### 7.1 Use of Complaint Narratives for AI Training
- **Question:** Can anonymized or redacted consumer complaint narratives (from CFPB, FTC, state AGs) be used as training data for a commercial AI product without violating consumer privacy expectations or regulatory restrictions?
- **Context:** CFPB narratives are published with consumer consent, but that consent may not extend to derivative AI training uses.
- **Owner:** Legal counsel (data privacy / consumer finance)
- **Status:** OPEN
- **Urgency:** High -- blocks training pipeline design

### 7.2 Fair Use of Government Data for Commercial AI
- **Question:** Does the aggregation, transformation, and embedding of U.S. government public-domain data into a commercial AI knowledge base raise any novel legal issues under federal data use policies?
- **Context:** Most federal data is public domain under 17 U.S.C. 105, but downstream AI products may face attribution or fairness requirements not yet defined.
- **Owner:** Legal counsel (IP / technology)
- **Status:** OPEN
- **Urgency:** Medium

### 7.3 Liability for AI Recommendations Based on Corpus Data
- **Question:** If the DefendableOS AI system generates recommendations, risk assessments, or guidance based on this research corpus, what liability exposure exists if the underlying data is incomplete, outdated, or misinterpreted?
- **Context:** This touches on product liability, professional malpractice (if used by attorneys), and consumer protection.
- **Owner:** Legal counsel (product liability / E&O)
- **Status:** OPEN
- **Urgency:** High -- product architecture depends on this

### 7.4 State-by-State Data Privacy Compliance
- **Question:** Does ingesting consumer complaint data, breach disclosures, and community posts trigger obligations under state privacy laws (CCPA/CPRA, VCDPA, CPA, CTDPA, etc.)?
- **Context:** State laws vary in definition of "personal information," "sale," and "automated decision-making." The corpus contains data about consumers even if individual PII is scrubbed.
- **Owner:** Legal counsel (data privacy / state compliance)
- **Status:** OPEN
- **Urgency:** High -- compliance architecture required

### 7.5 Terms of Service Compliance for Scraped Sources
- **Question:** Which sources in the corpus (BBB, community forums, news sites) have Terms of Service that prohibit automated collection or commercial use of their content?
- **Context:** Even if data is publicly visible, ToS restrictions may create contractual liability for scraping.
- **Owner:** Legal counsel (technology / contracts)
- **Status:** OPEN
- **Urgency:** Medium -- affects ingestion pipeline scope

### 7.6 Attribution and Provenance Requirements
- **Question:** What attribution obligations apply when government data is mixed with third-party data (news, community posts) in an AI training corpus? Does the product need to display provenance chains?
- **Context:** Creative Commons and government data licenses often require attribution; product design must accommodate this.
- **Owner:** Legal counsel (IP / open data)
- **Status:** OPEN
- **Urgency:** Low-Medium

### Legal Review Tracker

| Question | Owner | Urgency | Blocks | ETA |
|----------|-------|---------|--------|-----|
| 7.1 Complaint narratives for training | Privacy counsel | High | Training pipeline | TBD |
| 7.2 Government data commercial use | IP counsel | Medium | None directly | TBD |
| 7.3 AI recommendation liability | Product counsel | High | Product launch | TBD |
| 7.4 State privacy compliance | Privacy counsel | High | Compliance design | TBD |
| 7.5 ToS for scraped sources | Tech counsel | Medium | Pipeline scope | TBD |
| 7.6 Attribution requirements | IP counsel | Low-Med | UI design | TBD |

---

## 8. Recommended Second Research Run

### 8.1 Scope and Objectives

The second research run should focus on **closing the gap between strong and weak lanes** while **building the production ingestion pipeline** for sources that are already legally and technically ready.

**Primary Objectives:**
1. Move Lane 4 (Property) from Weak to Medium strength
2. Add transaction-level financial data to Lane 5 (Assets)
3. Ingest all P0 API sources into the staging pipeline
4. Begin cross-lane relationship discovery
5. Resolve the top 3 legal review questions (7.1, 7.3, 7.4)

### 8.2 Source Priorities

| Priority | Source | Lane | Action | Target Records |
|----------|--------|------|--------|---------------|
| P0 | CISA KEV | 3 | API ingestion | 1,000+ (full catalog) |
| P0 | NVD API | 3 | API ingestion | 10,000+ (filtered) |
| P0 | CFPB Bulk | 1 | API + bulk download | 50,000+ (with narratives flagged) |
| P1 | SEC EDGAR (8-K) | 1, 3 | API ingestion | 500+ (fraud/breach related) |
| P1 | CourtListener | 1, 2, 5 | API + manual review | 100 cases |
| P1 | HHS Breach Portal | 3 | HTML scrape | 1,000+ (full catalog) |
| P2 | State Contractor DBs (top 10 states) | 4 | Manual research | 200+ |
| P2 | State AG Actions | 1, 2, 4 | Manual research | 200+ |
| P2 | CPSC Recalls | 5 | API / scrape | 1,000+ |
| P3 | FDA MAUDE | 3, 6 | API / download | 5,000+ (filtered) |

### 8.3 New Lanes to Open

| New Lane | Description | Trigger | Priority |
|----------|-------------|---------|----------|
| **Lane 7: Professional Services Fraud** | Attorney, accountant, financial advisor misconduct | State bar + SEC data bridges Lane 2 and professional liability | P2 |
| **Lane 8: Regulatory Enforcement Patterns** | Cross-agency enforcement trends (CFPB + FTC + SEC + State AG joint actions) | Cross-lane pattern discovery will naturally reveal this need | P2 |
| **Lane 9: Infrastructure / Physical Security** | Critical infrastructure failures, utility disruptions, supply chain physical security | CISA KEV + CPSC + municipal data convergence | P3 |

### 8.4 Target Metrics

| Metric | Current (Run 1) | Target (Run 2) | Stretch |
|--------|----------------|---------------|---------|
| Total seed records | 250+ | 1,000+ | 2,000+ |
| Lane 4 records | <20 | 150+ | 250+ |
| Lane 5 records | ~40 | 250+ | 400+ |
| Cross-lane relationships | 0 | 50+ | 100+ |
| API-ingested records | 0 | 60,000+ | 100,000+ |
| PII-scanned records | 0 | 100% of narrative-containing records | -- |
| Legal review questions resolved | 0/6 | 3/6 | 4/6 |
| New lanes opened | 0 | 2 | 3 |
| Countries covered (non-US) | 0 | 1+ (UK/Canada/AU pilot) | 3+ |

### 8.5 Timeline Estimate

| Phase | Duration | Key Deliverables |
|-------|----------|-----------------|
| 8.1 Legal review sprint | 2-3 weeks | Answers to Q7.1, 7.3, 7.4; PII policy |
| 8.2 API pipeline build | 2-3 weeks | Ingestion jobs for P0 sources; staging DB |
| 8.3 Manual research sprint | 4-6 weeks | Lane 4 + 5 strengthening; court cases |
| 8.4 Cross-lane analysis | 2 weeks | Relationship edges; pattern report |
| 8.5 Quality assurance | 1-2 weeks | Spot-check; PII audit; legal sign-off |
| **Total** | **11-16 weeks** | **1,000+ verified records; production pipeline** |

---

## 9. Recommended First Production Ingestion Pipeline

### 9.1 Pipeline Architecture (Recommended)

```
+------------------+     +------------------+     +------------------+
|   SOURCE LAYER   | --> |  INGESTION LAYER | --> |   STAGING LAYER  |
+------------------+     +------------------+     +------------------+
  CFPB API/Bulk            Python extractors       PostgreSQL staging
  CISA KEV JSON            (requests, pandas)       + S3 raw archive
  NVD API 2.0              Scheduled (Airflow/     PII scan queue
  SEC EDGAR                cron)                    Entity resolution
  CourtListener API        Rate-limit respect       Deduplication
  HHS Breach HTML scraper  Retry + backoff          Normalization
  State AG press releases  (manual trigger)         Schema validation
  Manual research docs     (human upload)           Evidence tier tags
+------------------+     +------------------+     +------------------+
                                                          |
                                                          v
+------------------+     +------------------+     +------------------+
|  PRODUCTION DB   | <-- |  CURATION LAYER  | <-- |  QUALITY LAYER   |
+------------------+     +------------------+     +------------------+
  PostgreSQL /               Human review queue       Automated tests:
  Elasticsearch             (manual review UI)        - PII detection
  + Vector store              - Court cases             (Presidio)
    (embeddings)              - Community posts       - Schema validation
                              - Breach letters        - Source attribution
  Search + retrieval        Evidence tier upgrade     - Deduplication
  API for downstream        Cross-lane linking        - Freshness checks
  AI training export        Ontology alignment      Human tests:
                              - Spot-check 10%        - Random sample review
                              - Legal sign-off        - Legal review gate
+------------------+     +------------------+     +------------------+
```

### 9.2 Ingestion Order (Phased)

**Phase 1: Automated, Low-Risk (Weeks 1-2)**
1. CISA KEV Catalog -- full historical ingestion
2. NVD API -- filtered ingestion (CVSS >= 7.0 or KEV-linked)
3. HHS Breach Portal -- full historical scrape
4. CPSC Recalls -- full historical ingestion

**Phase 2: Structured Government Data (Weeks 3-4)**
5. CFPB Complaint Database -- structured fields (no narratives until legal review)
6. SEC EDGAR -- keyword-filtered 8-K and 10-K extracts
7. FTC Consumer Sentinel -- public report tables only

**Phase 3: Semi-Automated + Manual (Weeks 5-10)**
8. CourtListener -- API search + human curation queue
9. State AG press releases -- manual extraction + upload
10. State contractor databases -- manual research (top 10 states)
11. Breach notification letters -- OCR + LLM extraction + human validation

**Phase 4: Community + Unverified (Weeks 11-12, pending legal)**
12. Community posts -- PII scan required; human review mandatory
13. News articles -- manual extraction with source attribution

### 9.3 Validation Steps (Every Record)

| Step | Check | Automated? | Failure Action |
|------|-------|-----------|----------------|
| V1 | Schema conformance (required fields) | Yes | Reject to quarantine |
| V2 | Source URL validity | Yes | Flag for review |
| V3 | PII detection (narrative fields) | Yes | Quarantine + alert |
| V4 | Date range sanity | Yes | Flag for review |
| V5 | Deduplication (exact + fuzzy) | Yes | Merge or reject |
| V6 | Evidence tier assignment | Semi | Human override required |
| V7 | Legal review gate (Phase 2+) | No | Block until sign-off |
| V8 | Cross-lane entity linking | Semi | Analyst review queue |

### 9.4 Human Review Checkpoints

| Checkpoint | Trigger | Reviewer | SLA |
|------------|---------|----------|-----|
| H1: PII quarantine | V3 failure | Data steward | 24 hours |
| H2: Evidence tier upgrade | `unverified` -> `verified` | Senior analyst | 48 hours |
| H3: Court case extraction | New case ingestion | Legal analyst | 72 hours |
| H4: Cross-lane link approval | Relationship edge proposed | Ontology curator | 48 hours |
| H5: Legal sign-off | Batch ready for production | Legal counsel | 1 week |
| H6: Training data export | Corpus export for model training | Legal + privacy counsel | 2 weeks |

### 9.5 Storage and Indexing Approach

**Raw Layer (S3)**
- Format: Original source format (JSON, CSV, PDF, HTML)
- Organization: `s3://bucket/raw/{source}/{date_ingested}/{file}`
- Retention: Indefinite (immutable archive)
- Access: Write-once, read-many; restricted to ingestion pipeline

**Staging Layer (PostgreSQL)**
- Schema: Normalized relational tables aligned with ontology classes
- Purpose: Deduplication, entity resolution, PII scanning, quality checks
- Retention: Until promoted to production or rejected
- Access: Ingestion pipeline + quality tools

**Production Layer (PostgreSQL + Elasticsearch)**
- PostgreSQL: Canonical record store with full provenance
- Elasticsearch: Full-text search, faceted filtering, aggregation queries
- Purpose: API backend for product + research access
- Access: Product API + analyst tools

**Vector Layer (pgvector or dedicated)**
- Format: Embedding vectors for semantic search
- Source: Production records with narrative or descriptive fields
- Purpose: Semantic retrieval for AI downstream tasks
- Access: Model training pipeline + similarity search API

---

## 10. Unresolved Questions

These are known unknowns that remain after the initial research run. They are not yet blockers but may become so as the project progresses.

### 10.1 Data Volume and Scaling
- **Q:** What is the total addressable record count across all sources? Current estimate is 100K-1M structured records, but this is unverified.
- **Q:** At what volume does the current pipeline architecture require horizontal scaling?

### 10.2 Ontology Completeness
- **Q:** Does the current ontology capture all entity types needed for cross-lane reasoning? Are there missing relationship types (e.g., `precedes`, `enables`, `mitigates`)?
- **Q:** How should the ontology handle temporal evolution -- e.g., a company that changes name or a vulnerability that transitions from "exploited" to "patched"?

### 10.3 International Expansion
- **Q:** Which non-US jurisdictions have equivalent public data? (UK: FCA, ICO; EU: ENISA; Canada: OSFI, OPC; Australia: OAIC, ACSC)
- **Q:** What are the licensing and language implications of international sources?

### 10.4 Model Training Implications
- **Q:** What is the optimal train/validation split for a corpus with temporal structure (events unfold over time)?
- **Q:** How should class imbalance be handled across lanes (Lane 1 may have 10x records of Lane 4)?

### 10.5 Adversarial and Bias Risks
- **Q:** Does the corpus reflect reporting bias (e.g., overrepresentation of federal vs. state vs. local events)?
- **Q:** Could the AI system be gamed by adversarial submissions to public complaint databases?

### 10.6 Maintenance and Refresh
- **Q:** What is the required refresh cadence for each source? (Daily for CISA KEV, weekly for CFPB, annually for some state sources?)
- **Q:** How will record updates and corrections be handled? (Some sources update historical records retroactively.)

### 10.7 Commercial Viability
- **Q:** What is the competitive landscape for AI-assisted legal/fraud research? Are there incumbent products with comparable corpus coverage?
- **Q:** What is the pricing model -- per-query, subscription, or data licensing?

---

## Appendix A: Glossary

| Term | Definition |
|------|------------|
| **KEV** | Known Exploited Vulnerabilities (CISA catalog) |
| **NVD** | National Vulnerability Database (NIST) |
| **PACER** | Public Access to Court Electronic Records |
| **EDGAR** | Electronic Data Gathering, Analysis, and Retrieval (SEC) |
| **MAUDE** | Manufacturer and User Facility Device Experience (FDA) |
| **CPSC** | Consumer Product Safety Commission |
| **OCR** | Office for Civil Rights (HHS) |
| **PII** | Personally Identifiable Information |
| **PHI** | Protected Health Information (HIPAA) |
| **ToS** | Terms of Service |
| **FOIA** | Freedom of Information Act |
| **8-K** | SEC form for material events |
| **10-K** | SEC annual report |
| **CC0** | Creative Commons Zero (public domain dedication) |

## Appendix B: Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2025-01-15 | Research Team | Initial gap analysis post-Run 1 |

---

*This document is a living analysis. Priorities, legal conclusions, and pipeline designs will be updated as legal review proceeds and the second research run delivers new findings.*
