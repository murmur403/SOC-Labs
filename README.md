# SOC-Labs | Blue Team & Security Monitoring 🛡️

Hands-on cybersecurity laboratory focused on Security Operations Center (SOC) Level 1 activities, including security monitoring, log analysis, threat detection, and incident triage.

This repository documents practical investigations performed in an isolated virtual environment using Wazuh SIEM and Linux.

## Lab Architecture

The laboratory consists of two VirtualBox virtual machines connected through an isolated internal network.

| Component | Technology | IP Address |
|---|---|---|
| SIEM Server | Wazuh 4.14.0 | 192.168.100.10 |
| Monitored Endpoint | Kali Linux 2026.1 | 192.168.100.20 |
| Virtualization | Oracle VirtualBox | — |
| Internal Network | SOC-LAB | 192.168.100.0/24 |

Both virtual machines also use a separate NAT adapter for internet connectivity.

The Kali Linux endpoint runs a Wazuh agent that forwards monitored security events to the Wazuh server.

## Tools & Technologies

- **Wazuh SIEM:** Security event monitoring, alert detection, and investigation.
- **Kali Linux:** Monitored Linux endpoint and controlled security testing.
- **VirtualBox:** Virtualization and isolated laboratory networking.
- **OpenSSH:** SSH authentication testing and log generation.
- **Linux Journald:** System and authentication log analysis.
- **MITRE ATT&CK:** Security technique classification and contextual analysis.

## Documented Investigations

### SOC-001 — Sudo Event Analysis

**Wazuh Rule:** 5402

Investigation of a successful privileged command execution on a Linux endpoint.

The activity was confirmed as authorized administrative behavior.

[View SOC-001 Investigation](SOC-001-Sudo-Event/README.md)

### SOC-002 — SSH Failed Login Detection

**Wazuh Rule:** 5760

Controlled simulation of failed SSH authentication attempts, followed by log analysis and SIEM alert investigation.

The activity was classified as an authorized security test.

[View SOC-002 Investigation](SOC-002-SSH-Failed-Login/README.md)

## Investigation Methodology

Each laboratory follows a structured SOC Level 1 investigation workflow:

1. Generate or identify a security event.
2. Review the alert in Wazuh.
3. Analyze the original system logs.
4. Identify relevant users, IP addresses, commands, and timestamps.
5. Evaluate the security context and available evidence.
6. Classify the activity and determine whether escalation is required.
7. Document findings and supporting evidence.

## Learning Objectives

- Develop practical SOC Analyst Level 1 skills.
- Improve Linux security log analysis.
- Understand SIEM detection rules and alert severity.
- Practice distinguishing benign activity from suspicious behavior.
- Build a documented cybersecurity portfolio using real laboratory evidence.

## Security Disclaimer

All activities documented in this repository were performed in an isolated, authorized laboratory environment.

IP addresses, usernames, and hostnames belong to the laboratory infrastructure.

No unauthorized systems were targeted.

---

**Project Status:** Active — Additional security monitoring and incident investigation labs will be documented as the project progresses.
