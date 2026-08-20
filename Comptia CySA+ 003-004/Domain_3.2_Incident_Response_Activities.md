# CompTIA CySA+ (CS0-003) Domain 3.2 Study Guide
## Incident Response Activities

---

## Introduction: How Domain 3.2 Fits Together

Domain 3.2 is about what you actually do during an incident: detect it, analyze it, contain it, clean it up, and get back to normal operations—while **preserving evidence and improving the environment**.

For the exam, CompTIA expects you to:
- Recognize where you are in the incident response lifecycle (Detection & Analysis vs Containment/Eradication/Recovery)
- Choose the next best step in realistic scenarios
- Understand the practical meaning of terms like IoC, chain of custody, isolation, remediation, reimaging, and compensating controls

### High-Level Incident Response Flow

```
Detection & Analysis → Containment → Eradication → Recovery → Post-Incident (RCA, lessons learned)
```

---

## 1. Detection and Analysis

### 1.1 Indicators of Compromise (IoC)

#### Definition

An **Indicator of Compromise (IoC)** is any piece of data that suggests a system or network may be compromised or under attack. **IoCs do not prove an attack on their own; they are clues that require validation and context.**

#### Examples of IoCs

- Suspicious outbound connections to known malicious IPs/domains
- Unusual login activity (impossible travel, logins at odd hours, from new countries)
- Unexpected services/ports open (e.g., high-numbered ports listening suddenly)
- New or modified system files (especially binaries/config files/logs)
- Spikes in DNS queries to strange domains, large outbound data transfers
- AV/EDR alerts, SIEM correlation alerts

#### How IoCs Are Implemented in Practice

**Collection:**
- From tools: SIEM, EDR, IDS/IPS, firewall logs, application logs, NetFlow, DNS logs
- From threat intelligence feeds: IPs, domains, hashes, URLs, TTPs

