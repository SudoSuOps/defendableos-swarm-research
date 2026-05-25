# 09 STREETCHAT SIGNAL INGESTION POLICY
## DefendableOS Community-Signal Governance Framework

**Document ID:** DEF-OS-POL-009  
**Version:** 1.0.0  
**Effective Date:** 2025-07-01  
**Tier:** Tier 3 - Discovery Signal (Default)  
**Owner:** Data Governance & Trust Committee  
**Review Authority:** Tribunal Classification Board  
**Classification:** Enforcement Document — Violations Subject to Escalation

---

## 1. PURPOSE AND SCOPE

### 1.1 Purpose

This policy governs the ingestion, extraction, classification, storage, and promotion of signals originating from StreetChat — the DefendableOS community-signal layer that captures real-world expressions of pain, friction, fear, frustration, repair attempts, scam reports, and unresolved disputes. StreetChat is the system's ears in the field. It is not the system's mouth.

This policy exists to:

- **Protect individuals** whose language, experiences, or identifiers appear in community signals
- **Prevent overclaim** — the dangerous practice of treating Tier 3 discovery signals as Tier 1 or Tier 2 facts
- **Enable safe extraction** of valuable patterns from messy, emotional, high-friction language
- **Define enforceable boundaries** around what may be stored, how it may be used, and how it may graduate to higher trust tiers
- **Ensure compliance** with applicable privacy regulations (GDPR, CCPA, state biometric laws, and emerging AI governance frameworks)

### 1.2 Scope

This policy applies to:

| Component | Coverage |
|-----------|----------|
| **StreetChat** | All raw community inputs, including text, transcripts, summaries, and metadata |
| **StreetLedger** | Storage and provenance records for community signals |
| **SwarmCurator** | Grading, classifying, and verifying community signals |
| **SwarmJelly** | Messy/ambiguous training material derived from community signals |
| **Tribunal** | Classification decisions (Honey/Jelly/Propolis) applied to signals |
| **All operators** | Humans and automated agents that touch, move, or transform community signal data |

### 1.3 Policy Hierarchy

This policy sits at the intersection of:
- **DefendableOS Trust Tier Policy** (defines tiers 1-4)
- **DefendableOS PII & Data Minimization Policy**
- **DefendableOS AI Safety & Overclaim Prevention Policy**

In case of conflict, the Trust Tier Policy and PII Policy take precedence. Where those are silent, this policy governs.

---

## 2. WHY COMMUNITY LANGUAGE IS VALUABLE

### 2.1 The Signal Value Proposition

StreetChat captures language that formal complaint channels, surveys, and institutional datasets miss. The vocabulary of real-world pain does not arrive pre-sanitized. It arrives raw, emotional, and structurally honest. This makes it irreplaceable for three functions:

**A. Emerging Pain Vocabulary Detection**
- Community members invent language to describe harms that have no official label.
- Example: A cluster of posts describing "the thing where they text you a fake tracking number and then charge a re-delivery fee" signals a scam pattern before it has a BBB complaint code or a regulatory classification.
- Without StreetChat, the system has no early-warning mechanism for novel harms.

**B. Friction Topology Mapping**
- Users describe repair attempts, workarounds, and failures in natural sequences.
- Example: "I called the number on the letter, they said call this other number, that one said they couldn't help because my case starts with a Q" maps an institutional routing failure.
- This topology helps DefendableOS route future users around known failure points.

**C. Sentiment Trajectory Tracking**
- Repeated patterns of escalating language (frustration → helplessness → resignation → silence) predict systemic harm better than single complaint snapshots.
- Example: A user who posts three increasingly distressed messages about the same unresolved dispute, then disappears, may signal a harm that consumed them — not one they resolved.

### 2.2 The Value Is in the Pattern, Not the Person

Community language is valuable **only** as a source of extractable patterns. The identity, contact information, or personal circumstances of the individual who expressed the pain are **never** part of the signal's value proposition. This distinction is the foundation of everything that follows.

---

## 3. WHY IT IS NOT AUTOMATICALLY TRUSTED

### 3.1 Tier 3 Status Is Mandatory, Not Optional

**Every signal entering StreetChat is Tier 3 by default.** No exceptions. No fast-track. No "this one seems obviously true" bypass.

| Tier | Label | Definition | StreetChat Status |
|------|-------|------------|-------------------|
| **1** | Primary / Proven | Verified, corroborated, institutionally confirmed facts | StreetChat signals **never** enter as Tier 1 |
| **2** | High-Quality Secondary | Well-sourced, expert-reviewed, internally consistent signals | StreetChat signals **may** graduate here via promotion pathway |
| **3** | Discovery Signal | Raw, unverified, potentially biased community input | **Default tier for all StreetChat entries** |
| **4** | Reject / Quarantine | Harmful, false, PII-laden, or unrecoverable | StreetChat signals **may** be demoted here |

### 3.2 Tier 3 Limitations

StreetChat signals are subject to the following mandatory limitations:

1. **No unilateral promotion**: No single operator (human or automated) may promote a StreetChat signal above Tier 3.
2. **No downstream assertion**: Tier 3 signals may never be used as the sole source for any claim presented to end users.
3. **No training without review**: Tier 3 signals may not be used in any fine-tuning, training, or weight-updating process without Tribunal classification.
4. **No cross-reference without corroboration**: Tier 3 signals may not be linked to named individuals, specific cases, or institutional records until corroborated.
5. **Time-bound review**: All Tier 3 signals must be reviewed by SwarmCurator within 72 hours of ingestion.

### 3.3 Why Tier 3 Signals Are Untrustworthy

| Risk | Description | Example |
|------|-------------|---------|
| **Single-source bias** | One person's experience may be atypical, exaggerated, or fabricated | A user claims "everyone in my building was charged twice" — may be 2 people or 200 |
| **Emotional amplification** | Pain language systematically overstates frequency and severity | "They ALWAYS do this" rarely means always |
| **Selection bias** | People who post are different from people who do not post | StreetChat captures the loudest voices, not the most representative |
| **Misattribution** | Users may blame the wrong party, conflate events, or misremember sequences | A user attributes a fee to Company A when it was actually a third-party processor |
| **Scam reports that are themselves scams** | Bad actors plant false community signals to discredit competitors or create panic | A coordinated campaign of "Company X steals money" posts from sock-puppet accounts |
| **Temporal decay** | A signal may describe a problem that has since been fixed | A 6-month-old post about a billing bug may no longer apply |

---

## 4. SAFE EXTRACTION PROCESS

### 4.1 The Five-Stage Pipeline

Every raw StreetChat post must pass through the following five stages before any extracted pattern may be stored or used:

#### Stage 1: Intake & Timestamp
- Receive raw post, assign `signal_id`
- Record intake timestamp, source channel (forum, app, email, voice transcript), and ingestion operator
- **All posts enter at Tier 3. Label immediately.**

#### Stage 2: Automated Pre-Screen
- Run automated PII detection (regex + model-based)
- Flag potential identifiers: names, phone numbers, email addresses, physical addresses, account numbers, SSN/NIN equivalents, medical record numbers, geolocation data, device identifiers
- Generate `pii_flag_count` and `pii_types_detected`
- **If PII confidence > 0.85, hold for manual review. Do not proceed to Stage 3.**

