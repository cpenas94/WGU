# CompTIA CySA+ (CS0-003) Domain 3.1 Study Guide
## Attack Methodology Frameworks and Analysis

---

## Domain 3.1 Overview

### Objective

Be able to explain and differentiate major attack methodology frameworks and understand how they support real-world detection, analysis, and response activities.

### Key Learning Points

You're not expected to memorize every detail from the original publications, but you **must:**
- Know what each framework is for
- Understand its structure and main components
- Be able to explain where it fits in security operations and incident response
- Recognize how exam questions might test your understanding (definition vs. usage vs. comparison)

### Frameworks You Must Know

1. Cyber Kill Chain
2. Diamond Model of Intrusion Analysis
3. MITRE ATT&CK
4. OSSTMM (Open Source Security Testing Methodology Manual)
5. OWASP Web Security Testing Guide

---

## 1. Cyber Kill Chain

### 1.1 What It Is

The Cyber Kill Chain is a phase-based model that describes the lifecycle of a cyberattack from initial reconnaissance through achieving the attacker's objectives. It was developed by **Lockheed Martin**.

### 1.2 Key Phases (7 Stages)

| Phase | Name | Description |
|-------|------|-------------|
| **1** | **Reconnaissance** | Attacker gathers information about the target (OSINT, scanning, etc.) |
| **2** | **Weaponization** | Attacker creates or selects a malicious payload + exploit (e.g., malware-laced PDF) |
| **3** | **Delivery** | Payload is delivered to the target (email attachment, USB, drive-by website) |
| **4** | **Exploitation** | Vulnerability is exploited and malicious code is executed |
| **5** | **Installation** | Malware or backdoor is installed for persistence |
| **6** | **Command and Control (C2)** | Compromised system connects back to attacker for control |
| **7** | **Actions on Objectives** | Attacker performs final goals: data theft, destruction, lateral movement, etc. |

### 1.3 How It's Implemented

**In practice:**
- Used to map incidents to a lifecycle: "We detected the attack during Delivery" or "We stopped it at C2"
- Helps define defensive controls at each phase:
  - **Recon:** OSINT monitoring, attack surface reduction
  - **Delivery:** email security, web filters
  - **Exploitation/Installation:** endpoint protection, patching, EDR
  - **C2/Actions:** network monitoring, DLP, anomaly detection
- Used in threat hunting: start hunting indicators at early phases (e.g., unusual scanning → recon)

**In an incident response playbook:**
- Steps in the playbook can be explicitly tied to kill chain phases
- Example: "For phishing attacks, focus controls around Delivery and Exploitation stages"

### 1.4 Exam Watch Points

**You must know:**
- The 7 stages, in order, and what happens in each
- How to map described actions to kill chain phases

**Typical exam questions:**
- "What phase is installing a backdoor?" → **Installation**
- "What phase is data exfiltration?" → **Actions on Objectives**
- Scenario questions where you map a described action to a kill chain phase

**Important context:**
- Be aware of the criticism: It's seen as perimeter/malware-focused and not ideal for all threat types (e.g., insider threats, purely web-application logic abuse)
- It's more focused on traditional intrusion campaigns

---

## 2. Diamond Model of Intrusion Analysis

### 2.1 What It Is

The Diamond Model is a structured way to analyze and describe an intrusion event by relating **four key features:**
- **Adversary**
- **Infrastructure**
- **Capability**
- **Victim**

Each intrusion event is represented as a "diamond" connecting these four vertices.

### 2.2 Core Elements

| Element | Definition | Examples |
|---------|-----------|----------|
| **Adversary** | The attacker or threat actor | APT group, criminal gang, insider |
| **Infrastructure** | Systems and services used by the adversary | C2 servers, domains, hosting providers, compromised systems |
| **Capability** | Tools and techniques used | Malware, exploits, phishing kits, RATs |
| **Victim** | The target organization, systems, or users | Corporate employee, web server, entire industry vertical |

### 2.3 Additional Features

Each event can have:
- **Meta-features:** time, phase, result, and confidence level
- **Linking:** Multiple events can be linked into activity threads and campaigns

