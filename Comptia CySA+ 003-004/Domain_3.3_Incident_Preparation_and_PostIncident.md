# CompTIA CySA+ (CS0-003) Domain 3.3 Study Guide
## Incident Preparation and Post-Incident Activities

---

## 1. Introduction: Where 3.3 Fits in the Big Picture

CompTIA's incident management lifecycle (mirroring NIST SP 800-61) has five phases:

1. **Preparation**
2. **Detection & Analysis**
3. **Containment**
4. **Eradication & Recovery**
5. **Post-incident Activity**

**Domain 3.3 focuses on (1) and (5):**
- How you prepare before anything bad happens
- What you do afterward to learn and improve

### These phases touch every other domain:
- **Security Operations (1.x):** SIEM, SOC procedures, logging, automation
- **Vulnerability Management (2.x):** risk management, patching, attack surface management
- **Reporting & Communication (4.x):** stakeholder communication, metrics, lessons learned, incident reports

**If you think of your job as a loop, 3.3 is the "design & improve the system" part, not the "put out today's fire" part.**

---

## 2. Preparation Phase

### 2.1 Incident Response Plan (IRP)

#### Definition

A formal, written document that describes:
- What a security incident is
- Who is on the CSIRT/IR team and what authority they have
- The phases of response and high-level procedures
- Severity classifications and escalation paths
- Communication and reporting expectations

**Think:** "Master playbook" for the whole incident response program.

#### Implementation

**1. Policy Foundation**
- Draft an IR policy approved by senior leadership (often CEO/CIO)
- Define scope: Which systems? Which business units? Which types of incidents?

**2. Define Roles & Responsibilities**
- IR manager/lead, incident handlers, forensic analyst, SOC analysts
- Non-technical roles: legal, HR, PR, senior executives, system owners

**3. Severity and Classification**
- Define impact levels (high/medium/low, functional & economic impact)
- Define attack vectors (web, email, attrition, loss/theft, improper usage, impersonation, etc.)

**4. Integration with BC/DR and Governance**
- Align with business continuity and disaster recovery plans
- Tie into risk management and change control processes (domain 2)

#### Cross-Domain Correlations

- **Domain 1 (Security Operations):** IRP references SIEM, EDR, network architecture, logging
- **Domain 4 (Reporting & Communication):** IRP defines who talks to whom, when, and how

#### Exam Watchpoints

- **IRP vs playbook vs procedure:**
  - IRP = overarching plan
  - Playbooks = scenario-specific
  - Procedures = step-by-step tasks
- IRP is not detailed commands; it's policy and structure

---

### 2.2 Tools

#### Definition

The technical and non-technical resources you stage before an incident:
- **Security tools:** SIEM, EDR, IDS/IPS, netflow analyzers, vulnerability scanners
- **Forensic tools:** imaging tools, write blockers, analysis suites
- **Infrastructure:** forensic workstations, isolated networks, storage for evidence
- **Support tools:** ticketing systems, incident management systems, secure comms

#### Implementation

**1. Tool Selection and Integration**
- Standardize on tools that can integrate (via APIs, webhooks, SOAR)
- Tune SIEM rules and data sources as part of preparation

**2. Build an IR Toolkit**
- Pre-build forensic workstations
- Prepare bootable media with trusted tools, hashes pre-recorded
- Ensure capacity for centralized logging and log retention

**3. Runbooks & Automation**
- Identify tasks that can be automated (enrichment, blocking IPs, isolating hosts)
- Use SOAR or scripting to run those automatically from alerts

#### Cross-Domain Correlations

- **Domain 1.3:** "Given a scenario, use appropriate tools…" – the same tools you learn there are the ones you stage here
- **Domain 2:** Vulnerability scanners and configuration management tools feed into IR (e.g., confirming patch status)

#### Exam Watchpoints

- Questions may give you a bunch of tools and ask which belong in preparation vs which are used during containment or forensics
- Preparation is about **provisioning & integrating** them, not actively running them during a live incident

---

### 2.3 Playbooks

#### Definition

A playbook is a scenario-specific, step-by-step response guide for a given incident type:
- Ransomware
- Phishing/social engineering
- Data exfiltration
- Web app compromise

**Think:** "If X happens, follow these steps."

#### Implementation

**1. Identify Common/High-Impact Scenarios**
- Use threat intelligence, past incidents, risk assessments to pick scenarios

**2. Structure the Playbook**
- **Trigger/entry conditions:** what starts this playbook
- **Actions for each phase:** detection/analysis, containment, eradication, recovery
- **Communication steps:** who must be notified, when
- **Evidence collection and preservation steps**

