# Wazuh-OpenCanary-SOC-Lab
Honeypot-based threat detection and SIEM monitoring using OpenCanary and Wazuh.


# OpenCanary-Wazuh-SOC-Lab

## Overview

This project demonstrates a Security Operations Center (SOC) lab by integrating **OpenCanary Honeypot** with **Wazuh SIEM** for real-time threat detection and monitoring.

OpenCanary simulates vulnerable network services such as **HTTP** and **SSH**. When an attacker performs activities like an **Nmap scan** or attempts to access these services, OpenCanary generates security logs. Wazuh collects these logs, applies custom detection rules, and displays alerts on the Wazuh Dashboard.

---

## Project Objectives

- Deploy and configure OpenCanary as a honeypot.
- Detect suspicious HTTP and SSH activities.
- Integrate OpenCanary logs with Wazuh SIEM.
- Create custom Wazuh rules for OpenCanary events.
- Monitor and investigate security alerts through the Wazuh Dashboard.

---

## Architecture

```text
               Kali Linux (Attacker)
                      |
          Nmap Scan / HTTP / SSH
                      |
                      v
          OpenCanary Honeypot (Ubuntu)
                      |
          JSON Logs (/var/tmp/opencanary.log)
                      |
                      v
                 Wazuh Manager
                      |
              Custom Detection Rules
                      |
                      v
               Wazuh Dashboard
```

---

## Technologies Used

- Ubuntu Linux
- Kali Linux
- Wazuh SIEM
- OpenCanary
- Nmap
- Python
- JSON
- XML
- VMware Workstation

---

## How the Project Works

1. OpenCanary runs on the Ubuntu machine and simulates HTTP and SSH services.
2. Kali Linux is used to simulate attacker activity using Nmap or by connecting to the fake services.
3. OpenCanary records these activities in JSON log format.
4. Wazuh monitors the OpenCanary log file.
5. Custom Wazuh rules detect HTTP and SSH events.
6. Security alerts are displayed on the Wazuh Dashboard.

---

## Custom Wazuh Rules

Two custom rules were created:

| Rule ID | Description |
|---------|-------------|
| 100100 | Detects OpenCanary SSH activity |
| 100101 | Detects OpenCanary HTTP activity |

The rules are stored in:

```text
configs/local_rules.xml
```

---

## Testing

### Network Scan

```bash
nmap -sV <Ubuntu-IP>
```

### HTTP Service

Open in a browser:

```text
http://<Ubuntu-IP>:8081
```

These activities generate OpenCanary logs that are detected by Wazuh.

---

## Repository Structure

```text
OpenCanary-Wazuh-SOC-Lab/
│
├── README.md
├── configs/
│   └── local_rules.xml
│
├── screenshots/
│   ├── 01-wazuh-dashboard.png
│   ├── 02-http-alert.png
│   ├── 03-ssh-alert.png
│   ├── 04-nmap-scan.png
│   └── 05-opencanary-log.png
│
└── docs/
    └── project-report.pdf
```

---


## Results

- Successfully deployed OpenCanary as a honeypot.
- Integrated OpenCanary logs with Wazuh SIEM.
- Created custom Wazuh rules for HTTP and SSH detection.
- Generated real-time alerts for simulated attacker activities.
- Demonstrated an end-to-end SOC monitoring workflow.

---

## Future Enhancements

- Add FTP, SMB, and Telnet honeypot services.
- Integrate email or Slack notifications.
- Map alerts to the MITRE ATT&CK framework.
- Implement automated incident response.

---

## Disclaimer

This project was developed for educational purposes in a controlled virtual lab environment. All attack simulations were performed on systems owned and managed by the project author.
