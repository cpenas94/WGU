# Domain 1.3 — Use Appropriate Tools & Techniques to Determine Malicious Activity

A concise, practical study guide covering tools, techniques, and scripting languages used to identify, analyze, and confirm malicious activity. Each section includes definitions, key features, usage examples, detection scenarios, and actionable tips.

---

## Table of Contents
- Overview
- Packet Capture
  - Wireshark
  - tcpdump
- Log Analysis & Correlation
  - SIEM
  - SOAR
- Endpoint Security
  - EDR
- DNS / IP Reputation
  - WHOIS
  - AbuseIPDB
- File Analysis
  - Strings
  - VirusTotal
  - Sandboxing (Joe Sandbox, Cuckoo)
  - Hashing
- Common Techniques
  - Pattern Recognition
  - Command and Control (C2)
  - Interpreting Suspicious Commands
  - Email Analysis
- User Behavior Analysis
  - Abnormal Activity & Impossible Travel
- Programming Languages & Scripting
  - JSON, XML, Python, PowerShell, Shell, Regex
- Quick Reference: Commands & Examples
- Tips & Best Practices

---

## Overview
This guide focuses on tools and techniques for identifying malicious activity in networks, systems, files, and user behavior. Use the appropriate combination of capture, correlation, endpoint telemetry, reputation data, and file analysis to build confidence in detection and response.

---

## Packet Capture
Packet capture tools intercept, record, and analyze network traffic to reveal anomalies, exploits, or IoCs (Indicators of Compromise) such as beaconing, unusual protocols, and data exfiltration.

### Wireshark
- Description: Open-source GUI packet analyzer; real-time and offline analysis.
- Key features:
  - Live capture and offline pcap analysis
  - Rich display filters (e.g., `http contains "malware"` or `ip.src == 192.168.1.100`)
  - Protocol dissection, statistics, graphs, and object export
- Usage in detection:
  - Detect beaconing and C2 patterns
  - Analyze SMB traffic for lateral movement
  - Inspect HTTP/HTTPS flows; use SSL/TLS key logging for deeper inspection if available
- Example filter:
  - DNS queries: `udp.port == 53`
- Tips:
  - Use capture filters (BPF) to reduce noise
  - Combine with `tshark` for automation and scripting

### tcpdump
- Description: Lightweight CLI packet capture for Unix/Linux; saves PCAPs for later analysis
- Key features:
  - Scriptable, supports BPF filters
  - Outputs to stdout or PCAP files for Wireshark
- Usage in detection:
  - Capture specific traffic (P2P, unusual ports)
  - Detect port sweeps/scans (many SYNs without ACKs)
- Example commands:
  - Verbose HTTP capture and write to file:
    ```
    tcpdump -i eth0 -n -vv port 80 -w capture.pcap
    ```
  - Capture full packets:
    ```
    tcpdump -i eth0 -s0 -w full_capture.pcap
    ```
- Tips:
  - Use `-s0` to capture full packets
  - Pipe or schedule tcpdump captures and import to Wireshark for deeper analysis

---

## Log Analysis & Correlation
Aggregate and correlate events across systems to detect patterns (brute force, privilege escalation, impossible travel).

### SIEM (Security Information and Event Management)
- Description: Centralized collection, normalization, correlation, and analysis of logs
- Key features:
  - Real-time alerting, dashboards, correlation rules
  - Aggregation from syslog, Windows Events, EDR, network devices
  - Forensic retention
- Usage:
  - Correlate failed logins + new user creation = suspicious privilege escalation
  - Build behavioral baselines to surface anomalies
- Example Splunk query:
  ```
  index=security sourcetype=auth | stats count by src_ip | where count > 50
  ```
- Tips:
  - Tune rules to reduce false positives
  - Integrate threat intelligence and EDR telemetry

### SOAR (Security Orchestration, Automation, and Response)
- Description: Automates workflows and orchestrates responses across tools
- Key features:
  - Playbooks/runbooks for handling alerts
  - Integrates SIEM, EDR, threat intel, ticketing
- Usage:
  - Automate triage (WHOIS → VirusTotal → isolate host)
- Example runbook:
  - Alert → WHOIS lookup → block IP if malicious
- Tips:
  - Test playbooks to avoid unintended wide-impact actions

---

## Endpoint Security

### EDR (Endpoint Detection & Response)
- Description: Agent-based telemetry and behavioral detection on endpoints
- Key features:
  - Process monitoring, memory scanning, behavioral analytics
  - Automated isolation/quarantine
- Usage:
  - Detect living-off-the-land techniques (PowerShell abuse)
  - Identify odd parent-child process relationships (e.g., `cmd.exe` spawning RDP)
- Tips:
  - Enable full telemetry for investigation
  - Correlate EDR events with SIEM alerts for context

---

## DNS & IP Reputation

### WHOIS
- Use: Query registries for domain ownership, creation/expiration dates
- Use case: Newly registered domains, DGA domains, privacy-protected registration
- Tips: Combine WHOIS with passive DNS and geolocation for richer context

### AbuseIPDB
- Use: Community reports of abusive IPs (spam, phishing, brute-force)
- Use case: Quickly validate whether an IP has recent abuse reports
- Tips: Check recency of reports; programmatic API available for automation

---

