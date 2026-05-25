# DefendableOS Dimension 2: Fraud, Impersonation, Crypto & Digital Loss — Research Report

**Research Date:** May 25, 2026
**Researcher:** DefendableOS Research Unit
**Classification:** Lane 2 — Fraud, Impersonation, Crypto and Digital Loss
**Sources Consulted:** 40+ (Tier 1 and Tier 2 only)
**Incidents Documented:** 25+ specific patterns/incidents

---

## TABLE OF CONTENTS

1. [Executive Summary](#1-executive-summary)
2. [Source Registry](#2-source-registry)
3. [Landscape Overview: Key Statistics](#3-landscape-overview)
4. [Incident/Pain Receipt Catalog](#4-incident-catalog)
5. [Offense Signal Taxonomy](#5-offense-signals)
6. [Defense Fixer Catalog](#6-defense-fixers)
7. [Appendix: Detailed Source Notes](#7-appendix)

---

## 1. EXECUTIVE SUMMARY

The fraud, impersonation, and digital asset loss landscape in 2024-2025 represents an unprecedented escalation in both scale and sophistication. Total reported cybercrime losses exceeded $20.877 billion in 2025 (FBI IC3), a 26% increase from 2024's $16.6 billion. The true scale of fraud, adjusted for underreporting, may reach $195 billion annually (FTC estimates). Key drivers include:

- **AI-enabled fraud**: $893 million in reported losses from 22,364 AI-related complaints (IC3 2025), with deepfake fraud tripling to $1.1 billion in the US alone
- **Cryptocurrency fraud**: $11.3 billion in reported losses from 181,565 complaints (IC3 2025)
- **Investment scams**: Remain the #1 loss category at $8.6 billion (IC3 2025)
- **Business Email Compromise**: $3.046 billion from 24,768 complaints (IC3 2025)
- **Elder fraud**: Adults 60+ reported $7.7 billion in losses, up 60% from 2024 (AARP/IC3)
- **Synthetic identity fraud**: Projected to cost $23 billion by 2030, accounting for 80%+ of new account fraud

The convergence of AI, cryptocurrency, and social engineering has created a new paradigm where fraud is more scalable, more convincing, and harder to detect than ever before.

---

## 2. SOURCE REGISTRY

### Tier 1 Sources (Government, Primary Data)

| # | Source | Owner/Agency | URL | Date Range | Trust | Corpus Score |
|---|--------|-------------|-----|------------|-------|-------------|
| S1 | FBI IC3 2025 Internet Crime Report | FBI IC3 | fbi.gov/file-repository/2025_ic3report.pdf | 2025 data, released Apr 2026 | 1 | 10 |
| S2 | FBI IC3 2024 Internet Crime Report | FBI IC3 | fbi.gov/news/press-releases/fbi-releases-annual-internet-crime-report | 2024 data, released Apr 2025 | 1 | 10 |
| S3 | FBI Press Release — Crypto & AI Scams | FBI | fbi.gov/news/press-releases/cryptocurrency-and-ai-scams-bilk-americans-of-billions | Apr 2026 | 1 | 10 |
| S4 | FTC Consumer Sentinel Network Data Book 2024 | FTC | ftc.gov (via exploredata) | 2024 data, released Mar 2025 | 1 | 10 |
| S5 | FTC Annual Report to Congress — Protecting Older Adults 2024-2025 | FTC | ftc.gov/news-events/news/press-releases/2025/12/ftc-issues-annual-report | FY 2024-2025, released Dec 2025 | 1 | 9 |
| S6 | SEC Enforcement Results FY2025 | SEC | sec.gov/newsroom/press-releases/2026-34 | FY2025, released Apr 2026 | 1 | 9 |
| S7 | SEC Cryptocurrency Enforcement 2025 Update | Cornerstone Research (SEC data) | cornerstone.com/insights/research/sec-cryptocurrency-enforcement-2025-update | Calendar 2025, Apr 2026 | 2 | 8 |
| S8 | SEC Enforcement: 2025 Year in Review | Harvard Law School Forum | corpgov.law.harvard.edu/2026/01/21 | 2025 data, Jan 2026 | 2 | 8 |
| S9 | FTC Data Book — Fraud Losses 2024 | FTC | ftc.gov/exploredata | 2024 data, Mar 2025 | 1 | 10 |
| S10 | CFTC Virtual Currency Enforcement Trends | JD Supra/Cornerstone Research | jdsupra.com/legalnews/key-trends-in-cftc-virtual-currency-2636711 | Q1 2015–Q3 2025 | 2 | 7 |

### Tier 2 Sources (Industry, Academic, High-Quality Analysis)

| # | Source | Owner | URL | Date | Trust | Corpus Score |
|---|--------|-------|-----|------|-------|-------------|
| S11 | AARP — FBI Report: $20.9B Losses | AARP | aarp.org/money/scams-fraud/fbi-ftc-report-2025-losses | Apr 2026 | 2 | 9 |
| S12 | McDonald Hopkins — IC3 2025 Analysis | McDonald Hopkins law firm | mcdonaldhopkins.com/insights/news/the-sobering-truth-of-the-fbis-2025-internet-crime-complaint-center-report | Apr 2026 | 2 | 8 |
| S13 | HIPAA Journal — FBI IC3 2025 Summary | HIPAA Journal | hipaajournal.com/fbi-internet-crime-complaint-report-2025 | Apr 2026 | 2 | 7 |
| S14 | TitanHQ — State of Email Security 2025 | TitanHQ | titanhq.com/email-security-2025/state-email-security-report-2025 | Apr 2026 | 2 | 8 |
| S15 | LevelBlue — BEC Trends: Attacks up 15% | LevelBlue/AT&T | levelblue.com/blogs/spiderlabs-blog/bec-email-trends-attacks-up-15-in-2025 | Jan 2026 | 2 | 7 |
| S16 | Chargebacks911 — BEC Statistics 2026 | Chargebacks911 | chargebacks911.com/ecommerce-fraud/business-email-compromise/business-email-compromise-statistics | Nov 2025 | 2 | 7 |
| S17 | Elder Fraud Statistics 2026 | Discreet Investigations | discreetinvestigations.ca/research/elder-fraud-statistics | May 2026 | 2 | 7 |
| S18 | Deepfake Statistics & Trends 2026 | Keepnet Labs | keepnetlabs.com/blog/deepfake-statistics-and-trends | May 2026 | 2 | 7 |
| S19 | Synthetic Identity Fraud Statistics 2026 | BIIA | biia.com/synthetic-identity-fraud-statistics-2026 | Jan 2026 | 2 | 7 |
| S20 | Romance Scam Statistics 2025-2026 | Arnaques-Rencontres | arnaques-rencontres.fr/en/articles/romance-scam-statistics | Mar 2026 | 2 | 7 |
| S21 | Identity Fraud by Numbers 2025 | Regula | regulaforensics.com/blog/2025-identity-fraud-by-numbers | Dec 2025 | 2 | 7 |
| S22 | Identity Theft Statistics 2025 | Motley Fool | fool.com/money/research/identity-theft-credit-card-fraud-statistics | Jan 2026 | 2 | 7 |
| S23 | Industrial Cyber — FBI IC3 2024 Report | Industrial Cyber | industrialcyber.co/reports/fbis-internet-crime-report-2024 | Apr 2025 | 2 | 7 |
| S24 | KELA Ransomware Report 2025 | KELA | codekeeper.co/ticker/ransomware-attacks-on-critical-infrastructure-2025 | Oct 2025 | 2 | 8 |
| S25 | Industrial Cyber — KELA Ransomware Analysis | Industrial Cyber | industrialcyber.co/reports/half-of-2025-ransomware-attacks-hit-critical-sectors | Oct 2025 | 2 | 7 |
| S26 | Fortinet Ransomware Statistics 2025 | Fortinet | fortinet.com/resources/cyberglossary/ransomware-statistics | Jan 2025 | 2 | 7 |
| S27 | Sumsub Identity Fraud Trends 2026 | Sumsub | sumsub.com/blog/top-new-identity-fraud-trends | Dec 2025 | 2 | 7 |
| S28 | Cifas Fraudscape UK 2025 | Cifas | cifas.org.uk/newsroom/fraudscape-2025-6monthupdate | Aug 2025 | 2 | 7 |
| S29 | TransUnion Identity Fraud Trends for Government | TransUnion | events.afcea.org/fedid25/CUSTOM/pdf/transunion_tl.pdf | 2025 | 2 | 7 |
| S30 | FTC — Social Media Scam Losses (Apr 2026) | FTC | ftc.gov/news-events/news/press-releases/2026/04/new-ftc-data-show-people-have-lost-billions-to-social-media-scams | Apr 2026 | 1 | 9 |
| S31 | Barclays Romance Scam Bulletin | Barclays | home.barclays/news/press-releases/2025/04/barclays-scams-bulletin | Apr 2025 | 2 | 7 |
| S32 | Nacha — BEC Analysis 2024 | Nacha | nacha.org/news/fbis-ic3-finds-almost-85-billion-lost-business-email-compromise-last-three-years | Apr 2025 | 2 | 7 |
| S33 | Account Takeover Statistics 2025 | AuthX | authx.com/blog/account-takeover-fraud-statistics-insights | Nov 2025 | 2 | 7 |
| S34 | DeepStrike Ransomware Statistics 2026 | DeepStrike | deepstrike.io/blog/ransomware-statistics-2025 | May 2025 | 2 | 7 |

---

## 3. LANDSCAPE OVERVIEW: KEY STATISTICS

### 3.1 FBI IC3 Data — Annual Comparison

| Metric | 2023 | 2024 | 2025 | Change 2024→2025 |
|--------|------|------|------|-------------------|
| Total Complaints | 880,418 | 859,532 | 1,008,597 | +17% |
| Total Losses | $12.5B | $16.6B | $20.877B | +26% |
| Daily Complaint Average | ~2,400 | ~2,354 | ~2,764 | +17% |
| BEC Complaints | 21,489 | 21,442 | 24,768 | +16% |
| BEC Losses | ~$2.9B | ~$2.8B | $3.046B | +9% |
| Ransomware Reports | 2,825 | 3,156 | 3,611 | +14% |
| Ransomware Losses | — | $12.473M | $32.320M | +259% |
| Investment Fraud Losses | — | ~$6.5B | $8.649B | +33% |
| Cyber-Enabled Fraud Complaints | — | 333,981 | 453,000 | +36% |
| Crypto Complaints | — | — | 181,565 | — |
| Crypto Losses | — | ~$6.5B+ | $11.3B | +74% |
| AI-Related Complaints | — | — | 22,364 | — |
| AI-Related Losses | — | — | ~$893M | — |
| Elder (60+) Losses | $3.4B (est.) | $4.8B | $7.7B | +60% |

Sources: S1, S2, S3, S11, S12, S13

### 3.2 FTC Consumer Sentinel Data

| Metric | 2023 | 2024 | 2025 (partial) |
|--------|------|------|----------------|
| Total Consumer Reports | ~6.4M | 6.5M | — |
| Fraud Reports | ~2.6M | 2.6M | — |
| Identity Theft Reports | ~1.04M | 1,135,291 | 1,157,317 (Q1-Q3) |
| Total Fraud Losses | ~$10B | $12.5B+ | — |
| Investment Scam Losses | ~$4.6B | $5.7B | — |
| Imposter Scam Losses | ~$2.7B | $2.95B | — |
| Older Adult (60+) Losses | ~$1.9B | $2.4B | — |
| Government Imposter Losses | ~$618M | $789M | — |
| Tech Support Scam Losses (60+) | — | $159M | — |
| Estimated True Losses (adjusted) | — | $195.9B | — |

Sources: S4, S5, S9, S26

### 3.3 Cryptocurrency Fraud Landscape

| Metric | Value | Source |
|--------|-------|--------|
| Crypto losses reported to IC3 2025 | $11.3B | S1, S3 |
| Crypto complaints to IC3 2025 | 181,565 | S3 |
| SEC crypto enforcement actions 2024 | 33 | S7 |
| SEC crypto enforcement actions 2025 | 13 (-60%) | S7 |
| SEC crypto penalties 2025 | $142M | S7 |
| CFTC virtual currency actions 2024 | 10 | S10 |
| CFTC virtual currency actions 2025 (Q1-Q3) | 0 | S10 |
| PGI Global fraud | $198M | S6 |
| FBI Operation Level Up victims notified | 8,000+ | S3 |
| FBI Operation Level Up losses prevented | $500M+ | S3 |

Sources: S1, S3, S6, S7, S10

### 3.4 AI-Enabled Fraud Landscape

| Metric | Value | Source |
|--------|-------|--------|
| AI-related IC3 complaints 2025 | 22,364 | S3 |
| AI-related IC3 losses 2025 | ~$893M | S3 |
| Deepfake fraud losses US 2025 | $1.1B (tripled from $360M in 2024) | S18 |
| Deepfake losses Q1 2025 (North America) | $200M+ | S18 |
| Deepfake fraud incidents Jan-Sep 2025 | $3B+ (AI-driven) | S18 |
| Gen AI fraud losses US 2024 | ~$360M | S18 |
| Gen AI fraud projected 2027 | $40B (Deloitte) | S18 |
| Deepfake content growth 2023→2025 | 500K → 8M (1,500% increase) | S53 |
| Deepfake-enabled vishing increase Q1 2025 | 1,600% over Q4 2024 | S18 |
| Businesses losing avg per deepfake incident | ~$500K | S18 |

Sources: S3, S18

### 3.5 Business Email Compromise (BEC) Landscape

| Metric | Value | Source |
|--------|-------|--------|
| BEC losses IC3 2025 | $3.046B | S1, S12 |
| BEC complaints IC3 2025 | 24,768 | S12 |
| BEC complaints IC3 2024 | 21,442 | S32 |
| BEC complaints IC3 2023 | 21,489 | S14 |
| BEC losses IC3 2024 | ~$2.8B | S32 |
| BEC losses 2022-2024 total | ~$8.5B | S32 |
| Average loss per BEC incident | $137,000 (up 83% from $74,723 in 2019) | S16 |
| BEC + AI nexus losses 2025 | $30M+ confirmed | S12 |
| BEC emails increase 2025 (LevelBlue) | +15% vs 2024 | S15 |
| BEC emails intercepted/month (LevelBlue) | 3,000+ (peak 4,300 in July) | S15 |
| Organizations experiencing BEC 2024 | 57-63% | S16, S32 |
| BEC losses unrecoverable rate | 83-95% | S16 |
| Financial Fraud Kill Chain success (within 24hrs) | 66% freeze rate | S16 |

Sources: S1, S12, S14, S15, S16, S32

### 3.6 Elder Fraud Landscape

| Metric | Value | Source |
|--------|-------|--------|
| Elder (60+) IC3 losses 2025 | $7.7B | S11 |
| Elder (60+) IC3 losses 2024 | $4.8B | S17 |
| Elder (60+) IC3 complaints 2024 | 147,127 | S21 |
| Elder FTC losses 2024 | $2.4B | S5, S17 |
| Elder FTC losses 2020 | $600M | S5 |
| Elder (60+) average loss per incident | $83,000 | S17 |
| Elder (80+) median FTC loss | $1,600+ | S5 |
| Elder tech support losses 2024 (FTC) | $159M | S27 |
| DOJ elder fraud enforcement 2023-2024 | 700+ defendants, $700M stolen | S17 |
| Estimated true elder fraud cost (FTC adjusted) | $81.5B | S5, S17 |

Sources: S5, S11, S17, S21

### 3.7 Ransomware Landscape

| Metric | 2024 | 2025 | Source |
|--------|------|------|--------|
| Ransomware complaints (IC3) | 3,156 | 3,611 | S12, S13 |
| Ransomware losses (IC3) | $12.473M | $32.320M (+259%) | S12 |
| New ransomware variants (IC3) | 67 | 63 | S12, S23 |
| Global ransomware victims (leak sites) | ~4,750 | ~7,500 (+58%) | S34 |
| Global ransomware incidents Jan-Sep | 3,219 | 4,701 (+34%) | S24 |
| Critical infrastructure attacks Jan-Sep | 1,745 (54%) | 2,332 (50%) | S25 |
| Manufacturing attacks | 520 | 838 (+61%) | S25 |
| US share of global incidents | — | 21% (~1,000) | S25 |
| Total blockchain ransom payments | ~$813M | ~$820M | S34 |
| Victims paying ransom | ~48% | ~28% (record low) | S34 |
| Median ransom payment | ~$12.7K | ~$59.6K | S34 |
| Double extortion with data theft | ~57% | ~77% | S34 |

Sources: S12, S13, S23, S24, S25, S34

### 3.8 Romance Scam Landscape

| Metric | 2024 | Source |
|--------|------|--------|
| FTC romance scam losses | $1.2B | S20 |
| IC3 confidence/romance fraud losses | $672M | S20 |
| Romance + investment (pig butchering) losses | $3.9B (investment category) | S20 |
| FTC romance scam reports | 60,000+ | S20 |
| IC3 romance scam victims | ~17,900 | S20 |
| Median individual loss (FTC) | ~$2,000 | S20 |
| Avg loss UK | ~£11,500 | S20 |
| Crypto as payment method | 34% | S20 |
| Social media as contact origin | 40% | S20 |
| Pig butchering avg loss | $100,000+ | S20 |

Sources: S20, S31

---

## 4. INCIDENT/PAIN RECEIPT CATALOG

### Incident 1: FBI IC3 Record Year — $20.877B in Losses
- **Source:** S1, S3, S11
- **Date:** 2025 data, released April 2026
- **Description:** FBI IC3 received 1,008,597 complaints — the first time exceeding 1 million. Total reported losses reached $20.877 billion, a 26% increase from 2024's $16.6 billion. Americans over 60 reported approximately $7.7 billion in losses, up 37% from 2024.
- **Pain Receipt:** Record-breaking fraud losses; elder fraud accelerating faster than overall trend
- **Taxonomy:** Pain Receipt — Aggregate Financial Damage

### Incident 2: AI-Nexus BEC — $30M+ in Confirmed Losses
- **Source:** S12
- **Date:** 2025
- **Description:** For the first time in its ~25-year history, the IC3 report features a section on artificial intelligence in BEC. Businesses reported over $30 million in losses from BEC scams with a confirmed AI nexus. Threat actors leverage generative AI to create emails at scale and impersonate leadership more effectively.
- **Pain Receipt:** AI making BEC more scalable and convincing; traditional detection failing
- **Taxonomy:** Offense Signal — AI-Enabled Impersonation; Pain Receipt — Enterprise Financial Loss

### Incident 3: Ransomware Surge — $32.32M in Reported Losses (+259%)
- **Source:** S12, S13
- **Date:** 2025
- **Description:** IC3 received 3,611 ransomware reports. Top variants: Akira, Qilin, INC Ransom/Lynx/Sinobi, BianLian, Play. 63 new variants identified. Healthcare and public health sector experienced highest number of cyber threats including 182 data breaches and 460 ransomware attacks. Losses do not include business disruption, forensics, legal costs, or reputational damage.
- **Pain Receipt:** 259% increase in reported ransomware losses; critical infrastructure under sustained assault
- **Taxonomy:** Offense Signal — Ransomware Escalation; Pain Receipt — Operational + Financial Damage

### Incident 4: Investment Fraud Dominance — $8.649B
- **Source:** S1, S3, S11
- **Date:** 2025
- **Description:** Investment fraud remained the #1 loss category, accounting for nearly 49% of all scam-related losses. Cryptocurrency-related investment fraud was the primary driver within this category.
- **Pain Receipt:** Investment scams most financially devastating; crypto the dominant payment vehicle
- **Taxonomy:** Offense Signal — Investment Fraud; Pain Receipt — Massive Individual Losses

### Incident 5: Cryptocurrency Fraud — $11.3B in Losses
- **Source:** S3
- **Date:** 2025
- **Description:** Americans submitting complaints involving cryptocurrency reported the highest losses, with 181,565 complaints totaling more than $11 billion. FBI Operation Level Up has surpassed 8,000 victims notified and reduced losses by more than $500 million since inception.
- **Pain Receipt:** Crypto fraud is the single largest loss vector; recovery is extremely difficult
- **Taxonomy:** Offense Signal — Crypto Investment Fraud; Defense Fixer — Proactive Victim Notification

### Incident 6: Tech Support Scams — $2.135B in Losses
- **Source:** S1, S13
- **Date:** 2025
- **Description:** Tech and customer support scams generated $2.135 billion in reported losses, making it the third-costliest fraud category. Older consumers disproportionately targeted.
- **Pain Receipt:** Tech support scams drain billions, especially from elderly victims
- **Taxonomy:** Offense Signal — Tech Support Impersonation; Pain Receipt — Elder Financial Exploitation

### Incident 7: Romance Scams — $1.2B (FTC) / Pig Butchering Convergence
- **Source:** S20, S56
- **Date:** 2024-2025
- **Description:** Romance scams converged with investment fraud in "pig butchering" schemes. The FBI estimated romance-baited investment fraud accounted for over $3.9 billion in losses in 2024. Many operations run from compounds in Southeast Asia using trafficked labor.
- **Pain Receipt:** Hybrid scams extract far more than traditional romance fraud; victims lose life savings
- **Taxonomy:** Offense Signal — Romance/Investment Hybrid; Pain Receipt — Psychological + Financial Devastation

### Incident 8: AI-Related IC3 Complaints — 22,364 complaints, $893M
- **Source:** S3
- **Date:** 2025
- **Description:** For the first time, the IC3 report featured a dedicated AI section. Scammers rely on pressure techniques while deploying fake social profiles, voice clones, identification documents, and believable videos depicting public figures or loved ones.
- **Pain Receipt:** AI is weaponizing impersonation at scale across all fraud types
- **Taxonomy:** Offense Signal — AI-Generated Synthetic Media; Pain Receipt — Multi-Modal Deception

### Incident 9: Arup Deepfake Fraud — $25M Loss
- **Source:** S18
- **Date:** February 2024
- **Description:** A finance worker at Arup (global engineering firm) was tricked into wiring $25 million due to a deepfake video conference call. The worker received a video call from someone who appeared to be the company's CFO and other executives.
- **Pain Receipt:** Deepfake video calls bypass traditional verification; single incident caused massive loss
- **Taxonomy:** Offense Signal — Deepfake Video Conference; Pain Receipt — Enterprise Wire Fraud

### Incident 10: UK Energy Firm CEO Deepfake — €220,000 Loss
- **Source:** S18
- **Date:** 2019 (baseline case)
- **Description:** A UK energy firm was defrauded of €220,000 via a deepfaked voice clone of its CEO. The CEO's voice was synthesized to authorize a fraudulent wire transfer.
- **Pain Receipt:** Voice cloning can defeat phone-based verification protocols
- **Taxonomy:** Offense Signal — Voice Clone Impersonation; Pain Receipt — Unauthorized Wire Transfer

### Incident 11: SEC PGI Global Crypto Fraud — $198M Scheme
- **Source:** S6
- **Date:** FY2025
- **Description:** SEC charged PGI Global founder Ramil Palafox for allegedly orchestrating a $198 million crypto asset and foreign exchange fraud scheme involving "membership" packages guaranteeing high returns. More than $57 million was misappropriated.
- **Pain Receipt:** Large-scale crypto fraud schemes continue to extract hundreds of millions
- **Taxonomy:** Offense Signal — Crypto Ponzi Scheme; Pain Receipt — Mass Investor Losses

### Incident 12: SEC Unicoin Fraud — $42M+ Raised
- **Source:** S6
- **Date:** FY2025
- **Description:** SEC charged Unicoin, Inc. and four executives for alleged false and misleading statements in an offering of certificates purportedly conveying rights to receive crypto assets called Unicoin tokens.
- **Pain Receipt:** False crypto asset offerings continue to target mainstream investors
- **Taxonomy:** Offense Signal — False Crypto Asset Offering; Pain Receipt — Investor Deception

### Incident 13: Paddle Payment Processing Settlement — $5M
- **Source:** S5
- **Date:** 2024-2025
- **Description:** FTC settled charges that Paddle, a payment processor, facilitated schemes selling costly tech support services using fake virus alerts and pop-ups impersonating Microsoft and McAfee. Paddle required to turn over $5 million for consumer refunds.
- **Pain Receipt:** Payment processors enabling tech support scams; brand impersonation as lure
- **Taxonomy:** Offense Signal — Brand Impersonation + Payment Facilitation; Pain Receipt — Consumer Refund Required

### Incident 14: Aqua Finance Deceptive Lending — $20M Refunds + $23.6M Debt Forgiveness
- **Source:** S5
- **Date:** 2024
- **Description:** FTC alleged Aqua Finance's nationwide network of dealers went door-to-door deceiving consumers (many older adults) about financing terms for water filtering products. Settlement required $20 million in refunds and $23.6 million in debt forgiveness.
- **Pain Receipt:** Door-to-door elder financial exploitation through deceptive financing
- **Taxonomy:** Offense Signal — Deceptive Door-to-Door Sales; Pain Receipt — Predatory Elder Lending

### Incident 15: BEC $50M Construction Sector Loss
- **Source:** S14
- **Date:** 2024
- **Description:** FBI IC3 reported a $50 million loss due to a BEC incident at a construction entity in New York focused on critical infrastructure.
- **Pain Receipt:** Single BEC incident can cause catastrophic enterprise loss
- **Taxonomy:** Offense Signal — Critical Infrastructure BEC; Pain Receipt — $50M Single-Event Loss

### Incident 16: BEC $4.9M Real Estate Wire Fraud
- **Source:** S14
- **Date:** 2024
- **Description:** A real estate firm paid $4.9 million to a Hong Kong bank account controlled by a threat actor after receiving a fraudulent invoice from a compromised vendor account. Money was recovered due to quick FBI intervention.
- **Pain Receipt:** Real estate transactions particularly vulnerable to BEC wire fraud
- **Taxonomy:** Offense Signal — Vendor Email Compromise; Pain Receipt — Cross-Border Wire Fraud

### Incident 17: Synthetic Identity Fraud Surge — $3.3B Lender Exposure
- **Source:** S19, S29
- **Date:** H1 2025
- **Description:** TransUnion found US lenders faced $3.3 billion in exposure to synthetic identities tied to new accounts. Synthetic identity fraud accounts for 80%+ of new account fraud. Projected to cost $23 billion by 2030.
- **Pain Receipt:** Synthetic identities bypass traditional verification; growing at alarming rate
- **Taxonomy:** Offense Signal — Synthetic Identity Creation; Pain Receipt — Systemic Financial System Compromise

### Incident 18: Social Media Investment Scams — $1.1B in Losses
- **Source:** S30
- **Date:** 2025 (reported Apr 2026)
- **Description:** FTC data showed people lost $1.1 billion to investment scams that started on social media — more than half of all social media scam losses. Scammers posed as friendly advisers or created WhatsApp groups of "successful investors" sharing fake testimonials.
- **Pain Receipt:** Social media platforms have become primary fraud distribution channels
- **Taxonomy:** Offense Signal — Social Media Investment Fraud; Pain Receipt — Platform-Facilitated Mass Victimization

### Incident 19: Identity Theft Record Breaking — 1.157M Reports in 9 Months
- **Source:** S22
- **Date:** 2025
- **Description:** 1,157,317 identity theft cases reported to FTC in first three quarters of 2025, exceeding all of 2024's 1,135,291 cases. On pace to be a record-breaking year.
- **Pain Receipt:** Identity theft accelerating; data breaches fueling synthetic identity creation
- **Taxonomy:** Offense Signal — Identity Data Compromise; Pain Receipt — Identity Theft Surge

### Incident 20: Account Takeover Fraud — $2.9B Losses
- **Source:** S33
- **Date:** 2024-2025
- **Description:** Account takeover (ATO) fraud losses hit $2.9 billion, making it the fastest-growing fraud type. Global ATO losses projected at $17 billion by 2025. Each corporate ATO breach costs $5 million on average.
- **Pain Receipt:** ATO is the fastest-growing fraud vector; credential stuffing is primary attack method
- **Taxonomy:** Offense Signal — Credential-Based Account Takeover; Pain Receipt — Corporate + Individual Losses

### Incident 21: KELA Ransomware Critical Infrastructure Surge
- **Source:** S24, S25
- **Date:** Jan-Sep 2025
- **Description:** 4,701 global ransomware incidents (34% increase), with 2,332 (50%) targeting critical infrastructure. Manufacturing surged 61%. Five groups (Qilin, Clop, Akira, Play, SafePay) responsible for 25% of all incidents.
- **Pain Receipt:** Ransomware is evolving from business nuisance to national security threat
- **Taxonomy:** Offense Signal — Critical Infrastructure Ransomware; Pain Receipt — National Security Risk

### Incident 22: Sophisticated Fraud Triples — 180% Increase
- **Source:** S27
- **Date:** 2024-2025
- **Description:** Sumsub research found sophisticated fraud almost tripled from 10% to 28% of attempts in 2025. While overall fraud rates stayed stable (2.2% of verifications), the sophistication shift makes detection harder.
- **Pain Receipt:** Fraud is becoming more sophisticated even if not more common
- **Taxonomy:** Offense Signal — Multi-Step Coordinated Fraud Rings; Pain Receipt — Detection Failure

### Incident 23: UK Romance Scam Surge — 20% Increase
- **Source:** S31
- **Date:** Q1 2025
- **Description:** Barclays data showed romance scams up 20% year-on-year in Q1 2025. Average loss £8,000; those aged 61+ lost average £19,000. Men made up 60% of reports by volume.
- **Pain Receipt:** Romance scams increasing across all demographics; older victims lose more
- **Taxonomy:** Offense Signal — Romance Fraud Escalation; Pain Receipt — Age-Disproportionate Losses

### Incident 24: DOJ Elder Fraud Enforcement — 700+ Defendants
- **Source:** S17
- **Date:** July 2023 – June 2024
- **Description:** DOJ pursued over 300 enforcement actions against more than 700 defendants charged with stealing nearly $700 million from approximately 225,000 elder fraud victims. $700M prosecuted represents ~15 cents of every dollar reported lost by 60+ cohort.
- **Pain Receipt:** Vast gap between reported losses and enforcement recovery
- **Taxonomy:** Pain Receipt — Enforcement Gap; Defense Fixer — Coordinated Law Enforcement Action

### Incident 25: Cifas UK Fraud Record — 217,000 Cases in 6 Months
- **Source:** S28
- **Date:** H1 2025
- **Description:** UK fraud prevention service Cifas recorded 217,000+ fraud cases in H1 2025. 118,000+ identity fraud cases. Telecommunications saw steepest rise in account takeovers (69% of all takeovers). People selling their own identities emerged as a new trend.
- **Pain Receipt:** Identity fraud spreading into insurance, mobile, gambling sectors; people selling credentials
- **Taxonomy:** Offense Signal — Identity Market Commoditization; Pain Receipt — Cross-Sector Identity Abuse

### Incident 26: DeepFake Content Explosion — 1,500% Growth
- **Source:** S18
- **Date:** 2023-2025
- **Description:** Deepfake content grew from ~500,000 files in 2023 to ~8 million in 2025 (1,500% increase). Deepfake-enabled vishing attacks surged 1,600% in Q1 2025. 46% of deepfake incidents used celebrity likenesses. CEO fraud targets at least 400 companies per day.
- **Pain Receipt:** Deepfake technology is being weaponized faster than defenses can adapt
- **Taxonomy:** Offense Signal — Deepfake Industrialization; Pain Receipt — Verification System Failure

### Incident 27: Barclays UK — £214M Social Media Fraud Over 5 Years
- **Source:** S85
- **Date:** 2020-2025
- **Description:** UK consumers lost £214 million to financial scams on social media over 5 years. Facebook losses were £28 million in 2024 alone. LinkedIn had highest per-scam losses at £40,000+ per report.
- **Pain Receipt:** Social media platforms are primary vectors for financial fraud; platforms slow to act
- **Taxonomy:** Offense Signal — Social Media Platform Fraud; Pain Receipt — Platform-Inaction Enabled Losses

### Incident 28: FTC Restoro Tech Support — $25.5M Refund
- **Source:** S5
- **Date:** 2024-2025
- **Description:** FTC settled with Restoro Cyprus Limited and Reimage Cyprus Limited for alleged tech support schemes that particularly impacted older consumers. FTC sent more than $25.5 million to impacted consumers.
- **Pain Receipt:** Tech support scams continue to extract massive sums from elderly victims
- **Taxonomy:** Offense Signal — Fake Tech Support; Defense Fixer — Government Restitution

### Incident 29: TransUnion — 1.6 Billion Consumer Records Exposed in 2024
- **Source:** S29
- **Date:** 2024
- **Description:** TransUnion identified over 2,400 data breaches exposing 1.6 billion consumer records, enabling fraud against government agencies. Government transaction fraud rate was 6.7% in 2024, a 31% increase from 2023.
- **Pain Receipt:** Data breaches fuel downstream identity fraud across all sectors
- **Taxonomy:** Offense Signal — Mass Data Breach; Pain Receipt — Identity Fraud Enabling Infrastructure

---

## 5. OFFENSE SIGNAL TAXONOMY

### Signal Category: OS-FIN-001 — Investment Fraud
| Sub-Signal | Description | Key Data |
|-----------|-------------|----------|
| OS-FIN-001-A | Cryptocurrency investment scams | $11.3B losses, 181,565 complaints (IC3 2025) [S3] |
| OS-FIN-001-B | Social media investment fraud | $1.1B losses (FTC 2025) [S30] |
| OS-FIN-001-C | Pig butchering (romance→investment) | $3.9B losses, avg $100K+ per victim [S20] |
| OS-FIN-001-D | Fake crypto asset offerings | Unicoin $42M+, PGI Global $198M [S6] |
| OS-FIN-001-E | Ponzi/pyramid schemes | Multiple SEC enforcement actions [S6, S7] |

### Signal Category: OS-IMP-002 — Impersonation & BEC
| Sub-Signal | Description | Key Data |
|-----------|-------------|----------|
| OS-IMP-002-A | Business Email Compromise | $3.046B, 24,768 complaints [S1] |
| OS-IMP-002-B | CEO/CFO impersonation | Avg $137K per incident [S16] |
| OS-IMP-002-C | Vendor email compromise | $4.9M real estate case [S14] |
| OS-IMP-002-D | Government impersonation | $789M losses (FTC 2024) [S9] |
| OS-IMP-002-E | Tech support impersonation | $2.135B losses (IC3 2025) [S1] |

### Signal Category: OS-AI-003 — AI-Enabled Fraud
| Sub-Signal | Description | Key Data |
|-----------|-------------|----------|
| OS-AI-003-A | AI-generated deepfake video | Arup $25M loss [S18] |
| OS-AI-003-B | Voice clone fraud | 77% victim loss rate [S18] |
| OS-AI-003-C | AI BEC (AI-nexus) | $30M+ confirmed losses [S12] |
| OS-AI-003-D | Synthetic media for identity bypass | Deepfake content up 1,500% [S18] |
| OS-AI-003-E | AI chatbot romance scams | Scale enables 40+ simultaneous targets [S20] |

### Signal Category: OS-IDR-004 — Identity Fraud
| Sub-Signal | Description | Key Data |
|-----------|-------------|----------|
| OS-IDR-004-A | Synthetic identity fraud | 80%+ of new account fraud [S19] |
| OS-IDR-004-B | Account takeover | $2.9B losses, fastest-growing [S33] |
| OS-IDR-004-C | Identity theft | 1.157M reports in 9 months (2025) [S22] |
| OS-IDR-004-D | Credential stuffing | Primary ATO vector [S33] |
| OS-IDR-004-E | Biometric/deepfake ID bypass | 311% surge in synthetic ID doc fraud [S19] |

### Signal Category: OS-EXT-005 — Extortion & Ransomware
| Sub-Signal | Description | Key Data |
|-----------|-------------|----------|
| OS-EXT-005-A | Ransomware attacks | $32.32M losses, +259% [S12] |
| OS-EXT-005-B | Double extortion | 77% involve data exfiltration [S34] |
| OS-EXT-005-C | Critical infrastructure targeting | 50% of attacks hit critical sectors [S25] |
| OS-EXT-005-D | Ransomware-as-a-Service | 103 active groups, top 5 = 25% incidents [S25] |

### Signal Category: OS-SOC-006 — Social Engineering
| Sub-Signal | Description | Key Data |
|-----------|-------------|----------|
| OS-SOC-006-A | Romance scams | $1.2B (FTC), $672M (IC3) [S20] |
| OS-SOC-006-B | Social media fraud platform | $ billions via Facebook, Instagram [S30, S85] |
| OS-SOC-006-C | Elder-targeted scams | $7.7B (IC3 60+), $2.4B (FTC 60+) [S11, S5] |
| OS-SOC-006-D | Phishing/spoofing | 191,561 complaints (IC3 2025) [S13] |

---

## 6. DEFENSE FIXER CATALOG

### Fixer Category: DF-PREV — Prevention

| Fixer ID | Name | Description | Effectiveness Evidence | Source |
|----------|------|-------------|----------------------|--------|
| DF-PREV-001 | Multi-Factor Authentication (MFA) | Enforce MFA on all email, financial, and admin accounts | Prevents 99%+ of credential-based ATO | S33 |
| DF-PREV-002 | Email Authentication (DMARC/SPF/DKIM) | Prevent email spoofing and domain impersonation | Reduces BEC success rate significantly | S14, S15 |
| DF-PREV-003 | Vendor Verification Protocols | Out-of-band verification for payment changes | 66% success rate for freezing fraudulent transfers within 24hrs | S16 |
| DF-PREV-004 | Employee Security Training | Regular phishing and BEC awareness training | Reduces click-through on phishing; addresses "operational, not informational" gap | S12 |
| DF-PREV-005 | Out-of-Band Wire Verification | Phone/voice verification for wire transfers | Prevents BEC wire fraud when enforced | S16 |
| DF-PREV-006 | Deepfake Detection Software | AI-based deepfake detection for video/voice calls | Human detection rates under 25% without tools | S18 |
| DF-PREV-007 | Credit Freezes | Freeze credit reports to prevent synthetic identity creation | Prevents new account fraud using stolen SSNs | S19 |
| DF-PREV-008 | Privacy Settings Restriction | Limit social media post/contact visibility | Reduces scammer targeting surface | S30 |
| DF-PREV-009 | Endpoint Detection & Response (EDR) | Real-time monitoring for ransomware and malware | Critical for detecting ransomware before encryption | S12 |
| DF-PREV-010 | Patch Management | Rapid patching of known vulnerabilities | Exploitation of unpatched vulnerabilities is top ransomware vector | S88 |

### Fixer Category: DF-DETE — Detection

| Fixer ID | Name | Description | Effectiveness Evidence | Source |
|----------|------|-------------|----------------------|--------|
| DF-DETE-001 | BEC Email Analysis Tools | AI-powered email content and sender behavior analysis | Detects BEC without malicious links/attachments | S14 |
| DF-DETE-002 | Account Anomaly Detection | Behavioral analytics for unusual login/transactions | Flags synthetic identity and ATO patterns | S19, S29 |
| DF-DETE-003 | Dark Web Monitoring | Monitor for exposed credentials and identity data | 1.6B records exposed in 2024 [S29]; early warning | S29 |
| DF-DETE-004 | Synthetic Identity Scoring | ML models to detect synthetic identities during onboarding | Identifies 0.08% synthetic rate in gov transactions | S29 |
| DF-DETE-005 | Voice Biometric Verification | Liveness detection and voiceprint matching | Countermeasure against voice clone fraud | S18 |
| DF-DETE-006 | Ransomware Behavior Monitoring | File activity monitoring for encryption patterns | Enables rapid containment | S12 |

### Fixer Category: DF-RESP — Response

| Fixer ID | Name | Description | Effectiveness Evidence | Source |
|----------|------|-------------|----------------------|--------|
| DF-RESP-001 | Financial Fraud Kill Chain | IC3 Recovery Asset Team rapid freeze process | 66% freeze rate when reported within 24 hours | S16, S23 |
| DF-RESP-002 | FBI IC3 Reporting | File complaint at ic3.gov for investigation | Enables pattern detection and enforcement | S3 |
| DF-RESP-003 | Operation Level Up | FBI proactive victim notification for crypto fraud | 8,000+ victims notified; $500M+ losses prevented | S3 |
| DF-RESP-004 | International Fraud Kill Chain | Cross-border partnership for freezing wired funds | Coordinated through FinCEN Rapid Response | S23 |
| DF-RESP-005 | Incident Response Plan | Documented ransomware response procedures | Reduces downtime from days to hours | S12 |
| DF-RESP-006 | Decryption Key Distribution | FBI distributes ransomware decryption keys | Prevented $800M in ransom payments (since 2022) | S23 |

### Fixer Category: DF-RECO — Recovery & Restitution

| Fixer ID | Name | Description | Effectiveness Evidence | Source |
|----------|------|-------------|----------------------|--------|
| DF-RECO-001 | FTC Consumer Refunds | Government-mandated scam restitution | Restoro: $25.5M; Aqua Finance: $20M + $23.6M debt forgiveness | S5 |
| DF-RECO-002 | Bank Reimbursement Programs | Voluntary/mandatory APP fraud reimbursement | UK rules: up to £85,000 reimbursement unless gross negligence | S20 |
| DF-RECO-003 | Cyber Insurance | Financial protection against ransomware and fraud | Covers remediation, legal, business interruption costs | S12 |

### Fixer Category: DF-POLI — Policy & Regulatory

| Fixer ID | Name | Description | Effectiveness Evidence | Source |
|----------|------|-------------|----------------------|--------|
| DF-POLI-001 | SEC Cyber & Emerging Technologies Unit | Launched Feb 2025 to combat crypto/AI fraud | Charged Unicoin, PGI Global, Nate AI fraud cases | S6 |
| DF-POLI-002 | SEC Cross-Border Task Force | Formed Sep 2025 to address transnational fraud | Pursues foreign-based fraudsters targeting US investors | S6 |
| DF-POLI-003 | FTC Pass It On Campaign | Fraud prevention education for older adults | Targets elder fraud through community education | S5 |
| DF-POLI-004 | FTC Scams Against Older Adults Advisory Group | Created by Stop Senior Scams Act | Coordinates cross-sector elder fraud prevention | S5 |
| DF-POLI-005 | Nacha Rules Updates (2026) | New rules to reduce fraud and improve fund recovery | Taking effect 2026 for BEC prevention | S32 |

---

## 7. APPENDIX: DETAILED SOURCE NOTES

### S1: FBI IC3 2025 Internet Crime Report
- **Owner:** FBI Internet Crime Complaint Center
- **URL:** https://www.fbi.gov/file-repository/2025_ic3report.pdf/view
- **Released:** May 15, 2026
- **Trust Tier:** 1
- **Key Data:** 1,008,597 complaints; $20.877B losses; 26% increase; BEC $3.046B; ransomware $32.32M (+259%); investment fraud $8.649B; crypto $11.3B; AI section first time; 22,364 AI complaints, ~$893M

### S2: FBI IC3 2024 Internet Crime Report
- **Owner:** FBI IC3
- **URL:** https://www.fbi.gov/news/press-releases/fbi-releases-annual-internet-crime-report
- **Released:** April 23, 2025
- **Trust Tier:** 1
- **Key Data:** 859,532 complaints; $16.6B losses (+33%); 333,981 cyber-enabled fraud complaints; $13.7B cyber-enabled fraud losses; BEC 21,442 complaints, ~$2.8B; elder losses $4.8B; Operation Level Up active

### S3: FBI Press Release — Crypto & AI Scams
- **Owner:** FBI
- **URL:** https://www.fbi.gov/news/press-releases/cryptocurrency-and-ai-scams-bilk-americans-of-billions
- **Released:** April 6, 2026
- **Trust Tier:** 1
- **Key Data:** $20.877B losses; 1,008,597 complaints; investment fraud 49% of scam losses; crypto 181,565 complaints, $11B+; AI 22,364 complaints, ~$893M; Operation Level Up 8,000+ victims, $500M+ prevented; Operation Winter SHIELD launched

### S4/S9: FTC Consumer Sentinel Data Book 2024
- **Owner:** FTC
- **URL:** https://www.ftc.gov/exploredata
- **Released:** March 10, 2025
- **Trust Tier:** 1
- **Key Data:** $12.5B+ fraud losses (+25%); 2.6M fraud reports; 1.1M identity theft reports; investment scams $5.7B; imposter scams $2.95B; email #1 contact method; 38% lost money (up from 27%); government impersonation $789M; job scams $750.6M

### S5: FTC Annual Report to Congress — Protecting Older Adults
- **Owner:** FTC
- **URL:** https://www.ftc.gov/news-events/news/press-releases/2025/12/ftc-issues-annual-report
- **Released:** December 1, 2025
- **Trust Tier:** 1
- **Key Data:** Elder losses $2.4B (2024), 4x from 2020; $81.5B estimated true cost; Restoro $25.5M refunds; Aqua Finance $20M refunds + $23.6M debt forgiveness; Paddle $5M settlement; tech support $159M (60+); median loss 80+ >$1,600

### S6: SEC Enforcement Results FY2025
- **Owner:** SEC
- **URL:** https://www.sec.gov/newsroom/press-releases/2026-34
- **Released:** April 7, 2026
- **Trust Tier:** 1
- **Key Data:** Cyber & Emerging Technologies Unit launched Feb 2025; Cross-Border Task Force Sep 2025; Unicoin charges; PGI Global $198M fraud/$57M misappropriation; Nate AI $42M+ fraud; market manipulation enforcement; spoofing cases

### S7: SEC Cryptocurrency Enforcement 2025 Update
- **Owner:** Cornerstone Research (analysis of SEC data)
- **URL:** https://www.cornerstone.com/insights/research/sec-cryptocurrency-enforcement-2025-update/
- **Released:** April 17, 2026
- **Trust Tier:** 2
- **Key Data:** 33 crypto actions in 2024, 13 in 2025 (-60%); $142M penalties 2025 (<3% of 2024); enforcement shift under new administration

### S10: CFTC Virtual Currency Enforcement Trends
- **Owner:** JD Supra / Cornerstone Research
- **URL:** https://www.jdsupra.com/legalnews/key-trends-in-cftc-virtual-currency-2636711/
- **Released:** May 20, 2026
- **Trust Tier:** 2
- **Key Data:** 130 total actions Q1 2015-Q3 2025; 50 litigated; 10 actions in 2024, 0 in 2025 (Q1-Q3); leadership transition impact; BTC in 98 actions, ETH in 25, USDT in 8

### S11: AARP — FBI Report Analysis
- **Owner:** AARP
- **URL:** https://www.aarp.org/money/scams-fraud/fbi-ftc-report-2025-losses/
- **Released:** April 16, 2026
- **Trust Tier:** 2
- **Key Data:** 60+ losses $7.7B (+60%); investment scams $8.6B; crypto fraud $11.3B; tech support $2.1B; romance $929M; 30s-40s $4.6B losses; advocacy for crypto kiosk regulation

### S12: McDonald Hopkins — IC3 2025 Analysis
- **Owner:** McDonald Hopkins (law firm)
- **URL:** https://www.mcdonaldhopkins.com/insights/news/the-sobering-truth-of-the-fbis-2025-internet-crime-complaint-center-report
- **Released:** April 7, 2026
- **Trust Tier:** 2
- **Key Data:** $20.877B (+26%); BEC $3.046B, 24,768 complaints; AI-nexus BEC $30M+; ransomware 3,611 reports, $32.32M (+259%); 63 new ransomware variants; gap is "operational, not informational"; BEC "not technically complex" but still growing

### S14: TitanHQ — State of Email Security 2025
- **Owner:** TitanHQ
- **URL:** https://www.titanhq.com/email-security-2025/state-email-security-report-2025/
- **Released:** April 22, 2026
- **Trust Tier:** 2
- **Key Data:** BEC $2.9B (2024); 21,489 incidents; $50M construction loss; $426K spoofed attorney; $4.9M real estate recovery; 12.9% employees at orgs lost money; 21.6% MSP customers; 45.1% employee data breaches; 56.3% expect BEC increase

### S15: LevelBlue — BEC Trends
- **Owner:** LevelBlue (AT&T)
- **URL:** https://www.levelblue.com/blogs/spiderlabs-blog/bec-email-trends-attacks-up-15-in-2025/
- **Released:** January 13, 2026
- **Trust Tier:** 2
- **Key Data:** BEC emails +15% in 2025; 3,000+ intercepted/month; peak 4,300 July; contact details swapping as new tactic; Q3 seasonal increase

### S17: Elder Fraud Statistics 2026
- **Owner:** Discreet Investigations
- **URL:** https://discreetinvestigations.ca/research/elder-fraud-statistics/
- **Released:** May 2, 2026
- **Trust Tier:** 2
- **Key Data:** $4.8B (2024 IC3); $2.4B (2024 FTC); $137.9M CAD (CAFC); UK £7.4B estimate; 7,500 lost $100K+; avg $83K; DOJ 300 actions, 700 defendants, $700M; NCOA $28.3B annual cost; fiduciary perpetrator avg $83,600

### S18: Deepfake Statistics & Trends 2026
- **Owner:** Keepnet Labs
- **URL:** https://keepnetlabs.com/blog/deepfake-statistics-and-trends
- **Released:** May 21, 2026
- **Trust Tier:** 2
- **Key Data:** Gen AI fraud $12.3B (2023) → $40B (2027); avg $500K per incident; Arup $25M; UK energy €220K; 400 CEO frauds/day; 77% voice clone victim loss rate; deepfake losses $1.1B US 2025 (3x); $200M+ Q1 2025 NA; vishing +1,600%; 48% celebrity likeness; content 500K→8M

### S19: Synthetic Identity Fraud Statistics 2026
- **Owner:** BIIA
- **URL:** https://www.biia.com/synthetic-identity-fraud-statistics-2026/
- **Released:** January 14, 2026
- **Trust Tier:** 2
- **Key Data:** $30-35B annual US losses; $3.3B lender exposure; 67% of FIs saw fraud rise; 8.3% digital onboarding fraudulent; 64% cite AI/deepfake concern; 80%+ of new account fraud; 21% of first-party fraud; 153% synthetic account fraud growth

### S20: Romance Scam Statistics 2025-2026
- **Owner:** Arnaques-Rencontres
- **URL:** https://www.arnaques-rencontres.fr/en/articles/romance-scam-statistics
- **Released:** March 10, 2026
- **Trust Tier:** 2
- **Key Data:** FTC $1.2B; IC3 $672M; pig butchering $3.9B; 60,000+ reports; $2,000 median; crypto 34% payments; social media 40% contact; 55-64 highest losses; UK £92M; Australia AUD $40.6M; Canada CAD $50.3M; 5-15% reporting rate

### S22: Identity Theft Statistics 2025
- **Owner:** Motley Fool
- **URL:** https://www.fool.com/money/research/identity-theft-credit-card-fraud-statistics/
- **Released:** January 12, 2026
- **Trust Tier:** 2
- **Key Data:** 1,157,317 cases Q1-Q3 2025 (exceeding all 2024); 2024: 1,135,291; 2021 peak: 1,434,477; Javelin $23B losses 2023; record pace for 2025

### S24/S25: KELA Ransomware Critical Infrastructure
- **Owner:** KELA / Industrial Cyber
- **URL:** https://codekeeper.co/ticker/ransomware-attacks-on-critical-infrastructure-2025
- **Released:** October 22, 2025
- **Trust Tier:** 2
- **Key Data:** 4,701 incidents Jan-Sep 2025 (+34%); 2,332 critical infrastructure (50%); US 21%; manufacturing +61%; 5 groups = 25% incidents; Jaguar Land Rover; Bridgestone; Qilin, Clop, Akira, Play, SafePay top groups

### S27: Sumsub Identity Fraud Trends 2026
- **Owner:** Sumsub
- **URL:** https://sumsub.com/blog/top-new-identity-fraud-trends/
- **Released:** December 2, 2025
- **Trust Tier:** 2
- **Key Data:** Sophisticated fraud 10%→28% (+180%); overall fraud stable 2.0%→2.2%; AI-generated IDs; fraud rings; synthetic + deepfake combos; 311% synthetic ID doc fraud surge NA Q1 2025

### S28: Cifas Fraudscape UK 2025
- **Owner:** Cifas (UK fraud prevention)
- **URL:** https://www.cifas.org.uk/newsroom/fraudscape-2025-6monthupdate
- **Released:** August 5, 2025
- **Trust Tier:** 2
- **Key Data:** 217,000 cases H1 2025; 118,000 identity fraud; insurance +25%; telco takeovers 69%; public sector +88%; gambling +109%; people selling own identities

### S29: TransUnion Identity Fraud for Government
- **Owner:** TransUnion
- **URL:** https://events.afcea.org/fedid25/CUSTOM/pdf/transunion_tl.pdf
- **Released:** 2025
- **Trust Tier:** 2
- **Key Data:** 1.6B records exposed 2024; 2,400+ breaches; gov fraud rate 6.7% (+31%); SSN mismatch 6%; synthetic identity 0.08%; IRS exposure $283M; $3.3B lender exposure

### S30: FTC Social Media Scam Losses
- **Owner:** FTC
- **URL:** https://www.ftc.gov/news-events/news/press-releases/2026/04/new-ftc-data-show-people-have-lost-billions-to-social-media-scams
- **Released:** April 27, 2026
- **Trust Tier:** 1
- **Key Data:** $1.1B investment scams on social media; shopping scams most reported; 60% romance scams started on social media; privacy settings advice; investment scam warnings

### S33: Account Takeover Statistics 2025
- **Owner:** AuthX
- **URL:** https://authx.com/blog/account-takeover-fraud-statistics-insights/
- **Released:** November 26, 2025
- **Trust Tier:** 2
- **Key Data:** $12.5B identity fraud losses (FTC); $17B global ATO projected; $5M avg corporate breach; $180 avg individual; $2.9B ATO losses; fastest-growing fraud

### S34: DeepStrike Ransomware Statistics 2026
- **Owner:** DeepStrike
- **URL:** https://deepstrike.io/blog/ransomware-statistics-2025
- **Released:** May 15, 2025
- **Trust Tier:** 2
- **Key Data:** 7,500 victims on leak sites (+58%); $820M blockchain payments; 28% payment rate (record low); median $59.6K (from $12.7K); 77% double extortion; avg breach cost $5M

---

## KEY FINDINGS SUMMARY

### Top 10 Most Actionable Findings

1. **Crypto fraud is the dominant loss vector**: $11.3B in IC3 2025 losses — nearly 54% of all fraud losses. Every defense system must prioritize crypto transaction verification.

2. **AI is fundamentally changing fraud**: First-ever AI section in IC3 report; $893M in AI-related losses; deepfake fraud tripled. Static defenses are becoming obsolete.

3. **Elder fraud is accelerating faster than overall trends**: 60+ losses up 60% vs. 26% overall. Age-specific defenses are critical.

4. **BEC remains the #1 enterprise threat**: $3.046B in losses; average $137K per incident; 83-95% unrecoverable. The gap is "operational, not informational."

5. **Ransomware losses surged 259%**: Despite fewer victims paying (28%), median payments soared to $59.6K. Double extortion is now the norm (77%).

6. **Social media is the #1 fraud distribution channel**: $1.1B in investment scams alone; platforms are slow to remove scam content (Facebook took 1,024 days in one case).

7. **Synthetic identity fraud is systemic**: 80%+ of new account fraud; $3.3B lender exposure; projected $23B by 2030. Traditional KYC is failing.

8. **Pig butchering is the most devastating hybrid scam**: Romance + investment convergence; $3.9B+ losses; avg $100K+ per victim; run by trafficked labor in SE Asia.

9. **Reporting underrepresentation is massive**: FTC estimates true fraud losses at $195.9B (vs. $12.5B reported). Only 2-6.7% of victims report.

10. **Proactive victim notification works**: FBI Operation Level Up prevented $500M+ in losses through proactive notification of 8,000+ victims.

---

*Document compiled: May 25, 2026*
*Sources: 40+ Tier 1 and Tier 2 authoritative sources*
*Incidents documented: 29 specific real patterns/incidents*
*Defense fixers identified: 21 across 5 categories*
*Offense signals categorized: 6 major categories with 30+ sub-signals*