**Analysis:**
- Correlate multiple IoCs to avoid false positives (e.g., suspicious login plus anomalous data transfer)
- Compare with baselines (what's normal for that host/user/network segment?)

**Application:**
- Feed IoCs into SIEM rules, IDS signatures, EDR policies, and blocklists
- Use IoC searches (hunts) across environment to find other affected hosts

#### What to Know for the Exam

- IoCs are forensic clues; they may indicate compromise but **require analysis**
- Expect scenario questions like: "Given these logs, which entry is an IoC?" or "What's the next best action after seeing X IoC?"
- Know the difference between **IoC** (evidence of or after compromise) and **IoA** (attack behavior in progress)

---

### 1.2 Evidence Acquisition Concepts

You will see questions that combine incident response and digital forensics. The key is: **collect and preserve evidence in a way that keeps it admissible, trustworthy, and usable.**

#### a) Chain of Custody

**Definition:**
Chain of custody is the **documented history of who collected, handled, transferred, stored, and accessed evidence, and when and where**. It proves that evidence hasn't been tampered with.

**Implementation:**
- Every piece of evidence gets:
  - Unique identifier (ID, serial, hostname, etc.)
  - Description (what it is and where it came from)
  - Date/time of collection (with time zone)
  - Name/role of each handler
- Every transfer or access is logged:
  - From whom → to whom
  - Date/time, purpose, storage location
- Evidence stored in secure, access-controlled locations

**On the Exam:**
- If law enforcement or legal action is possible, expect "document chain of custody" to be the correct next step
- Don't "just hand a disk to someone" or "modify original media" without logging; chain of custody is almost always the best-practice answer

#### b) Validating Data Integrity

**Definition:**
Validating data integrity means **proving that the evidence you collected has not changed since acquisition**. Typically done via cryptographic hashes.

**Implementation:**
- Before analysis:
  - Calculate hash (e.g., SHA-256) of disk images, memory dumps, key files/logs at acquisition
  - Record hashes in the evidence log
- During/after analysis:
  - Recalculate hashes of evidence copies and compare with original
  - If hashes match, integrity is intact; if not, evidence is suspect

**On the Exam:**
- If they ask: "How do you ensure a forensic image hasn't been altered?" → **hashing / validate data integrity**
- Hashing + chain of custody are almost always paired in evidence questions

#### c) Preservation

**Definition:**
Preservation is the **process of acquiring evidence and storing it securely so that it remains intact, accessible, and trustworthy for future analysis or legal use**.

**Implementation:**
- Collect and preserve:
  - **Volatile data first** (RAM, network sessions, running processes)
  - Then non-volatile (disk images, logs, configs, external media)
- Store evidence:
  - In tamper-evident containers/bags when physical
  - On secure servers/storage with strict access controls for digital
- Avoid altering live systems when possible; if you must, document every action

**On the Exam:**
- If a question says "for possible legal case" or "pending investigation," look for:
  - "Preserve the evidence," "acquire a forensic image," "ensure preservation and chain of custody," etc.
- Avoid answers like "reformat," "reboot to clear memory," or "delete logs"

#### d) Legal Hold

**Definition:**
**Legal hold (litigation hold)** is a formal instruction (usually from legal counsel) to preserve potentially relevant data because litigation or regulatory investigation is pending or underway.

**Implementation:**
- Legal issues a written legal hold notice
- Incident responders and IT:
  - Preserve relevant data regardless of normal retention/purge schedules
  - Suspend automatic deletion where necessary (e.g., log rotation, mailbox retention)
  - Create defensible, verifiable copies if needed
- Document all preservation actions

**On the Exam:**
- When you see "pending litigation," "regulatory investigation," "eDiscovery," best answer often involves legal hold plus preservation and chain of custody
- **Do not choose answers that involve destroying or altering data** after a legal hold is in place

---

### 1.3 Data and Log Analysis

#### Definition

Data and log analysis is the **core analytical work of incident response: reviewing logs and data from various sources** to detect, validate, and understand incidents.

#### Key Sources

- **OS logs:** Windows Event Logs, syslog
- **Application logs:** web servers, DBs, custom apps
- **Security devices:** firewalls, IDS/IPS, VPNs, proxies, WAFs
- **Identity sources:** AD, SSO, IAM, MFA logs
- **Network data:** NetFlow, PCAP, DNS logs
- **EDR/AV logs**

#### Implementation Process

**1. Centralize**
- Use a SIEM to aggregate logs from many sources
- Normalize data to common fields (IP, user, event type, timestamp)

**2. Correlate & Filter**
- Build and tune rules to detect:
  - Brute-force, password spraying, impossible travel
  - Unusual port/protocol usage, beaconing, scanning
  - Data exfiltration patterns (large outbound transfers)
- Use queries and dashboards to highlight anomalies

**3. Contextualize**
- Compare to baselines (normal log patterns, typical login times/locations)
- Link logs together: same user, machine, and timestamps

**4. Decide**
- Classify alerts: false positive, benign anomaly, suspicious, confirmed incident
- Use results to inform containment and response decisions

#### On the Exam

- Expect questions asking: "Given these log snippets, what's happening?" or "What's the next step after reviewing this log?"
- **SIEM is almost always the central tool** for correlation and incident detection
- They like patterns: e.g., **multiple failed logins followed by success from new IP** → likely compromise

---

## 2. Containment, Eradication, and Recovery

Once you've determined something bad is really happening, you move from mostly passive analysis to **active defense**.

### 2.1 Scope

#### Definition

Scope is the **extent of the incident—how many systems, accounts, networks, applications, and data sets are affected**.

#### Implementation

- Use IoCs and log searches to identify:
  - All affected hosts, segments, user accounts, applications, and data
- Map out:
  - Which business processes are impacted
  - Which environments (prod, test, dev, cloud, OT/ICS)

#### On the Exam

- If they ask: "Before containment, what must you determine?" → **scope and impact are frequent answers**
- Scope decisions drive how broad your containment and remediation actions must be

---

### 2.2 Impact

#### Definition

Impact is the **effect of the incident on confidentiality, integrity, availability, financial standing, legal/compliance posture, and reputation**.

#### Common Impact Dimensions

- **Functional:** which services are degraded or down
- **Economic:** direct and indirect financial loss
- **Data:** what kind of data was accessed/altered/exfiltrated (PII, PHI, IP, card data)
- **Time:** how long systems/services are unavailable
- **Recoverability:** how hard/long it will take to restore

#### Implementation

- Combine scope with:
  - Data classification
  - Business impact analysis (what this service/data means to the org)
- Use impact to:
  - Prioritize incidents
  - Decide on involvement of leadership, legal, regulators, and law enforcement

#### On the Exam

- Watch for classification questions: "This affected 30% of users' email access" → medium functional impact
- **Impact and scope drive severity level and escalation**

---

### 2.3 Isolation

#### Definition

Isolation is a **containment strategy where you prevent an affected system or component from communicating with other systems** to stop spread or damage.

#### Forms of Isolation

**Network Isolation:**
- Move host to a quarantine VLAN
- Apply firewall rules to block inbound/outbound traffic
- Block certain protocols or destinations

**Account Isolation:**
- Disable or lock accounts suspected of compromise
- Remove group memberships and privileges

**Service Isolation:**
- Stop specific services or application instances
- Take a node out of a cluster or load balancer

#### Implementation

- Use firewall, NAC, EDR, or network segmentation to:
  - Keep attacker contained but possibly still observable (for monitoring)
  - Protect remaining production assets

#### On the Exam

- If they ask how to "prevent lateral movement" or "contain damage," **isolation/segmentation is often correct**
- Know the difference:
  - **Segmentation** – broader network design separation (proactive & reactive)
  - **Isolation** – targeted, usually ad hoc reaction to an ongoing incident
- **Beware "powering off immediately"** as a first step—it can destroy volatile evidence; isolating is usually preferred

---

### 2.4 Remediation

#### Definition

Remediation is the **set of corrective actions taken to fix the root causes and remove the attacker's foothold** so the incident cannot easily recur.

#### Implementation

Based on root cause analysis, remediation could include:
- **Patching** vulnerabilities exploited in the attack
- **Fixing misconfigurations** (open ports, weak ACLs, default creds)
- **Improving authentication** (MFA, password policy, disabling legacy protocols)
- **Updating** firewall/WAF/EDR policies
- **Removing** malicious users, access rights, and backdoors

**Remediation is broader than just "cleaning malware"—it addresses the weaknesses that enabled the incident.**

#### On the Exam

- When asked what to do "to prevent the same incident," think **remediation**:
  - Patch + harden + fix design issues
- It often appears alongside reimaging as part of eradication and recovery

---

### 2.5 Re-imaging

#### Definition

Re-imaging means **wiping a system's storage and reinstalling the OS and applications from a known-good, trusted baseline image**.

#### Why It's Important

- Malware is often stealthy and resilient; relying on AV clean-up can miss rootkits/backdoors
- Re-imaging ensures you remove all malicious artifacts and configuration changes

#### Implementation

1. **Before re-imaging:**
   - Acquire forensic images if needed (for evidence and RCA)

2. **Wipe drive:**
   - Use proper disk wiping tools, not just quick format

3. **Deploy golden image:**
   - A hardened, fully patched baseline OS + standard software stack

4. **Reconfigure:**
   - Restore necessary settings and applications
   - Restore data from backups taken prior to compromise

5. **Validate:**
   - Patch levels, AV/EDR, logging, and monitoring are in place

#### On the Exam

- If the question is about fully purging a compromised system, **re-imaging is usually the best answer**
- They like the tension: "re-image vs remove malware with AV" – **re-imaging wins for assurance**
- Remember: **forensic acquisition should occur before re-imaging** when evidence is needed

---

### 2.6 Compensating Controls

#### Definition

A **compensating control** is an alternative control that provides equivalent or adequate risk reduction when a primary or ideal control is not feasible (e.g., due to legacy systems, uptime requirements, vendor limitations).

#### Examples

**Legacy system can't be patched:**
- Place it on an isolated VLAN behind strict firewall rules
- Add a dedicated reverse proxy or WAF in front of it
- Increase monitoring and logging around it

**Can't implement MFA on an old app:**
- Enforce strong VPN with MFA + network segmentation
- Use strict IP allowlists

#### Implementation

- Identify constraint (e.g., cannot patch without breaking vendor support)
- Assess risk
- Design and document compensating control:
  - What it is, how it mitigates risk, and any residual risk
- Monitor and revisit:
  - Ensure it actually works and is kept up to date

#### On the Exam

- Look for phrases like "system is end-of-life and cannot be patched," "proprietary/legacy system," or "uptime requirement prohibits patching" → **compensating controls**
- Compensating controls reduce risk but do not necessarily fix root cause; they often accompany long-term remediation plans

---

## 3. Summary – How It All Connects

### Detection & Analysis Phase

- Use **IoCs** to suspect compromise
- Use **data/log analysis** (via SIEM, EDR, etc.) to validate and understand it
- When evidence matters, always pair:
  - **Acquisition → Preservation → Chain of custody → Integrity validation → Legal hold** (if applicable)

### Containment, Eradication, and Recovery Phases

- **Determine scope** (what's affected?) and **impact** (how bad?)
- **Contain** via segmentation and isolation to prevent spread and further damage
- **Eradicate** by removing artifacts (malware, accounts, backdoors); often via re-imaging
- **Recover** by restoring systems, services, and data and validating controls
- **Implement remediation** to fix root causes; compensating controls when ideal controls are not feasible

### Sequential Thinking

1. **Detect** something odd (IoCs)
2. **Analyze** logs/data to confirm and understand
3. **Preserve** evidence correctly (chain of custody, integrity)
4. **Determine** scope & impact
5. **Contain** via isolation/segmentation
6. **Eradicate:** remove malware/backdoors; re-image as needed
7. **Recover:** restore services securely
8. **Remediate** underlying issues; apply compensating controls when needed

---

## 4. What to Look Out For on the Exam

### 1. Phase Awareness

- Questions will implicitly test whether you know which phase you're in
- Example: Don't jump to re-image before collecting forensic evidence; don't start remediation before understanding root cause

### 2. Best-Next-Step Style Questions

- You'll often see multiple good actions; you must pick the most appropriate next one
- **After seeing an IoC:** confirm via log analysis before declaring incident or reimaging everything
- **After evidence is collected:** document chain of custody and validate integrity

### 3. Terminology Traps

| Concept | Definition |
|---------|-----------|
| **IoC vs log vs normal event** | IoC is suspicious; log is record; event is documented occurrence |
| **Isolation vs segmentation vs removal** | Isolation = block communications; Removal = completely cut off; Segmentation = network design |
| **Remediation vs reimaging** | Remediation = fix root cause; Reimaging = technical clean slate |
| **Compensating control vs workaround** | Compensating = formally recognized; Workaround = temporary measure |

### 4. Legal/Evidence Hygiene

- **Any mention of legal cases, lawsuits, regulatory investigations** → think:
  - Preserve evidence, legal hold, chain of custody, validate integrity
- **Destroying, wiping, or altering data** before considering legal impact is almost always wrong

### 5. Legacy/High-Uptime Systems

- If they say "cannot be patched" or "downtime is not acceptable," expect:
  - **Compensating controls, additional monitoring, segmentation/isolation**

---

## Quick Reference: Incident Response Checklist

### Detection & Analysis
- ☐ Identify IoCs
- ☐ Correlate logs/data in SIEM
- ☐ Validate findings (avoid false positives)
- ☐ Plan evidence acquisition

### Evidence Preservation (if legal/forensic needed)
- ☐ Acquire forensic images (volatile data first)
- ☐ Calculate and record hashes
- ☐ Document chain of custody
- ☐ Initiate legal hold (if applicable)
- ☐ Store securely with access controls

### Containment
- ☐ Determine scope and impact
- ☐ Isolate affected systems/segments
- ☐ Block lateral movement
- ☐ Preserve evidence

### Eradication
- ☐ Remove malware, backdoors, rogue accounts
- ☐ Re-image compromised systems (after forensic acquisition)
- ☐ Verify removal via scanning/validation

### Recovery
- ☐ Restore systems from clean backups
- ☐ Restore data (post-compromise verified)
- ☐ Validate monitoring/logging is operational
- ☐ Restore to production

### Remediation & Prevention
- ☐ Identify root causes
- ☐ Patch vulnerabilities
- ☐ Fix misconfigurations
- ☐ Implement/review compensating controls for legacy systems
- ☐ Improve authentication and access controls
- ☐ Document lessons learned

---

## Exam Strategy

**For Domain 3.2 questions:**

1. **Identify the incident phase** you're in (Detection, Containment, Eradication, Recovery, or Post-Incident)
2. **Look for constraints** (legal, technical, uptime)
3. **Choose the action** that best addresses the current phase while respecting constraints
4. **Avoid premature actions** (e.g., don't wipe evidence before collecting it)
5. **Remember: evidence first, then cleanup** when legal/forensic needs are present

**Common wrong answers:**
- "Immediately power off the system" (loses evidence)
- "Delete logs and reformat" (destroys evidence, violates legal hold)
- "Skip re-imaging and just run antivirus" (misses persistent malware)
- "Patch without understanding root cause" (treating symptom, not disease)
