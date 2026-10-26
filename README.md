# NETWORK-PERIMETER-LOG-ANALYSIS-PROJECT
THIS IS MY NETWORK PERIMETER LOG ANALYSIS HANDS ON PRACTICAL PROJECT
Perimeter Protection & Log Forensics Lab: Security Monitoring & Breach Analysis. A hands-on threat hunting and log analysis project focusing on perimeter defense, reconnaissance detection, credential attacks, command-and-control (C2) beaconing, lateral movement, and data exfiltration analysis using Linux command-line utilities.
Table of Contents
1. Project Overview
2. Log Sources & Analysis Scope
3. Tools & Technologies Used
4. Key Investigation Areas
5. Conclusion


📌 Project Overview
Network perimeter monitoring involves examining generated logs across firewalls, Web Application Firewalls (WAF), VPN gateways, and Intrusion Detection Systems (IDS). This project simulates a security analyst reviewing a month of perimeter logs to uncover adversary techniques, determine whether the perimeter was breached, track lateral movement, and identify data exfiltration attempts.


⚙️ Log Sources & Analysis Scope
Analyzed Log Artifacts:
- Firewall Logs (firewall.log): Inbound/outbound traffic logs, blocked port scans, and session records.
- WAF Logs (waf.log): Web application attack vectors and blocked source IP records.
- VPN Auth Logs (vpn_auth.log): Authentication attempts, success/failure statuses, target accounts, and assigned internal IP leases.
- IDS Alert Logs (ids_alerts.log / alert_file.log): Signature-based threat detections, Command-and-Control (C2) beaconing alerts, and suspicious payload activity.
🛠️ Tools & Technologies Used
- Linux CLI Utility Suite: (cat, grep, cut, uniq, sort, head) for rapid log parsing, filtering, frequency analysis, and pattern extraction.
- Log Analysis Techniques: Command-line text manipulation, IP correlation, port scanning identification, and timeline reconstruction.

🔍 Key Investigation Areas
- Reconnaissance & Port Scanning: Analyzing blocked connection requests across multiple ports (e.g., ports 21, 22, 23, 445, 4444) to identify probing external IPs and primary internal targets.
- Web & Gateway Attack Detection: Filtering WAF logs to isolate single-source IPs responsible for blocked web attacks, and parsing VPN logs to identify brute-force patterns and targeted user accounts (e.g., svc_backup).
- Breach Verification & Compromise Tracking: Tracking successful VPN logins, internal IP leases assigned to attackers, and subsequent lateral movement using protocols such as SMB.
- C2 Beaconing & Intrusion Analysis: Cross-referencing IDS alerts to discover internal hosts beaconing out to external Command-and-Control infrastructure.
- Data Exfiltration Investigation: Querying firewall logs for outbound connections from compromised internal hosts to external C2 IPs to confirm data exfiltration activity.

🛡️ Conclusion
Perimeter log analysis is essential for detecting early-stage reconnaissance and identifying successful network intrusions. Utilizing command-line text parsing utilities enables rapid correlation across disparate log sources—from firewalls to IDS alerts—allowing security analysts to reconstruct the entire attack lifecycle from initial probe to data exfiltration.
