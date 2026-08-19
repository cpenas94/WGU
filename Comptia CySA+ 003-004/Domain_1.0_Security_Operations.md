# Domain 1.0 — Security Operations

---

## Table of contents
- Logging levels
- Windows registry
- File structure & config locations
- System processes
- Hardware architecture
- Infrastructure concepts (Serverless / Virtualization / Containerization)
- Network architecture & segmentation
- Identity & access management (IAM)
- Encryption & PKI
- Sensitive data protection

---

## Logging levels (0–7)
| Level | Name      | Description               | Example                 |
|------:|:----------|:--------------------------|:------------------------|
| 0     | Emergency | System unusable           | Kernel panic            |
| 1     | Alert     | Immediate action needed   | RAID failure            |
| 2     | Critical  | Critical conditions       | Hardware failure        |
| 3     | Error     | Error conditions          | App crash               |
| 4     | Warning   | Warning conditions        | High CPU usage          |
| 5     | Notice    | Normal but significant    | Config change           |
| 6     | Info      | Informational messages    | Service start           |
| 7     | Debug     | Debug-level messages      | Troubleshooting details |

> **Mnemonic:** Eager Astronauts Cook Eggs While Navigating Into Darkness

---

## Windows Registry
- Structure: five root keys (hives)
  - HKEY_CLASSES_ROOT (HKCR) — COM registrations, file associations
  - HKEY_LOCAL_MACHINE (HKLM) — System info: drivers, services, installed software
  - HKEY_USERS (HKU) — All user accounts
  - HKEY_CURRENT_USER (HKCU) — Current user's settings
  - HKEY_CURRENT_CONFIG (HKCC) — Hardware profile info
- System hardening guidance: CIS Benchmarks, DoD STIGs

---

## File structure (OS locations)
- Purpose: Organizes storage/access; important for forensics and anomaly detection

Common locations:
- Windows
  - Registry (HKLM / HKCU)
  - C:\ProgramData, C:\Program Files, C:\Windows\System32
- Linux
  - /etc (configuration), /var/log (logs), /home (user data), /usr, /opt
- macOS
  - ~/Library/Preferences, /Library/Preferences

---

## System processes
- Overview: Core OS tasks — monitor to detect anomalies/malware.
- Windows core processes (examples)
  - ntoskrnl.exe — C:\Windows\System32 — NT kernel (PID 4)
  - smss.exe — Session Manager
  - csrss.exe — Client/Server Runtime Subsystem
  - wininit.exe — Initialization
  - services.exe — Service Control Manager
  - lsass.exe — Local Security Authority
- Linux monitoring: ps, top, htop; init/systemd is PID 1

---

## Hardware architecture
- x86 (Intel/AMD): Dominant for desktops/servers — common malware target
- ARM: Mobile/IoT; Apple M1/M2 use ARM — binaries compiled for x86 generally won't run natively on ARM
- Security implication: architecture mismatches can limit malware, but emulation and cross-compilation exist

---

## Infrastructure concepts

### 1) Serverless (FaaS)
- Definition: Run functions in response to events; no server provisioning required (e.g., AWS Lambda, Azure Functions)
- Process: Event → Provider provisions runtime/container → Function runs → Container torn down → Billing per execution
- Pros: Cost-effective, no server maintenance, auto-scaling, rapid dev
- Cons: Execution time limits, cold starts, vendor lock-in, harder debugging
- Security implications & mitigations:
  - Treat functions as code: secure coding, input validation
  - Principle of least privilege for IAM roles
  - Use API gateways, secure secrets, logging/monitoring

### 2) Virtualization (VMs)
- Definition: Create full guest OS instances via a hypervisor
  - Type 1 (bare-metal): ESXi, Hyper-V
  - Type 2 (hosted): VirtualBox
- Pros: Strong isolation, OS diversity, snapshots, migrations
- Cons: Resource overhead, hypervisor is a single point of failure
- Security implications & mitigations:
  - Risk of VM escape, hypervisor vulnerabilities
  - Harden hypervisor, isolate management interfaces, network segmentation

