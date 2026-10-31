Project 01 – Cybersecurity Home Lab Infrastructure

1. Project Overview

This project documents the design, installation and configuration of my cybersecurity home lab using Oracle VirtualBox.

The environment is used to practise Linux administration, network security, vulnerability assessment and SIEM operations.

2. Host Environment

Component                    Configuration
Host OS                      Windows 11
Virtualisation               Oracle VirtualBox
Lab Type                     Virtualized cybersecurity environment
Current Network Mode         Bridged Adapter

3. Virtual Machine Inventory

Virtual Machine| Purpose| Status
Kali Linux| Security testing and network scanning| Installed
Ubuntu Linux| Linux administration| Installed
Metasploitable| Vulnerability assessment| Installed
IBM QRadar| SIEM monitoring and investigation| Installed

4. Network Architecture

The current lab uses Bridged Adapter networking.

This allows virtual machines to connect through the physical network interface of the Windows host.

Individual VM network configurations and IP addresses will be documented after validation.

5. Network Configuration Details

VM| Network Mode| IP Address
Kali Linux| To be verified| To be recorded
Ubuntu| To be verified| To be recorded
Metasploitable| To be verified| To be recorded
IBM QRadar| To be verified| To be recorded

6. Connectivity Testing

Planned validation activities:

- Check network interfaces on each VM.
- Identify assigned IP addresses.
- Verify default gateway configuration.
- Test Kali-to-Ubuntu connectivity.
- Test Kali-to-Metasploitable connectivity.
- Verify QRadar network accessibility.

7. Security Considerations

Metasploitable is an intentionally vulnerable operating system.

A dedicated isolated virtual network is recommended for vulnerability assessment exercises.

Bridged networking should not be used for Metasploitable in the recommended lab configuration.

8. Evidence and Screenshots

Screenshots to be added:

- VirtualBox Manager showing installed VMs.
- Kali Linux network configuration.
- Ubuntu network configuration.
- Metasploitable network configuration.
- IBM QRadar network configuration.
- Connectivity test results.

9. Learning Outcomes

- Understanding virtualisation and virtual machines.
- Understanding Bridged, NAT and Host-only networking.
- Configuring virtual network adapters.
- Identifying IP addresses and default gateways.
- Testing connectivity between virtual machines.
- Designing a safer cybersecurity home lab.

10. Future Improvements

- Configure an isolated Host-only lab network.
- Separate vulnerable targets from the home network.
- Configure controlled network communication.
- Integrate SIEM monitoring with lab systems.
- Document security testing and investigation exercises.
