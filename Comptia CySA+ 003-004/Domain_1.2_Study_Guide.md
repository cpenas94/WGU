# CompTIA CySA+ (CS0-003) Domain 1.2 Study Guide
## Analyze Indicators of Potentially Malicious Activity

---

## Overview

Domain 1.2 focuses on recognizing and interpreting indicators of potentially malicious activity across network, host, application, and other categories. These indicators signal possible compromise, attack attempts, or anomalies. Analysis involves correlating data from logs, tools (e.g., SIEM, EDR, packet captures), baselines, and patterns to differentiate benign issues from threats.

### Key Steps

- **Establish Baselines**: Understand normal behavior (e.g., traffic volumes, process usage) for anomaly detection.
- **Detection Methods**: Use tools like Wireshark, tcpdump, SIEM, EDR, and log analysis.
- **Correlation**: Combine indicators (e.g., high bandwidth + beaconing = exfiltration).
- **Prioritization**: Assess impact (e.g., critical systems) and likelihood.
- **Mitigation**: Isolate, scan, and remediate while preserving evidence.

---

## Network-Related Indicators

These involve unusual traffic patterns, often detected via NetFlow, SIEM, or packet analysis.

### Bandwidth Consumption

**Description**  
Sudden or sustained high network usage exceeding baselines, indicating resource exhaustion or data movement.

**Malicious Context**  
DDoS floods, worm propagation, data exfiltration (e.g., large file transfers), or crypto-mining.

**Detection**
- Monitor bytes/packets sent/received; compare to baselines.
- Flow data (NetFlow/sFlow) shows spikes; SNMP tracks interface utilization.
- Tools: MRTG for graphing, SIEM for alerts.

**Examples**  
DRDoS (DNS/NTP amplification); worm self-replication saturating links.

**Mitigation**  
Rate limiting, traffic shaping, DDoS scrubbing services; baseline thresholds for alerts.

---

### Beaconing

**Description**  
Periodic, regular outbound traffic from hosts to external IPs/domains (e.g., every 10-60 seconds).

**Malicious Context**  
Malware "phoning home" to C2 servers for commands, updates, or exfiltration; uses HTTP/HTTPS/DNS to blend in.

**Detection**
- Jitter analysis (random delays evade fixed-interval rules)
- High NXDOMAIN errors (DGA)
- Tools: SIEM rules, Wireshark filters (e.g., `http.request.uri contains "beacon"`)

**Examples**  
Botnets beaconing C2; fast-flux DNS rotates IPs.

**Mitigation**  
DNS sinkholing, proxy inspection, block known C2 IPs/domains; monitor query entropy.

---

### Irregular Peer-to-Peer Communication

**Description**  
Unexpected direct host-to-host traffic (e.g., clients communicating laterally instead of client-server).

**Malicious Context**  
Lateral movement (e.g., SMB for propagation); ARP poisoning for MiTM.

**Detection**
- Baselines show client-server norms; anomalies via flow analysis.
- Tools: Wireshark (smb or arp), SIEM for peer traffic spikes.

**Examples**  
SMB abuse (PsExec, WMI); Pass-the-Hash (PtH) for credential reuse.

**Mitigation**  
Micro-segmentation, L2 ACLs; monitor ARP caches (`arp -a`).

---

### Rogue Devices on the Network

**Description**  
Unauthorized hardware/software (e.g., rogue AP, USB, VM).

**Malicious Context**  
Backdoors, MiTM (evil twin AP), data exfiltration.

**Detection**
- Visual inspection, NAC/802.1x, wireless monitoring (unknown SSIDs).
- Tools: Nmap sweeps, DHCP logs.

**Examples**  
USB taps, rogue WAPs, unauthorized VMs.

**Mitigation**  
Port security, NAC, certificate-based auth; segment IoT.

---

### Scans/Sweeps

**Description**  
Probing multiple ports/IPs for open services (e.g., SYN floods).

**Malicious Context**  
Reconnaissance for exploits; precursors to attacks.