## File Analysis
Analyze binaries, documents, and scripts to extract IoCs and behavior.

### Strings
- Description: Extract human-readable strings from binaries
- Usage:
  - Quickly reveal embedded URLs, IPs, and commands
- Example:
  ```
  strings suspicious.exe | grep -i "http"
  ```
- Tips:
  - Pipe to `grep` for targeted keywords (e.g., `http`, `curl`, `eval`)

### VirusTotal
- Description: Multi-engine scanning + sandbox/signal insights
- Usage:
  - Upload or hash-check files/URLs
  - Review engine detections, relations, and community score
- Tips:
  - Use Retrohunt for retrospective scans and hunting

### Sandboxing
- Joe Sandbox: Commercial/cloud sandbox with detailed behavior and network graphs
- Cuckoo Sandbox: Open-source, customizable malware detonation environment
- Usage:
  - Dynamic analysis to observe runtime behavior and extract IoCs
- Tips:
  - Customize the environment (language packs, network, VPN) to elicit realistic behavior
  - Combine sandbox results with EDR telemetry and PCAPs

### Hashing
- Use: Generate MD5, SHA-1, SHA-256 for reputation lookups (VirusTotal, intel feeds)
- Example:
  - `sha256sum suspicious.exe`

---

## Common Techniques

### Pattern Recognition
- Description: Identify recurring malicious patterns like periodic callbacks or unusual protocol usage
- Usage:
  - SIEM rules for periodic outbound connections (beaconing)
- Scenario:
  - Hourly outbound requests to DGA-like domains → possible C2 beaconing
- Tip:
  - Baseline normal traffic and look for deviations

### Command & Control (C2)
- Look for:
  - Low-volume periodic connections, non-standard ports, high-entropy DNS
- Usage:
  - Monitor DNS for high-entropy domain names or frequent NXDOMAINs
- Tip:
  - Block confirmed C2 or isolate the host; enrich with WHOIS and passive DNS

### Interpreting Suspicious Commands
- Monitor for living-off-the-land techniques and suspicious cmdlets
- Examples of suspicious PowerShell:
  - Use of `Invoke-WebRequest`, `IEX`, or base64-encoded commands
- Example lateral movement:
  - `net use \\evil.com\share` → unexpected SMB share usage
- Tips:
  - Log command histories and alert on unsigned or obfuscated scripts

### Email Analysis
- Inspect headers and payloads for phishing indicators
- Key checks:
  - SPF/DKIM/DMARC validation
  - Received headers for path tracing
  - Embedded links (resolve redirects carefully)
- Tips:
  - Decode MIME parts; check URLs against reputation feeds and sandbox suspicious attachments

---

## User Behavior Analysis
- Monitor for baseline deviations (abnormal account activity)
- Examples:
  - Multiple failed logins followed by success (possible brute-force)
  - Impossible travel: logins from distant geolocations in short time (geoIP + timestamp)
- Tips:
  - Use SIEM to correlate geo and time; create alerts for impossible travel and off-hours privileged access

---

## Programming Languages & Scripting (for automation & analysis)
- JSON: Common format for SIEM, APIs, and cloud logs
  - Example: `{"ip": "1.2.3.4", "threat": "high"}`
- XML: Used in older feeds and OVAL/STIX
- Python: Versatile for parsing pcaps, APIs, automation
  - Example snippet:
    ```python
    import requests
    r = requests.get('https://www.virustotal.com/api/v3/files/{hash}')
    ```
- PowerShell: Windows-focused automation; inspect cmdlets and scripts
  - Example: `Get-Process | Where-Object {$_.Path -like "*temp*"}`
- Shell script (bash): Log parsing and automation
  - Example: `egrep "(login|fail)" /var/log/syslog | wc -l`
- Regular expressions: Essential for pattern matching in logs
  - IP regex example: `\d+\.\d+\.\d+\.\d+`

---

## Quick Reference: Commands & Filters
- Wireshark DNS filter: `udp.port == 53`
- Wireshark SMB filter (example): `smb.cmd == 0x72`
- tcpdump capture HTTP:
  ```
  tcpdump -i eth0 -n -vv port 80 -w capture.pcap
  ```
- Capture full packets:
  ```
  tcpdump -i eth0 -s0 -w full_capture.pcap
  ```
- strings:
  ```
  strings sample.exe | grep -i "http"
  ```
- SHA256 hash:
  ```
  sha256sum sample.exe
  ```
- Splunk example:
  ```
  index=security sourcetype=auth | stats count by src_ip | where count > 50
  ```

---

## Tips & Best Practices
- Combine data sources: Packet captures + EDR + SIEM produce stronger evidence than any single source.
- Baseline first: Know normal behavior to recognize anomalies.
- Automate low-risk triage with SOAR; keep human-in-loop for high-impact decisions.
- Preserve evidence: Save PCAPs, logs, and sandbox reports with timestamps for forensics.
- Tune detection rules to minimize noisy alerts and focus on high-confidence indicators.
- Test playbooks and sandbox environments to avoid false negatives/positives.

- If you want, I can:
  - Add a short checklist for incident triage (first 60 minutes vs next steps)
  - Create a printable cheat-sheet version (single-page)
  - Commit this file to your repository (I can prepare a PR if you provide repository/branch details)