#### Stage 3: Redaction (Mandatory)
- Strip all PII (see Section 5 for full list)
- Replace with standardized tokens: `[NAME]`, `[PHONE]`, `[ADDRESS]`, `[ACCOUNT]`, `[EMAIL]`, `[LOCATION]`, `[ORG]`, `[DATE_OF_BIRTH]`, `[MEDICAL_ID]`, `[DEVICE_ID]`
- Generate `redacted_version` with full audit trail of replacements
- **Two-person rule**: Two reviewers must sign off on redaction completeness before proceeding

#### Stage 4: Pattern Extraction
- Extract structural patterns from the redacted text
- Identify: harm type, affected process, emotional valence, attempted resolution, outcome category
- Generate `extracted_pattern` object (see Section 10 for schema)
- **The extracted pattern must contain zero original-language quotations longer than 5 words.**

#### Stage 5: Tribunal Classification
- Submit extracted pattern to Tribunal for Honey / Jelly / Propolis classification
- Honey: Clear, actionable, well-structured pattern → candidate for Tier 2 promotion
- Jelly: Messy, ambiguous, structurally unclear → routed to SwarmJelly for messy-material processing
- Propolis: Contaminated, unrecoverable, policy-violating → quarantined (Tier 4)

### 4.2 Pipeline Failure Handling

| Failure Mode | Response | Timeout |
|--------------|----------|---------|
| PII detection inconclusive (0.5 < confidence < 0.85) | Manual review queue | 24 hours |
| Both reviewers disagree on redaction completeness | Escalate to Data Governance Committee | 48 hours |
| Pattern extraction produces no viable pattern | Archive raw post (Tier 4 quarantine), log reason | Immediate |
| Tribunal backlog exceeds capacity | Pause new intakes, alert operations | 72 hours |
| Any stage detects potential legal issue (threat, subpoena reference, active litigation) | Immediate legal hold, notify General Counsel | Immediate |

---

## 5. REDACTION AND PII POLICY

### 5.1 Mandatory Redaction List

The following MUST be redacted from every StreetChat signal before pattern extraction. No exceptions.

| Category | Examples | Token Replacement |
|----------|----------|-------------------|
| **Personal Names** | Full names, maiden names, aliases, usernames when identifiable | `[NAME]` |
| **Contact Numbers** | Phone numbers (all formats), fax numbers, pager numbers | `[PHONE]` |
| **Email Addresses** | All email addresses, including partials that enable reconstruction | `[EMAIL]` |
| **Physical Addresses** | Street addresses, apartment numbers, ZIP+4, geocoded coordinates | `[ADDRESS]` |
| **Account Identifiers** | Bank account numbers, utility account numbers, case numbers, ticket numbers, claim numbers | `[ACCOUNT]` |
| **Government IDs** | Social Security numbers, National Insurance numbers, passport numbers, driver's license numbers, state ID numbers | `[GOVT_ID]` |
| **Medical Identifiers** | Medical record numbers (MRN), health insurance policy numbers, Medicare/Medicaid numbers, prescription identifiers | `[MEDICAL_ID]` |
| **Financial Identifiers** | Credit/debit card numbers (any digits), routing numbers, IBAN, SWIFT codes, cryptocurrency wallet addresses | `[FINANCIAL_ID]` |
| **Biometric References** | Explicit references to fingerprints, facial recognition data, voiceprints, DNA | `[BIOMETRIC]` |
| **Device Identifiers** | IMEI numbers, MAC addresses, serial numbers tied to individuals, IP addresses | `[DEVICE_ID]` |
| **Employment Identifiers** | Employee ID numbers, specific job titles when rare enough to identify | `[EMPLOYMENT_ID]` |
| **Date of Birth** | Full birth dates, age when combined with location/name enables identification | `[DATE_OF_BIRTH]` |
| **Location Precision** | City/town names with population < 50,000; neighborhood names in small cities; building names; floor numbers | `[LOCATION]` |
| **Relationship Graphs** | Mentions of specific family members, employers, landlords when combined enable doxxing | `[RELATIONSHIP]` |
| **Temporal Precision** | Exact dates of events when combined with other data enable identification (e.g., "my surgery on March 14") | `[PRECISE_DATE]` |
| **Images/Media** | Photographs of individuals, documents, screenshots containing any above identifiers | `[MEDIA_REDACTED]` |

### 5.2 Contextual Redaction Rules

Some identifiers are context-dependent. Apply these rules:

**A. Organization Names**
- Redact **small, local organizations** (a specific landlord, a local clinic, a neighborhood store) → `[ORG]`
- Do NOT redact **large national entities** (major banks, telecoms, insurers, government agencies) — these are part of the pattern
- Borderline case (regional chain with < 20 locations): Redact unless the entity is central to the harm pattern

**B. Geographic References**
- Always redact: specific neighborhoods in cities < 100,000 population; rural routes; landmarks tied to individuals
- Do NOT redact: states, large metropolitan areas (> 500,000 population), countries — these provide useful pattern context
- Borderline: medium cities (100,000-500,000). Redact if combined with any other identifying detail.

**C. Occupational Details**
- Redact: rare job titles, specific employers, workplace floor/department combinations
- Do NOT redact: general occupational categories ("healthcare worker," "retail employee," "teacher")

### 5.3 Redaction Verification

Every redaction must pass the **Re-identification Risk Test**:

> Can a reasonable adversary, using only publicly available databases and the unredacted portions of this signal, identify the individual with > 5% probability?

If **yes** → redact more. Repeat until **no**.

### 5.4 Special Categories (Enhanced Protection)

Under GDPR Article 9 and equivalent frameworks, the following are **special category data** requiring additional safeguards:

- Health information (including mental health, disability status, pregnancy)
- Racial or ethnic origin
- Religious or philosophical beliefs
- Trade union membership
- Genetic or biometric data
- Sex life or sexual orientation
- Criminal convictions or alleged offenses

**Rule**: Any StreetChat signal containing special category data must be:
1. Flagged `special_category: true`
2. Reviewed by a senior data steward before any extraction
3. Stored with enhanced encryption (at-rest and in-transit)
4. Subject to automatic deletion review every 30 days
5. Never used in training without explicit legal review

### 5.5 Redaction Audit Trail

Every redaction must produce:

```json
{
  "redaction_id": "uuid",
  "signal_id": "uuid",
  "redacted_by": ["reviewer_a_id", "reviewer_b_id"],
  "redaction_timestamp": "ISO-8601",
  "tokens_applied": [
    {"type": "PHONE", "count": 2, "positions": [[45, 57], [234, 246]]},
    {"type": "NAME", "count": 1, "positions": [[12, 24]]}
  ],
  "reidentification_risk_score": 0.03,
  "special_category": false,
  "verification_status": "passed"
}
```

---

## 6. CORROBORATION RULES

### 6.1 Definition

Corroboration is the process of confirming that an extracted StreetChat pattern reflects a real, repeatable phenomenon — not a single anomalous experience, fabrication, or misattribution. A corroborated signal has crossed the threshold from "one person said this" to "this is a detectable pattern."

