# QRadar SIEM Incident Triage & Case Study Workbook

A comprehensive hands-on workbook documenting the manual analysis, offense triage, MITRE ATT&CK mapping, and incident reporting for four distinct simulated security breaches using IBM QRadar SIEM.

---

## 📂 Project Overview
This repository contains formal classification worksheets, executive-level ticket summaries, and threat analysis for four complex enterprise security scenarios. The objective is to bridge theoretical SIEM alerting with practical Tier-1/Tier-2 SOC investigation methodologies.

---

## 🔍 Case Study Breakdown

### Offense 1: Brute Force Against a Jump Host (OFF-40881)
* **Rule Triggered:** Authentication: Excessive Failed Logins to Same Destination
* **Analysis:** 63 failed login attempts over 4 minutes targeting default accounts on a Tier-1 jump host (`10.20.1.55`), culminating in a successful `AuthSuccess` on the `svc_backup` account.
* **MITRE ATT&CK:** Credential Access -> Brute Force (T1110)
* **Classification:** True Positive (Active Internal Compromise / Lateral Movement)

### Offense 2: Regular Interval Outbound Connection / C2 Beaconing (OFF-40907)
* **Rule Triggered:** Anomaly: Regular Interval Outbound Connection (Beaconing Candidate)
* **Analysis:** 212 flows over a 6-hour window showing a strict 90-second heartbeat connection to an external IP (`185.220.101.44`) preceded by a high-entropy DNS query (`x7f2ak9v.dyn-update-cdn.net`).
* **MITRE ATT&CK:** Command and Control -> Dynamic Resolution (T1568) & Web Protocols (T1071.001)
* **Classification:** True Positive (Unconfirmed Impact / Pending Endpoint Telemetry)

### Offense 3: Sequential Port Scan Followed by Exploit Attempt (OFF-40922)
* **Rule Triggered:** Recon: Sequential Port Scan Followed by Exploit Signature
* **Analysis:** External source (`203.0.113.77`) performed a rapid port scan across 9 ports, followed 10 minutes later by an SQL injection payload (`UNION SELECT`) against a public-facing web app (`198.51.100.20`), resulting in an HTTP 500 Internal Server Error.
* **MITRE ATT&CK:** Reconnaissance -> Port Scanning (T1595) / Initial Access -> Exploit Public-Facing Application (T1190)
* **Classification:** True Positive (Failed Exploit Attempt)

### Offense 4: High-Entropy DNS Subdomain Exfiltration (OFF-40955)
* **Rule Triggered:** DNS: High Entropy Subdomain Volume to Single Parent Domain
* **Analysis:** An internal engineering host (`10.20.9.41`) generated 884 queries using unique, high-entropy subdomains requesting `TXT` records against a newly registered domain (`exfil-relay.io`).
* **MITRE ATT&CK:** Exfiltration -> Exfiltration Over Alternative Protocol (T1048.003)
* **Classification:** True Positive (Active Data Exfiltration)

---

## 🛠️ Skills & Methodologies Demonstrated
* **5-Step Manual Analysis Framework:** Parsing log data, establishing timelines, identifying root causes, assessing impact, and defining containment strategies.
* **SIEM Scoring Metrics:** Evaluating Offense Magnitude based on Severity, Credibility, and Relevance.
* **Incident Reporting:** Writing concise, executive-ready Tier-2 ticket summaries under strict word limits.
* **Telemetry Gap Analysis:** Determining required endpoint (EDR/Sysmon) and network (PCAP/Database Audit) telemetry to transition hypotheses into confirmed findings.

---

## 👤 Author
* **Muhammad Ibrahim**
* GitHub: [MIbrahimM67](https://github.com/MIbrahimM67)
