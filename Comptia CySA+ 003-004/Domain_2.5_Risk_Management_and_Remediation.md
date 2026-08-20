# CompTIA CySA+ (CS0-003) Domain 2.5 Study Guide
## Risk Management and Remediation

---

## Overview: Domain 2.5 Framework

This study guide breaks down each concept into:
- **Definition:** Clear, concise explanation
- **Key Characteristics:** Bullet points for quick recall
- **Exam Spotting Tips:** Keywords, scenarios, or distractors to identify on the exam
- **Differentiation:** How it differs from similar concepts

### Exam-Wide Advice for Domain 2.5

**Look for:**
- Risk-based decisions, prioritization (severity/criticality), trade-offs (e.g., cost vs. mitigation), and processes (e.g., testing/rollback)
- Scenarios often involve balancing business needs (e.g., uptime) with security

**Common Distractors:**
- Confusing types (Managerial/Operational/Technical) with functions (Preventative/Detective/etc.)
- Patching steps out of order
- Risk responses mixed up (e.g., Avoid vs. Accept)

**Question Style:**
- "Recommend controls for X vulnerability" or "What to do if patching breaks functionality?"
- Prioritize: least privilege, testing, and documentation

---

## 1. Compensating Control

### Definition

A substitute control that provides equivalent protection when the primary control can't be implemented (e.g., due to cost, compatibility, or business needs).

### Key Characteristics

- Temporary or alternative fix (e.g., firewall rules instead of patching a legacy app)
- Must match primary control's intent and rigor (same risk reduction level)
- Documented with approval, review timeline, and monitoring

### Exam Spotting Tips

- Scenario: "Can't patch due to downtime—recommend alternative"
- Keywords: "substitute," "equivalent protection," "workaround"

### Differentiation

| Concept | Compensating | Corrective |
|---------|--------------|-----------|
| **Purpose** | Long-term alternative to primary control | Short-term fix after incident |
| **Timing** | Proactive (prevents issue) | Reactive (post-incident) |
| **Example** | Extra logging if MFA unavailable | Patch after exploit |

---

## 2. Control Types

**Three Categories:** How controls are implemented. Spot: Questions grouping by "people/processes" vs. "tech."

### a. Managerial (Administrative)

**Definition:**
- High-level oversight via policies/procedures (e.g., risk assessments, training plans)

**Key Characteristics:**
- "Paper" controls; guides others; non-technical

**Exam Spotting:**
- "Policy for X," "Training program," "Risk framework"

### b. Operational (Procedural)

**Definition:**
- Day-to-day processes executed by people (e.g., incident response procedures, audits)

**Key Characteristics:**
- Human-focused; supports managerial; includes physical (e.g., guards)

**Exam Spotting:**
- "Daily checks," "Response playbook," "Patrols"

### c. Technical (Logical)

**Definition:**
- Tech-enforced (e.g., firewalls, encryption, IDS)

**Key Characteristics:**
- Automated; protects CIA triad directly

**Exam Spotting:**
- "Firewall rule," "Encryption," "Access list"

### Differentiation (Types vs. Functions)

| Aspect | Types (Implementation) | Functions (Purpose) |
|--------|------------------------|-------------------|
| **Focus** | How (people/tech) | What (prevent/detect) |
| **Examples** | Policy (Managerial), Firewall (Technical) | Block traffic (Preventative) |

---

## 3. Control Functions

**Four Main Functions:** What controls do. Spot: Action-oriented (e.g., "stop before," "detect during").

### a. Preventative

**Definition:**
- Stops incidents before occurring (e.g., firewalls, MFA)

**Key Characteristics:**
- Proactive; blocks access

**Exam Spotting:**
- "Prevent unauthorized access"

### b. Detective

**Definition:**
- Identifies incidents in progress (e.g., logs, IDS alerts)

**Key Characteristics:**
- Reactive detection; records evidence

**Exam Spotting:**
- "Alert on anomaly," "Log review"

### c. Responsive

**Definition:**
- Reacts during/after incident (e.g., auto-quarantine, IPS block)

**Key Characteristics:**
- Dynamic response; limits spread