### 6.2 Corroboration Requirements by Dimension

| Dimension | Minimum Requirement | Valid Sources |
|-----------|---------------------|---------------|
| **Frequency** | Pattern observed in ≥ 3 independent signals within 180 days | Other StreetChat signals, formal complaints, regulatory filings |
| **Structural consistency** | Core harm pattern identical across ≥ 3 sources, allowing for language variation | Cross-signal comparison via SwarmCurator |
| **Temporal persistence** | Pattern not explained by a single, resolved incident | Source timestamps spanning > 14 days |
| **Source independence** | Signals must originate from distinct individuals or organizational channels | IP analysis, writing style differentiation, submission channel diversity |
| **Plausibility** | Harm mechanism must be technically/institutionally possible | Expert review by subject-matter analyst |

### 6.3 Corroboration Sources (Ranked)

| Priority | Source Type | Weight |
|----------|-------------|--------|
| 1 | Independent regulatory complaint (CFPB, FTC, state AG, BBB) with matching pattern | **High** |
| 2 | Litigation filing (public court record) describing same harm | **High** |
| 3 | News media report (Tier 2+ source) documenting same pattern | **Medium-High** |
| 4 | Another StreetChat signal from independent source, matching structure | **Medium** |
| 5 | Corporate disclosure, terms-of-service change, or settlement acknowledging the issue | **Medium** |
| 6 | Expert analyst confirmation of institutional plausibility | **Low-Medium** |
| 7 | Internal consistency check (signal logically coherent, no contradictions) | **Low** |

**Rule**: To advance a signal, at least **two corroboration sources from different priority levels** must confirm the pattern, OR **one source from Priority 1 or 2** alone is sufficient.

### 6.4 Anti-Corroboration (Disqualifying Factors)

The following **invalidate** corroboration and may trigger demotion to Tier 4:

| Factor | Action |
|--------|--------|
| Sock-puppet detection: Multiple signals from same actor | Strip duplicate signals, flag source for monitoring |
| Coordinated campaign: Temporal clustering + language similarity suggesting organized posting | Quarantine all related signals, escalate to Trust & Safety |
| Contradictory evidence: Reliable Tier 1 or Tier 2 source explicitly refutes the pattern | Demote to Tier 4, annotate with refutation source |
| Stale signal: Pattern describes a process that has been demonstrably changed | Demote to Tier 4 with `stale` label, retain for historical reference only |
| Legal settlement with non-disclosure: Pattern confirmed but legally suppressed | Legal hold, do not promote, consult General Counsel |

### 6.5 Corroboration Record

Every corroboration decision must be documented:

```json
{
  "corroboration_id": "uuid",
  "signal_id": "uuid",
  "sources": [
    {"source_type": "regulatory_complaint", "reference": "CFPB-2025-001234", "match_confidence": 0.91},
    {"source_type": "streetchat_signal", "reference": "SIG-2025-005678", "match_confidence": 0.78}
  ],
  "minimum_requirements_met": true,
  "disqualifying_factors": [],
  "corroborated_by": "analyst_id",
  "corroboration_timestamp": "ISO-8601",
  "corroboration_tier": 2
}
```

---

## 7. PROMOTION PATHWAY

### 7.1 Tier 3 → Tier 2: Corroborated Discovery Signal

A Tier 3 StreetChat signal may be promoted to Tier 2 **only** by completing all of the following:

**Step 1: Redaction Verified**
- PII fully stripped (Section 5)
- Re-identification risk score < 0.05
- Two reviewers have signed off

**Step 2: Pattern Extracted**
- Extracted pattern follows the StreetChat JSONL schema (Section 10)
- Contains zero original-language quotations > 5 words
- Harm type, affected process, and outcome category are specified

**Step 3: Tribunal Classification = Honey**
- Tribunal has classified the extracted pattern as Honey (clear, actionable)
- Classification confidence > 0.80

**Step 4: Corroboration Complete**
- All corroboration requirements met (Section 6)
- At least two independent sources confirm the pattern, OR one Priority 1/2 source

**Step 5: Dual Authorization**
- Two authorized data stewards independently approve the promotion
- Both stewards must be trained on this policy and have no conflict of interest

**Step 6: Promotion Recorded**
- Promotion event logged in StreetLedger with full provenance chain
- Original Tier 3 signal preserved (with audit trail), Tier 2 copy created

### 7.2 Tier 2 → Tier 1: Institutional Confirmation

A Tier 2 signal may be promoted to Tier 1 **only** by:

- Institutional confirmation: the entity responsible for the harm has acknowledged it (settlement, policy change, regulatory action, court ruling)
- **OR** independent expert verification by a recognized authority in the relevant domain
- **OR** direct empirical measurement confirming the harm (controlled study, audit, data analysis)

Tier 2 → Tier 1 promotion requires:
- Data Governance Committee vote (majority)
- Legal review for defamation and liability risk
- Record in StreetLedger with full justification

### 7.3 No Reverse Promotion

Signals may not be promoted from Tier 2 back to Tier 3 "for convenience." If a Tier 2 signal's corroboration is undermined, it must be:
- Demoted to Tier 4 (quarantine) if the undermining is strong
- **OR** returned to Tier 3 for re-review if the undermining is partial
- The reason for demotion must be recorded and auditable

### 7.4 Promotion Prohibition

The following **never** qualify for promotion, regardless of corroboration:

- Signals containing unredacted PII
- Signals based on a single anonymous source with no structural detail
- Signals describing ongoing litigation where DefendableOS is or may become a party
- Signals flagged as special category data without legal clearance
- Signals whose corroboration source is itself a StreetChat signal at Tier 3 (circular corroboration)

---

## 8. ACCEPTABLE EXTRACTED PATTERNS

### 8.1 What CAN Be Stored

The following extracted patterns are acceptable for storage and may be candidates for Tier 2 promotion:

**A. Structural Harm Patterns**
```
ACCEPTABLE: "Consumer receives unexpected fee after canceling service. 
Fee is not disclosed in initial terms but appears in secondary document. 
Customer service denies refund, citing policy clause."
```
This is acceptable because it describes a structural pattern without identifying any individual, organization (at actionable precision), or specific incident.

**B. Process Failure Patterns**
```
ACCEPTABLE: "User submits dispute through official online portal. 
Portal confirms submission but provides no case number. 
User calls support; support has no record of submission. 
User resubmits; cycle repeats."
```
This is acceptable because it maps a process failure topology without referencing any specific person, case, or system identifier.

**C. Emerging Scam Signatures**
```
ACCEPTABLE: "Scam pattern: victim receives text message claiming 
package delivery failure with link to 'reschedule.' Link leads to 
payment page requesting credit card and 'verification fee.' 
Multiple consumers report identical message structure."
```
This is acceptable because it documents a scam signature for community defense without reproducing the actual link, phone numbers, or victim details.

**D. Emotional Valence Markers (Aggregated)**
```
ACCEPTABLE: "Pattern observed in N=47 signals: consumers describing 
billing disputes show escalating frustration over 3+ interactions, 
typically followed by abandonment of dispute (no resolution)."
```
This is acceptable because it reports an aggregated emotional trajectory, not individual emotional states.

