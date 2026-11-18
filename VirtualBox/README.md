# Project 01 – Cybersecurity Home Lab Infrastructure

## 1. Project Overview

This project documents the design, installation and configuration of my cybersecurity home lab using Oracle VirtualBox.

The environment is used to practise Linux administration, network security, vulnerability assessment, SIEM operations and log analysis.

The lab includes Kali Linux, Ubuntu Linux, Metasploitable2, IBM QRadar and Splunk Enterprise. The Windows 11 host is also configured as a log source using Splunk Universal Forwarder.

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

### Virtual Machine Overview

The following screenshot shows the virtual machines configured in Oracle VirtualBox.

![VirtualBox VM Inventory](screenshots/virtualbox/virtualbox-vm-inventory.png)

## 4. Network Architecture

The lab uses different VirtualBox network modes depending on the purpose of each virtual machine.

- **NAT:** Provides network access to a virtual machine through VirtualBox's network address translation.
- **Bridged Adapter:** Connects a virtual machine through the physical network interface of the Windows host.
- **Internal Network:** Allows selected virtual machines to communicate through a private virtual network.

An Internal Network named `cyber-lab` is configured for Kali Linux, Ubuntu Linux and Metasploitable2 to support isolated lab communication.

For Splunk log forwarding:

- Kali Linux communicates with Ubuntu through the `cyber-lab` Internal Network.
- The Windows 11 host communicates with Ubuntu through the Bridged Network.
- Both systems forward events to the same Splunk Enterprise instance on Ubuntu using TCP port `9997`.
- Ubuntu also collects its own local system and Apache logs.

## 5. Network Configuration Details

The virtual machines use a combination of NAT, Bridged Adapter and Internal Network configurations.

Detailed network configuration and connectivity testing are documented separately:

- [Static IP Configuration](network-configuration/static-ip-configuration.md)
- [Network Connectivity Testing](network-configuration/connectivity-testing.md)

## 6. Splunk Integration

Splunk Enterprise is installed on Ubuntu Linux and acts as the central log collection and SIEM platform.

Splunk Universal Forwarder is installed on Kali Linux and the Windows 11 host to collect and forward logs to Ubuntu. Ubuntu also collects its own local system and Apache logs.

### Log Collection Overview

| Log Source | Collection Method | Splunk Index |
|---|---|---|
| Kali Linux | Splunk Universal Forwarder | `kalilogs` |
| Windows 11 | Splunk Universal Forwarder | `main` |
| Ubuntu Linux | Splunk Enterprise local monitoring | `mylogs` |

The receiving port on Ubuntu is TCP `9997`.

Log forwarding and ingestion have been validated across all three systems.

For detailed configuration, validation commands and screenshots, see [Splunk Log Forwarding and Ingestion](splunk/log-forwarding.md).

## 7. Security Considerations

Metasploitable2 is an intentionally vulnerable operating system designed for security testing.

Security precautions:

- Keep Metasploitable2 on an isolated Internal Network.
- Avoid connecting vulnerable machines directly to the home network.
- Restrict communication with vulnerable machines to the lab environment.
- Avoid exposing vulnerable services to external networks.
- Do not publish passwords, credentials, public IP addresses or sensitive configuration details.

## 8. Learning Outcomes

Through this project, I am developing practical experience in:

- Virtualisation and virtual machine management.
- VirtualBox networking modes: NAT, Bridged Adapter and Internal Network.
- Linux network interface configuration.
- IP address and default gateway identification.
- Network isolation for vulnerable testing environments.
- Splunk Universal Forwarder and Splunk Enterprise.
- Centralised log collection from Linux and Windows systems.
- SIEM monitoring and basic log analysis.

## 9. Future Improvements

- Document IP addressing and routing in greater detail.
- Practise Splunk Search Processing Language (SPL).
- Create Splunk dashboards and security alerts.
- Integrate additional log sources into SIEM platforms.
- Practise vulnerability assessment using Metasploitable2.
- Develop security monitoring and incident investigation use cases.
- Explore IBM QRadar configuration and log monitoring.

---

**Project Status:** Virtual machines installed, network configuration documented, connectivity between lab machines validated, and centralised Splunk log collection confirmed across Kali Linux, Ubuntu Linux and Windows 11. Further SIEM configuration, log analysis and security testing are ongoing.