### 2.4 How It's Implemented

**In practice:**

**Used by threat intel and IR teams to:**
- **Pivot along vertices:**
  - From one infrastructure (IP) to see other victims
  - From one adversary to find other infrastructure or capabilities used
- **Build attack graphs and campaign views**

**Good for attribution and pattern analysis:**
- "This IP + this malware + this targeting profile strongly suggest group X"

**In tools:**
- Underpins automated threat intel platforms that correlate IoCs into related events and campaigns

### 2.5 Exam Watch Points

**Know:**
- The four vertices and what each represents
- The idea of pivoting along vertices (e.g., from victim to infrastructure)

**Typical exam questions:**
- "In the Diamond Model, which element is the malware itself?" → **Capability**
- "Which element is the compromised web server used as C2?" → **Infrastructure**

**Remember:**
- It's more about **analysis and attribution** than "step-by-step attack phases"
- Differs from Kill Chain: Diamond is for correlating related events; Kill Chain is for sequential phases

---

## 3. MITRE ATT&CK

### 3.1 What It Is

**MITRE ATT&CK** is a knowledge base of **adversary tactics, techniques, and procedures (TTPs)**. It's organized into matrices, most notably the Enterprise matrix, and is based on real-world adversary behavior.

### 3.2 Core Components

**Tactics – The high-level goals of the attacker (the "why")**

Examples: 
- Initial Access
- Execution
- Persistence
- Privilege Escalation
- Defense Evasion
- Credential Access
- Discovery
- Lateral Movement
- Collection
- Command & Control (C2)
- Exfiltration
- Impact

**Techniques – The ways attackers achieve those goals (the "how")**

Example:
- Tactic: Credential Access → Techniques: Brute force, credential dumping, keylogging

**Procedures – Actual, concrete implementations**
- Specific tools, command lines, exact usage patterns

**Additional objects:**
- Data sources, Mitigations, Groups, Software, Campaigns

### 3.3 How It's Implemented

**Threat hunting:**
- Form a hypothesis: "Adversaries often use Pass-the-Hash (Lateral Movement). Let's search our logs for corresponding indicators."

**Detection engineering:**
- Map existing detections to ATT&CK techniques
- Identify coverage gaps

**IR and reporting:**
- Post-incident, map observed behavior to ATT&CK tactics/techniques
- Example: "The adversary used T1078 (Valid Accounts) under the Initial Access tactic"

**Adversary emulation:**
- Red teams simulate specific adversary groups based on ATT&CK technique lists

### 3.4 Exam Watch Points

**Know that ATT&CK is:**
- **Behavior-oriented (TTPs)**, not just vulnerabilities or signatures
- **Organized by tactics (columns) and techniques (rows)**

**Understand how it differs from the Kill Chain:**
- Kill Chain is a **linear lifecycle** (1→2→3...→7)
- ATT&CK is a **matrix of behaviors** – sequence is **flexible**

**Typical exam questions:**
- "Which framework provides a database of adversary TTPs mapped by tactic?" → **MITRE ATT&CK**
- "Which framework is best suited to map and compare threat group behaviors?" → **MITRE ATT&CK**

**Remember:**
- You don't have to memorize all tactics, but be comfortable with the concept of tactics vs. techniques
- Be familiar with typical examples: Initial Access, Lateral Movement, etc.

---

## 4. OSSTMM (Open Source Security Testing Methodology Manual)

### 4.1 What It Is

**OSSTMM** is a security testing methodology that provides a **structured way to perform practical, measurable security tests**. It's **broader than just cyber**—it includes operational, human, and physical aspects.

### 4.2 Key Characteristics

- **Emphasizes fact-based, repeatable, measurable testing**
- **Covers multiple domains:**
  - Human Security Testing (social engineering, awareness)
  - Physical Security Testing (locks, barriers, cameras)
  - Wireless Security Testing
  - Telecommunications Security Testing
  - Data Network Security Testing
- **Uses structured workflows and metrics** (e.g., risk scores) to express results

### 4.3 How It's Implemented

