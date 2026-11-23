# Linux Authentication Log Analysis

## 1. Overview

Linux authentication logs provide information about authentication-related activities, user sessions and privilege-related operations.

In this practical exercise, I explored authentication logs on Kali Linux and used command-line tools to identify password verification failures and session activity.

## 2. Log File Location

Authentication log file:

```bash
/var/log/auth.log
```

Display the latest 10 entries:

```bash
sudo tail -n 10 /var/log/auth.log
```

The observed entries included:
- User session activity.
- Sudo command execution.
- Password verification failures.

## 3. Investigating Password Verification Failures

To search for password verification failures:

```bash
sudo grep -ai "password check failed" /var/log/auth.log
```

During the practical exercise, I deliberately entered an incorrect password on my own Kali login screen.

The resulting log entries contained:

- Process: `unix_chkpwd`
- Affected user: `kali`
- Event: `password check failed`

Count matching entries:

```bash
sudo grep -ai "password check failed" /var/log/auth.log | wc -l
```

**Observation:** Two matching entries were identified during the later count exercise.

These events were generated during controlled testing on my own virtual machine.

## 4. Grep Command Options Practised

| Option | Description |
|---|---|
| `-i` | Ignore case differences |
| `-a` | Treat binary data as text |
| `-v` | Display lines that do not match |
| `-w` | Match whole words |
| `-E` | Use extended regular expressions |

## 5. Log Investigation Commands

### Search for sudo activity

```bash
sudo grep -i "sudo:" /var/log/auth.log
```

### Search for successful user sessions

```bash
sudo grep -ai "session opened for user kali" /var/log/auth.log
```

### Search for SSH-related entries

```bash
sudo grep -ai "ssh" /var/log/auth.log
```

No matching SSH entries were found in the inspected log.

### Exclude entries containing sudo

```bash
sudo grep -avi "sudo:" /var/log/auth.log
```

### Search for failed or opened events

```bash
sudo grep -aiE "failed|opened" /var/log/auth.log
```

### Count matching entries

```bash
sudo grep -ai "password check failed" /var/log/auth.log | wc -l
```

## 6. Understanding Pipes

The pipe operator (`|`) passes the output of one command to another command.

Example:

```bash
sudo grep -ai "password check failed" /var/log/auth.log | wc -l
```

In this example:
1. `grep` searches for matching log entries.
2. `wc -l` counts the matching lines.

## 7. SOC Analyst Relevance

Authentication log analysis helps security analysts:

- Identify password verification failures.
- Investigate user session activity.
- Examine privilege-related activity.
- Filter large log files for relevant events.
- Count matching events for further investigation.

Repeated authentication failures may require further investigation. A failed password entry alone does not establish a brute-force attack. Analysts should examine timestamps, frequency, affected accounts and other available event details.

## 8. Practical Environment

- Operating System: Kali Linux
- Virtualization: Oracle VirtualBox
- Host Operating System: Windows 11
- Log Source: `/var/log/auth.log`

## 9. Key Takeaways

- Authentication logs are useful for investigating user activity.
- `grep` helps filter relevant log entries.
- `wc -l` counts matching lines.
- Pipes connect commands and allow combined analysis.
- Log context is important when interpreting security events.

**Status:** Authentication log exploration and grep practical exercises completed.