**E. Repair Attempt Taxonomy**
```
ACCEPTABLE: "Common repair attempts for [harm type]: (1) call customer 
service → transferred 2+ times; (2) file online dispute → no 
confirmation; (3) contact regulatory body → referred back to company; 
(4) post on social media → generic response, no resolution."
```
This is acceptable because it taxonomizes repair failures without identifying who attempted them.

### 8.2 Acceptable Content Rules

| Attribute | Rule |
|-----------|------|
| **No direct quotes** | Maximum 5 contiguous words from original signal |
| **No identifiers** | All PII replaced with tokens (Section 5) |
| **No attribution** | Never state "User X reported" or "[Name] said" |
| **Aggregate counts** | Use "N=47 signals" not "47 people" |
| **Structural focus** | Describe the system failure, not the individual experience |
| **Time granularity** | Use month/year or quarter, not specific dates |
| **Reversible** | Pattern must be deletable without orphaning higher-tier data |

---

## 9. PROHIBITED STORAGE AND OVERCLAIMING

### 9.1 What MUST NOT Be Stored

The following must never appear in any extracted pattern, training set, or promoted signal:

**A. Raw Quoted Text from Individuals**
```
PROHIBITED: "As one user wrote: 'I called them five times and 
every time they said the same thing, that my case was pending 
and someone would call back but no one ever did and I'm so 
tired of this whole thing.'"
```
This is prohibited because it reproduces identifiable personal expression, creates liability risk, and adds no structural value.

**B. Named or Identifiable Individuals**
```
PROHIBITED: "Sarah M. from Denver reported that Kaiser Permanente 
denied her MRI pre-authorization three times."
```
This is prohibited because it names an individual, provides a location + organization combination that narrows identification, and describes a specific case.

**C. Specific Case Details**
```
PROHIBITED: "Claim #2024-839271 was denied on March 14, 2025, 
despite the patient having met their deductible."
```
This is prohibited because it includes a specific claim number, exact date, and individual circumstances that enable identification.

**D. Contact Information (Even Redacted)**
```
PROHIBITED: "Call 1-800-XXX-XXXX and ask for extension 4721." 
[even with redaction]
```
This is prohibited because phone numbers with extensions can sometimes be reverse-engineered, and the instruction implies a specific, contactable person.

**E. Medical Details**
```
PROHIBITED: "Patient was prescribed Ozempic for Type 2 diabetes 
but insurance required prior auth which was denied after 3 weeks."
```
This is prohibited because it includes medical diagnosis, medication, and insurance details — all special category data.

**F. Allegations of Criminal Conduct by Named Parties**
```
PROHIBITED: "John Smith at Acme Corp is running a Ponzi scheme. 
He stole $50,000 from my retirement account."
```
This is prohibited because it names an individual and accuses them of a crime. Such allegations must go through formal legal channels, not community signal storage.

**G. Content That Could Enable Harassment**
```
PROHIBITED: "The manager at the Elm Street location works 
Tuesdays and Thursdays and is the one who approves all returns."
```
This is prohibited because it provides information that could be used to target an individual, even if no name is given.

### 9.2 Overclaiming: The Cardinal Sin

**Overclaiming** is the act of presenting a Tier 3 signal as if it were Tier 1 or Tier 2. It is the most dangerous violation of this policy.

#### 9.2.1 Forms of Overclaiming

| Form | Example | Consequence |
|------|---------|-------------|
| **Tier misrepresentation** | Storing a signal at Tier 2 when it has not completed the promotion pathway | Systemic trust degradation, potential defamation liability |
| **Sole-source assertion** | Using a single StreetChat signal as the basis for a claim presented to end users | Factual errors, reputational harm, regulatory scrutiny |
| **Implied authority** | Presenting a community signal with language like "studies show" or "data confirms" | Fraudulent misrepresentation |
| **Untagged presentation** | Showing a Tier 3 signal to end users without a clear "Community Signal — Unverified" tag | Consumer deception |
| **Training contamination** | Using un-reviewed Tier 3 signals to fine-tune or train models | Model bias, hallucination amplification, regulatory violation |

#### 9.2.2 Overclaiming Prevention Checklist

Before any StreetChat-derived content is presented, stored above Tier 3, or used in training, the following must be confirmed:

- [ ] Signal has passed all five extraction stages (Section 4)
- [ ] All PII has been redacted and verified (Section 5)
- [ ] Corroboration requirements are met (Section 6)
- [ ] Tribunal classification is Honey (for Tier 2 promotion)
- [ ] Dual authorization is recorded (Section 7)
- [ ] The content carries appropriate tier labeling
- [ ] No single source is presented as definitive

### 9.3 Retention Limits for Prohibited Content

Raw posts that cannot be safely extracted **must not be retained** beyond the minimum necessary for the following:

| Content Type | Maximum Retention | Action After Period |
|--------------|-------------------|---------------------|
| Raw post with irreparable PII | 30 days | Secure deletion with certificate |
| Raw post with special category data | 30 days (or legal minimum, whichever is shorter) | Secure deletion with certificate |
| Raw post failing re-identification risk test | 7 days | Secure deletion with certificate |
| Quarantined (Tier 4) signals | 90 days | Review for learning value; then delete or anonymize |
| Sock-puppet / coordinated campaign signals | 180 days | Retain for Trust & Safety pattern analysis only; then delete |

---

## 10. STREETCHAT JSONL SCHEMA

### 10.1 Extracted Pattern Record