**Used as a penetration testing and security assessment methodology:**
- Define scope (humans, physical sites, networks)
- Carry out tests per OSSTMM procedures
- Produce a structured **Security Test Audit Report (STAR)** and/or RAV-like metrics

**Helps ensure:**
- Consistency across different testers and assessments
- Coverage across operational, physical, and technical controls

### 4.4 Exam Watch Points

**Recognize OSSTMM as:**
- **A testing methodology**, not a threat-behavior catalogue
- **Covers operational/physical/human security** as well as network

**Typical exam angle:**
- "Which framework would you reference to design a comprehensive security testing methodology, including physical and human controls?" → **OSSTMM**

**Distinguish from:**
- Kill Chain/ATT&CK → focused on attack behavior
- OWASP Testing Guide → focused specifically on web applications

---

## 5. OWASP Web Security Testing Guide

### 5.1 What It Is

The **OWASP Web Security Testing Guide (WSTG)** is a methodology for testing the security of web applications. It's developed and maintained by **OWASP**.

**Note:** It's related to, but distinct from, the **OWASP Top 10** (which lists the most critical web app risks).

### 5.2 Structure and Areas

The guide provides a structured approach to test areas such as:

1. **Information Gathering**
2. **Configuration and Deployment Management Testing**
3. **Identity Management Testing**
4. **Authentication Testing**
5. **Authorization Testing / Access Control**
6. **Input Validation Testing** (e.g., SQL injection, XSS)
7. **Error Handling and Logging**
8. **Cryptography Testing**
9. **Business Logic Testing**
10. **Client-side Testing**
11. **Web Services Testing**
12. **Mobile Testing**

### 5.3 How It's Implemented

**Used by appsec testers and auditors to:**
- Define the scope of the test
- Walk through test cases in each section (e.g., test for XSS, CSRF, SQL injection)

**Often paired with tools:**
- Interception proxies (Burp Suite, ZAP)
- Specialized scanners (e.g., Nikto, Arachni)

**Also used to validate and measure secure development:**
- Teams use it as a checklist before going to production

### 5.4 Exam Watch Points

**Know that OWASP Testing Guide is:**
- **Web-application specific**
- **A testing methodology**, not just a vulnerability list

**Typical exam questions:**
- "Which framework would you use to structure testing for web applications?" → **OWASP Testing Guide**
- "Which resource focuses on SQL injection, XSS, access control, and other web app issues?" → **OWASP Testing Guide / OWASP Top 10**

**Be able to distinguish:**
- **OWASP Top 10:** risk list (most critical vulnerabilities)
- **OWASP Testing Guide:** how to test for those (and more) vulnerabilities

---

## 6. Comparing the Frameworks (High-Yield for Exam)

### 6.1 By Purpose

| Framework | Purpose | Use Case |
|-----------|---------|----------|
| **Cyber Kill Chain** | Models the phases of an attack from recon to exfiltration | Mapping, detection, and disruption of campaigns |
| **Diamond Model** | Models intrusion events and relationships (adversary, capability, infrastructure, victim) | Analysis, correlation, and attribution |
| **MITRE ATT&CK** | Provides a detailed catalogue of TTPs | Detection engineering, threat hunting, adversary emulation |
| **OSSTMM** | General security testing methodology covering physical, human, wireless, telecom, and networks | Comprehensive security assessments |
| **OWASP Testing Guide** | Web application testing methodology | Web app penetration testing and secure development |

### 6.2 Quick Decision Matrix

**When you see exam language, think:**

| Exam Language | Framework |
|---------------|-----------|
| "Map TTPs, compare threat groups, build detections" | **MITRE ATT&CK** |
| "Linear steps from recon through data theft" | **Cyber Kill Chain** |
| "Understand how adversary, capability, infra, and victim relate" | **Diamond Model** |
| "Structured methodology for testing physical and network security" | **OSSTMM** |
| "Testing web app security (SQLi, XSS, auth, access control)" | **OWASP Testing Guide** |

### 6.3 Typical Exam Gotchas

