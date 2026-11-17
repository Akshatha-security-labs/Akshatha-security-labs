
# Static IP Configuration – VirtualBox Cybersecurity Lab

## 1. Objective

Configure static IPv4 addresses for Kali Linux, Ubuntu Linux and Metasploitable2 within an isolated VirtualBox Internal Network named `cyber-lab`.

Actual IP addresses have been masked in this public documentation for privacy.

## 2. Lab Network Configuration

| Virtual Machine | Network Interface | IP Address | Network Mode |
|---|---|---|---|
| Kali Linux | eth0 | `NAT_IP` | NAT |
| Kali Linux | eth1 | `192.168.56.X` | Internal Network |
| Ubuntu Linux | enp0s3 | `HOME_NETWORK_IP` | Bridged Adapter |
| Ubuntu Linux | enp0s8 | `192.168.56.X` | Internal Network |
| Metasploitable2 | eth0 | `192.168.56.X` | Internal Network |

**Internal Network:** `cyber-lab`

**Subnet:** `192.168.56.0/24`

## 3. Kali Linux Configuration

NetworkManager (`nmcli`) was used to configure a static IP address on `eth1`.

```bash
sudo nmcli connection modify "Wired connection 2" \
  ipv4.method manual \
  ipv4.addresses <KALI_LAB_IP>/24 \
  ipv4.gateway "" \
  ipv4.dns "" \
  ipv4.never-default yes
```

The NAT interface (`eth0`) was left unchanged.

## 4. Ubuntu Linux Configuration

NetworkManager was used to configure a static IP address on `enp0s8`.

```bash
sudo nmcli connection modify "Wired connection 1" \
  ipv4.method manual \
  ipv4.addresses <UBUNTU_LAB_IP>/24 \
  ipv4.gateway "" \
  ipv4.dns "" \
  ipv4.never-default yes
```

The existing Bridged Adapter (`enp0s3`) configuration was preserved.

## 5. Metasploitable2 Configuration

The network configuration file `/etc/network/interfaces` was updated.

A backup was created before making changes:

```bash
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

Static IP configuration:

```text
auto eth0
iface eth0 inet static
    address <METASPLOITABLE_LAB_IP>
    netmask 255.255.255.0
```

The configuration was applied using:

```bash
sudo ifdown eth0 && sudo ifup eth0
```

## 6. Verification

The network interfaces were checked using:

**Kali and Ubuntu:**

```bash
ip -br addr
```

**Metasploitable2:**

```bash
ifconfig eth0
```

The configured lab addresses were confirmed.

## 7. Network Connectivity

Network connectivity between the virtual machines was tested successfully using ICMP ping.

For detailed test results and screenshots, see [Connectivity Testing](connectivity-testing.md).

## 8. Learning Outcomes

- Configured static IPv4 addresses on three Linux virtual machines.
- Used NetworkManager to manage network connection profiles.
- Learned traditional Linux network configuration using `/etc/network/interfaces`.
- Separated the isolated lab network from the home network.
- Verified network interfaces and IP addressing.

## 9. Pending Validation

- [ ] Reboot all three virtual machines.
- [ ] Verify that IP addresses persist after reboot.
- [ ] Repeat connectivity tests after reboot.

**Note:** Static configurations have been saved and activated. Persistence across a reboot has not yet been verified.