```json
{
  "schema_version": "1.0.0",
  "signal_id": "uuid-v4",
  "streetledger_ref": "SL-YYYY-NNNNNN",
  
  "provenance": {
    "source_channel": "forum|app|email|voice|api",
    "intake_timestamp": "2025-01-15T09:23:17Z",
    "ingestion_operator": "operator_id_or_system_name",
    "collection_method": "voluntary_submission|scraped_public|partner_feed|other",
    "original_url": "[REDACTED]",
    "retention_authorized": true
  },
  
  "trust_tier": {
    "current_tier": 3,
    "tier_history": [
      {"tier": 3, "changed_at": "2025-01-15T09:23:17Z", "reason": "intake"}
    ],
    "promotion_blocked": false,
    "promotion_block_reason": null
  },
  
  "redaction": {
    "redaction_id": "uuid-v4",
    "redacted_by": ["reviewer_a_id", "reviewer_b_id"],
    "redaction_timestamp": "2025-01-15T10:45:33Z",
    "tokens_applied": [
      {"type": "PHONE", "count": 1},
      {"type": "NAME", "count": 2},
      {"type": "LOCATION", "count": 1}
    ],
    "reidentification_risk_score": 0.02,
    "special_category": false,
    "verification_status": "passed"
  },
  
  "extracted_pattern": {
    "pattern_id": "uuid-v4",
    "harm_type": "billing_dispute|service_denial|scam|identity_theft|contract_violation|discrimination|other",
    "harm_type_confidence": 0.89,
    "harm_subtype": "unexpected_fee|denial_of_coverage|phishing|impersonation|terms_change|delay|other",
    
    "affected_process": {
      "process_category": "billing|claims|support|onboarding|cancellation|delivery|other",
      "process_stage": "initiation|processing|review|approval|fulfillment|post_completion",
      "touchpoint": "online_portal|phone|mail|in_person|mobile_app|third_party"
    },
    
    "harm_description": "Structural description of the harm pattern (max 500 chars)",
    "original_language_sample": null,
    
    "emotional_valence": {
      "primary": "frustration|fear|anger|helplessness|confusion|relief|other",
      "escalation_observed": true,
      "valence_confidence": 0.75
    },
    
    "repair_attempts": [
      {
        "method": "called_support|filed_dispute|posted_social|contacted_regulator|hired_attorney|other",
        "outcome": "resolved|partially_resolved|denied|no_response|escalated|abandoned",
        "attempt_order": 1
      }
    ],
    
    "entity_category": "bank|insurer|telecom|utility|healthcare|government|retail|tech_platform|other",
    "entity_size": "national|regional|local|unknown",
    
    "temporal_context": {
      "signal_quarter": "2025-Q1",
      "pattern_duration_estimate": "single_event|days|weeks|months|ongoing",
      "recency": "recent|moderate|stale"
    },
    
    "pattern_confidence": 0.82,
    "extracted_by": "swarmcurator_model_version_or_analyst_id",
    "extraction_timestamp": "2025-01-15T11:02:08Z"
  },
  
  "tribunal_classification": {
    "classification": "honey|jelly|propolis",
    "classification_confidence": 0.85,
    "classified_by": "tribunal_agent_id",
    "classification_timestamp": "2025-01-15T14:30:00Z",
    "classification_reason": "Clear structure, identifiable harm type, replicable pattern"
  },
  
  "corroboration": {
    "status": "pending|partial|complete|failed",
    "corroboration_id": null,
    "source_count": 0,
    "sources": [],
    "corroborated_at": null
  },
  
  "usage_permissions": {
    "training_allowed": false,
    "user_facing_allowed": false,
    "analyst_viewing_allowed": true,
    "tier_2_promotion_eligible": false
  },
  
  "audit_log": [
    {
      "event": "intake",
      "timestamp": "2025-01-15T09:23:17Z",
      "actor": "system",
      "details": "Signal ingested from forum channel"
    },
    {
      "event": "redaction_complete",
      "timestamp": "2025-01-15T10:45:33Z",
      "actor": "reviewer_a_id",
      "details": "PII redacted, risk score 0.02"
    }
  ]
}
```

### 10.2 Schema Compliance Requirements

- Every field marked in the schema is **mandatory** (may be `null` where specified)
- `harm_description` maximum length: 500 characters
- `original_language_sample` must be `null` at intake; may only be populated after legal review
- `trust_tier.tier_history` must contain every tier change with timestamp and reason
- `audit_log` must contain an entry for every operation performed on the signal
- Schema version must be incremented for any structural changes

### 10.3 JSONL Export Format

For batch processing and storage, records are exported as JSONL (one JSON object per line):

```jsonl
{"schema_version":"1.0.0","signal_id":"...",...}
{"schema_version":"1.0.0","signal_id":"...",...}
```

- No pretty-printing in production JSONL
- UTF-8 encoding required
- Maximum line length: 64KB
- Files must be encrypted at rest and in transit

---

## 11. SWARMJELLY VS SWARMCURATOR USE

### 11.1 SwarmCurator: Grader, Classifier, Verifier

**SwarmCurator** is the structured processing layer. It handles signals that are clean enough to grade.

| Function | Input | Output |
|----------|-------|--------|
| **Grading** | Redacted StreetChat signal | Quality score (0.0-1.0) based on structure, clarity, specificity |
| **Classification** | Extracted pattern | Harm type, subtype, confidence scores |
| **Verification** | Extracted pattern + external sources | Corroboration assessment, source matching |
| **Tier promotion recommendation** | Corroborated Tier 3 signal | Tier 2 recommendation with justification |

**SwarmCurator processes:**
- Redacted signals only
- Signals that have passed Stage 3 (redaction) of the extraction pipeline
- Signals intended for Tier 2 promotion
- Honey-classified patterns

**SwarmCurator does NOT process:**
- Raw, unredacted community posts
- Signals classified as Propolis (quarantined)
- Signals with re-identification risk > 0.05

### 11.2 SwarmJelly: Messy/Ambiguous Training Material

**SwarmJelly** is the unstructured learning layer. It handles language that is too messy, emotional, or ambiguous for structured extraction but still has training value.

| Function | Input | Output |
|----------|-------|--------|
| **Messy language collection** | Raw community posts (fully redacted) | Corpus of natural pain/friction language |
| **Pattern seeding** | Jelly-classified signals | Candidate patterns for curator review |
| **Bias detection** | Aggregated Jelly corpus | Identification of systemic gaps in signal coverage |
| **Edge case training** | Ambiguous, contradictory signals | Training material for disagreement and uncertainty modeling |

**SwarmJelly receives:**
- Jelly-classified signals from Tribunal (ambiguous, unclear structure)
- Redacted signals that SwarmCurator could not grade above 0.4 quality
- Aggregated emotional valence data (not individual emotional states)
- Language patterns for embedding/semantic analysis (no individual attribution)

### 11.3 Routing Decision Matrix

```
                    ┌─────────────────────────────────────────┐
                    │         Tribunal Classification          │
    ┌───────────────┼─────────────┬─────────────┬─────────────┤
    │               │   HONEY     │    JELLY    │  PROPOLIS   │
┌───┴───────────────┼─────────────┼─────────────┼─────────────┤
│ Redaction Quality │             │             │             │
│ > 0.7             │ SwarmCurator│ SwarmJelly  │  Tier 4     │
├───────────────────┼─────────────┼─────────────┼─────────────┤
│ Redaction Quality │             │             │             │
│ 0.4 - 0.7         │ SwarmCurator│ SwarmJelly  │  Tier 4     │
├───────────────────┼─────────────┼─────────────┼─────────────┤
│ Redaction Quality │             │             │             │
│ < 0.4             │ Manual Rev. │ SwarmJelly  │  Tier 4     │
└───────────────────┴─────────────┴─────────────┴─────────────┘
```

### 11.4 Key Boundary: Jelly Must Never Present as Fact

**Critical rule**: Material in SwarmJelly must never be presented as factual claims, used in user-facing outputs, or treated as verified patterns. SwarmJelly material is:

- **Learning data**, not **truth data**
- **Pattern seeds**, not **pattern confirmations**
- **Language samples**, not **factual assertions**

Any operator who uses SwarmJelly material in a user-facing output without SwarmCurator verification and Tribunal Honey classification has committed a Tier 1 policy violation (see Section 12).

---

## 12. ENFORCEMENT AND VIOLATIONS

### 12.1 Violation Classification

Violations of this policy are classified into four tiers:

