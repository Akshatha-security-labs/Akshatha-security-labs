
# Project 01 – Cybersecurity Home Lab Infrastructure

## 1. Project Overview

This project documents the design, installation and configuration of my cybersecurity home lab using Oracle VirtualBox.

The environment is used to practise Linux administration, network security, vulnerability assessment, SIEM operations and log analysis.

The lab includes Kali Linux, Ubuntu Linux, Metasploitable2, IBM QRadar and Splunk Enterprise.

## 2. Host Environment

| Component | Configuration |
|---|---|
| Host Operating System | Windows 11 |
| Virtualisation Platform | Oracle VirtualBox |
| Lab Type | Virtualised cybersecurity environment |
| Network Configuration | NAT, Bridged Adapter and Internal Network |

## 3. Virtual Machine Inventory

| Virtual Machine | Purpose | Status |
|---|---|---|
| Kali Linux | Security testing, network scanning and Splunk Universal Forwarder | Installed |
| Ubuntu Linux | Linux administration and Splunk Enterprise | Installed |
| Metasploitable2 | Vulnerability assessment and penetration-testing practice | Installed |
| IBM QRadar | SIEM monitoring and security event investigation | Installed |

## 4. Network Architecture

The lab uses different VirtualBox network modes depending on the purpose of each virtual machine.

- **NAT:** Provides network access to a virtual machine through VirtualBox's network address translation.
- **Bridged Adapter:** Connects a virtual machine through the physical network interface of the Windows host.
- **Internal Network:** Allows selected virtual machines to communicate through a private virtual network.

An Internal Network named `cyber-lab` is configured for Kali Linux and Metasploitable2 to support isolated security testing.

Ubuntu hosts Splunk Enterprise and receives forwarded log data from Kali Linux.

## 5. Network Configuration Details

| Virtual Machine | Adapter | Network Mode | Network Name |
|---|---|---|---|
| Kali Linux | Adapter 1 | NAT | Default NAT |
| Kali Linux | Adapter 2 | Internal Network | cyber-lab |
| Ubuntu | Adapter 1 | Bridged Adapter | Physical Wi-Fi adapter |
| Metasploitable2 | Adapter 1 | Internal Network | cyber-lab |
| IBM QRadar | Adapter 1 | Bridged Adapter | Physical Wi-Fi adapter |

### IP Address Information

| Virtual Machine | IP Address | Status |
|---|---|---|
| Kali Linux | To be documented | Further validation |
| Ubuntu | 192.168.178.xxx | Verified (masked) |
| Metasploitable2 | To be documented | Further validation |
| IBM QRadar | To be documented | Further validation |

Private network addresses are masked in this public repository.

## 6. Splunk Integration

Splunk Enterprise is installed on Ubuntu Linux, while Splunk Universal Forwarder is installed on Kali Linux.

The Kali Universal Forwarder is configured to send log data to the Ubuntu Splunk Enterprise instance.

| Component | Configuration |
|---|---|
| Log Source | Kali Linux |
| Forwarder | Splunk Universal Forwarder |
| SIEM Server | Ubuntu Linux |
| SIEM Platform | Splunk Enterprise |
| Receiving Port | TCP 9997 |
| Forwarding Status | Active |
| Log Source | Linux system logs |

### Validation Performed

- Verified Splunk Enterprise service on Ubuntu.
- Verified Splunk Universal Forwarder service on Kali.
- Confirmed that Ubuntu was listening on TCP port 9997.
- Verified the active forwarding destination.
- Confirmed Kali and Ubuntu events were visible in Splunk Search & Reporting.
- Identified multiple Kali Linux log sources, including authentication, cron, kernel and system logs.

Detailed documentation:

[Splunk Log Forwarding and Analysis](splunk/log-forwarding.md)

## 7. Connectivity Testing

The following activities are part of the lab validation process:

- Check network interfaces on each virtual machine.
- Identify assigned IP addresses.
- Verify default gateway configuration.
- Validate Kali-to-Ubuntu Splunk communication.
- Test Kali-to-Metasploitable2 connectivity over `cyber-lab`.
- Verify QRadar network accessibility.

Splunk log forwarding has been validated. Other network connectivity tests will be documented as they are completed.

## 8. Security Considerations

Metasploitable2 is an intentionally vulnerable operating system designed for security testing.

Security precautions:

- Keep Metasploitable2 on an isolated Internal Network.
- Avoid connecting vulnerable machines directly to the home network.
- Use controlled communication between lab machines.
- Avoid exposing vulnerable services to external networks.
- Do not publish passwords, credentials, public IP addresses or sensitive configuration details.

## 9. Evidence and Screenshots

Screenshots are stored in the `screenshots` directory.

| Screenshot | Description |
|---|---|
| `splunk-log-ingestion.png` | Splunk search results showing Kali and Ubuntu events |
| `splunk-kali-log-analysis.png` | Kali Linux log source analysis in Splunk |

Additional screenshots will be added as network validation and SIEM configuration activities are completed.

## 10. Learning Outcomes

Through this project, I am developing practical experience in:

- Virtualisation and virtual machine management.
- VirtualBox networking modes: NAT, Bridged Adapter and Internal Network.
- Linux network interface configuration.
- IP address and default gateway identification.
- Network isolation for vulnerable testing environments.
- Splunk Universal Forwarder and Splunk Enterprise.
- Centralised log collection and basic log analysis.
- SIEM monitoring and security investigation.

## 11. Future Improvements

- Complete network connectivity testing between lab machines.
- Document IP addressing and routing.
- Configure additional Linux log sources.
- Create Splunk dashboards and security alerts.
- Integrate additional log sources into SIEM platforms.
- Practise vulnerability assessment using Metasploitable2.
- Develop security monitoring and incident investigation use cases.

---

**Project Status:** Virtual machines installed, initial network configuration documented, and Splunk log forwarding validated. Further network validation and security testing are ongoing.