**Don't confuse:**
- **ATT&CK** (TTPs, tactics/techniques matrix) vs. **Kill Chain** (linear phases)
- **OSSTMM** (broad testing methodology) vs. **OWASP Testing Guide** (web-only)
- **OWASP Top 10** (risk list) vs. **OWASP Testing Guide** (testing steps)

---

## Framework Comparison Deep Dive

### Kill Chain vs. ATT&CK

| Aspect | Cyber Kill Chain | MITRE ATT&CK |
|--------|------------------|-------------|
| **Structure** | Linear, 7-phase lifecycle | Matrix of tactics/techniques |
| **Focus** | Sequential attack progression | Behavioral techniques (flexible order) |
| **Use Case** | Map campaign flow, disrupt at phases | Detect techniques, threat hunting, attribution |
| **Flexibility** | Attackers follow phases in order | Attackers may use techniques in any order |

### Diamond Model vs. Kill Chain

| Aspect | Diamond Model | Cyber Kill Chain |
|--------|---------------|-----------------|
| **Focus** | Event relationships and correlation | Attack lifecycle phases |
| **Key Elements** | Adversary, Infrastructure, Capability, Victim | Reconnaissance through Actions on Objectives |
| **Use Case** | Attribution, pivot analysis | Disruption strategy |

### OSSTMM vs. OWASP Testing Guide

| Aspect | OSSTMM | OWASP Testing Guide |
|--------|--------|-------------------|
| **Scope** | Broad (physical, human, network, wireless, telecom) | Web applications only |
| **Type** | General testing methodology | Web app-specific methodology |
| **Output** | STAR, risk metrics | Vulnerability findings |

---

## How to Study These for the Exam

### Master These Facts

1. **Cyber Kill Chain Phases** — Memorize all 7 phases in order and be able to match actions to phases
2. **Diamond Model's Four Vertices** — Know what each represents and how to pivot
3. **MITRE ATT&CK Structure** — Understand tactics vs. techniques and how it's used
4. **OSSTMM vs. OWASP** — Remember OSSTMM is broad; OWASP is web-focused

### Practice Mental Exercise

For each scenario question, ask yourself:
- **"Which framework is most appropriate for this situation?"**

If you can comfortably:
- Explain each framework in your own words
- Pick the right one in short scenarios
- Identify what element each framework emphasizes

You're in good shape for Domain 3.1.

---

## Quick Reference: Framework Cheat Sheet

### Cyber Kill Chain
- **Linear, 7 phases:** Recon → Weaponization → Delivery → Exploitation → Installation → C2 → Actions
- **Use:** Map incidents to phases, define defensive controls
- **Exam tip:** "What phase is X action?"

### Diamond Model
- **Four vertices:** Adversary, Infrastructure, Capability, Victim
- **Use:** Correlate events, pivot analysis, attribution
- **Exam tip:** "Which element is X?"

### MITRE ATT&CK
- **Structure:** Tactics (goals) contain Techniques (methods)
- **Use:** Threat hunting, detection engineering, emulation
- **Exam tip:** "Which framework lists TTPs?" or "Compare threat groups?"

### OSSTMM
- **Scope:** Physical, Human, Wireless, Telecom, Network
- **Use:** Comprehensive security testing methodology
- **Exam tip:** "Broad testing methodology including physical?"

### OWASP Testing Guide
- **Scope:** Web applications only
- **Use:** Web app penetration testing, secure development
- **Exam tip:** "Testing web app security?"

---

## Exam Strategy

**When faced with a framework question:**

1. **Identify the question type:**
   - Defining a framework? → Give definition + components
   - Using a framework? → Explain practical application
   - Comparing frameworks? → Use the decision matrix

2. **Eliminate wrong answers:**
   - Kill Chain? (Not for correlation/attribution → eliminate Diamond)
   - Web app focused? (Not OSSTMM → eliminate OSSTMM)
   - Tactics/techniques matrix? (Not Kill Chain → eliminate Kill Chain)

3. **Choose the best fit:**
   - Most specific match wins
   - If multiple seem right, consider the **primary use case** in the question