| Class | Severity | Examples |
|-------|----------|----------|
| **Class 1** | Critical | Storing unredacted PII; overclaiming (presenting Tier 3 as fact); using prohibited content in training; unauthorized promotion |
| **Class 2** | Serious | Incomplete redaction (risk score > 0.05); failure to obtain dual authorization for promotion; retaining prohibited content beyond retention limit |
| **Class 3** | Moderate | Missing audit log entries; schema violations; failure to flag special category data; delayed Tribunal submission |
| **Class 4** | Minor | Formatting errors in JSONL; late review (beyond 72 hours); incomplete documentation |

### 12.2 Consequences by Class

| Class | First Violation | Repeat Violation (within 12 months) |
|-------|----------------|-------------------------------------|
| **Class 1** | Immediate suspension of data access; investigation by Data Governance Committee; potential termination; legal review | Termination; referral to legal counsel; regulatory notification if required |
| **Class 2** | Written warning; mandatory retraining; supervised operation for 30 days | Suspension pending investigation; restriction to non-signal operations |
| **Class 3** | Informal coaching; documented reminder | Written warning; mandatory process review |
| **Class 4** | Correction required within 48 hours | Escalation to Class 3 treatment |

### 12.3 Automated Enforcement

The following policy rules are **automated** and enforced without human discretion:

| Rule | Automated Action |
|------|------------------|
| PII confidence > 0.85 in raw signal | Automatic pipeline hold; manual review queue |
| Re-identification risk score > 0.05 | Automatic block on pattern extraction |
| Signal at Tier 3 used in training data | Automatic pipeline halt; alert to Data Governance |
| Signal promoted without dual authorization | Automatic tier revert to 3; alert to committee |
| Prohibited content pattern detected in storage | Automatic quarantine; legal hold notification |
| Retention period exceeded | Automatic scheduling for secure deletion |

### 12.4 Reporting and Whistleblower Protection

Any operator who observes or suspects a violation of this policy must report it via:
- **Internal**: Secure reporting channel (`ethics@defendableos.internal`)
- **Anonymous**: Anonymous tip line (no IP logging, no account required)

**Whistleblower protections**:
- No retaliation for good-faith reports
- Reporter identity protected to the maximum extent legally permissible
- Reports investigated within 5 business days
- Reporter notified of outcome (without compromising privacy of investigation)

### 12.5 Escalation Pathway

```
Violation Detected
        │
        ▼
┌───────────────┐    Class 1 or 2?    ┌─────────────────┐
│ Auto-hold /   │ ──────────────────► │ Data Governance   │
│ Manual Report │                     │ Committee         │
└───────────────┘                     │ (meets within 48h)│
        │                             └─────────────────┘
        │ Class 3 or 4?                       │
        ▼                                     ▼
┌───────────────┐                     ┌─────────────────┐
│ Supervisor    │                     │ Investigation   │
│ Review        │                     │ (complete in    │
│ (within 72h)  │                     │  10 business    │
└───────────────┘                     │  days)          │
                                      └─────────────────┘
                                                │
                                                ▼
                                      ┌─────────────────┐
                                      │ Disciplinary    │
                                      │ Action /        │
                                      │ Policy Update   │
                                      └─────────────────┘
```

---

## 13. REVIEW CADENCE

### 13.1 Scheduled Reviews

| Review Type | Frequency | Owner | Scope |
|-------------|-----------|-------|-------|
| **Operational review** | Weekly | Signal Operations Lead | Pipeline health, backlog, error rates, PII detection accuracy |
| **Compliance review** | Monthly | Data Governance Committee | Redaction quality, retention compliance, promotion accuracy, audit log completeness |
| **Policy review** | Quarterly | Policy Owner + Tribunal Board | Full policy text, effectiveness metrics, incident analysis, regulatory updates |
| **External audit** | Annually | Independent auditor + legal counsel | Full system audit, regulatory compliance, penetration testing of PII controls |
| **Emergency review** | Ad hoc (triggered) | Data Governance Committee | Post-incident, regulatory change, significant technology change |

### 13.2 Review Triggers

An emergency policy review is triggered by any of the following:

- Any Class 1 violation
- Regulatory change affecting PII handling (new state law, GDPR update, etc.)
- Technology change affecting PII detection accuracy (model update, new signal source)
- Legal hold or subpoena involving StreetChat data
- Breach or suspected breach of StreetChat data
- External audit finding requiring policy change
- Change in DefendableOS Trust Tier Policy (this policy must align)

### 13.3 Review Documentation

Every review must produce:
- Review date, participants, scope
- Findings (compliant / non-compliant / needs-improvement per section)
- Action items with owners and due dates
- Policy amendment recommendations (if any)
- Sign-off by Policy Owner and Data Governance Committee chair

---

## 14. EXAMPLE WORKFLOWS

### 14.1 Workflow A: Successful Tier 3 → Tier 2 Promotion

**Scenario**: Multiple community posts describe a new credit card fee pattern.

```
STEP 1 — Intake
━━━━━━━━━━━━━━━
Raw post received from forum: "I got charged a $12 'account maintenance 
fee' on my Chase card even though I have autopay set up. Called them 
and they said everyone got it starting January. My friend got the same 
fee on her Capital One card too."
  → signal_id assigned
  → Tier 3 applied
  → intake_timestamp recorded

STEP 2 — Automated Pre-Screen
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PII detection:
  - "Chase" → org name (large national — DO NOT redact)
  - "Capital One" → org name (large national — DO NOT redact)
  - "$12" → financial amount (not an identifier — keep)
  - No phone numbers, addresses, account numbers detected
  → pii_flag_count = 0
  → Proceed to Stage 3

STEP 3 — Redaction
━━━━━━━━━━━━━━━━━━━━
No PII tokens required.
Reviewers confirm: "No identifying information present. Signal describes 
structural pattern at national bank level."
  → reidentification_risk_score = 0.00
  → Both reviewers sign off

STEP 4 — Pattern Extraction
━━━━━━━━━━━━━━━━━━━━━━━━━━━
Extracted pattern:
  harm_type: "billing_dispute"
  harm_subtype: "unexpected_fee"
  affected_process: {"process_category": "billing", "process_stage": "post_completion", "touchpoint": "statement"}
  harm_description: "Consumers report unexpected 'account maintenance fee' 
    appearing on credit card statements despite autopay enrollment. Fee 
    appears to affect multiple card issuers simultaneously."
  entity_category: "bank"
  entity_size: "national"
  temporal_context: {"signal_quarter": "2025-Q1", "pattern_duration_estimate": "weeks", "recency": "recent"}
  pattern_confidence: 0.85

STEP 5 — Tribunal Classification
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Tribunal reviews: Pattern is clear, structural, actionable.
  → classification: "honey"
  → classification_confidence: 0.88

STEP 6 — Corroboration
━━━━━━━━━━━━━━━━━━━━━━
Analyst searches for corroboration:
  - Source 1: CFPB complaint #2025-004321 (Priority 1) — same fee pattern described
  - Source 2: Second StreetChat signal (Priority 4) — independent user, same pattern
  → Both sources confirm structural match
  → Corroboration complete

STEP 7 — Dual Authorization
━━━━━━━━━━━━━━━━━━━━━━━━━━━
Data steward A reviews: Corroboration valid, pattern clear, PII clean.
Data steward B reviews: Independent confirmation of above.
Both authorize Tier 2 promotion.

STEP 8 — Promotion Recorded
━━━━━━━━━━━━━━━━━━━━━━━━━━━
  → Tier updated to 2
  → tier_history appended
  → StreetLedger entry created with full provenance
  → usage_permissions updated: user_facing_allowed = true

RESULT: Signal promoted to Tier 2. May be used in user-facing outputs 
with appropriate attribution label.
```

