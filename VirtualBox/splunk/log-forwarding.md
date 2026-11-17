
# Project 01: Splunk Log Forwarding and Log Analysis

## 1. Project Overview

This project demonstrates centralized log collection and analysis using Splunk Universal Forwarder and Splunk Enterprise in a VirtualBox cybersecurity lab.

Kali Linux is configured as the log source with Splunk Universal Forwarder installed. Ubuntu Linux hosts Splunk Enterprise and receives forwarded log data from Kali.

The objective is to collect Linux system logs, forward them to a centralized SIEM platform, and analyse the collected events using Splunk Search & Reporting.

### Project Objectives

- Install and configure Splunk Universal Forwarder on Kali Linux.
- Install and run Splunk Enterprise on Ubuntu Linux.
- Configure centralized log forwarding.
- Verify communication using TCP port 9997.
- Monitor Linux system logs.
- Search and analyse collected events using Splunk Search & Reporting.
- Validate successful log ingestion.

---

## 2. Lab Environment

| Component | Configuration |
|---|---|
| Host Operating System | Windows 11 |
| Virtualisation Platform | Oracle VirtualBox |
| Log Source | Kali Linux |
| Log Forwarder | Splunk Universal Forwarder |
| SIEM Server | Ubuntu Linux |
| SIEM Platform | Splunk Enterprise |
| Communication Protocol | TCP |
| Receiving Port | 9997 |
| Ubuntu IP Address | 192.168.178.xxx (masked) |

### Virtual Machine Details

| Virtual Machine | Purpose |
|---|---|
| Kali Linux | Security testing and log generation |
| Ubuntu Linux | Splunk Enterprise and centralized log collection |

---

## 3. Installation Details

### Kali Linux – Splunk Universal Forwarder

Splunk Universal Forwarder was installed on Kali Linux.

Installation directory:

```bash
/opt/splunkforwarder
```

The Universal Forwarder collects configured log files and forwards events to the Splunk Enterprise instance running on Ubuntu.

### Ubuntu Linux – Splunk Enterprise

Splunk Enterprise was installed on Ubuntu Linux.

Installation directory:

```bash
/opt/splunk
```

Ubuntu acts as the centralized log collection and analysis server.

---

## 4. Network and Forwarding Configuration

The Splunk Universal Forwarder on Kali Linux is configured to send log data to Splunk Enterprise on Ubuntu.

| Parameter | Configuration |
|---|---|
| Source Machine | Kali Linux |
| Destination Machine | Ubuntu Linux |
| Destination IP | 192.168.178.xxx (masked) |
| Destination Port | 9997 |
| Protocol | TCP |
| Forwarding Status | Active |

### Network Architecture

```text
              Windows 11 Host
                     |
              Oracle VirtualBox
                     |
          +----------+----------+
          |                     |
      Kali Linux             Ubuntu Linux
          |                     |
  Splunk Universal          Splunk Enterprise
     Forwarder                    |
          |                       |
          +----- TCP 9997 --------+
              Log Forwarding
```

---

## 5. Service and Port Validation

### 5.1 Ubuntu – Splunk Enterprise Status

Command:

```bash
sudo /opt/splunk/bin/splunk status
```

Observed result:

```text
splunkd is running
splunk helpers are running
```

Result: Splunk Enterprise was running successfully.

### 5.2 Ubuntu – Receiving Port Validation

Command:

```bash
sudo ss -lntp | grep 9997
```

Observed result:

```text
LISTEN 0 128 0.0.0.0:9997 0.0.0.0:* users:(("splunkd",...))
```

Result: Splunk Enterprise was listening on TCP port 9997 for incoming forwarded data.

### 5.3 Kali Linux – Universal Forwarder Status

Command:

```bash
sudo /opt/splunkforwarder/bin/splunk status
```

Observed result:

```text
splunkd is running
splunk helpers are running
```

Result: Splunk Universal Forwarder was running successfully.

### 5.4 Kali Linux – Forwarding Destination Validation

Command:

