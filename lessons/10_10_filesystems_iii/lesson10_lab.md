# Lesson 10 — 10 Filesystems III

> AutoFS, loop devices, LUKS.

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

### LUKS loop
```bash
dd if=/dev/zero of=~/luks.img bs=1M count=256
printf 'YES' | cryptsetup luksFormat ~/luks.img || true
cryptsetup open ~/luks.img luksloop || true
mkfs.ext4 /dev/mapper/luksloop || true
```

## Verification
- Capture outputs into `lab10_results.txt`.
- Instructor validates state and answers.

## Troubleshooting
- `dmesg | tail` for device/kernel issues.
- `journalctl -u <service>` for services.
- Network: `ss -tulpen`, `tcpdump`, `nft list ruleset`.

## Challenge
Design/describe a small extension scenario and provide commands & outputs.