### 14.2 Workflow B: Jelly Classification (Messy but Valuable)

**Scenario**: A raw post is highly emotional and structurally unclear, but contains potentially valuable language.

```
STEP 1 — Intake
━━━━━━━━━━━━━━━
Raw post received: "I dont even know what to do anymore ive been 
trying for MONTHS to get them to fix this and every time its like 
talking to a WALL they just keep saying the same thing over and 
over and NOTHING ever changes im so tired of all of this why do 
they make it so hard"
  → signal_id assigned
  → Tier 3 applied

STEP 2 — Automated Pre-Screen
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PII detection: No identifiers found. No org names. No financial data.
  → pii_flag_count = 0

STEP 3 — Redaction
━━━━━━━━━━━━━━━━━━━━
Nothing to redact. No PII present.
Reviewers confirm signal contains no identifying information.
  → reidentification_risk_score = 0.00

STEP 4 — Pattern Extraction Attempt
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SwarmCurator attempts extraction:
  - harm_type: unclear (confidence 0.32)
  - entity_category: unknown
  - affected_process: unknown
  - harm_description: Insufficient structural detail to extract pattern
  → pattern_confidence = 0.25 (too low)

STEP 5 — Tribunal Classification
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Tribunal reviews: Emotional, lacks structure, but represents genuine 
frustration pattern.
  → classification: "jelly"
  → classification_confidence: 0.80
  → Reason: "High emotional valence, low structural clarity. Contains 
     frustration language pattern but no actionable harm description."

STEP 6 — Routing to SwarmJelly
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  → Signal routed to SwarmJelly corpus
  → Emotional valence recorded: frustration, escalation, abandonment
  → Language pattern added to messy-material training set
  → usage_permissions: training_allowed = true (for uncertainty modeling 
     only), user_facing_allowed = false

RESULT: Signal remains Tier 3. Contributes to emotional valence 
corpus and language pattern recognition. Never presented as fact. 
May seed a future pattern if corroborating signals provide structural 
detail.
```

### 14.3 Workflow C: Propolis Classification (Quarantine)

**Scenario**: A raw post contains PII, makes a criminal allegation against a named individual, and includes contact information.


<!-- BEGIN PEDAGOGICAL_PII_TEST_FIXTURE: NOT LIVE PERSONAL DATA -->
```
STEP 1 — Intake
━━━━━━━━━━━━━━━
Raw post received: "BEWARE of John Smith at ABC Insurance in 
Springfield. He stole my social security number 123-45-6789 and 
sold it to hackers. His direct line is 555-123-4567. He works 
on the 3rd floor. Avoid him at all costs. His email is 
john.smith@abcins.com."
  → signal_id assigned
  → Tier 3 applied

STEP 2 — Automated Pre-Screen
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PII detection ALERT (multiple high-confidence hits):
  - "John Smith" → NAME (confidence: 0.97)
  - "123-45-6789" → GOVT_ID / SSN (confidence: 0.99)
  - "555-123-4567" → PHONE (confidence: 0.99)
  - "john.smith@abcins.com" → EMAIL (confidence: 0.99)
  - "3rd floor" → LOCATION precision (confidence: 0.72)
  - "Springfield" → LOCATION (borderline, flagged for review)
  → pii_flag_count = 6
  → AUTOMATIC PIPELINE HOLD

STEP 3 — Manual Review (Required due to hold)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Senior reviewer assessment:
  - SSN present → immediate special category flag
  - Criminal allegation against named individual → legal risk
  - Contact information for alleged perpetrator → harassment risk
  - Multiple identifiers = impossible to safely redact while 
    preserving any signal value
  
  Decision: Signal is unrecoverable.
  → classification recommendation: "propolis"

STEP 4 — Tribunal Classification
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Tribunal confirms: Propolis.
  → classification: "propolis"
  → classification_confidence: 0.95
  → Reason: "Contains unredactable PII including SSN, names named 
     individual with criminal allegation, provides contact info 
     enabling harassment. No recoverable pattern."

STEP 5 — Quarantine
━━━━━━━━━━━━━━━━━━━
  → Signal moved to Tier 4 quarantine
  → All raw data encrypted and isolated
  → Retention clock starts: 30 days maximum
  → Access restricted to Data Governance Committee + General Counsel
  → Alert sent to Trust & Safety for potential pattern monitoring 
    (if similar allegations arise against same entity, may indicate 
    broader issue)

STEP 6 — Retention and Disposal
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
After 30 days:
  - Signal securely deleted with cryptographic wipe
  - Deletion certificate generated
  - Audit log updated: "Deleted per retention policy, propolis 
    classification, unredactable PII"
  - Only metadata retained: "Signal [ID] received [date], classified 
    propolis, deleted [date]. No pattern extracted."

RESULT: Signal quarantined and destroyed. No pattern stored. 
Metadata retained for audit trail only. If Trust & Safety detects 
related signals about ABC Insurance, a new investigation may be 
opened through formal channels.
```
<!-- END PEDAGOGICAL_PII_TEST_FIXTURE -->


### 14.4 Workflow D: Special Category Data Handling

**Scenario**: A post contains detailed medical information about a denied insurance claim.

