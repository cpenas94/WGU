# Domain 1.4 — Compare and Contrast Threat Intelligence and Threat Hunting Concepts

A comprehensive study guide covering threat intelligence strategies, threat actor classifications, TTPs, confidence assessment, intelligence sharing, and proactive threat hunting methodologies for the CompTIA CySA+ (CS0-003) exam.

---

## Table of Contents

- Overview & Key Comparison
- Threat Actors (Classification & Profiles)
- Tactics, Techniques, and Procedures (TTPs)
- Confidence Levels & Assessment
- Collection Methods and Sources
- Threat Intelligence Sharing
- Threat Hunting Fundamentals
- Study Tips & Mnemonics
- Practice Questions

---

## Overview & Key Comparison

**Threat Intelligence** and **Threat Hunting** are complementary but distinct approaches to defending against adversaries.

### Quick Comparison Table

| Aspect | Threat Intelligence | Threat Hunting |
|--------|-------------------|-----------------|
| **Approach** | Reactive/Informative: Collects, analyzes, and disseminates data on known/anticipated threats | Proactive: Assumes breach; actively searches networks for undetected threats using hypotheses |
| **Focus** | External data (feeds, reports); provides context (TTPs, actors) | Internal data (logs, endpoints); validates intelligence with real-time hunts |
| **Output** | Reports, IOCs, feeds for tools (SIEM, firewalls) | Discoveries (IOCs, misconfigurations); improves detection rules |
| **Timing** | Ongoing; pre-breach awareness | Post-assumption of breach; iterative hunts |
| **Tools/Methods** | Feeds, STIX/TAXII, OSINT | EDR, SIEM queries, behavioral analytics |
| **Goal** | Reduce risk via awareness and sharing | Confirm/uncover active threats; refine defenses |

### Exam Tip
Intelligence feeds hunting (e.g., IOCs from feeds become hunt hypotheses). Hunting validates and enriches intelligence.

---

## Threat Actors (Classification & Profiles)

Threat actors are individuals or groups responsible for malicious activities. Classify by motivation, capability, and sophistication.

### Advanced Persistent Threat (APT)

- **Definition:** Highly sophisticated, stealthy actors (often state-sponsored)
- **Characteristics:**
  - Long-term access (persistence) for espionage/data theft
  - Use custom tools and zero-day exploits
  - Resource-heavy operations with anti-forensics
  - Typical dwell time: 6–18 months
- **Example:** APT29 (Cozy Bear) targeting governments
- **Key Traits:** Sophisticated, persistent, stealth-focused

### Hacktivists

- **Definition:** Politically/ideologically motivated attackers
- **Characteristics:**
  - Motivation: Political or social causes
  - Use DDoS, defacement, and data leaks for publicity
  - Lower sophistication; rely on commodity tools
  - Opportunistic targeting
- **Example:** DDoS attacks against government/corporate sites
- **Key Traits:** Visible, message-driven, lower skill level

### Organized Crime

- **Definition:** Profit-driven cybercriminal groups
- **Characteristics:**
  - Highly sophisticated operations for scale
  - Use botnets, ransomware, and financial fraud
  - Well-organized and business-like
  - High financial impact
- **Example:** REvil ransomware gangs
- **Key Traits:** Profit-motivated, well-funded, scalable

### Nation-State

- **Definition:** Government-backed threat actors
- **Characteristics:**
  - Strategic motivation (espionage, sabotage, geopolitics)
  - Highest resource availability
  - Custom malware and supply-chain attacks
  - Most sophisticated capabilities
- **Example:** Chinese APTs targeting intellectual property theft
- **Key Traits:** Highest sophistication, unlimited resources, state backing

### Script Kiddies

- **Definition:** Novice/inexperienced attackers
- **Characteristics:**
  - Use pre-built tools (e.g., Metasploit, public exploits)
  - Opportunistic; low sophistication
  - No deep technical knowledge
  - Often attention-seeking
- **Example:** Running automated vulnerability scanners without understanding attacks
- **Key Traits:** Low skill, low threat, high noise

### Insider Threats