```bash
sudo /opt/splunkforwarder/bin/splunk list forward-server
```

Observed result:

```text
Active forwards:
    192.168.178.xxx:9997

Configured but inactive forwards:
    None
```

Result: The Ubuntu Splunk destination appeared under Active forwards.

---

## 6. Log Ingestion Validation

Splunk Search & Reporting was used to verify the incoming events.

### Search Query

```spl
index=* host=* | stats count by host, source, sourcetype
```

The search results displayed events from the Kali Linux and Ubuntu hosts.

### Observed Host Summary

| Host | Event Count | Percentage |
|---|---:|---:|
| Kali | 12 | 75% |
| Ubuntu | 4 | 25% |
| Total | 16 | 100% |

These counts represent the captured search results at that stage of validation.

### Validation Result

- Kali Linux events were visible in Splunk.
- Ubuntu Linux events were visible in Splunk.
- The log source `/var/log/syslog` was identified.
- Kali NetworkManager events appeared in the search results.

This provided evidence that events from both hosts were available in Splunk Search & Reporting.

---

## 7. Kali Linux – Log Source Analysis

A further Splunk search was performed to examine the different log sources collected from Kali Linux.

### Search Query

```spl
index=* host=kali | stats count by host, source, sourcetype
```

### Observed Search Results

The captured search returned 76 matching events across four log sources.

| Host | Log Source | Sourcetype | Event Count |
|---|---|---|---:|
| kali | /var/log/auth.log | auth-3 | 2 |
| kali | /var/log/cron.log | cron-too_small | 1 |
| kali | /var/log/kern.log | kern-3 | 3 |
| kali | /var/log/syslog | syslog | 70 |
| **Total** | | | **76** |

### Log Source Description

| Log File | Purpose |
|---|---|
| `/var/log/auth.log` | Authentication-related events |
| `/var/log/cron.log` | Scheduled task and cron-related events |
| `/var/log/kern.log` | Linux kernel-related events |
| `/var/log/syslog` | General system and service logs |

The results demonstrated that multiple Kali Linux system log sources were being collected and made searchable in Splunk.

---

## 8. Screenshots and Evidence

Screenshots are stored in the `screenshots/splunk` directory.

| Screenshot | Description |
|---|---|
| `virtualbox-manager.png` | VirtualBox virtual machine inventory |
| `kali-network.png` | Kali Linux network configuration |
| `ubuntu-network.png` | Ubuntu Linux network configuration |
| `splunk-log-ingestion.png` | Splunk search results showing Kali and Ubuntu events |
| `splunk-kali-log-analysis.png` | Kali Linux log source analysis in Splunk |

### Evidence 1 – Splunk Log Ingestion

![Splunk Log Ingestion](../screenshots/splunk/splunk-log-ingestion.png)

### Evidence 2 – Kali Linux Log Source Analysis

![Kali Linux Log Analysis](../screenshots/splunk/splunk-kali-log-analysis.png)
## 9. Learning Outcomes

Through this project, I gained practical experience in:

- Installing and managing Splunk Universal Forwarder.
- Operating Splunk Enterprise on Ubuntu Linux.
- Configuring centralized log forwarding.
- Understanding Splunk receiving ports and TCP communication.
- Checking Linux network interfaces and IP addresses.
- Verifying Splunk services and listening ports.
- Validating forwarding destinations.
- Searching and analysing Linux system logs.
- Identifying different log sources and sourcetypes.
- Using Splunk Search & Reporting for basic log analysis.

---

## 10. Future Improvements

- Collect additional Linux authentication and system logs.
- Create dashboards for system and security monitoring.
- Develop alerts for failed authentication attempts.
- Investigate suspicious network activity.
- Integrate additional lab machines as log sources.
- Explore security event correlation and detection use cases.

---

## Project Status

**Completed:** Initial Splunk Universal Forwarder setup, forwarding destination validation, receiving port verification, and log ingestion validation.

**Future work:** Additional log collection, dashboards, security alerts, and integration with other lab machines.
