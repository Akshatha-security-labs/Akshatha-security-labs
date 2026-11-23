# Linux Directory Structure

## 1. Overview

Linux uses a hierarchical filesystem structure that starts from the root directory (`/`).

Understanding the directory structure helps administrators and security analysts locate system files, user data, configuration files and system logs.

## 2. Important Linux Directories

| Directory | Purpose |
|---|---|
| `/` | Root of the Linux filesystem |
| `/root` | Home directory of the root user |
| `/bin` | Contains essential command executables |
| `/usr` | Contains shared resources, applications and utilities |
| `/home` | Contains home directories of normal users |
| `/sbin` | Contains system binaries and administrative commands |
| `/etc` | Contains system and application configuration files |
| `/lib` | Contains libraries and dependencies required by programs |
| `/var` | Contains variable data, including logs |

## 3. Practical Commands

The following commands were used to explore the Linux filesystem:

```bash
# Display the current working directory
pwd

# List directories and files under the root filesystem
ls /

# Explore system configuration files
ls /etc

# Explore system log directories
ls /var/log
```

## 4. Security Operations Relevance

Understanding Linux directories is useful for SOC investigations:

- `/etc`: Configuration files can be examined when investigating unexpected system changes.
- `/var/log`: System and authentication logs can provide evidence of user activity and security events.
- `/home`: User directories can help identify files and activity associated with normal user accounts.
- `/root`: Contains files belonging to the privileged root account.

## 5. Key Takeaways

- The Linux filesystem starts from `/`.
- `/root` and `/home` serve different user accounts.
- `/etc` is important for system configuration.
- `/var/log` is an important location for security log investigations.
- Linux directory knowledge helps analysts navigate systems during investigations.

## 6. Practical Environment

- Operating System: Kali Linux
- Virtualization: Oracle VirtualBox
- Host Operating System: Windows 11

**Status:** Initial directory structure exploration and practical commands completed.
