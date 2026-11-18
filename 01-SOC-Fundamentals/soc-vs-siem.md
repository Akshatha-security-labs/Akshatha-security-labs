# SOC vs SIEM

## 1. What is a SOC?

A Security Operations Centre (SOC) is a centralised team or unit responsible for monitoring, detecting, analysing and responding to cybersecurity threats.

SOC analysts monitor security events, investigate alerts, identify suspicious activities and support incident response.

### Main Responsibilities

- Monitor network and system activities.
- Detect suspicious or malicious activities.
- Analyse security alerts.
- Identify Indicators of Compromise (IoCs).
- Investigate potential security incidents.
- Escalate incidents when necessary.
- Document investigation findings.

## 2. What is SIEM?

Security Information and Event Management (SIEM) is a technology platform used to collect and analyse security logs from different sources.

A SIEM platform helps security analysts identify suspicious patterns and generates alerts based on configured rules and detection logic.

### Main Functions

- Collect logs from different systems and devices.
- Centralise security-related information.
- Normalise and analyse log data.
- Correlate events from multiple sources.
- Generate alerts for suspicious activities.
- Support security investigations.

## 3. SOC vs SIEM – Key Differences

| SOC | SIEM |
|---|---|
| A team or operational function | A security technology platform |
| Monitors and investigates threats | Collects and analyses security logs |
| Makes investigation and response decisions | Generates alerts based on detection logic |
| Consists of people and processes supported by technology | Supports SOC analysts with security data |

## 4. Example from a SOC Environment

Imagine multiple failed login attempts occur on a company server.

1. The SIEM collects authentication logs from the server.
2. The SIEM detects repeated failed login attempts based on a configured rule.
3. An alert is generated.
4. A SOC L1 Analyst reviews the alert.
5. The analyst checks the source IP, username, timestamps and related events.
6. The analyst determines whether the activity is suspicious and escalates it if necessary.

## 5. Key Takeaway

A SOC is the team responsible for security monitoring and incident response. SIEM is one of the important technologies that helps the SOC collect, analyse and investigate security events.

**Remember:** SOC is the team; SIEM is the tool.