**Exam Spotting:**
- "Isolate during attack," "Automated block"

### d. Corrective

**Definition:**
- Fixes post-incident (e.g., patches, backups restore)

**Key Characteristics:**
- Recovery-focused; restores normalcy

**Exam Spotting:**
- "Restore from backup," "Apply patch after breach"

### Differentiation (Functions)

| Function | Timing | Example Scenario |
|----------|--------|------------------|
| **Preventative** | Before | ACL blocks bad IP |
| **Detective** | During | SIEM flags flood |
| **Responsive** | During/Immediate After | EDR isolates host |
| **Corrective** | After | Patch applied |

---

## 4. Patching and Configuration Management

### Definition

Processes to fix vulnerabilities (patches) and enforce secure settings (configs).

### Key Components

**Testing:** Validate patches/configs in lab (e.g., no breakage)
- Spot: "Test before deploy"

**Implementation:** Deploy after testing (e.g., staged rollout)
- Spot: "Roll out to prod"

**Rollback:** Revert if issues arise (e.g., backup restore)
- Spot: "Undo failed patch"

**Validation:** Scan post-change to confirm fix (e.g., rescan)
- Spot: "Verify mitigation"

### Exam Spotting

- **Sequence questions:** Test → Implement → Rollback → Validate
- **Distractor:** Skip testing

### Differentiation (Patching vs. Config Mgmt)

| Aspect | Patching | Config Mgmt |
|--------|----------|------------|
| **Focus** | Code fixes | Settings/rules |
| **Example** | OS update | Disable service |

---

## 5. Maintenance Windows

### Definition

Scheduled downtime for patches/config changes (e.g., weekends).

### Key Characteristics

- Planned to minimize disruption; documented

### Exam Spotting Tips

- "Off-hours patching," "Avoid business hours"

### Differentiation

- **vs. Exceptions:** Planned vs. ad-hoc
- **vs. Rollback:** Pre-planned vs. emergency

---

## 6. Exceptions

### Definition