```
STEP 1 — Intake
━━━━━━━━━━━━━━━
Raw post received: "My doctor prescribed Wegovy for my obesity 
and pre-diabetes. UnitedHealthcare denied the prior auth saying 
it's not medically necessary even though my BMI is 38 and I have 
A1C of 7.2. My member ID is UHC-8847391. I've been fighting 
this for 6 weeks."
  → signal_id assigned
  → Tier 3 applied

STEP 2 — Automated Pre-Screen
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PII detection:
  - "UnitedHealthcare" → org name (large national — DO NOT redact)
  - "UHC-8847391" → ACCOUNT / member ID (confidence: 0.95)
  - Medical terms detected: "Wegovy", "obesity", "pre-diabetes", 
    "BMI", "A1C"
  → SPECIAL CATEGORY FLAG auto-triggered (health data)
  → pii_flag_count = 1 (member ID)

STEP 3 — Senior Data Steward Review (Required for special category)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Senior steward assessment:
  - Medical diagnosis present → special category confirmed
  - Member ID present → must be redacted
  - Large national insurer named → may keep (structural pattern)
  - Specific medication named → borderline; medication is part of 
    harm pattern but also health data
  
  Decision: Redact member ID. Keep insurer name. Keep medication 
  name as it is central to the harm pattern (medication denial). 
  Flag for enhanced encryption.

STEP 4 — Redaction
━━━━━━━━━━━━━━━━━━━━
  - "UHC-8847391" → [ACCOUNT]
  - Enhanced encryption applied to all fields
  - special_category: true
  - reidentification_risk_score = 0.01 (after redaction)

STEP 5 — Pattern Extraction
━━━━━━━━━━━━━━━━━━━━━━━━━━━
Extracted pattern (limited):
  harm_type: "service_denial"
  harm_subtype: "denial_of_coverage"
  affected_process: {"process_category": "claims", "process_stage": "review", "touchpoint": "insurer_portal"}
  harm_description: "Consumer reports prescription medication denied 
    by insurer via prior authorization process despite documented 
    medical indication."
  entity_category: "insurer"
  entity_size: "national"
  → pattern_confidence = 0.70

  NOTE: Specific medical details (BMI, A1C, specific medication) 
  are NOT included in extracted pattern despite being in raw signal.

STEP 6 — Tribunal Classification
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  → classification: "honey" (clear structural pattern)
  → classification_confidence: 0.82

STEP 7 — Corroboration
━━━━━━━━━━━━━━━━━━━━━━
Analyst searches for corroboration:
  - Found: 3 similar patterns in StreetChat (different insurers, 
    same prior-auth denial structure)
  - Found: News article about prior auth delays for GLP-1 medications 
    (Priority 3)
  → Corroboration partial (insufficient for Tier 2 due to special 
     category restrictions)

STEP 8 — Special Category Handling
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Despite honey classification and partial corroboration, signal 
remains Tier 3 due to special category flag.
  → usage_permissions: 
    training_allowed = false (pending legal review)
    user_facing_allowed = false
    analyst_viewing_allowed = true (for subject-matter analysis only)
  → Automatic deletion review scheduled: 30 days
  → Signal may be used for aggregate trend analysis only (N=1 → 
    combined with N=X for statistical reporting)

RESULT: Signal remains Tier 3. Pattern extracted but restricted 
due to health data classification. May contribute to aggregate 
analysis only. Tier 2 promotion blocked pending legal clearance.
```

### 14.5 Workflow E: Sock-Puppet Detection and Coordinated Campaign

**Scenario**: Multiple posts appear within a 4-hour window using similar language to attack a specific company.

```
STEP 1 — Intake (Multiple Signals)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
12 signals received between 14:00-18:00 on the same day, all 
mentioning "XYZ Mortgage" and using similar phrasing: "worst 
company ever," "total scam," "steals your money."
  → Each assigned signal_id, all enter at Tier 3

STEP 2 — Automated Clustering Alert
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SwarmCurator anomaly detection:
  - Temporal clustering: 12 signals in 4 hours (expected: 2-3/day)
  - Language similarity: Jaccard similarity 0.78 across all 12 
    (expected: < 0.3 for independent posts)
  - Entity focus: All 12 target same organization
  - Source diversity: Only 3 distinct IP addresses across 12 posts
  → AUTOMATIC COORDINATION ALERT

STEP 3 — Trust & Safety Review
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Trust & Safety analyst investigation:
  - 3 IP addresses, all from same ASN, same geographic region
  - Writing style analysis: high probability same author for 
    multiple "different" accounts
  - No corroboration found in regulatory complaints, news, or 
    litigation
  - XYZ Mortgage: no prior StreetChat signals, no regulatory actions
  
  Decision: Coordinated campaign detected. All 12 signals are 
  sock-puppet or astroturf posts.

STEP 4 — Tribunal Classification
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
All 12 signals:
  → classification: "propolis"
  → subclassification: "coordinated_campaign"
  → classification_confidence: 0.92

STEP 5 — Quarantine and Source Flagging
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  - All 12 signals moved to Tier 4 quarantine
  - Source accounts flagged for monitoring
  - IP addresses logged in Trust & Safety watchlist
  - Retention: 180 days for campaign pattern analysis
  - After 180 days: secure deletion
  
  Aggregate data retained (no individual signals):
  - "Campaign detected: 12 synthetic signals targeting XYZ Mortgage, 
    [date range]. Coordinated posting pattern documented."

STEP 6 — Counter-Intelligence Value
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Extracted insight (aggregate only, no individual signals):
  "Astroturf campaign signature: rapid temporal clustering, high 
  language similarity, low source diversity, absence of corroborating 
  evidence. Target: mortgage lender."
  → Added to SwarmJelly as "disinformation pattern" training material
  → Used to improve SwarmCurator sock-puppet detection model

RESULT: Individual signals quarantined and destroyed. Campaign 
pattern retained for detection training. XYZ Mortgage receives no 
negative signal in the system. Source accounts monitored for future 
campaigns.
```

---

## APPENDIX A: GLOSSARY

| Term | Definition |
|------|------------|
| **Astroturf** | Coordinated campaign designed to simulate grassroots community sentiment |
| **Corroboration** | Process of confirming a pattern through independent sources |
| **Honey** | Tribunal classification: clear, actionable, well-structured pattern |
| **Jelly** | Tribunal classification: messy, ambiguous, structurally unclear material |
| **Overclaim** | Presenting a lower-tier signal as if it were a higher-tier fact |
| **Propolis** | Tribunal classification: contaminated, unrecoverable, policy-violating material |
| **Re-identification risk** | Probability that a redacted signal can be linked back to an individual |
| **Sock-puppet** | Fake online identity used to deceptively amplify a position |
| **Special category data** | Data revealing racial/ethnic origin, political opinions, religious beliefs, trade union membership, genetic/biometric data, health data, sex life/orientation, or criminal data |
| **StreetLedger** | DefendableOS provenance and storage layer |
| **SwarmCurator** | Grader, classifier, and verifier for community signals |
| **SwarmJelly** | Messy/ambiguous training material repository |
| **Tier** | Trust level assigned to a signal (1-4) |
| **Tribunal** | Classification system using Honey/Jelly/Propolis categories |

## APPENDIX B: COMPLIANCE MATRIX

| Regulation / Framework | Relevant Section(s) | How This Policy Addresses It |
|------------------------|---------------------|------------------------------|
| GDPR Article 5 (Principles) | Sections 5, 9 | Lawfulness, fairness, data minimization, purpose limitation |
| GDPR Article 9 (Special Categories) | Section 5.4 | Enhanced protection for health, biometric, and other special data |
| GDPR Article 17 (Right to Erasure) | Section 9.3 | Defined retention limits and secure deletion procedures |
| CCPA / CPRA | Sections 5, 9 | Consumer privacy rights, deletion obligations |
| State Biometric Laws (BIPA, CCPA biometric) | Section 5.1 | Explicit biometric reference redaction |
| FTC Act Section 5 (Unfair/Deceptive Practices) | Sections 3, 9.2 | Overclaiming prevention, prohibition on presenting unverified signals as fact |
| Emerging AI Governance (EU AI Act, NIST AI RMF) | Sections 3, 9.2, 11 | Training data governance, bias prevention, transparency about signal tiers |

## APPENDIX C: CHANGE LOG

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0.0 | 2025-07-01 | Data Governance Committee | Initial release |

---

**END OF DOCUMENT**

*This policy is a living document. All operators are required to acknowledge receipt and understanding upon onboarding and after each quarterly review. Questions, concerns, and violation reports should be directed to the Data Governance Committee.*