- **Definition:** Authorized users abusing their access
- **Types:**

  **Intentional (Malicious):**
  - Malicious data theft or sabotage
  - Motivations: Revenge, greed, ideological
  - Example: Disgruntled employee stealing proprietary data

  **Unintentional (Accidental):**
  - Accidental exposure through mistakes
  - Example: Employee falling for phishing; sharing credentials
  - Often due to lack of security awareness

- **Key Traits:** Internal access, high damage potential, hard to detect

### Supply Chain

- **Definition:** Attacks on vendors/suppliers to infiltrate target organizations
- **Characteristics:**
  - Compromise updates, firmware, or software
  - Exploit trust relationships
  - High impact due to wide distribution
  - Advanced actors (APT, Nation-State)
- **Example:** SolarWinds Orion supply-chain compromise (2020)
- **Key Traits:** Indirect access, high reach, trust-based

### Threat Actor Comparison Table

| Actor Type | Motivation | Sophistication | Common Tactics | Detection Difficulty |
|------------|-----------|-----------------|-----------------|----------------------|
| **APT** | Espionage | High | Persistence, C2, lateral movement | High |
| **Hacktivist** | Ideology | Medium | DDoS, defacement, leaks | Medium |
| **Organized Crime** | Profit | High | Ransomware, fraud, extortion | High |
| **Nation-State** | Strategic | Highest | Zero-days, supply chain, diplomacy | Highest |
| **Script Kiddie** | Thrill/Attention | Low | Scripted exploits, scanning | Low |
| **Insider (Intentional)** | Revenge/Greed | Varies | Privilege abuse, data theft | Medium–High |
| **Insider (Unintentional)** | Accident | N/A | Phishing falls, misconfiguration | Low |
| **Supply Chain** | Access/Reach | High | Firmware tampering, update poisoning | Very High |

### Exam Tip
- **APT/Nation-State** = stealthy, long-term, persistent
- **Script Kiddie** = basic tools, high noise, low impact
- **Insider** = internal access, high damage
- **Supply Chain** = trust-based, wide impact

---

## Tactics, Techniques, and Procedures (TTPs)

**TTPs** describe the behaviors and patterns of adversaries. They are hierarchical and complementary.

### TTP Breakdown

**Tactics: "Why?"**
- High-level goals/objectives of an adversary
- Answer the question: What is the attacker trying to achieve?
- Examples: Initial Access, Persistence, Lateral Movement, Data Exfiltration, Defense Evasion
- Usually 10–15 per framework

**Techniques: "How?"**
- Specific methods used to achieve a tactic
- Answer the question: What method does the attacker use?
- Examples: Phishing (Initial Access), Scheduled Task (Persistence), Pass-the-Hash (Lateral Movement)
- One tactic typically has multiple techniques

**Procedures: "Specific Details"**
- Exact implementation or variation of a technique
- Answer the question: How specifically does the attacker implement this?
- Examples: Spear-phishing with a malicious PDF, PowerShell scheduled task creation, Windows credential extraction via LSASS dump
- Procedure = Technique + Implementation details

### Example: APT29 Attack Chain

| Level | Example | Description |
|-------|---------|-------------|
| **Tactic** | Initial Access | Establish first foothold in target network |
| **Technique** | Phishing / Spear-Phishing | Send targeted email with malicious attachment |
| **Procedure** | Spear-phishing with Office macro-enabled document | Send email to CFO with "Q4 Budget.docm" containing hidden macro that downloads Cobalt Strike |

### Usage in Defense

1. **Intelligence Analysts** profile TTPs from threat reports
2. **Threat Hunters** use TTP profiles as hunting hypotheses
3. **Detection Engineers** create rules to detect TTP execution
4. **Incident Responders** map discovered IOCs to TTPs

### MITRE ATT&CK Framework

- Industry standard TTP taxonomy
- Organizes techniques by tactic
- Includes real-world examples
- Used for: Threat modeling, red-team planning, detection engineering

### Exam Tip
**TTPs flow:** Intelligence (TTP profile) → Hunting (hypothesis based on TTP) → Detection (IOC rules)

---

## Confidence Levels & Assessment

**Confidence Level** (or **Credibility Rating**) assesses the reliability of threat intelligence. High confidence ≠ immediate action; it means act faster with fewer caveats.

### Three Assessment Dimensions