Approved deviations from policy (e.g., can't patch legacy system).

### Key Characteristics

- Documented (reason, duration, compensating controls)
- Reviewed periodically

### Exam Spotting Tips

- "Document waiver," "Temporary non-compliance"

### Differentiation

| Concept | Definition | Scope |
|---------|-----------|-------|
| **Exceptions** | Specific policy waiver | Individual system/control |
| **Risk Acceptance** | Overall risk tolerance | Broader organizational level |
| **Compensating** | Alternative control | Exception requires one |

---

## 7. Risk Management Principles

**Four Responses:** How to handle risk. Spot: "Best response to X risk."

| Response | Definition | Example | Exam Keywords |
|----------|-----------|---------|----------------|
| **Accept** | Tolerate low risk (monitor only) | Minor vuln on non-critical system | "Monitor," "No action" |
| **Transfer** | Shift to third party (e.g., insurance) | Cyber insurance for breach costs | "Outsource," "Insure" |
| **Avoid** | Stop activity causing risk | Shut down risky legacy app | "Eliminate," "Cease" |
| **Mitigate** | Reduce via controls (most common) | Patch, firewall rules | "Implement controls" |

### Exam Spotting

- Risk scenarios; choose based on **cost/effort vs. impact**
- **Distractor:** Mitigate vs. Accept (high vs. low risk)

---

## 8. Policies, Governance, and Service Level Objectives (SLOs)

### Definitions

- **Policies:** High-level rules (e.g., "All systems patched quarterly")
- **Governance:** Oversight/enforcement (e.g., audits, compliance)
- **SLOs:** Measurable targets (e.g., "99.9% uptime," "Patch in 7 days")

### Key Characteristics

- Policies guide; Governance enforces; SLOs measure

### Exam Spotting

- "Mandate X," "Compliance check," "Uptime target"

### Differentiation

| Concept | Definition | Scope |
|---------|-----------|-------|
| **Policies** | Rules | High-level guidance |
| **Procedures** | Steps | How to execute |
| **SLOs** | Measurable targets | Performance metrics |
| **SLAs** | Vendor contracts | External obligations |

---

## 9. Prioritization and Escalation

### Definitions

- **Prioritization:** Rank by severity/criticality (e.g., CVSS + asset value)
- **Escalation:** Escalate high-risk items to mgmt (e.g., zero-day on critical server)

### Key Characteristics

- Severity first
- Escalate unresolvable issues

### Exam Spotting

- "High CVSS + critical asset?" "Escalate if X"

### Differentiation

- **Prioritization:** Rank internally
- **Escalation:** Notify higher-ups

---

## 10. Attack Surface Management

### Definition

Reduce exploitable entry points. Spot: "Discovery + testing."

### Components

**Edge Discovery:**
- Scan external perimeter (e.g., public IPs)

**Passive Discovery:**
- Monitor traffic (no active probes)

**Security Controls Testing:**
- Verify controls work (e.g., firewall rules)

**Penetration Testing/Adversary Emulation:**
- Simulate attacks

**Bug Bounty:**
- Crowdsource vuln reports (rewards for ethical hackers)

**Attack Surface Reduction:**
- Minimize (e.g., disable services)

### Exam Spotting

- "External scan," "Simulate attacker," "Reward reporters"

### Differentiation

| Concept | Focus | Method |
|---------|-------|--------|
| **Passive Discovery** | Observe | Monitor traffic |
| **Edge Discovery** | Probe perimeter | Active scans |
| **Bug Bounty** | Crowd | Reward reports |
| **Pentest** | Professional | Authorized team |

---

## 11. Secure Coding Best Practices

### Definition

Code techniques to prevent vulnerabilities. Spot: "Prevent injection/XSS."

### Practices and Purposes

| Practice | Purpose | Exam Example |
|----------|---------|-------------|
| **Input Validation** | Reject bad data (e.g., SQLi, XSS) | Sanitize user input |
| **Output Encoding** | Safe display (e.g., HTML escape) | Encode < > as &lt; &gt; |
| **Session Management** | Secure sessions (e.g., no fixation) | Regenerate IDs |
| **Authentication** | Strong login (e.g., MFA) | Rate-limit logins |
| **Data Protection** | Encrypt in transit (e.g., TLS) | Hash passwords |
| **Parameterized Queries** | Prevent injection (e.g., prepared statements) | Use ? placeholders |

### Exam Spotting

- Vulnerability scenarios (e.g., "Prevent SQLi?")
- **Distractor:** Encoding vs. Validation (output vs. input)

---

## 12. Secure Software Development Lifecycle (SDLC)

### Definition

Integrate security into SDLC (requirements → maintenance).

### Key Characteristics

- Security at every phase (design, code, test)

### Exam Spotting

- "Security in dev process," "Shift-left security"

### Differentiation

| Concept | Definition | Approach |
|---------|-----------|----------|
| **Secure SDLC** | Security integrated throughout | Proactive |
| **Traditional SDLC** | Security added after coding | Reactive |
| **Waterfall** | Linear phases | Sequential |
| **Agile** | Iterative development | Continuous |

---

## 13. Threat Modeling

### Definition

Identify threats pre-development (e.g., STRIDE: Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege).

### Key Characteristics

- Adversary view
- Attack surface and vectors
- Likelihood and impact assessment

### Exam Spotting

- "Model threats early," "What attacker sees"

### Differentiation

| Concept | Timing | Purpose |
|---------|--------|---------|
| **Threat Modeling** | Before/during design | Identify threats proactively |
| **SDLC** | Throughout development | Integrate security practices |
| **Threat Hunting** | During operations | Reactive search for threats |

---

## Quick Reference: Control Functions and Types Matrix

| Control Type | Preventative | Detective | Responsive | Corrective |
|--------------|-------------|-----------|------------|-----------|
| **Managerial** | Policy for access control | Audit results | Policy updates | Risk assessment |
| **Operational** | Employee training | Log review process | Incident response playbook | Recovery procedures |
| **Technical** | Firewall rules, MFA | IDS/IPS alerts, SIEM logs | EDR auto-isolate | Patch deployment |

---

## Patching Sequence: Best Practice Order

1. **Test** → Validate in lab/sandbox
2. **Implement** → Deploy via maintenance window
3. **Validate** → Rescan to confirm vulnerability fixed
4. **Rollback** → Revert if critical issues (failsafe)

**Exam Tip:** Questions about "what step should happen next?" — Know this sequence cold.

---

## Risk Response Decision Tree

```
HIGH RISK & HIGH IMPACT
↓
Can we mitigate? → YES → MITIGATE (implement controls)
                 → NO → Can we avoid? → YES → AVOID (stop activity)
                                     → NO → Can we transfer? → YES → TRANSFER (insurance/outsource)
                                                           → NO → Document & Accept

LOW RISK & LOW IMPACT
↓
ACCEPT (monitor only)
```

---

## Exam Preparation Tips for Domain 2.5

**Master these concepts:**
1. **Control Types** (Managerial/Operational/Technical) — The "WHO/HOW"
2. **Control Functions** (Preventative/Detective/Responsive/Corrective) — The "WHEN/WHAT"
3. **Risk Responses** (Accept/Transfer/Avoid/Mitigate) — The "HOW TO HANDLE"
4. **Patching Process** (Test → Implement → Validate → Rollback) — The "ORDER"

**Recognize exam wording:**
- "Policy requiring X" → Managerial Control
- "Daily log review" → Operational + Detective
- "Firewall blocks traffic" → Technical + Preventative
- "Auto-quarantine infected host" → Technical + Responsive
- "Restore from backup" → Corrective
- "Can't patch due to business need" → Compensating control + Exception

**Common trap answers to avoid:**
- Using Technical controls when question asks for Managerial (e.g., firewall for a policy question)
- Mixing up Prevention (before) with Response (during) — they're different
- Suggesting Mitigation when Risk Acceptance is appropriate (e.g., low-risk vuln on isolated lab system)
- Skipping Validation after patching — always verify the fix worked

**Practice scenarios:**
- "A critical zero-day on a legacy system that can't be patched. What do you recommend?"
  - Answer: Accept the exception, implement compensating controls (segmentation, increased monitoring), set review timeline
- "Patching breaks application functionality. What's the next step?"
  - Answer: Rollback, then plan re-patch with more testing
- "Low CVSS vuln on non-critical test system. Response?"
  - Answer: Accept (document), monitor, no immediate action needed

**Score Weight:** Domain 2.5 carries significant weight. It tests your ability to make **risk-based, business-aware decisions** — not just technical prowess. Expect 20-30% of exam questions to touch these concepts.

---

## Final Quick Reference

| Concept | Key Point | Exam Tell |
|---------|-----------|-----------|
| **Compensating Control** | Alternative when primary can't work | "Can't patch, use instead" |
| **Managerial Control** | Policy/procedure-based | "Mandate," "require," "policy" |
| **Operational Control** | Human process-based | "Daily," "weekly," "staff," "review" |
| **Technical Control** | Automated/tech-enforced | "Firewall," "encryption," "IDS" |
| **Preventative** | Stop before incident | "Block," "prevent," "restrict" |
| **Detective** | Identify during incident | "Alert," "flag," "detect," "log" |
| **Responsive** | React during incident | "Isolate," "auto-respond," "quarantine" |
| **Corrective** | Fix after incident | "Patch," "restore," "recover" |
| **Mitigate** | Reduce risk | "Implement controls," "patch" |
| **Accept** | Tolerate risk | "Monitor," "document," "low impact" |
| **Transfer** | Shift to third party | "Insurance," "outsource," "vendor" |
| **Avoid** | Stop activity | "Shut down," "eliminate," "cease" |
| **Maintenance Window** | Scheduled change | "Off-hours," "weekend," "planned" |
| **Exception** | Policy waiver | "Temporary," "documented," "approved" |
| **Prioritization** | Rank by risk | "CVSS + asset criticality" |
| **Escalation** | Notify higher-ups | "Critical," "zero-day," "C-level" |
| **Threat Modeling** | Pre-dev threat identification | "STRIDE," "early," "design phase" |
| **Secure SDLC** | Security throughout development | "Shift-left," "security first" |