**3. Automate Where Possible**
- Convert parts of playbooks into runbooks or SOAR workflows
- Example: automatically isolate endpoint, enrich alert with threat intel, open ticket

#### Cross-Domain Correlations

- **Domain 1.5 (Process Improvement):** playbooks embody standardized, repeatable processes
- **Domain 4.2:** playbooks often embed communication templates and reporting requirements

#### Exam Watchpoints

**Playbooks are not the same as the IRP:**
- **IRP** = framework & governance
- **Playbook** = detailed steps for a specific incident type
- Playbooks can be physical (paper) as well as digital – often referenced in questions about resilience during attacks

---

### 2.4 Tabletop Exercises

#### Definition

A **discussion-based simulation** of an incident with no live systems involved.
- Participants walk through a scenario, explaining what they would do
- Focus on process, communication, and decision-making

#### Implementation

**1. Plan the Scenario**
- Pick a realistic incident (e.g., ransomware, insider misuse, data breach)
- Define injects: new information that complicates the scenario (e.g., media inquiries while responding)

**2. Gather Stakeholders**
- Include IR team, IT ops, legal, PR, management, possibly external partners

**3. Facilitate and Document**
- A neutral facilitator presents the scenario step by step
- Capture decisions, gaps, timing, confusion points

**4. Feed Results Back into Improvements**
- Update IRP, playbooks, training, and technical controls

#### Cross-Domain Correlations

- **Domain 3.2 & 3.3:** Tabletops test both preparation and the overall IR lifecycle
- **Domain 4:** Tabletops often surface communication and reporting issues

#### Exam Watchpoints

**Be able to distinguish between:**
- **Tabletop** = discussion only
- **Walkthrough** = step-through procedures, still no real systems
- **Full-scale exercise / Live fire / Pen test** = real systems involved

---

### 2.5 Training

#### Definition

Activities that ensure everyone knows what to do when an incident happens, and can actually do it:
- **Technical training:** IR team, SOC analysts
- **Awareness training:** general staff recognizing phishing, reporting suspicious activity
- **Cross-functional training:** HR, legal, PR, business managers

#### Implementation

**1. Role-Based Training**
- **IR staff:** tools, forensics basics, containment procedures
- **Help desk:** triage tickets that might be incidents
- **End users:** report phishing, not ignoring warnings

**2. Protocols and Soft Skills**
- Teach staff to stay calm, follow chain of command, and collaborate under stress
- Train on reporting procedures, escalation thresholds, and use of secure communications

**3. Tie Training to Exercises**
- Use tabletops and walkthroughs as training mechanisms
- After real incidents, update training based on lessons learned

#### Cross-Domain Correlations

- **Domain 1 & 2:** Training on secure operations and vulnerability management
- **Domain 4:** Training about communication with media, regulators, customers

#### Exam Watchpoints

- **Training is explicitly called out in the Preparation phase**
- If the question asks what to do before incidents to improve IR capability, "training" is almost always a correct part of the answer

---

### 2.6 Business Continuity (BC) / Disaster Recovery (DR)

#### Definitions

**Business Continuity (BC):**
How the organization continues critical operations during and after a disruptive event (including cyber incidents).

**Disaster Recovery (DR):**
Focused on restoring IT systems and data quickly after a disruption (short-term, technical).

#### Implementation

**1. Identify Critical Systems & Processes**
- Use Business Impact Analysis (BIA) to find what is mission-critical
- Map incidents that cross the line from "IR" into "disaster"

**2. Define Strategies**
- **Recovery time & point objectives (RTO/RPO)**
- **Alternate sites:** hot / warm / cold
- **Backup schemes** and offline/off-site storage

**3. Integrate with IR**
- IR plan spells out when to escalate an incident to BC/DR activation (e.g., ransomware taking out all desktops)
- Ensure BC/DR exercises include cyber-incident scenarios

#### Cross-Domain Correlations

- **Domain 2 (Risk Management):** BC/DR decisions are risk management decisions
- **Domain 4:** BC/DR has heavy regulatory reporting and stakeholder communication requirements

#### Exam Watchpoints

- **BC = keep business running; DR = restore IT quickly. Don't invert them.**
- Some scenarios start as a "small" incident and become a disaster when impact and scope grow—know that escalation path

---

## 3. Post-Incident Activity

Now we're in the **"learn and improve"** phase.

### 3.1 Forensic Analysis

#### Definition

The systematic collection, preservation, and examination of digital evidence to:
- Understand what happened (timeline, actions)
- Potentially support legal proceedings

**For CySA+, you're expected to know the process and where it fits into IR, not become a full forensics expert.**

#### Typical Process

