# Security Controls

## 1. Overview

Security controls are safeguards, techniques, policies or measures implemented to protect an organisation's systems, networks, devices and information from security threats and attacks.

They help reduce security risks and prevent unauthorised access, misuse or damage.

The main security controls covered here are:

- Defence in Depth
- Administrative Controls
- Technical Controls
- Physical Controls

## 2. Defence in Depth

Defence in Depth is a security approach that uses multiple layers of protection instead of relying on a single security measure.

If one security layer is bypassed or compromised, additional layers can help protect the system or information.

### Example: Smartphone security

A smartphone may use:

- **Screen lock:** Prevents unauthorised people from accessing the device.
- **Application lock:** Adds another layer of protection for selected applications.

Even if someone can unlock the phone, an additional application lock can help protect sensitive information.

### Example: Account security

An online account may use both a username and password and two-factor authentication (2FA).

After entering the correct password, the user must provide an additional verification factor, such as a one-time password (OTP).

This provides another layer of protection if the password is compromised.

**Key point:** Defence in Depth reduces reliance on a single security control by combining multiple protective layers.

## 3. Administrative Controls

Administrative controls are policies, procedures and guidelines established by an organisation to manage security risks and guide employee behaviour.

Examples include:

| Control | Purpose |
|---|---|
| Password policies | Define requirements for creating and protecting passwords |
| USB device policies | Restrict the use of unauthorised external USB devices |
| Security policies | Establish rules for protecting company systems and information |
| Incident response plans | Define how security incidents should be handled |
| Incident response playbooks | Provide procedures for responding to specific types of attacks |

### Incident Response Playbooks

A playbook provides predefined steps for handling a particular security incident.

Examples include:

- Phishing attack playbook
- Malware attack playbook
- Denial-of-Service (DoS) attack playbook

When an incident is detected, the relevant playbook helps the security team follow an organised response process.

**Key point:** Administrative controls establish the rules and procedures that employees and security teams should follow.

## 4. Technical Controls

Technical controls use technology and security tools to protect systems, networks and devices.

Examples include:

| Control | Purpose |
|---|---|
| Firewall | Filters network traffic based on defined security rules |
| IDS (Intrusion Detection System) | Detects suspicious activity and generates alerts |
| IPS (Intrusion Prevention System) | Detects and can block suspicious activity |
| EDR (Endpoint Detection and Response) | Monitors and helps protect endpoint devices |
| Two-Factor Authentication (2FA) | Adds an additional authentication layer |

### Host-Based and Network-Based Firewalls

**Host-Based Firewall**

A host-based firewall protects an individual device or system by controlling its incoming and outgoing network traffic.

**Network-Based Firewall**

A network-based firewall protects a network by monitoring and controlling traffic entering or leaving that network.

Using both can provide additional protection. If network-level protection is bypassed, a host-based firewall may still help protect an individual device.

**Key point:** Technical controls use security technologies to detect, prevent or reduce security threats.

## 5. Physical Controls

Physical controls protect an organisation's buildings, equipment, facilities and infrastructure from unauthorised physical access.

Examples include:

| Control | Purpose |
|---|---|
| Biometric authentication | Verifies identity using biometric characteristics |
| PIN-based access | Requires an authorised access code |
| CCTV cameras | Monitor physical areas and help identify suspicious activity |
| Security guards | Monitor premises and help prevent unauthorised entry |
| Restricted access areas | Limit entry to authorised personnel |

### Example: Server Room Security

A company's server room contains critical infrastructure and requires physical protection.

Possible security measures include:

1. Biometric or PIN-based authentication at the entrance.
2. CCTV cameras to monitor activity.
3. Security personnel to monitor access to the premises.
4. Restricted access for authorised employees only.

These measures help protect servers and other infrastructure from unauthorised physical access.

**Key point:** Physical controls protect the organisation's physical assets and facilities.

## 6. Security Controls – Comparison

| Control Type | Main Focus | Examples |
|---|---|---|
| Defence in Depth | Multiple layers of protection | Screen lock, application lock, 2FA |
| Administrative | Policies and procedures | Password policies, USB policies, incident response plans |
| Technical | Technology-based protection | Firewalls, IDS, IPS, EDR |
| Physical | Physical security | CCTV, biometrics, security guards |

## 7. Practical Relevance in a SOC

Security controls support an organisation's overall security strategy.

A SOC analyst should understand the purpose of these controls when reviewing security events and investigating alerts.

Examples:

- Reviewing authentication alerts related to repeated failed login attempts.
- Investigating suspicious network activity detected by security tools.
- Reviewing endpoint alerts generated by EDR solutions.
- Understanding whether an incident may involve unauthorised access to systems or facilities.
- Following the organisation's incident response procedures and relevant playbooks.

## 8. Key Takeaways

- Security controls help protect organisational systems, networks, devices and information.
- Defence in Depth uses multiple layers of security.
- Administrative controls establish security policies and procedures.
- Technical controls use security tools and technologies.
- Physical controls protect facilities, equipment and infrastructure.
- Combining different types of controls provides broader protection against security threats.