**1. Timeliness: How current?**
- Recent intelligence is more actionable
- Old/stale data may be irrelevant (e.g., expired IOCs, patched vulnerabilities)
- Example: 0-day IOC (hours old) vs. 2-year-old malware hash

**2. Relevancy: Does it match your environment?**
- Is the threat applicable to your organization's technology stack?
- Example: Linux malware irrelevant for Windows-only organization; iOS exploits irrelevant for Android-focused shop
- Relevancy depends on: Industry, infrastructure, asset types, geography

**3. Accuracy: Is it correct & reliable?**
- Single source = lower confidence
- Multiple independent sources confirming = higher confidence
- Proven track record of source = higher confidence
- Example: Accurate vendor (CrowdStrike) vs. anonymous blog = higher vs. lower confidence

### Admiralty Scale (1–6)

| Rating | Confidence | Interpretation |
|--------|-----------|-----------------|
| **1** | Confirmed | Multiple independent reliable sources agree |
| **2** | Probably True | Several credible sources; minor conflicts |
| **3** | Possibly True | Single credible source or multiple weak sources |
| **4** | Doubtful | Significant contradictions; weak sourcing |
| **5** | Improbable | Directly contradicts known information |
| **6** | Speculation | Unverified; theoretical/rumor |

### Usage Guidelines

- **High Confidence (1–2):** Act quickly; use for immediate detection/blocking
- **Medium Confidence (3–4):** Investigate further; add context; prioritize but verify
- **Low Confidence (5–6):** Background awareness; requires significant validation before action

### Exam Tip
**Low confidence = investigate further; High confidence = act quickly. Always consider TRA (Timeliness, Relevancy, Accuracy).**

---

## Collection Methods and Sources

### Open Source Intelligence (OSINT)

**Definition:** Free, publicly available threat intelligence

**Types:**

| Source | Description | Speed | Accuracy | Cost |
|--------|-------------|-------|----------|------|
| **Social Media** | Twitter, Reddit, Facebook for real-time trends/campaign tracking | Fast | Medium | Free |
| **Blogs/Forums** | Security vendor blogs (Krebs, Malwarebytes), expert forums (SANS ISC) | Medium | Medium–High | Free |
| **Government Bulletins** | Alerts from CISA, US-CERT, FBI | Medium | High | Free |
| **CERT/CSIRT Reports** | Incident reports from cert.org, ICS-CERT | Medium | High | Free |
| **Deep/Dark Web Monitoring** | TOR forums, dark web marketplaces (high-risk, requires tools) | Slow | Medium | Free–Paid |

**Characteristics:**
- Broad coverage; includes global trends
- Fast aggregation and sharing
- May contain noise/misinformation
- Requires curation and vetting

### Closed Source Intelligence

**Definition:** Restricted, paid, or proprietary threat intelligence

**Types:**

| Source | Description | Speed | Accuracy | Cost |
|--------|-------------|-------|----------|------|
| **Paid Feeds** | Commercial feeds (CrowdStrike, Recorded Future, ThreatStream) | Very Fast | Very High | Expensive |
| **ISACs/Information Sharing Orgs** | Sector-specific (FS-ISAC for finance, H-ISAC for healthcare, EE-ISAC for energy) | Medium | High | Membership Fee |
| **Internal Sources** | Logs, EDR telemetry, endpoint data from your own infrastructure | Very Fast | Highest | Internal Cost |
| **Law Enforcement** | FBI, Secret Service, international partners (limited sharing) | Variable | High | Partner arrangement |

**Characteristics:**
- Precise, curated, validated intelligence
- Proprietary insights and early warnings
- Expensive; requires subscription/partnership
- Faster than OSINT; higher confidence

### Strategic vs. Tactical Intelligence

| Dimension | Strategic | Tactical |
|-----------|-----------|----------|
| **Scope** | Big-picture trends, actor motivations, geopolitical | Specific campaigns, IOCs, technical indicators |
| **Sources** | Vendor reports, threat feeds, industry analysis | SIEM/EDR logs, incident data, IOC databases |
| **Audience** | C-level, risk management | SOC, incident response, hunters |
| **Timeliness** | Medium–Slow | Very Fast |
| **Action** | Policy/budget/hiring decisions | Block, alert, isolate, investigate |