### 3) Containerization
- Definition: Package apps and dependencies; containers share host kernel (Docker, Kubernetes)
- Pros: Lightweight, portable, fast startup, efficient resource use
- Cons: Shared kernel risk, less isolation than VMs, image supply-chain risks
- Security implications & mitigations:
  - Kernel exploits can affect all containers
  - Use image scanning, signing, minimal base images, runtime controls (seccomp, AppArmor), network/pod policies

Exam tip: Serverless ≠ containers/VMs. Use serverless for event-driven stateless functions, containers for microservices, VMs for legacy/strong isolation.

---

## Network architecture

### On-premises
- Components: routers, switches, firewalls, IDS/IPS, NAC, UTM, access points
- Topology: core → distribution → access layers; VLANs for segmentation
- Best practices: patch hardware, limit ACLs, physical controls, monitor via NAC

### Cloud
- Components/providers: AWS, Azure, GCP; use VPCs, security groups, IAM
- Shared responsibility model: provider secures infra; you secure config, identities, data
- Best practices: least privilege IAM, encryption, centralized logging (CloudTrail), regular audits

### Hybrid
- Combine on-prem + cloud; secure links via VPN, Direct Connect, ExpressRoute
- Best practices: unified identity, consistent monitoring, CASB for visibility

### Network segmentation
- Methods: physical separation, VLANs/ACLs, microsegmentation (app-level)
- Benefits: limit lateral movement, contain breaches
- Threats: VLAN hopping, misconfigured ACLs

### Zero Trust
- Principle: "Never trust, always verify" — verify all access requests continuously
- Components: MFA, microsegmentation, continuous monitoring, JIT access

### SASE (Secure Access Service Edge)
- Cloud-delivered combination of SD-WAN + security services (FWaaS, CASB, ZTNA)
- Use for identity-centric and global policy enforcement

### SDN (Software-Defined Networking)
- Decouples control plane from data plane; uses controllers and APIs
- Secure controllers, secure APIs, and isolate management plane

Key takeaways: Hybrid is common; segmentation + zero trust reduce risk; SASE is useful for remote/cloud setups.

---

## Identity & Access Management (IAM)

### Single Sign-On (SSO)
- Allows logging in once to access multiple services
- Exam tip: SSO is often within an organization; federation spans organizations

### Federation
- Share identity across domains (SAML, OAuth, OpenID Connect)
- Roles: Identity Provider (IdP) vs Service Provider (SP)

### Privileged Access Management (PAM)
- Controls and monitors privileged accounts; provides just-in-time elevation, session recording

### Passwordless
- Authentication without passwords: biometrics, hardware tokens (YubiKey), magic links
- Use possession + inherence factors where possible

### CASB (Cloud Access Security Broker)
- Gateway between users and cloud services to enforce policies (visibility, compliance, threat protection, data security)

---

## Encryption & PKI

### Encryption
- Protects confidentiality and integrity of data at rest and in transit
- Use strong algorithms, proper key management, and rotate keys regularly

### Public Key Infrastructure (PKI)
- Components: Certificate Authority (CA), Registration Authority (RA), certificate repository, management system
- Flow: Request → RA verifies → CA issues certificate → revoke via CRL/OCSP when needed
- SSL/TLS inspection: decrypts/inspects TLS traffic; requires trusted root and has privacy/compatibility implications (not for pinned certs)

---

## Sensitive data protection

### Data Loss Prevention (DLP)
- Pillars: Discover & classify, monitor, enforce
- Enforcement actions: alert, block, quarantine
- Use DLP on endpoints, networks, and cloud

### Personally Identifiable Information (PII)
- Direct identifiers: SSN, passport, full name + identifying attributes
- Indirect identifiers: DOB + ZIP combination
- Regulated by GDPR, CCPA — treat sensitive PII with stronger controls

### Cardholder Data (CHD)
- PAN, cardholder name, expiration; CVV has special handling (often not stored)
- PCI DSS: segment, minimize storage, encrypt, scan regularly