**Detection**
- Imbalanced SYN/ACK/RST; high ARP queries.
- Tools: IDS (Snort/Suricata), SIEM rules.

**Examples**  
Nmap sweeps; fragmented probes.

**Mitigation**  
Honeypots, rate limiting; log external scans.

---

### Unusual Traffic Spikes

**Description**  
Sharp increases in volume/frequency vs. baseline.

**Malicious Context**  
DDoS, exfiltration; slashdotting (legit overload).

**Detection**
- Flow graphs; HTTP 503 errors.
- Tools: SIEM, NetFlow analyzers.

**Examples**  
Botnet floods; worm scans.

**Mitigation**  
DDoS services (Cloudflare); caching.

---

### Activity on Unexpected Ports

**Description**  
Traffic on non-standard ports (e.g., HTTP on TCP 8080).

**Malicious Context**  
C2 evasion, tunneling.

**Detection**
- Mismatched port/protocol (e.g., DNS on TCP 443).
- Tools: Nmap (`nmap -sV`), speedguide.net.

**Examples**  
Malware on dynamic ports.

**Mitigation**  
Whitelist ports; app-aware firewalls.

---

## Host-Related Indicators

Focus on system resources, processes; detect via EDR, baselines.

### Processor Consumption

**Description**  
Sudden/spiking CPU usage by unknown processes.

**Malicious Context**  
Crypto-miners, brute-force, malware scans.

**Detection**
- Task Manager/Perfmon (Windows)
- top/ps (Linux)
- Baselines; per-process monitoring.

**Examples**  
Miner using 90% CPU.

**Mitigation**  
EDR behavioral rules; resource limits.

---

### Memory Consumption

**Description**  
High RAM usage without workload.

**Malicious Context**  
Fileless malware, memory injection.

**Detection**
- Resource Monitor
- Volatility for dumps
- Tools: `free` (Linux); high per-process.

**Examples**  
Process hollowing.

**Mitigation**  
Memory forensics; EDR.

---

### Drive Capacity Consumption

**Description**  
Rapid disk fill-up.

**Malicious Context**  
Staging exfiltration, ransomware encryption.

**Detection**
- `df`/`du` (Linux)
- TreeSize (Windows)
- Large temp files, staging dirs.

**Examples**  
Ransomware encrypting files.

**Mitigation**  
DLP; quota enforcement.

---

### Unauthorized Software

**Description**  
Rogue apps (e.g., tools, VMs).

**Malicious Context**  
Attack kits (Mimikatz).

**Detection**
- Prefetch/Amcache/Shimcache
- Inventory scans.

**Examples**  
Nmap on workstation.

**Mitigation**  
App whitelisting (AppLocker).

---

### Malicious Processes

**Description**  
Suspicious execution (e.g., renamed svchost.exe).

**Malicious Context**  
DLL injection, process hollowing.

**Detection**
- Process Explorer
- Sysinternals
- Parent-child anomalies.

**Examples**  
CertUtil downloading malware.

**Mitigation**  
EDR; signed binaries.

---

### Unauthorized Changes

**Description**  
Modified configs/files/registry.

**Malicious Context**  
Persistence (run keys).

**Detection**
- FIM (Tripwire)
- Baselines.

**Examples**  
New startup entries.

**Mitigation**  
Immutable files; auditing.

---

### Unauthorized Privileges

**Description**  
Escalation (user to admin).

**Malicious Context**  
PtH, UAC bypass.

**Detection**
- AccessChk
- Privilege logs.

**Examples**  
Guest account enabled.

**Mitigation**  
Least privilege; MFA.

---

### Data Exfiltration

**Description**  
Large outbound transfers.

**Malicious Context**  
Staging/compression.

**Detection**
- DLP
- NetFlow spikes.

**Examples**  
RAR in temp dirs.

**Mitigation**  
Encrypt at rest/transit.

---

### Abnormal OS Process Behavior

**Description**  
Legit processes acting oddly.

**Malicious Context**  
Injection.