### Exam Tip
**OSINT** = broad/fast/free; **Closed** = precise/expensive; **Internal** = gold standard (most relevant).

---

## Threat Intelligence Sharing

Threat intelligence is most valuable when shared across the organization and with partners.

### Functions That Benefit from Intelligence Sharing

**Incident Response (IR)**
- Use: IOCs speed triage and remediation
- Example: IOC feed updated → SIEM rules auto-block malicious IPs/domains
- Impact: Faster containment

**Vulnerability Management**
- Use: Prioritize vulnerabilities actively exploited in the wild
- Example: Intelligence reports CVE-2024-1234 used in campaigns → prioritize patching
- Impact: Risk reduction

**Risk Management**
- Use: Quantify threat actor capabilities, intent, and likelihood
- Example: "Nation-state APT X targets our sector; uses zero-days" → budget for advanced detection
- Impact: Better risk quantification

**Security Engineering**
- Use: Design controls and architecture to defend against known TTPs
- Example: "Attackers use DGA for C2" → implement DNS monitoring and threat feed correlation
- Impact: Hardened infrastructure

**Detection & Monitoring (SOC/SIEM)**
- Use: Update detection rules, add IOCs to blocklists, tune alerts
- Example: Add malicious domains to firewall/DNS blocklist
- Impact: Prevented intrusions

### Sharing Frameworks

**STIX (Structured Threat Information Expression)**
- Standard format for encoding threat intelligence
- Machine-readable (JSON/XML)
- Represents: Indicators, campaigns, malware, threat actors
- Example: `{"type": "malware", "name": "Emotet", "labels": ["trojan", "banking"]}`

**TAXII (Trusted Automated Exchange of Indicator Information)**
- Protocol for sharing STIX objects
- Server-client model for real-time feeds
- Enables automated subscription to threat feeds

### Benefits of Sharing

- Faster detection/response across organizations
- Reduced blind spots; community resilience
- Economies of scale (shared cost of analysis)
- Cross-organization threat correlation
- Tactical (IR) and strategic (risk) improvements

### Exam Tip
**Sharing reduces blind spots. TTP sharing → faster detection; IOC sharing → faster blocking. Use STIX/TAXII.**

---

## Threat Hunting Fundamentals

**Threat Hunting:** Proactive search for threats already present in the network. **Assumes breach has occurred** and searches for evidence.

### Key Principle
*"Assume the breach."* Hunters operate under the assumption that sophisticated attackers are already in the network, evading detection.

### Core Hunting Workflow

```
Hypothesis Formulation
         ↓
  Profile Threat Actor
         ↓
   Identify TTPs
         ↓
 Reduce Attack Surface
         ↓
   Execute Hunt (Query/Investigate)
         ↓
  Document Findings & Improve Rules
```

### Indicators of Compromise (IOCs)

**Definition:** Technical artifacts or evidence left by attackers

**Types of IOCs:**

| Type | Example | Detection Method |
|------|---------|------------------|
| **IP Address** | `192.0.2.50` (C2 server) | Network logs, SIEM |
| **Domain Name** | `evil.com`, `dga-domain.xyz` | DNS logs, passive DNS |
| **File Hash** | MD5: `d41d8cd98f00b204e9800998ecf8427e` | Endpoint scanning, file reputation |
| **Email Address** | `attacker@phish.com` | Email logs, incident reports |
| **Registry Key** | `HKLM\Software\Microsoft\Malware` | EDR/endpoint scanning |
| **File Path** | `C:\Temp\malware.exe` | Endpoint logs, SIEM |
| **Port & Protocol** | `Port 4444/TCP` (reverse shell) | Network logs |
| **User Agent String** | Custom/suspicious UA | Web logs |
| **SSL Certificate Hash** | SHA1 of C2 cert | Network appliances, SIEM |

### IOC Lifecycle (Collection → Analysis → Application)

**1. Collection**
- Gather raw data from logs, network traffic, endpoints
- Correlate data across multiple sources (SIEM, EDR, network)

**2. Analysis**
- Contextualize and validate IOCs
- Test hypothesis: Does this pattern indicate malicious activity?
- Reduce false positives by cross-referencing threat feeds and baseline behavior

