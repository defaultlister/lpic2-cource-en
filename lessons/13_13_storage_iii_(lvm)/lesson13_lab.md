# Lesson 13 — 13 Storage III (LVM)

> pv/vg/lv create/extend/shrink, snapshots.

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

### LVM pv/vg/lv
```bash
sudo losetup -fP disk2.img || true
sudo pvcreate /dev/loop1 || true
sudo vgcreate vgdata /dev/loop1 || true
sudo lvcreate -n lv01 -L 1G vgdata || true
sudo mkfs.xfs /dev/vgdata/lv01 || true
```

## Verification
- Capture outputs into `lab13_results.txt`.
- Instructor validates state and answers.

## Troubleshooting
- `dmesg | tail` for device/kernel issues.
- `journalctl -u <service>` for services.
- Network: `ss -tulpen`, `tcpdump`, `nft list ruleset`.

## Challenge
Design/describe a small extension scenario and provide commands & outputs.
