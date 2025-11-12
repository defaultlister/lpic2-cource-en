# Lesson 04 — 04 Linux Kernel II

> Kernel build workflow: menuconfig, bzImage, initramfs.

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

### Kernel build outline
```bash
## Ubuntu build deps
sudo apt install -y build-essential libncurses-dev bison flex libssl-dev libelf-dev || true
## Rocky build deps
sudo dnf groupinstall -y 'Development Tools' || true
sudo dnf install -y ncurses-devel bison flex elfutils-libelf-devel openssl-devel || true
echo 'make menuconfig && make -j$(nproc) && sudo make modules_install install'
```

## Verification
- Capture outputs into `lab04_results.txt`.
- Instructor validates state and answers.

## Troubleshooting
- `dmesg | tail` for device/kernel issues.
- `journalctl -u <service>` for services.
- Network: `ss -tulpen`, `tcpdump`, `nft list ruleset`.

## Challenge
Design/describe a small extension scenario and provide commands & outputs.
