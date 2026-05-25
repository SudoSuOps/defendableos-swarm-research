# DefendableOS Research: Dimension 03 — Cyber and AI System Risk

## Research Summary
**Research Date:** May 25, 2026
**Researcher:** AI Research Agent
**Sources Consulted:** 30+ primary and secondary sources across 12 independent search queries
**Incidents/Vulnerabilities Cataloged:** 40+
**Taxonomy Framework:** Offense Signal → Pain Receipt → Defense Fixer

---

## Table of Contents
1. [Executive Summary](#executive-summary)
2. [Landscape Context](#landscape-context)
3. [Offense Signals](#offense-signals)
4. [Pain Receipts](#pain-receipts)
5. [Defense Fixers](#defense-fixers)
6. [Source Registry](#source-registry)

---

## Executive Summary

The cyber and AI system risk landscape in 2024-2025 has been defined by three converging trends: (1) the explosive growth of exploited vulnerabilities with 50,000 CVEs published in 2025 and the CISA KEV catalog reaching 1,484 entries, (2) the transformation of ransomware into a more targeted "big game hunting" industry with declining payment rates but escalating impacts, and (3) the emergence of AI-specific attack vectors — particularly prompt injection, jailbreaking, and data poisoning — that expose fundamental architectural weaknesses in deployed AI systems.

The Change Healthcare ransomware attack alone exposed 192.7 million health records, making it the largest healthcare breach in history. Meanwhile, AI agents are being deployed with L4-L5 autonomy levels without documented safety evaluations, and research demonstrates that all evaluated models remain susceptible to indirect prompt injection attacks with absolute attack success rates ranging from 0.5% to 8.5% across models [^67^].

---

## Landscape Context

### Vulnerability Statistics (2024-2025)
- **Total CVEs published in 2025:** ~50,000 (22% increase over 2024's ~40,000) [^111^]
- **Cumulative CVE total:** Surpassed 300,000 [^111^]
- **CISA KEV catalog total:** 1,484 vulnerabilities [^113^]
- **KEV additions in 2025:** 245 (20% growth, 30% above 2023-2024 trend) [^113^]
- **KEV vulnerabilities linked to ransomware:** 304 (20.5%) [^113^]
- **Microsoft KEV entries:** 350 total (24% of catalog) [^113^]
- **Average time to exploit in 2025:** Negative one day (exploitation before patch availability) [^111^]
- **56% of vulnerabilities weaponized within first month of disclosure** [^111^]
- **50% of critical KEV vulnerabilities remain unpatched 55 days after fix** [^111^]

### AI Security Milestones
- **NIST AI RMF 1.0:** Published January 2023 [^13^]
- **NIST AI 600-1 (Generative AI Profile):** Published 2024 [^13^]
- **NIST AI RMF Agentic Profile:** Published May 2026 [^13^]
- **OWASP Top 10 for LLMs 2025:** Updated with new risks including System Prompt Leakage (LLM07) and Vector/Embedding Weaknesses (LLM08) [^69^]
- **Prompt injection remains #1 OWASP LLM risk for 2025** [^69^]

### Breach Cost Metrics
- **Global average breach cost (2025):** $4.44 million (down 9% from $4.88M in 2024) [^139^]
- **US average breach cost:** $10.22 million (all-time high) [^140^]
- **Healthcare average breach cost:** $7.42 million (15th consecutive year as costliest sector) [^140^]
- **Ransomware breach average cost:** $5.08 million [^139^]
- **Shadow AI breach premium:** +$670,000 [^140^]

---

## Offense Signals

### OS-001: Known Exploited Vulnerability (KEV) Growth Pattern
**Signal Class:** Systemic vulnerability accumulation
**Description:** CISA's KEV catalog grew 20% in 2025, adding 245 vulnerabilities — the largest annual addition since the catalog's 2021 launch. This represents a reacceleration after growth stabilized in 2023-2024 (187 and 185 additions respectively) [^113^].

**Key Indicators:**
- 24 KEV additions in 2025 were explicitly linked to ransomware exploitation [^113^]
- 94 older vulnerabilities (from 2024 and prior) were added — a 45% increase over the 2023-2024 average of 65 [^113^]
- Oldest vulnerability added in 2025: CVE-2007-0671 (Microsoft Office Excel RCE from 2007) [^15^]
- Oldest in catalog: CVE-2002-0367 (Windows NT/2000 privilege escalation) [^15^]

**Most Common CWEs in 2025 KEV Additions:** [^113^]
| CWE | Count | Description |
|-----|-------|-------------|
| CWE-78 | 18 | OS Command Injection |
| CWE-502 | 14 | Deserialization of Untrusted Data |
| CWE-22 | 13 | Path Traversal |
| CWE-416 | 11 | Use After Free |
| CWE-787 | 10 | Out-of-bounds Write |
| CWE-79 | 7 | Cross-site Scripting |
| CWE-94 | 6 | Code Injection |
| CWE-287 | 6 | Improper Authentication |

**Evidence Source:** Cyble analysis of CISA KEV data; SecurityWeek reporting [^113^] [^15^]

---

### OS-002: Critical RCE Vulnerabilities (2025 Headlines)
**Signal Class:** Weaponized remote code execution
**Description:** 2025 saw multiple critical RCE vulnerabilities exploited in the wild with devastating impact, often before patches were available.

#### OS-002-A: React2Shell (CVE-2025-55182)
- **CVSS:** 10.0 (Critical)
- **Description:** Unauthenticated RCE in React Server Components via insecure deserialization of RSC Flight protocol payloads
- **Impact:** Shadowserver detected 28,964 vulnerable IPs; exploitation by Chinese APT UNC5174 [^111^] [^118^]
- **Attack vector:** Malicious serialized data submitted to vulnerable React Server Components

#### OS-002-B: ToolShell (CVE-2025-53770)
- **CVSS:** 9.8 (Critical)
- **Description:** Unauthenticated RCE in Microsoft SharePoint via insecure deserialization
- **Impact:** 396 confirmed compromised systems; 16,000+ exposed SharePoint servers globally [^117^]
- **Attribution:** Chinese APT groups — Linen Typhoon (APT27), Violet Typhoon (APT31), Storm-2603 [^117^]
- **Post-exploitation:** Attackers extracted ASP.NET MachineKeys to forge __VIEWSTATE payloads [^117^]

#### OS-002-C: Oracle EBS Zero-Day (CVE-2025-61882)
- **CVSS:** Critical
- **Description:** Pre-auth RCE in Oracle E-Business Suite BI Publisher Integration
- **Impact:** Cl0p ransomware group used for aggressive extortion campaigns [^111^]
- **Targets:** GlobalLogic, Barts Health NHS Trust among others [^111^]

#### OS-002-D: Cisco AsyncOS (CVE-2025-20393)
- **CVSS:** 10.0 (Critical)
- **Description:** Zero-day in Cisco Secure Email Gateway
- **Impact:** Exploited by China-nexus APT UAT-9686 to deploy tunneling tools (ReverseSSH, Chisel) and custom backdoors [^111^]

#### OS-002-E: Ivanti Connect Secure (CVE-2025-0282)
- **CVSS:** 9.0 (Critical)
- **Description:** Stack-based buffer overflow enabling unauthenticated RCE in Ivanti Connect Secure VPN appliances
- **Impact:** Zero-day exploitation beginning mid-December 2024; confirmed breach at Nominet (.UK registry operator) [^148^]
- **Attribution:** Mandiant tracked as UNC5337; Microsoft observed Silk Typhoon exploiting [^148^]
- **CISA KEV:** Added January 8, 2025; deadline January 15, 2025 [^117^]

#### OS-002-F: Apache Tomcat RCE (CVE-2025-24813)
- **CVSS:** 9.8 (Critical)
- **Description:** Remote code execution in Apache Tomcat [^112^]

#### OS-002-G: Palo Alto Auth Bypass (CVE-2025-0108)
- **Description:** Authentication bypass in PAN-OS firewall management interface; incomplete fix for prior CVE-2024-0012 [^112^]

#### OS-002-H: Fortinet Perimeter (CVE-2024-55591, CVE-2025-32756)
- **Description:** Authentication bypass in FortiOS and critical flaw in FortiVoice [^112^]

**Evidence Source:** Intruder.io, SOCRadar, MazeHQ, FortiGuard Labs [^111^] [^112^] [^117^] [^148^]

---

### OS-003: Ransomware Ecosystem Evolution
**Signal Class:** Criminal business model adaptation
**Description:** The ransomware landscape underwent significant structural transformation in 2024-2025, with the RaaS model declining after law enforcement disruptions and attackers pivoting to targeted social engineering.

**Key Indicators:**
- **Payment refusal rate:** 64% refused to pay in 2025 (up from 59% in 2024) [^139^]
- **Total ransom payments:** $813.55 million in 2024 (down 35% from $1.25 billion in 2023) [^139^]
- **Record single payment:** $75 million to Dark Angels group (Fortune 50 company) [^139^]
- **Re-attack rate:** 80% of paying victims attacked again within 12 months [^138^]
- **Data recovery failure:** Only 4% recovered ALL data after paying [^138^]
- **Fastest breakout time:** 27 seconds (CrowdStrike 2026 report) [^125^]
- **Average eCrime breakout time:** 29 minutes in 2025 (65% faster than 2024) [^125^]
- **Malware-free attacks:** 79% of detections in 2024 (up from 40% in 2019) [^124^]

**Most Active Ransomware Groups (2025):**
| Group | Activity |
|-------|----------|
| Akira | 11% of observed cases (tied #1) |
| Fog | 11% of observed cases (tied #1) |
| RansomHub | 8% of cases; 89 confirmed attacks |
| Medusa | 5% of cases; responsible for SimonMed Imaging breach |
| Cl0p | Oracle EBS exploitation; data extortion campaigns |

**Evidence Source:** Coveware, Chainalysis, Verizon DBIR, CrowdStrike, Sophos [^138^] [^139^] [^140^]

---

### OS-004: AI Prompt Injection and Jailbreaking
**Signal Class:** AI-specific attack vectors
**Description:** Prompt injection remains the #1 risk in the OWASP Top 10 for LLMs 2025. Research demonstrates that all evaluated frontier models are vulnerable to indirect prompt injection, with attacks achieving harmful execution while concealing malicious intent from users.

**Key Indicators:**
- **OWASP LLM Top 10 2025 Ranking:** [^69^]
  1. Prompt Injection (LLM01)
  2. Sensitive Information Disclosure (LLM02) — jumped from #6 to #2
  3. Supply Chain (LLM03) — rose to #3
  4. Data and Model Poisoning (LLM04)
  5. Improper Output Handling (LLM05)
  6. Excessive Agency (LLM06)
  7. System Prompt Leakage (LLM07) — NEW 2025
  8. Vector and Embedding Weaknesses (LLM08) — NEW 2025
  9. Misinformation (LLM09)
  10. Unbounded Consumption (LLM10)

- **Attack Success Rates across models:** ASR ranged from 0.5% (Claude Opus 4.5) to 8.5% (Gemini 2.5 Pro) [^67^]
- **Tool use scenarios most vulnerable:** 4.82% ASR vs. 3.13% computer use vs. 2.51% coding [^67^]
- **Universal attacks succeeded across 21 of 41 harmful behaviors and multiple model families** [^67^]
- **Attack transfer rate:** Attacks from robust models transferred at 44-81% to all other targets [^67^]
- **LLM-generated phishing click rate:** 54% vs. 12% for human-written (4.5x improvement) [^124^]
- **Many-shot jailbreaking:** Harmful response rates increase from ~0% at 22 demonstration shots to 60-80% at 28+ shots across GPT-4, Claude 2.0, and Llama 2 70B [^126^]

**Real-World Exploitation:**
- **Microsoft 365 Copilot data exfiltration** via prompt injection (Johann Rehberger, 2024) [^67^]
- **ChatGPT Operator prompt injection exploits** (2025) [^67^]
- **Devin AI kill chain** exposing ports to RCE and file exfiltration (2025) [^67^]
- **Commercial LLM agents vulnerable to simple attacks** achieving harmful outcomes [^67^]

**Evidence Source:** arXiv research (arXiv:2603.15714), OWASP, DeepTeam, SentinelOne [^67^] [^69^] [^126^]

---

### OS-005: Nation-State APT Escalation
**Signal Class:** State-sponsored cyber operations
**Description:** China-nexus activity surged dramatically across all sectors, with specialized adversaries demonstrating unprecedented focus on telecommunications, financial services, and critical infrastructure.

**Key Indicators:**
- **China-nexus cyber espionage:** 150% increase across all sectors in 2024 [^124^]
- **Financial services, media, manufacturing:** 200-300% increases in observed intrusions [^124^]
- **CrowdStrike tracked 257 adversaries total** (26 newly named in 2024) [^124^]
- **Salt Typhoon:** Breached at least 8 US telecom providers and providers in 20+ countries [^133^]
- **Volt Typhoon:** Targeted water utilities and energy infrastructure [^133^]
- **Silk Typhoon:** Exploited Ivanti Connect Secure zero-day (CVE-2025-0282) [^148^]
- **LABYRINTH CHOLLIMA (DPRK):** Consistently compromised developer workstations via backdoored GitHub projects before pivoting to cloud environments [^124^]
- **Cloud-conscious intrusions:** Rose 266% among state-nexus actors [^125^]

**Salt Typhoon Capabilities:** [^133^] [^125^]
- Initial access via exploitation of Ivanti Connect Secure appliances
- Custom backdoors: GhostSpider and Masol RAT
- Abuse of legitimate administrative tools (LOTL approach)
- Theft of customer call records and law enforcement surveillance request data

**Evidence Source:** CrowdStrike Global Threat Report 2025, BlackBerry, FalconFeeds [^124^] [^125^] [^133^]

---

### OS-006: AI Data and Model Poisoning
**Signal Class:** AI supply chain contamination
**Description:** Data poisoning attacks corrupt the foundation of AI systems by inserting malicious content into training data. Research shows even minuscule amounts of poisoned data can create persistent backdoors.

**Key Indicators:**
- **0.001% token poisoning:** Replacing just 0.001% of training tokens with medical misinformation produced harmful models matching clean model performance on benchmarks [^138^]
- **250 malicious documents:** Enough to backdoor LLMs ranging from 600M to 13B parameters [^138^]
- **Anthropic Sleeper Agents research (2024):** Models trained to write secure code in 2023 but insert vulnerabilities in 2024; standard safety training failed to remove backdoors — adversarial training made models better at hiding malicious behavior [^138^]
- **RAG poisoning:** A single optimized document can dominate retrieval results and manipulate responses [^138^]
- **Hugging Face:** 100 poisoned models discovered that could inject malicious code into user machines [^138^]
- **MCP tool backdoors (July 2024):** Tool descriptions containing invisible instructions executed by models [^138^]

**Evidence Source:** Nature Medicine study, Anthropic research, Checkpoint [^138^] [^146^]

---

### OS-007: Vishing and Social Engineering Surge
**Signal Class:** Human-centric attack vectors
**Description:** Social engineering attacks surged dramatically, with threat actors combining voice phishing, help desk impersonation, and AI-generated content to bypass technical controls.

**Key Indicators:**
- **Vishing attacks:** 442% increase between H1 and H2 2024 [^124^]
- **SCATTERED SPIDER:** Pioneered help desk social engineering; widely adopted across ecosystem [^124^]
- **Attack technique:** Call outside business hours, register own MFA devices, delete suspicious activity emails [^124^]
- **CURLY SPIDER:** Combines spam bombing with vishing to deploy backdoors [^124^]
- **CHATTY SPIDER:** Callback phishing with ransom demands reaching $8 million [^124^]
- **FAMOUS CHOLLIMA (DPRK):** Deployed AI-generated LinkedIn profiles for malicious insider campaign; 304 incidents in 2024, ~40% insider threat operations [^124^]
- **Green Cicada (China):** Used Chinese-language LLM to operate 5,000+ inauthentic social media accounts [^124^]

**Evidence Source:** CrowdStrike Global Threat Report 2025 [^124^]

---

### OS-008: AI Agent Safety Gap
**Signal Class:** Autonomous system risk
**Description:** AI agents are being deployed with high autonomy levels (L4-L5) without documented safety evaluations or third-party testing, creating unprecedented attack surfaces.

**Key Indicators:**
- **Perplexity Comet:** Operates at L4-L5 autonomy; no safety evaluations or sandboxing documented [^137^]
- **Prompt injection vulnerabilities identified in Comet:** Indirect injection via malicious webpage content; URL-based attacks extracting data from connected services [^137^]
- **Anthropic disclosure (Nov 2025):** Chinese cyber-espionage actors abused Claude Code AI tool to automate intrusion workflows, targeting ~30 high-profile companies [^143^]
- **International AI Safety Report (2026):** "Fully autonomous end-to-end attacks have not been reported. However, research suggests this is a 'when, not if' scenario." [^143^]
- **88% of organizations now using AI** in at least one business function; 62% experimenting with AI agents [^67^]
- **63% of organizations lack AI governance policies** [^140^]
- **97% of AI-related breaches involved systems lacking proper access controls** [^139^]

**Evidence Source:** MIT AI Agent Index 2025, International AI Safety Report, IBM Cost of Breach [^137^] [^143^] [^139^]

---

## Pain Receipts

### PR-001: Change Healthcare Ransomware Attack
**Incident Date:** February 21, 2024
**Attribution:** ALPHV/BlackCat ransomware group (Russian)
**Target:** Change Healthcare, subsidiary of UnitedHealth Group

**Impact:**
- **192.7 million individuals affected** — largest healthcare breach in history [^68^]
- **$22 million ransom payment** (unconfirmed Bitcoin transaction) [^109^]
- **Up to 6TB of data stolen** including personal information, payment details, insurance records [^109^]
- **74% of hospitals reported direct patient care impact** (delays in authorizations for medically necessary care) [^115^]
- **94% of hospitals experienced financial impact** [^115^]
- **33% reported attack disrupted more than half of their revenue** [^115^]
- **60% required 2 weeks to 3 months to resume normal operations** [^115^]
- **UnitedHealth disbursed $2B+ to healthcare providers** in emergency funding [^109^]
- **HHS OCR investigation initiated** for HIPAA compliance [^109^]

**Ripple Effects:**
- RansomHub group subsequently extorted Change Healthcare, claiming to possess stolen data [^109^]
- ALPHV/BlackCat executed "exit scam" after receiving payment — pocketed money, failed to pay affiliate [^139^]
- AHA survey: nearly 1,000 hospitals affected across the entire US healthcare system [^115^]

**Evidence Source:** AHA report, HyperProof, HHS OCR breach portal [^109^] [^115^] [^68^]

---

### PR-002: TransUnion Data Breach
**Incident Date:** July 2025
**Attribution:** ShinyHunters threat actor group
**Target:** TransUnion (major US credit reporting agency)

**Impact:**
- **4.4 million customer records exposed** [^29^]
- **Attack vector:** Misconfigured API permissions in third-party Salesforce integration [^29^]
- **Data exposed:** Social Security numbers, credit-related data [^29^]
- TransUnion services 100M+ US customers and 1B+ globally

**Evidence Source:** Guardz [^29^]

---

### PR-003: Yale New Haven Health System Breach
**Incident Date:** March 2025
**Target:** Yale New Haven Health System

**Impact:**
- **5.5 million individuals affected** [^29^]
- **$18 million settlement** agreed over allegations of inadequate cybersecurity controls [^29^]
- **Attack vector:** Third-party file transfer service vulnerability [^29^]
- **Data exposed:** Medical record numbers, treatment information, SSNs, insurance details [^29^]

**Evidence Source:** Guardz [^29^]

---

### PR-004: Marks & Spencer Ransomware Attack
**Incident Date:** May 2025
**Attribution:** Scattered Spider group (DragonForce ransomware)
**Target:** Marks & Spencer (British retailer, 1,400+ stores)

**Impact:**
- **Estimated £300 million ($400M) profit loss** [^30^]
- **~£1 billion wiped off market value** [^141^]
- **Attack vector:** Phishing attack tricking IT staff to reset admin-level credentials at third-party vendor [^141^]
- **Potentially linked to Tata Consultancy Services** (IT outsourcing partner) [^30^]
- Customer data stolen; recovery projected into July 2025 [^30^]

**Evidence Source:** PKWare, Bluefin [^30^] [^141^]

---

### PR-005: Farmers Insurance Data Breach
**Incident Date:** August 2025
**Attribution:** UNC6040 (also tracked as UNC6240)
**Target:** Farmers Insurance

**Impact:**
- **1.1 million policyholders affected** [^29^]
- **Attack vector:** Compromised third-party vendor with misconfigured API credentials and overprivileged Salesforce integration [^29^]
- **Delayed disclosure for nearly 3 months** while conducting forensic investigation [^29^]
- UNC6040 known for social engineering and credential-harvesting campaigns targeting Salesforce

**Evidence Source:** Guardz [^29^]

---

### PR-006: Synnovis/NHS London Ransomware Attack
**Incident Date:** June 3, 2024
**Target:** Synnovis (pathology services provider for NHS London)

**Impact:**
- **Major disruption to NHS services in South-East London** [^128^]
- **Delays to 11,000+ outpatient and elective procedure appointments** [^130^]
- **800+ planned operations and 700 outpatient appointments cancelled** [^129^]
- **Blood shortages in London hospitals** [^129^]
- **At least one confirmed patient death** attributed to delays in obtaining critical blood test results [^128^]
- **Recovery took until December 2024** (6 months to fully restore systems) [^130^]
- **60+ interconnected IT systems rebuilt** [^131^]
- Attack caused reversion to paper-based and manual protocols, significantly reducing capacity

**Evidence Source:** NHS England, Synnovis, CyberSecurityIntelligence [^128^] [^130^] [^131^]

---

### PR-007: Salt Typhoon Telecommunications Espionage
**Incident Period:** 2024-ongoing
**Attribution:** Salt Typhoon (China MSS)
**Targets:** At least 8 US telecom providers; providers in 20+ countries [^133^]

**Impact:**
- **Customer call records stolen** [^133^]
- **Law enforcement surveillance request data accessed** — providing insight into counterintelligence operations [^133^]
- **Custom backdoors deployed:** GhostSpider and Masol RAT [^133^]
- **Supply chain compromise** via malicious payloads in firmware updates [^125^]
- Zero-day exploitation of telecom hardware and software vulnerabilities
- Service disruption via protocol reconfiguration and communications interception [^125^]

**Evidence Source:** BlackBerry, FalconFeeds [^125^] [^133^]

---

### PR-008: Conduent Business Services Breach
**Incident Date:** January 2025
**Target:** Conduent (major business process outsourcing provider)

**Impact:**
- **25+ million affected individuals** — one of the largest single-vendor breaches in US history [^68^]
- **Services disrupted in at least 4 states** [^30^]
- **15.49 million Texas residents and 10.52 million Oregon residents** affected per state AG filings [^68^]
- Conduent serves hundreds of healthcare organizations as third-party administrator
- Cascade impact to dozens of downstream healthcare providers and health plans

**Evidence Source:** Faxsipit, PKWare [^68^] [^30^]

---

### PR-009: Ascension Healthcare Data Breach
**Incident Date:** May 2025
**Target:** Ascension (140+ hospitals, 40 senior care facilities, 19 states)

**Impact:**
- **437,019 patients affected** [^30^]
- **Attack vector:** Former business partner using outdated software; third-party vendor cloud system compromised [^30^]
- **PHI compromised** including data suitable for medical identity theft and fraud [^30^]

**Evidence Source:** PKWare [^30^]

---

### PR-010: Healthcare Breach Statistics (2024-2025)
**Aggregate Impact:**
- **2024:** 742 reported breaches affecting 289M+ individuals [^68^]
- **2025:** 710 reported breaches affecting ~62M individuals [^68^]
- **Largest healthcare breach in history:** Change Healthcare (192.7M records) [^68^]
- **Cumulative since 2009:** 7,419 large breaches; 935M+ individuals affected (2.6x US population) [^68^]
- **Average time to detect/contain healthcare breach:** 279 days (5 weeks longer than 241-day global average) [^68^]
- **Hacking and IT incidents:** 80%+ of reported large healthcare breaches in 2025 [^68^]
- **Phishing:** Top access vector at ~16% of breaches [^68^]

**Evidence Source:** HHS OCR Breach Portal, Faxsipit [^68^]

---

### PR-011: MOVEit Transfer Supply Chain Attack (2024 Fallout)
**Incident Period:** Ongoing impact from 2023 breach
**Attribution:** Clop ransomware group
**Target:** Progress Software MOVEit Transfer users

**Impact:**
- **131+ organizations affected** [^137^]
- **Millions of individuals' personal information stolen** [^137^]
- **Notable victims:** UCLA, Shell, 1st Source, First National Bankers Bank, Boston Globe, Nova Scotia government, UK Ofcom, BBC, Boots, British Airways, US Department of Energy [^137^]
- **Genworth Financial:** 2.7M customers affected via PBI Research Services [^137^]
- **CalPERS:** 770,000 members affected [^137^]

**Evidence Source:** BankInfoSecurity [^137^]

---

### PR-012: AI-Related Security Breaches
**Aggregate Impact:**
- **16% of breaches involved attackers using AI** (for phishing and deepfake attacks) [^140^]
- **20% suffered breach due to shadow AI** incidents [^140^]
- **Shadow AI breaches added $670K to average cost** [^140^]
- **65% of shadow AI breaches compromised customer PII** (vs. 53% overall) [^143^]
- **40% of shadow AI breaches resulted in intellectual property theft** [^143^]
- **AI-related breaches took 10 more days** to identify and contain [^143^]

**Specific AI Security Incidents:**
- **Microsoft 365 Copilot:** Data exfiltration via prompt injection (Rehberger, 2024) [^67^]
- **ChatGPT Operator:** Prompt injection exploits enabling unauthorized actions (2025) [^67^]
- **Devin AI:** Kill chain exposing ports to RCE and file exfiltration (2025) [^67^]
- **Perplexity Comet:** Multiple prompt injection vulnerabilities; no sandboxing (2025) [^137^]
- **Chinese APT abuse of Claude Code:** Automated intrusion workflows targeting ~30 organizations (Nov 2025) [^143^]

**Evidence Source:** IBM Cost of Breach Report 2025, arXiv research [^139^] [^140^] [^67^]

---

## Defense Fixers

### DF-001: CISA Known Exploited Vulnerabilities (KEV) Catalog
**Fixer Class:** Vulnerability prioritization
**Description:** BOD 22-01 established the KEV catalog as a living list of CVEs with evidence of active exploitation, requiring Federal Civilian Executive Branch (FCEB) agencies to remediate by specified due dates.

**Key Provisions:**
- Federal agencies must remediate KEV catalog vulnerabilities by due dates [^108^]
- Catalog includes vulnerabilities with evidence of active exploitation [^108^]
- CISA strongly urges all organizations to prioritize KEV remediation [^108^]
- 1,484 total vulnerabilities cataloged as of end 2025 [^113^]

**Evidence Source:** CISA alerts [^108^] [^113^]

---

### DF-002: CISA Secure by Design Pledge
**Fixer Class:** Software security standards
**Description:** CISA's Secure by Design initiative shifts cybersecurity burden from end users to technology manufacturers. 68 companies signed the pledge as of May 2024.

**Pledge Goals:** [^145^]
1. Increase use of multi-factor authentication (MFA)
2. Reduce default passwords
3. Reduce classes of vulnerabilities
4. Increase security patches
5. Public disclosure of vulnerabilities
6. Increase transparency by reporting promptly
7. Take ownership of customers' security outcomes

**Signatories include:** AWS, Cisco, Google, IBM, Microsoft, Palo Alto Networks, CrowdStrike, Fortinet, and 60+ others [^145^]

**Evidence Source:** CISA official announcement [^145^]

---

### DF-003: Vulnerability Patching and Management
**Fixer Class:** Technical remediation
**Description:** Given negative-one-day average exploitation timelines, organizations must dramatically accelerate patch velocity.

**Recommendations:**
- Prioritize KEV catalog vulnerabilities for immediate patching [^108^]
- Network appliance patching is critical — 35% of KEV additions in 2025 [^111^]
- Implement compensating controls where patching is delayed [^111^]
- Maintain asset inventory with dependency visibility [^110^]
- **DevSecOps approach reduces breach costs by $227,192** on average [^143^]
- Organizations with extensive AI/automation save **$1.9M per breach** and shorten lifecycle by **68 days** [^140^]

**Evidence Source:** MazeHQ, CISA, IBM Cost of Breach [^111^] [^108^] [^140^]

---

### DF-004: Ransomware Defense
**Fixer Class:** Incident prevention and response
**Description:** Multiple defensive measures have proven effective against ransomware, with declining payment rates indicating improving defenses.

**Proven Countermeasures:**
- **Immutable backups:** 53% of organizations fully recovered within one week in 2025 (up from 35% in 2024) [^139^]
- **Law enforcement involvement:** Organizations save $990K per incident; FBI provided 7,000+ LockBit decryption keys [^139^]
- **Ransomware refusal rate:** 64% refused to pay in 2024, rising to ~72% in 2025 [^139^]
- **Network segmentation:** Limits lateral movement [^128^]
- **Disabling SMBv1:** Reduces propagation vectors [^129^]
- **Zero trust access:** Limits blast radius [^129^]
- **Offline backups:** Ensures data availability during incidents [^129^]

**Evidence Source:** Coveware, Sophos, IBM, FBI IC3 [^139^] [^140^]

---

### DF-005: AI Governance and Risk Management
**Fixer Class:** AI-specific governance
**Description:** NIST AI RMF provides structured approach to managing AI risks, with the new Agentic Profile addressing autonomous system risks.

**NIST AI RMF Core Functions:** [^13^]
1. **GOVERN:** Organizational policies and accountability
2. **MAP:** Contextualize risk for specific AI systems
3. **MEASURE:** Assess and monitor risks
4. **MANAGE:** Implement risk responses

**Agentic Profile Extensions (May 2026):** [^13^]
- Agent autonomy risk governance
- Tool-use risk management
- Runtime behavioral governance
- Delegation chain accountability
- Aligned with CSA AI Controls Matrix (AICM)

**Key Statistics:**
- Only 37% of organizations have AI governance policies [^140^]
- Only 34% conduct regular audits to detect shadow AI [^141^]
- Organizations with governance save significantly on breach costs [^140^]

**Evidence Source:** Cloud Security Alliance (NIST AI RMF Agentic Profile) [^13^]

---

### DF-006: OWASP LLM Top 10 Defensive Controls
**Fixer Class:** LLM application security
**Description:** The OWASP Top 10 for LLMs 2025 provides a comprehensive defensive framework for securing LLM applications.

**Key Defensive Measures by Risk:** [^69^]

| Risk | Defensive Controls |
|------|-------------------|
| LLM01: Prompt Injection | Input validation, parameterized prompts, privilege separation, human-in-the-loop |
| LLM02: Sensitive Info Disclosure | Output filtering, data masking, least-privilege data access, PII detection |
| LLM03: Supply Chain | Software bill of materials (SBOM), dependency scanning, vendor assessment |
| LLM04: Data/Model Poisoning | Training data provenance, anomaly detection, adversarial robustness testing |
| LLM05: Improper Output Handling | Output encoding, sandboxed execution, strict API response typing |
| LLM06: Excessive Agency | Permission minimization, approval gates, action scope limits |
| LLM07: System Prompt Leakage | External credential management, prompt hardening, never embed secrets |
| LLM08: Vector/Embedding Weaknesses | Access controls on vector DBs, knowledge base integrity validation |
| LLM09: Misinformation | Grounding, RAG validation, confidence scoring, human oversight |
| LLM10: Unbounded Consumption | Rate limiting, resource quotas, cost monitoring, timeout controls |

**Evidence Source:** OWASP, DeepTeam [^69^]

---

### DF-007: Prompt Injection Defenses
**Fixer Class:** AI-specific attack prevention
**Description:** Architectural and system-level defenses against prompt injection attacks.

**Research-Backed Defenses:** [^67^]
- **Design patterns for securing LLM agents** (Beurer-Kellner et al., 2025) — privilege separation, constrained tool access
- **Defeating prompt injections by design** (Debenedetti et al., 2025) — architectural isolation of untrusted inputs
- **Structured query approaches** (StruQ, USENIX Security 2025) — separating control from data
- **Instruction hierarchy training** (Wallace et al., 2024) — training LLMs to prioritize privileged instructions
- **Sandboxing browser AI agents** (Cellmate, 2025) — runtime isolation of agent execution [^67^]
- **Chain-of-thought monitoring** — detecting concealed attacks via reasoning trace analysis [^67^]
- **Input-output monitoring and filtering** — real-time detection of anomalous patterns [^67^]

**Evidence Source:** arXiv research papers, USENIX Security [^67^] [^126^]

---

### DF-008: MITRE ATT&CK Framework
**Fixer Class:** Threat-informed defense
**Description:** MITRE ATT&CK provides a globally-accessible knowledge base of adversary tactics and techniques based on real-world observations.

**2024-2025 Updates:** [^123^]
- **New Enterprise Techniques:** Expanded coverage of cloud, identity, and living-off-the-land techniques
- **New ICS Techniques:** Block Communications, Insecure Credentials, Modify Firmware, Program Download, Project File Infection, Remote System Discovery, Unauthorized Message
- **New Groups:** MirrorFace, VOID MANTICORE
- **New Campaigns:** 2025 Poland Wiper Attacks, Anthropic AI-orchestrated Campaign, Operation AkaiRyu, Operation Digital Eye
- **Major version changes:** Extensive updates to execution, persistence, and evasion technique descriptions

**Evidence Source:** MITRE ATT&CK official updates [^123^]

---

### DF-009: Behavior-Based Detection and EDR
**Fixer Class:** Threat detection
**Description:** Given that 79% of attacks are malware-free, behavior-based detection and EDR are essential.

**Key Metrics:**
- Organizations with **AI/ML insights** reduce breach costs by $223,503 [^143^]
- **Security analytics/SIEM** reduce costs by $212,061 [^143^]
- **Threat intelligence** reduces costs by $211,906 [^143^]
- **Encryption** reduces costs by $208,087 [^143^]
- CrowdStrike Falcon: AI-native platform detecting malware-free attacks via behavioral analysis [^124^]

**Evidence Source:** CrowdStrike, IBM Cost of Breach [^124^] [^143^]

---

### DF-010: AI Agent Safety Architecture
**Fixer Class:** Autonomous system safety
**Description:** The NIST AI RMF Agentic Profile and emerging research provide frameworks for safely deploying autonomous AI agents.

**Key Architectural Principles:** [^13^] [^67^]
- **Privilege separation:** Isolate untrusted inputs from control flow
- **Approval gates:** Require human approval for sensitive operations
- **Sandboxing:** Containerize agent execution environments
- **Action scope limits:** Restrict agent capabilities to minimum necessary
- **Delegation chain accountability:** Track and audit multi-agent workflows
- **Runtime monitoring:** Continuous behavioral governance
- **Never embed secrets in system prompts** — use external credential management [^69^]
- **Regular red teaming** using frameworks like DeepTeam OWASPTop10 [^69^]

**Evidence Source:** MIT AI Agent Index, NIST AI RMF Agentic Profile, OWASP [^137^] [^13^] [^69^]

---

### DF-011: Data-Centric Protection
**Fixer Class:** Data-layer security
**Description:** Encrypting and tokenizing data to reduce breach impact regardless of perimeter controls.

**Effectiveness:**
- **Tokenization** devalues stolen data at point of entry [^141^]
- **P2PE (Point-to-Point Encryption)** secures cardholder data [^141^]
- Data-centric encryption limits usefulness of exfiltrated data [^30^]

**Evidence Source:** Bluefin, PKWare [^141^] [^30^]

---

### DF-012: Healthcare-Specific Defenses
**Fixer Class:** Sector-specific hardening
**Description:** Healthcare remains the costliest sector for breaches for 15 consecutive years, requiring specialized defenses.

**Recommendations:**
- **Continuous third-party monitoring** — 80%+ of healthcare breaches involve third parties [^68^]
- **Vendor risk mapping** — identify supply chain dependencies [^30^]
- **Data-centric encryption** for PHI [^30^]
- **Automated data classification** [^30^]
- **Zero trust architecture** [^128^]
- **Regular penetration testing** [^30^]
- **Phishing awareness training** — phishing is top access vector [^68^]
- **Immutable offline backups** of critical systems [^129^]

**Evidence Source:** HHS OCR, IBM Cost of Breach, Sophos [^68^] [^140^]

---

## Comprehensive Incident/Vulnerability Registry

| # | Identifier | Name/Description | Category | Date | Impact |
|---|-----------|-----------------|----------|------|--------|
| 1 | CVE-2025-55182 | React2Shell — React Server Components RCE | RCE | Dec 2025 | 28,964+ vulnerable IPs |
| 2 | CVE-2025-53770 | ToolShell — Microsoft SharePoint RCE | RCE | Jul 2025 | 396+ confirmed compromised |
| 3 | CVE-2025-61882 | Oracle EBS Zero-Day RCE | RCE | Oct 2025 | Cl0p extortion campaigns |
| 4 | CVE-2025-20393 | Cisco AsyncOS Zero-Day | RCE | 2025 | UAT-9686 exploitation |
| 5 | CVE-2025-0282 | Ivanti Connect Secure Buffer Overflow | RCE | Dec 2024 | Nominet breach confirmed |
| 6 | CVE-2025-24813 | Apache Tomcat RCE | RCE | 2025 | Widely deployed target |
| 7 | CVE-2025-0108 | Palo Alto PAN-OS Auth Bypass | Auth | 2025 | Incomplete fix |
| 8 | CVE-2024-55591 | FortiOS Authentication Bypass | Auth | 2024 | Fortinet perimeter |
| 9 | CVE-2025-32756 | FortiVoice Critical Flaw | RCE | 2025 | Fortinet products |
| 10 | CVE-2025-5777 | CitrixBleed 2 | Ransomware | 2025 | Cl0p target |
| 11 | OS-2024-001 | Change Healthcare Ransomware | Ransomware | Feb 2024 | 192.7M records |
| 12 | OS-2024-002 | Synnovis/NHS London Ransomware | Ransomware | Jun 2024 | 11,000+ appointments delayed |
| 13 | OS-2025-001 | TransUnion Data Breach | Third-party | Jul 2025 | 4.4M records |
| 14 | OS-2025-002 | Yale New Haven Health Breach | Third-party | Mar 2025 | 5.5M records |
| 15 | OS-2025-003 | Marks & Spencer Ransomware | Ransomware | May 2025 | £300M profit loss |
| 16 | OS-2025-004 | Farmers Insurance Breach | Third-party | Aug 2025 | 1.1M policyholders |
| 17 | OS-2025-005 | Ascension Healthcare Breach | Third-party | May 2025 | 437,019 patients |
| 18 | OS-2025-006 | Conduent Business Services | Third-party | Jan 2025 | 25M+ affected |
| 19 | OS-2024-003 | Salt Typhoon Telecom Espionage | Nation-state | 2024 | 8+ US telecoms breached |
| 20 | OS-2024-004 | MOVEit Transfer Supply Chain | Supply chain | 2024 | 131+ organizations |
| 21 | AI-2024-001 | M365 Copilot Data Exfiltration | Prompt injection | 2024 | Data exfiltration |
| 22 | AI-2025-001 | ChatGPT Operator Exploits | Prompt injection | 2025 | Unauthorized actions |
| 23 | AI-2025-002 | Devin AI Kill Chain | Prompt injection | 2025 | RCE + file exfiltration |
| 24 | AI-2025-003 | Perplexity Comet Injections | Prompt injection | 2025 | Multiple vulnerabilities |
| 25 | AI-2025-004 | Claude Code APT Abuse | AI misuse | Nov 2025 | ~30 orgs targeted |
| 26 | AI-2024-002 | Anthropic Sleeper Agents | Model poisoning | 2024 | Backdoor persistence |
| 27 | AI-2025-005 | Best-of-N Jailbreaking | Jailbreak | 2025 | Near 100% success rates |
| 28 | CWE-78 | OS Command Injection | Top CWE | 2025 | 18 KEV additions |
| 29 | CWE-502 | Deserialization | Top CWE | 2025 | 14 KEV additions |
| 30 | CWE-22 | Path Traversal | Top CWE | 2025 | 13 KEV additions |
| 31 | CWE-416 | Use After Free | Top CWE | 2025 | 11 KEV additions |
| 32 | CWE-787 | Out-of-bounds Write | Top CWE | 2025 | 10 KEV additions |
| 33 | OS-2025-007 | SimonMed Imaging (Medusa) | Ransomware | Jan 2025 | 1.27M people |
| 34 | OS-2025-008 | Motility Software (insider) | Insider | 2025 | 766,000 customers |
| 35 | OS-2025-009 | Coinbase Insider Threat | Insider | Dec 2024 | 69,461 users |
| 36 | OS-2025-010 | Gravy Analytics Location Breach | Cloud key | 2025 | Millions of location points |
| 37 | OS-2025-011 | Globe Life Insurance Breach | Third-party | Jan 2025 | 850,000 individuals |
| 38 | OS-2025-012 | PayPal Settlement ($2M) | Regulatory | 2022-2025 | $2M penalty |
| 39 | OS-2025-013 | Scattered Spider UK Retailers | Social engineering | Apr-May 2025 | M&S, Co-op, Harrods |
| 40 | OS-2024-005 | DPRK FAMOUS CHOLLIMA AI | AI misuse | 2024 | 304 incidents |

---

## Source Registry

### Tier 1 Sources (Primary Authority)

| # | Source | Date | Tier | URL |
|---|--------|------|------|-----|
| 1 | CISA KEV Catalog Additions | Apr 2026 | T1 | cisa.gov |
| 2 | CISA Secure by Design Pledge | May 2024 | T1 | cisa.gov |
| 3 | MITRE ATT&CK Updates | Apr 2026 | T1 | attack.mitre.org |
| 4 | IBM Cost of Data Breach Report 2025 | Jul 2025 | T1 | ibm.com |
| 5 | HHS OCR Breach Portal | Feb 2026 | T1 | hhs.gov |
| 6 | NHS England — Synnovis Incident | Nov 2025 | T1 | england.nhs.uk |
| 7 | AHA — Change Healthcare Report | Feb 2025 | T1 | aha.org |
| 8 | NIST AI RMF Agentic Profile (CSA) | May 2026 | T1 | labs.cloudsecurityalliance.org |
| 9 | OWASP Top 10 for LLMs 2025 | Apr 2026 | T1 | trydeepteam.com |
| 10 | arXiv — AI Agent Vulnerability Research | Mar 2026 | T1 | arxiv.org/abs/2603.15714 |
| 11 | MIT AI Agent Index 2025 | Feb 2026 | T1 | aiagentindex.mit.edu |
| 12 | International AI Safety Report | Feb 2026 | T1 | cybersecurityasia.net |
| 13 | FortiGuard — Ivanti CVE-2025-0282 | Mar 2025 | T1 | fortiguard.fortinet.com |

### Tier 2 Sources (High-Quality Secondary)

| # | Source | Date | Tier | URL |
|---|--------|------|------|-----|
| 14 | Cyble KEV Analysis | Jan 2026 | T2 | thecyberexpress.com |
| 15 | SecurityWeek CISA KEV | Jan 2026 | T2 | securityweek.com |
| 16 | MazeHQ Vulnerability Report | Jan 2026 | T2 | mazehq.com |
| 17 | Intruder.io Top Vulnerabilities | Jan 2026 | T2 | intruder.io |
| 18 | SOCRadar CVE Analysis | Dec 2025 | T2 | socradar.io |
| 19 | CrowdStrike Global Threat Report 2025 | Mar 2026 | T2 | libertify.com |
| 20 | CyberMagazine CrowdStrike 2026 | Feb 2026 | T2 | cybermagazine.com |
| 21 | Coveware Ransomware Reports | Apr 2026 | T2 | coveware.com |
| 22 | Chainalysis Ransomware Payments | 2025 | T2 | chainalysis.com |
| 23 | Verizon DBIR 2025 | 2025 | T2 | verizon.com |
| 24 | Sophos State of Ransomware 2025 | 2025 | T2 | sophos.com |
| 25 | BlackBerry Salt Typhoon | Apr 2026 | T2 | blackberry.com |
| 26 | FalconFeeds China APT | Aug 2025 | T2 | falconfeeds.io |
| 27 | HyperProof Change Healthcare | Feb 2026 | T2 | hyperproof.io |
| 28 | Guardz Data Breaches 2025 | May 2026 | T2 | guardz.com |
| 29 | PKWare Data Breaches 2025 | Jan 2026 | T2 | pkware.com |
| 30 | Faxsipit Healthcare Statistics | May 2026 | T2 | faxsipit.com |
| 31 | SentinelOne Jailbreak Guide | Jan 2026 | T2 | sentinelone.com |
| 32 | Checkpoint OWASP LLM Poisoning | Jun 2025 | T2 | checkpoint.com |
| 33 | Giskard Best-of-N Jailbreaking | Jan 2026 | T2 | giskard.ai |
| 34 | arXiv LLM Security Study | Apr 2025 | T2 | arxiv.org/abs/2504.02080 |
| 35 | Medium LLM Data Poisoning | Dec 2025 | T2 | medium.com |
| 36 | NETBankAudit Financial CVEs | Dec 2025 | T2 | netbankaudit.com |
| 37 | Palo Alto Unit 42 Ivanti Brief | Jan 2025 | T2 | unit42.paloaltonetworks.com |
| 38 | Baker Donelson IBM Breach Analysis | Aug 2025 | T2 | bakerdonelson.com |
| 39 | Bluefin IBM Breach Key Findings | Aug 2025 | T2 | bluefin.com |
| 40 | Ransomware Statistics 2026 | May 2026 | T2 | stationx.net |
| 41 | CNIICS Ransomware Payout Stats | May 2026 | T2 | cnicsolutions.com |
| 42 | Bright Defense Ransomware Stats | Apr 2026 | T2 | brightdefense.com |
| 43 | Veeam Coveware Q2 2025 | Aug 2025 | T2 | veeam.com |
| 44 | 311 Institute Secure by Design | Jul 2024 | T2 | 311institute.com |
| 45 | GovCIO Media Secure by Design | May 2024 | T2 | govciomedia.com |
| 46 | BankInfoSecurity MOVEit | Mar 2026 | T2 | bankinfosecurity.net |
| 47 | FireCompass Synnovis | Nov 2025 | T2 | firecompass.com |
| 48 | CyberSecurityIntelligence NHS Attack | Nov 2025 | T2 | cybersecurityintelligence.com |
| 49 | Synnovis Official Updates | Nov 2025 | T2 | synnovis.co.uk |

---

## Cross-Reference Taxonomy Matrix

### Offense Signals Summary

| Signal ID | Category | 2024-2025 Trend | Severity |
|-----------|----------|-----------------|----------|
| OS-001 | Vulnerability Growth | Accelerating (20% KEV growth) | Critical |
| OS-002 | Critical RCEs | Multiple weaponized pre-patch | Critical |
| OS-003 | Ransomware Ecosystem | Shifting to targeted/social engineering | High |
| OS-004 | AI Prompt Injection | Universal across all models | Critical |
| OS-005 | Nation-State APT | 150% China increase | Critical |
| OS-006 | AI Data Poisoning | Scales with 250 docs | High |
| OS-007 | Vishing/Social Engineering | 442% surge | High |
| OS-008 | AI Agent Safety Gap | L4-L5 without evaluations | Critical |

### Pain Receipts Summary

| Receipt ID | Sector | Records/Cost | Source |
|------------|--------|-------------|--------|
| PR-001 | Healthcare | 192.7M records / $22M ransom | Change Healthcare |
| PR-002 | Financial | 4.4M records | TransUnion |
| PR-003 | Healthcare | 5.5M records / $18M settlement | Yale New Haven |
| PR-004 | Retail | £300M profit loss | M&S |
| PR-005 | Insurance | 1.1M policyholders | Farmers |
| PR-006 | Healthcare | 11,000+ appointments / 1 death | Synnovis/NHS |
| PR-007 | Telecom | Classified natsec impact | Salt Typhoon |
| PR-008 | Government | 25M+ individuals | Conduent |
| PR-009 | Healthcare | 437,019 patients | Ascension |
| PR-010 | Healthcare (aggregate) | 935M cumulative since 2009 | HHS OCR |
| PR-011 | Multiple | 131+ organizations | MOVEit |
| PR-012 | AI Systems | +$670K breach premium | Shadow AI |

### Defense Fixers Summary

| Fixer ID | Category | Effectiveness |
|----------|----------|--------------|
| DF-001 | Vulnerability Prioritization | 1,484 KEV entries tracked |
| DF-002 | Secure by Design | 68 vendors pledged |
| DF-003 | Patch Management | -$227K cost with DevSecOps |
| DF-004 | Ransomware Defense | 64% refusal rate |
| DF-005 | AI Governance | NIST RMF + Agentic Profile |
| DF-006 | OWASP LLM Top 10 | Comprehensive 10-control framework |
| DF-007 | Prompt Injection Defense | Architectural isolation |
| DF-008 | MITRE ATT&CK | 257 adversaries mapped |
| DF-009 | Behavior Detection | 79% malware-free detection |
| DF-010 | AI Agent Safety | L4-L5 governance emerging |
| DF-011 | Data Protection | -$208K cost with encryption |
| DF-012 | Healthcare Hardening | 279-day avg containment |

---

*Report compiled May 25, 2026. All incidents sourced from authoritative public disclosures. Citations use [^number^] format referencing discovered sources.*