**Detection**
- Handles, network anomalies.

**Examples**  
svchost.exe outbound to C2.

**Mitigation**  
Behavioral EDR.

---

### File System Changes/Anomalies

**Description**  
Unexpected mods/deletions.

**Malicious Context**  
Anti-forensics.

**Detection**
- FIM
- Timestamps.

**Examples**  
Log clearing.

**Mitigation**  
WORM storage.

---

### Registry Changes/Anomalies

**Description**  
Modified keys (Windows).

**Malicious Context**  
Persistence.

**Detection**
- RegRipper
- Event logs.

**Examples**  
Run keys added.

**Mitigation**  
AppLocker.

---

### Unauthorized Scheduled Tasks

**Description**  
New/cron jobs.

**Malicious Context**  
Persistence.

**Detection**
- Task Scheduler
- `crontab -l`.

**Examples**  
Root cron for backdoor.

**Mitigation**  
Restrict task creation.

---

## Application-Related Indicators

App logs, behaviors; focus on web/DB.

### Anomalous Activity

**Description**  
Deviations (e.g., web/DB spikes).

**Malicious Context**  
Injection, scraping.

**Detection**
- Logs; baselines (reads/queries).

**Examples**  
SQLi via large HTTP responses.

**Mitigation**  
WAF; input validation.

---

### Introduction of New Accounts

**Description**  
Rogue admins/service accounts.

**Malicious Context**  
Persistence/backdoors.

**Detection**
- Logs; audits.

**Examples**  
New domain admin.

**Mitigation**  
Approval workflows.

---

### Unexpected Output

**Description**  
Errors, pop-ups, garbled data.

**Malicious Context**  
Injection, defacement.

**Detection**
- Logs; UAC alerts.

**Examples**  
SQL errors in web response.

**Mitigation**  
Custom error pages.

---

### Unexpected Outbound Communication

**Description**  
Apps phoning home.

**Malicious Context**  
C2, exfil.

**Detection**
- Netstat; proxies.

**Examples**  
DB to C2.

**Mitigation**  
App whitelisting.

---

### Service Interruption

**Description**  
Crashes, DoS.

**Malicious Context**  
Exploits.

**Detection**
- Logs; monitoring.

**Examples**  
Reloads.

**Mitigation**  
Failover.

---

### Application Logs

**Description**  
Errors, access anomalies.

**Malicious Context**  
Failed auth, injections.

**Detection**
- SIEM; patterns.

**Examples**  
High 404s.

**Mitigation**  
Centralized logging.

---

## Other Indicators

Non-technical/human factors.

### Social Engineering Attacks

**Description**  
Phishing, pretexting, baiting.

**Malicious Context**  
Credential theft.

**Detection**
- User reports; anomalies.

**Examples**  
Urgent password reset emails.

**Mitigation**  
Training, awareness.

---

### Obfuscated Links

**Description**  
Shortened/masked URLs.

**Malicious Context**  
Phishing.

**Detection**
- URL scanners; rewriters.

**Examples**  
Bit.ly to malware.

**Mitigation**  
Link scanners; training.

**Note**: Using Percent Encoding (e.g., `%2e%2e%2f` for `../`) or URL shorteners to hide a malicious destination or perform a Directory Traversal attack.

---

## Quick Reference: Tools & Techniques

| Category | Detection Tool | Key Commands |
|----------|---|---|
| **Network** | SIEM, Wireshark, NetFlow | `tcpdump`, `nmap -sV` |
| **Host** | EDR, Task Manager, Perfmon | `top`, `ps`, `df`, `du` |
| **Process** | Process Explorer, Sysinternals | `crontab -l`, `arp -a` |
| **File** | FIM (Tripwire), RegRipper | File hashing, `crontab -l` |
| **Application** | WAF, SIEM | Log analysis, anomaly patterns |
| **Social** | User reports, URL scanners | Awareness training |

---

**Last Updated**: August 2024  
**Source**: CompTIA CySA+ Exam Guide (CS0-003)
