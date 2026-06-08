# NetHunter Kernel for LG K10 (m216)

[![Build NetHunter Kernel](https://github.com/abdotch/android_kernel_lge_msm8916/actions/workflows/build.yml/badge.svg)](https://github.com/abdotch/android_kernel_lge_msm8916/actions/workflows/build.yml)

Custom Kali NetHunter kernel for the LG K10 (m216 / K420 series) with HID attacks, WiFi injection, and external adapter support.

## 📱 Device Info

| Spec | Detail |
|------|--------|
| **Device** | LG K10 (K420N/K420DS/K420) |
| **Codename** | m216 |
| **Chipset** | Qualcomm MSM8916 Snapdragon 410 |
| **CPU** | Quad-core 1.2 GHz Cortex-A53 |
| **GPU** | Adreno 306 |
| **RAM** | 1.5GB / 2GB |
| **Kernel** | 3.10.49-NetHunter |

## ⚡ Features

- ✅ **HID Keyboard Attacks** (BadUSB / Rubber Ducky)
- ✅ **HID Mouse Attacks**
- ✅ **mac80211 Packet Injection**
- ✅ **Monitor Mode Support**
- ✅ **RTL8188EUS Driver** (TP-Link WN722N v2/v3, etc.)
- ✅ **RTL8812AU Driver** (ALFA AWUS036ACH, etc.)
- ✅ **WireGuard Support**
- ✅ Based on LineageOS 14.1 kernel

## 🚀 Quick Start

### Download Pre-built Kernel

Go to [Actions](https://github.com/abdotch/android_kernel_lge_msm8916/actions) → Latest workflow run → Download artifacts.

### Flash on Device

```bash
# Reboot to TWRP
adb reboot recovery

# Push kernel zip
adb push anykernel-NetHunter.zip /sdcard/

# In TWRP:
# 1. Backup Boot partition
# 2. Flash anykernel-NetHunter.zip
# 3. Wipe cache/dalvik
# 4. Reboot
🔨 Build from Source
Automated (GitHub Actions)
Fork this repo

Go to Actions → Enable workflows

Run "Build NetHunter Kernel" workflow

Download artifacts

Manual Build
bash
# Clone
git clone https://github.com/abdotch/android_kernel_lge_msm8916.git -b cm-14.1
cd android_kernel_lge_msm8916

# Run build script
chmod +x build_nethunter_m216.sh
./build_nethunter_m216.sh
Requirements
Ubuntu 20.04 (has ncurses5)

GCC 4.9 ARM toolchain (Linaro)

build-essential, flex, bison, bc

bash
# Install dependencies
sudo apt install -y build-essential bc flex bison git wget \
    libncurses5 libncurses5-dev patch

# Download toolchain
wget https://releases.linaro.org/components/toolchain/binaries/4.9-2017.01/arm-linux-gnueabihf/gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
tar xf gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf.tar.xz
export CROSS_COMPILE=$(pwd)/gcc-linaro-4.9.4-2017.01-x86_64_arm-linux-gnueabihf/bin/arm-linux-gnueabihf-

# Build
export ARCH=arm
make m216_defconfig
make -j$(nproc)
📦 Patches Applied
Patch	Description	Source
add-HID-km-support	USB HID Keyboard/Mouse gadget	NetHunter
add-mac80211-packet-injection	WiFi packet injection	NetHunter
add-rtl8xxxu-with-rtl8188eus	RTL8188EUS driver support	NetHunter
🐛 Known Issues
"Unsupported device" in TWRP: Set do.devicecheck=0 in anykernel.sh

Bootloop: Restore boot backup in TWRP

WiFi not working: Load modules manually: insmod /system/lib/modules/rtl8xxxu.ko

HID not working: Enable in NetHunter app settings

🔗 Credits
Kali NetHunter

LineageOS - Base kernel source

NetHunter Kernel Builder

📄 License
This kernel is based on LineageOS kernel which is licensed under GPL v2.
