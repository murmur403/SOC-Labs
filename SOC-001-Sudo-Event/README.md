# SOC-001 — Sudo Event Analysis

## 1. Objective

Investigate a Linux privilege escalation-related event detected by Wazuh and determine whether the activity is legitimate or suspicious.

## 2. Lab Environment

- **SIEM:** Wazuh 4.14.0
- **Endpoint:** Kali Linux 2026.1
- **Agent:** murmur-kali
- **Agent IP:** 192.168.100.20
- **Wazuh Manager IP:** 192.168.100.10
- **Virtualization:** VirtualBox

## 3. Alert Information

| Field | Value |
|---|---|
| Rule ID | 5402 |
| Rule Description | Successful sudo to ROOT executed. |
| Source User | murmur |
| Target User | root |
| Event Type | Successful sudo execution |

## 4. Log Evidence

```text
Nov 22 19:27:08 kali sudo[16686]: murmur : TTY=pts/0 ; PWD=/home/murmur ; USER=root ; COMMAND=/usr/bin/systemctl status wazuh-agent --no-pager
```

## 5. Investigation

The Wazuh alert was triggered when the user `murmur` executed a command with elevated privileges.

The command was:

```bash
sudo systemctl status wazuh-agent --no-pager
```

This command checks the status of the Wazuh agent service.

The investigation confirmed that:

- The command was executed by the expected laboratory user.
- The command was used to verify the Wazuh agent status.
- The activity was performed intentionally during laboratory setup.
- No malicious activity was identified in the reviewed event.

## 6. Conclusion

**Classification:** Benign — Authorized Administrative Activity

**Incident Confirmed:** No

**Escalation Required:** No

The alert correctly identified a successful sudo execution. However, the activity was expected and authorized within the laboratory environment.

## 7. Skills Demonstrated

- SIEM alert investigation
- Linux log analysis
- Wazuh rule interpretation
- Privileged command analysis
- Security event classification
- SOC Level 1 triage