**1. Evidence Acquisition**
- Forensically image disks, capture memory, collect logs
- Respect order of volatility (RAM before disk, etc.)
- Use write blockers and hashing to preserve integrity

**2. Preservation & Chain of Custody**
- Document who collected what, when, where it's stored, and every transfer
- This is crucial if there's any chance of legal action

**3. Analysis**
- Reconstruct actions, identify malware, trace C2 connections, find exfiltrated data
- Use specialized forensic tools, but conceptually you're just answering: who/what/when/where/how

#### Implementation in IR

- Forensics can start during detection/analysis and containment, and continues after recovery
- Output feeds:
  - Root cause analysis
  - New IoCs
  - Lessons learned & recommendations

#### Cross-Domain Correlations

- **Domain 1 & 3.2:** Tools (SIEM, EDR, packet capture) often provide the evidence analyzed
- **Domain 4:** Evidence supports incident reports and sometimes regulatory/legal reporting

#### Exam Watchpoints

- **Forensics is part of Post-incident Activity AND Detection/Analysis**—questions may test that it starts early but is formalized post-incident
- Know terms like **order of volatility, chain of custody, legal hold, and evidence preservation**

---

### 3.2 Root Cause Analysis (RCA)

#### Definition

A structured process to **identify the underlying reasons an incident occurred**, not just the visible symptoms.

**Goal:** Prevent recurrence by fixing the real issue (e.g., process, policy, or control failure), not just rebuilding a server.

#### Typical Steps

**1. Define and Scope the Incident**
- What happened? Which systems? Which data? Impact?

**2. Build a Timeline**
- Time-ordered sequence of events (attack phases, internal responses)

**3. Identify Causal Factors vs Root Causes**
- **Causal factors:** contributed to the problem
- **Root cause:** if fixed, would prevent or materially reduce likelihood/impact

**4. Propose Fixes**
- Technical, procedural, and organizational changes

#### Implementation

- Use outputs of forensic analysis, SIEM data, logs, interviews, threat intel
- Link root causes to risk management: e.g.,
  - Bad patch management
  - Misconfiguration
  - Overbroad privileges
  - Missing monitoring or alerts

#### Common Root Causes Found in RCA

| Category | Examples |
|----------|----------|
| **Vulnerability Management** | Unpatched systems, weak configurations, outdated software |
| **Access Control** | Excessive privileges, poor IAM, weak authentication |
| **Monitoring & Detection** | Blind spots in SIEM, missing EDR, inadequate logging |
| **Process & Procedure** | Missing or outdated incident response, poor change control |
| **Training & Awareness** | Employees falling for phishing, lack of security knowledge |

#### Cross-Domain Correlations

- **Domain 2:** Many root causes end up being vulnerability management failures (unpatched systems, weak configs)
- **Domain 1:** Architecture, IAM, logging often show up in root cause discussions

#### Exam Watchpoints

