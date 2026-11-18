# CIA Triad – Information Security

## Overview

The CIA Triad is a fundamental model of information security that describes three essential principles for protecting information and systems.

CIA stands for:

- **Confidentiality**
- **Integrity**
- **Availability**

These principles help organisations protect sensitive information, prevent unauthorised modifications and ensure that systems and services remain accessible to authorised users.

## 1. Confidentiality

Confidentiality ensures that information is accessible only to authorised individuals, systems or processes.

Its primary purpose is to prevent unauthorised access to sensitive information.

### Examples

- Protecting mobile phones with screen locks.
- Restricting access to sensitive files.
- Using encryption to protect information during transmission.
- Implementing authentication before granting access to systems.

### Security Techniques

- Authentication
- Access control
- Encryption
- Multi-factor authentication (MFA)

**Example scenario:**

An employee sends confidential information to another employee over a network. Encryption helps protect the information from being understood by unauthorised parties.

If an unauthorised person accesses confidential information, confidentiality has been compromised.

## 2. Integrity

Integrity ensures that information remains accurate, complete and protected against unauthorised modification.

Only authorised users or processes should be able to modify information.

### Examples

- Preventing unauthorised changes to files.
- Protecting financial transaction records.
- Ensuring system configuration files are not modified without permission.
- Verifying that downloaded files have not been altered.

### Security Techniques

- Access control and permissions.
- Authentication.
- Hashing.
- File integrity monitoring.

### Hashing and Integrity Verification

Hashing converts input data into a fixed-length value using a mathematical algorithm.

A file's hash can be calculated before and after transfer or storage. If the calculated hashes differ, the file may have been modified.

Common hashing algorithms include:

- SHA-256
- SHA-512
- MD5 (legacy; not recommended for security-sensitive integrity verification)

**Example scenario:**

A security analyst calculates the SHA-256 hash of a downloaded file and compares it with a trusted reference hash.

If both values match, this provides evidence that the file contents are unchanged relative to the reference.

If an unauthorised person modifies information, integrity may be compromised.

## 3. Availability

Availability ensures that systems, services and information remain accessible to authorised users whenever they are needed.

Organisations must maintain the availability of their critical IT infrastructure.

### Examples

- Keeping business applications operational.
- Maintaining access to company servers.
- Ensuring websites and services remain accessible.
- Maintaining reliable network connectivity.

### Security Techniques

- Regular backups.
- Redundant systems and infrastructure.
- Continuous monitoring.
- Disaster recovery planning.
- System maintenance.
- High availability configurations.

**Example scenario:**

An organisation hosts an important business application on a server. If the server becomes unavailable, employees cannot access the application.

Using redundant servers and maintaining backups can help improve service availability.

A Distributed Denial-of-Service (DDoS) attack is an example of a threat that can affect availability by overwhelming a service with traffic.

##  CIA Triad – Comparison

| Principle | Meaning | Example of a Security Breach |
|---|---|---|
| Confidentiality | Prevent unauthorised access to information | An attacker accesses confidential customer records. |
| Integrity | Prevent unauthorised modification of information | An attacker modifies financial records. |
| Availability | Ensure authorised users can access services | A DDoS attack makes a website unavailable. |

##  Additional Elements of Information Security

In addition to the CIA Triad, two important information security elements are Authentication and Non-repudiation.

### 1. Authentication

Authentication verifies the identity of a user or system before granting access.

Common authentication methods include:

- PIN-based authentication.
- Password-based authentication.
- Pattern-based authentication.
- Biometric authentication.
- Multi-factor authentication (MFA).

**Example:**

A user enters a password and completes an additional verification step before accessing a company application.

Authentication helps enforce access restrictions and supports confidentiality and integrity.

### 2. Non-repudiation

Non-repudiation provides evidence that a particular action or transaction occurred and can be attributed to the responsible party.

It helps prevent individuals from falsely denying actions they performed.

### Examples

- Digital signatures.
- Transaction records.
- Audit logs.
- Signed electronic documents.

**Example:**

A digitally signed document can provide evidence of who signed it and whether it has been modified after signing.

##  CIA Triad in a SOC Environment

SOC analysts help organisations identify security events that may affect confidentiality, integrity or availability.

| Security Principle | Example Security Event | SOC Investigation Focus |
|---|---|---|
| Confidentiality | Unauthorised access to sensitive data | Review authentication logs and access events. |
| Integrity | Unexpected modification of critical files | Examine file changes and relevant system logs. |
| Availability | Service disruption or DDoS activity | Investigate network traffic and service availability. |

### Practical SOC Relevance

- Monitor authentication events to identify possible unauthorised access.
- Investigate suspicious file modifications.
- Analyse network activity associated with service disruptions.
- Review security alerts that may indicate a compromise of sensitive information.

## Key Takeaways

- Confidentiality protects information from unauthorised access.
- Integrity protects information from unauthorised modification.
- Availability ensures that information and services remain accessible.
- Authentication verifies the identity of users and systems.
- Non-repudiation provides evidence of actions and transactions.

**Remember:**

CIA = Confidentiality + Integrity + Availability.

These principles form an important foundation for information security and security operations.