**3. Application**
- Update detection rules in SIEM/EDR/firewall
- Block/quarantine malicious IOCs
- Alert security team for investigation
- Share with threat intelligence team for dissemination

### Threat Hunting Focus Areas

**1. Misconfigurations & Weak Settings**
- Overpermissive file shares, weak access controls
- Unpatched systems, default credentials
- Hunt: Search for unusual access patterns, privilege escalations
- Example Query: "Find accounts accessing sensitive shares outside normal hours"

**2. Isolated Networks (Air-Gapped Systems)**
- Systems without automated monitoring
- Require manual hunting and forensic investigation
- Hunt: Periodic manual review, USB activity logs, physical access logs
- Example: Lab environments, OT networks, legacy systems

**3. Business-Critical Assets/Processes**
- High-value targets (databases, file servers, cloud infrastructure)
- Assume attackers prioritize these for data theft or ransomware
- Hunt: Monitor for unusual activity, failed authentication, data movement
- Example: Finance systems, customer databases, IP repositories

### Active Defense Techniques

**Honeypots & Deception**

**Honeypot:** Decoy system designed to attract and study attackers

**Low-Interaction Honeypots**
- Simulates services (e.g., fake SSH, HTTP server)
- Low resource cost; limited data collection
- Example: Cowrie (SSH honeypot)
- Best for: Rapid detection of scanning/exploitation attempts

**High-Interaction Honeypots**
- Full operating system with real services
- Captures detailed attacker behavior and tools
- High resource and monitoring cost
- Example: Full Windows/Linux VM with monitoring
- Best for: Understanding attacker techniques, malware analysis

**Advantages:**
- Alert on any interaction (low false positives)
- Capture malware, exploit code, attacker tools
- Study attacker behavior without risk to production

### Example Hunting Workflow

**Scenario:** Intelligence indicates APT using DNS tunneling for C2

1. **Hypothesis:** "Attackers are using DNS queries to tunnel C2 traffic to external servers"
2. **Profile Actor:** APT with high sophistication; stealth-focused; targets high-value data
3. **TTPs:** Command & Control, Lateral Movement (using DNS)
4. **Reduce Surface:** Identify systems with unrestricted external DNS resolution
5. **Hunt:** Query SIEM for DNS traffic with unusual entropy/patterns; correlate with process execution
6. **Document:** If found, extract IOCs (domain, IP); update DNS firewall rules; create SIEM detection rule

### Exam Tip
**Hunting = "assume breach." Hypothesis-driven. Uses IOCs from intelligence. Honeypots = active defense.**

---

## Study Tips & Mnemonics

### Actor Classification Mnemonic: **A-H-O-N-S-I-S**

- **A** — Advanced Persistent Threat (APT)
- **H** — Hacktivists
- **O** — Organized Crime
- **N** — Nation-State
- **S** — Script Kiddies
- **I** — Insider Threats
- **S** — Supply Chain

### TTP Breakdown Mnemonic: **W-H-D**

- **W** — Why? = **Tactic** (goal/objective)
- **H** — How? = **Technique** (method)
- **D** — Details? = **Procedure** (specific implementation)

### Confidence Assessment Mnemonic: **T-R-A**

- **T** — Timeliness (How current?)
- **R** — Relevancy (Does it apply to us?)
- **A** — Accuracy (Is it correct?)

### Intelligence Collection Mnemonic: **OSINT → Open (Social/Blogs/Gov/CERT/Deep)**

- **S** — Social Media
- **B** — Blogs/Forums
- **G** — Government Bulletins
- **C** — CERT/CSIRT Reports
- **D** — Deep/Dark Web

**Closed Sources:** **P-I-I** (Paid feeds, ISACs, Internal)

### Intelligence Sharing Recipients Mnemonic: **I-V-R-S-D**

- **I** — Incident Response (IOCs speed triage)
- **V** — Vulnerability Management (prioritize patches)
- **R** — Risk Management (quantify threats)
- **S** — Security Engineering (design controls)
- **D** — Detection/Monitoring (update rules)

### Threat Hunting Process Mnemonic: **H-P-T-R-H-D**