- **RCA is explicitly a post-incident activity**
- It focuses on **"why" and "how"** at a systemic level, not just "what malware ran" (that's forensics)

---

### 3.3 Lessons Learned

#### Definition

A structured review of the incident and the response to identify:
- What went well
- What went poorly
- What must change

Outputs are used to update IRP, playbooks, controls, and training.

#### Implementation

**1. Hold a Lessons-Learned Meeting**
- Include IR staff, system owners, support teams, management, sometimes legal
- Encourage candid input; avoid blame, focus on improvement

**2. Ask Key Questions**
- Did we detect the incident early enough?
- Were procedures and playbooks followed? Were they adequate?
- Where did communication break down?
- What controls were missing or misconfigured?
- What would we do differently next time?

**3. Produce Artifacts**

**Lessons Learned Report / After-Action Report (AAR):**
- Timeline summary
- Root cause
- Effective actions
- Deficiencies and recommendations

**Use this to:**
- Update IRP and playbooks
- Drive new training
- Adjust metrics/KPIs and controls

#### Cross-Domain Correlations

- **Domain 4.2:** Lessons learned explicitly feed future reporting and stakeholder communication improvements
- **Domain 1 & 2:** Output often includes changes to security operations and vulnerability management processes

#### Exam Watchpoints

- **Lessons learned is NOT about punishment; it's about process improvement**
- Often tested along with root cause analysis and incident reporting as distinct but related concepts

---

## 4. Concise Summary (Key Takeaways)

### Preparation Phase

Everything you do before an incident:

| Component | Purpose |
|-----------|---------|
| **IRP** | Sets authority, scope, and structure |
| **Tools** | Build and integrate SIEM, EDR, forensics kits |
| **Playbooks** | Scenario-specific steps to respond |
| **Tabletops** | Low-risk, discussion-based simulations to test the plan |
| **Training** | Make sure people know their roles and can execute |
| **BC/DR** | Ensure business can continue and IT can be restored when incidents become disasters |

### Post-Incident Activity Phase

Learning and improving:

| Component | Purpose |
|-----------|---------|
| **Forensic Analysis** | Collect and examine evidence in a defensible way |
| **Root Cause Analysis** | Determine why it happened and what really failed |
| **Lessons Learned** | Capture what worked, what didn't, and push changes into IRP, playbooks, controls, and training |

**Everything in 3.3 feeds a continuous improvement loop:**

```
Prepare → Respond → Learn → Improve Preparation
```

---

## 5. What to Watch for on the Exam

### 1. Lifecycle Mapping Questions

Be ready to pick which phase a task belongs to:

| Task | Phase |
|------|-------|
| "Train staff on reporting phishing" | **Preparation** |
| "Update IR plan based on gaps" | **Post-incident activity** |
| "Isolate an infected host" | **Containment (not 3.3)** |
| "Build forensic toolkit" | **Preparation** |
| "Conduct RCA meeting" | **Post-incident activity** |

### 2. Term Confusion

Know the distinctions:

| Concept | Definition |
|---------|-----------|
| **IRP vs Playbooks** | IRP = overarching governance; Playbooks = specific scenarios |
| **Playbooks vs Procedures** | Playbooks = "if X, then do Y"; Procedures = detailed "how-to" steps |
| **Tabletop vs Full-Scale Exercise** | Tabletop = discussion only; Full-scale = real systems involved |
| **BC vs DR** | BC = keep business running; DR = restore IT quickly |
| **Forensics vs RCA** | Forensics = "what happened"; RCA = "why it happened" |

### 3. Scenario-Based Traps

A question might say: **"After reimaging and restoring services, what should be done next?"**

- **Right answers:** lessons learned meeting, update IRP, or RCA
- **Wrong answers:** "patch again" or "monitor for 24 hours"

### 4. Cross-Domain Linkage

- **Root causes** frequently tie back to vulnerability management, IAM, logging, or patching
- **Lessons learned** often lead to:
  - New KPIs (mean time to detect/respond/remediate)
  - Updated training
  - Revised playbooks and IRP

### 5. Legal / Evidence Aspects

When the scenario hints at lawsuits or law enforcement:
- Think **forensics, preservation, legal hold, chain of custody, and evidence retention**
- These are all part of **post-incident work** (though evidence collection starts earlier)

---

## Quick Reference: Preparation vs Post-Incident

### Preparation Checklist

- ☐ Develop and document Incident Response Plan (IRP)
- ☐ Define incident severity levels and escalation paths
- ☐ Build incident response team and define roles
- ☐ Procure and integrate security tools (SIEM, EDR, forensics)
- ☐ Create playbooks for common scenarios (ransomware, phishing, etc.)
- ☐ Plan and conduct tabletop exercises
- ☐ Conduct IR team training and awareness training
- ☐ Document Business Continuity and Disaster Recovery plans
- ☐ Establish backup and restoration procedures
- ☐ Test tools, playbooks, and procedures regularly

### Post-Incident Activity Checklist

- ☐ Conduct forensic analysis (image systems, analyze malware, timeline)
- ☐ Preserve evidence with proper chain of custody
- ☐ Perform root cause analysis (identify why the incident happened)
- ☐ Hold lessons learned meeting (what went well, what didn't)
- ☐ Document findings in After-Action Report (AAR)
- ☐ Update IRP based on findings
- ☐ Update playbooks with new procedures or triggers
- ☐ Conduct additional training based on gaps identified
- ☐ Implement new controls or adjust existing ones
- ☐ Update metrics and KPIs
- ☐ Communicate findings to stakeholders as appropriate

---

## Exam Strategy for Domain 3.3

**When you see a question about Domain 3.3:**

1. **Identify which phase:** Preparation (before incident) or Post-Incident (after)
2. **Match the activity:** IRP, Tools, Playbooks, Tabletops, Training, BC/DR vs. Forensics, RCA, Lessons Learned
3. **Look for key phrases:**
   - "Before the incident" → Preparation
   - "After response," "improve," "document findings" → Post-Incident
   - "Test," "simulate," "discussion" → Tabletop
   - "Understand why," "underlying reasons" → RCA
   - "What worked, what didn't" → Lessons Learned
4. **Avoid common traps:**
   - Don't confuse IRP (governance) with playbooks (tactics)
   - Don't put containment activities into 3.3
   - Don't forget legal/evidence considerations
5. **Remember the continuous loop:** Everything learned in post-incident feeds back into preparation for next time
