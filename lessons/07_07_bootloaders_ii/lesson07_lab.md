# Lesson 07 — 07 Bootloaders II

> PXE/SYSLINUX basics.

## Goal
Gain hands-on mastery of the topic with dual-distro commands (Ubuntu 24.04 LTS & Rocky Linux 9).

## Environment Setup
- Ubuntu 24.04 LTS: `sudo apt update && sudo apt install -y net-tools dnsutils bind9-utils xfsprogs e2fsprogs smartmontools lvm2 nfs-common samba`
- Rocky Linux 9: `sudo dnf install -y iproute bind-utils xfsprogs e2fsprogs smartmontools lvm2 nfs-utils samba`

## Tasks

### Baseline system info
```bash
uname -a
cat /etc/os-release
uptime && free -h && df -h
```

### PXE/SYSLINUX (theory)
```bash
echo '/tftpboot, pxelinux.0, DHCP opts 66/67; grub2-pxe for UEFI'
```

## Verification
- Capture outputs into `lab07_results.txt`.
- Instructor validates state and answers.

## Troubleshooting
- `dmesg | tail` for device/kernel issues.
- `journalctl -u <service>` for services.
- Network: `ss -tulpen`, `tcpdump`, `nft list ruleset`.

## Challenge
Design/describe a small extension scenario and provide commands & outputs.