- **H** — Hypothesis formulation
- **P** — Profile threat actor
- **T** — Identify TTPs
- **R** — Reduce attack surface
- **H** — Hunt (execute queries/investigation)
- **D** — Document & improve detection

---

## Key Takeaways

### Intelligence vs. Hunting

| Aspect | Intelligence | Hunting |
|--------|-------------|---------|
| **Stance** | Defensive/Reactive | Offensive/Proactive |
| **Assumption** | May be attacked | Breach has occurred |
| **Data Source** | External feeds, reports | Internal logs, endpoints |
| **Timeline** | Before incident | During/after incident (assumed) |
| **Outcome** | Awareness, IOC feed | Discovered threats, refined rules |

### Threat Actor Quick Reference

- **Most Sophisticated:** Nation-State > APT > Organized Crime
- **Most Visible:** Hacktivists > Script Kiddies
- **Most Damaging:** Nation-State > Supply Chain > Organized Crime
- **Easiest to Detect:** Script Kiddies > Hacktivists > Insider (Unintentional)
- **Hardest to Detect:** APT > Nation-State > Supply Chain

### Intelligence Sources Quick Reference

- **Fastest:** Internal logs/EDR
- **Cheapest:** OSINT
- **Most Reliable:** Paid closed-source feeds
- **Most Relevant:** Internal data

### Hunting Quick Reference

- **Start:** Hypothesis based on threat intelligence TTP profile
- **Middle:** Query SIEM/EDR for evidence; correlate with IOCs
- **End:** Document findings; update detection rules; share IOCs

---

## Practice Questions

**1. Which threat actor type is most likely to use custom zero-day exploits for long-term espionage?**
- Answer: APT (or Nation-State)

**2. What is the key difference between a Tactic and a Technique in TTPs?**
- Answer: Tactic = goal/why (e.g., persistence); Technique = method/how (e.g., scheduled task)

**3. Intelligence source with high confidence but low speed?**
- Answer: Closed-source paid feeds (CrowdStrike, Recorded Future)

**4. What does low-confidence intelligence require before action?**
- Answer: Further investigation, cross-referencing with other sources, validation

**5. Which organization function uses threat intelligence to prioritize patches?**
- Answer: Vulnerability Management

**6. What is the core assumption of threat hunting?**
- Answer: Breach has already occurred; actively search for evidence

**7. Example of an IOC?**
- Answer: Malicious IP, domain name, file hash, registry key, email address, etc.

**8. What is the purpose of a honeypot in threat hunting?**
- Answer: Attract attackers; study their behavior; collect malware/tools without risk to production

**9. Which intelligence sharing protocol uses STIX/TAXII?**
- Answer: Automated, structured threat intelligence exchange (standards for encoding and sharing)

**10. Threat actor motivated by profit; high sophistication; uses botnets?**
- Answer: Organized Crime

---

## Final Review Checklist

- [ ] Understand the distinction between reactive (Intelligence) and proactive (Hunting)
- [ ] Memorize threat actor types, motivations, and sophistication levels
- [ ] Distinguish TTPs: Tactics (Why) → Techniques (How) → Procedures (Details)
- [ ] Know confidence assessment: Timeliness, Relevancy, Accuracy
- [ ] Categorize sources: OSINT (open/free) vs. Closed (paid/restricted) vs. Internal (gold standard)
- [ ] Understand intelligence sharing benefits and recipients (I-V-R-S-D)
- [ ] Master threat hunting workflow: Hypothesis → Profile → TTP → Hunt → Document
- [ ] Know IOC types and their role in detection rules
- [ ] Understand active defense tools: Honeypots (low/high interaction)
- [ ] Practice scenario mapping: Intel feed → TTP hypothesis → Hunting query → Detection rule

---

## Additional Resources

- **MITRE ATT&CK Framework:** https://attack.mitre.org
- **STIX Documentation:** https://oasis-open.github.io/cti-documentation/
- **CISA Alerts:** https://www.cisa.gov/alerts-and-tips
- **Recorded Future Intelligence:** https://www.recordedfuture.com
- **Krebs on Security:** https://krebsonsecurity.com
- **SANS ISC Diary:** https://isc.sans.edu

---

**Last Updated:** 2024  
**Exam:** CompTIA CySA+ (CS0-003)  
**Status:** Ready for review and integration
