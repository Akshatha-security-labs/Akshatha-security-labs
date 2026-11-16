
# Project 01: Splunk Log Forwarding – Kali Linux to Ubuntu

## 1. Project Overview

This project demonstrates centralized log collection using Splunk Universal Forwarder and Splunk Enterprise in a VirtualBox cybersecurity lab.

Kali Linux acts as the log source, while Ubuntu hosts Splunk Enterprise and receives forwarded log data.

### Objectives
- Install and configure Splunk Universal Forwarder.
- Forward Linux system logs from Kali Linux to Ubuntu.
- Configure and verify Splunk receiving port 9997.
- Monitor and search collected logs using Splunk Search & Reporting.
- Validate successful log ingestion.

## 2. Lab Environment

| Component | Configuration |
|---|---|
| Host Operating System | Windows 11 |
| Virtualisation Platform | Oracle VirtualBox |
| Log Source | Kali Linux |
| Log Forwarder | Splunk Universal Forwarder |
| SIEM Server | Ubuntu Linux |
| SIEM Platform | Splunk Enterprise |
| Network Protocol | TCP |
| Receiving Port | 9997 |
| Ubuntu IP Address | 192.168.178.xxx (masked for public documentation) |

## 3. Installation Details

### Kali Linux – Splunk Universal Forwarder

Installation directory:

```bash
/opt/splunkforwarder
```

### Ubuntu – Splunk Enterprise

Installation directory:

```bash
/opt/splunk
```

## 4. Network and Forwarding Configuration

The Splunk Universal Forwarder on Kali Linux is configured to send data to the Splunk Enterprise instance on Ubuntu.

| Parameter | Configuration |
|---|---|
| Source | Kali Linux |
| Destination | Ubuntu |
| Destination IP | 192.168.178.xxx (masked) |
| Destination Port | 9997 |
| Protocol | TCP |
| Forwarding Status | Active |

## 5. Service Validation

### Ubuntu – Splunk Enterprise

Check Splunk service status:

```bash
sudo /opt/splunk/bin/splunk status
```

**Observed result:** Splunk Enterprise was running.

Verify the receiving port:

```bash
sudo ss -lntp | grep 9997
```

**Observed result:** Splunk was listening on TCP port 9997.

### Kali Linux – Splunk Universal Forwarder

Check the forwarder service:

```bash
sudo /opt/splunkforwarder/bin/splunk status
```

**Observed result:** Splunk Universal Forwarder was running.

Verify the forwarding destination:

```bash
sudo /opt/splunkforwarder/bin/splunk list forward-server
```

**Observed result:**
- Ubuntu destination appeared under Active forwards.
- No configured but inactive forwarding destinations were reported.

## 6. Log Ingestion Validation

Splunk Search & Reporting was used to verify incoming events.

Search query:

```spl
index=* | stats count by host, source, sourcetype
```

**Observed results in the captured search:**

| Host | Event Count |
|---|---:|
| Kali | 12 |
| Ubuntu | 4 |

The search results also displayed:

- Host: `kali`
- Host: `ubuntu`
- Source: `/var/log/syslog`
- Kali NetworkManager events

This confirmed that events from Kali and Ubuntu were visible in Splunk.

## 7. Network Architecture

```text
Windows 11 Host
      |
 Oracle VirtualBox
      |
      +----------------------+
      |                      |
  Kali Linux              Ubuntu Linux
      |                      |
 Splunk Universal         Splunk Enterprise
 Forwarder                     |
      |                        |
      +---- TCP Port 9997 -----+
```

## 8. Evidence and Screenshots

Screenshots are stored in the `screenshots` directory.

| Screenshot | Description |
|---|---|
| `virtualbox-manager.png` | Virtual machine inventory |
| `kali-network.png` | Kali network configuration |
| `ubuntu-network.png` | Ubuntu network configuration |
| `splunk-log-ingestion.png` | Splunk search results showing Kali and Ubuntu events |

## 9. Learning Outcomes

Through this project, I practised:

- Installing and managing Splunk Universal Forwarder.
- Operating Splunk Enterprise on Ubuntu.
- Configuring centralized log forwarding.
- Checking Linux network interfaces and IP addresses.
- Verifying Splunk services and listening ports.
- Validating log ingestion using Splunk Search & Reporting.
- Investigating Linux system and NetworkManager logs.

## 10. Future Improvements

- Collect authentication logs and additional Linux system logs.
- Create dashboards for security monitoring.
- Develop alerts for failed login attempts.
- Investigate suspicious network activity.
- Integrate additional lab machines as log sources.
