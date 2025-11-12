# Lesson 02 — 02 Capacity Planning II

> Trend analysis, bottlenecks, iotop/lsof/sar.

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

### Bottlenecks & trending
```bash
iotop -b -n1 | head -n 10 || echo 'install iotop'
lsof -p 1 | head -n 5
sar -n DEV 1 5 || echo 'install sysstat'
```

## Verification
- Capture outputs into `lab02_results.txt`.
- Instructor validates state and answers.

## Troubleshooting
- `dmesg | tail` for device/kernel issues.
- `journalctl -u <service>` for services.
- Network: `ss -tulpen`, `tcpdump`, `nft list ruleset`.

## Challenge
Design/describe a small extension scenario and provide commands & outputs.
