<div align="center">

<img src=".github/assets/image.png" alt="Nuwa — Ameba Zephyr SDK" width="800">

# Nuwa — Ameba Zephyr SDK

**The official [Zephyr RTOS](https://zephyrproject.org/)-based IoT development framework for Realtek Ameba series chips.**

[![RTOS](https://img.shields.io/badge/RTOS-Zephyr-1384C5?style=flat-square&logo=zephyrproject&logoColor=white)](https://zephyrproject.org/)
[![Language](https://img.shields.io/badge/Language-C-A97BFF?style=flat-square&logo=c&logoColor=white)](https://github.com/Ameba-AIoT/nuwa/search?l=c)
[![License](https://img.shields.io/badge/License-Apache%202.0-brightgreen?style=flat-square)](LICENSE)
[![Last Commit](https://img.shields.io/github/last-commit/Ameba-AIoT/nuwa/main?style=flat-square&logo=github&logoColor=white)](https://github.com/Ameba-AIoT/nuwa/commits/main)

[English](README.md) · [中文版](README_CN.md) · [文档 / Docs](https://aiot.realmcu.com/en/latest/zephyr/) · [Products](https://aiot.realmcu.com/en/solution/zephyr.html)

</div>

Nuwa is the official Zephyr RTOS-based IoT development framework for Realtek Ameba series SoCs. It uses [west](https://docs.zephyrproject.org/latest/develop/west/index.html) as its meta-tool for multi-repository management, and this repository is the **west manifest repository** that tracks commit versions of all sub-repositories.

## 🔌 Supported Chips

| Chip       | Zephyr Support |
|:---------- |:--------------:|
| RTL8721F   | ✅ Supported   |
| RTL8721Dx  | ✅ Supported   |
| RTL8730E   | ✅ Supported   |

For the full chip and driver support matrix, visit [Ameba Zephyr Solutions](https://aiot.realmcu.com/en/solution/zephyr.html).

## 📥 Getting Started

The SDK uses a multi-repository structure managed by `west`. The [Zephyr SDK Documentation](https://aiot.realmcu.com/en/latest/zephyr/) covers environment setup, build system, peripheral drivers, Wi-Fi, OTA, TF-M, and more.

### Quick Start

```bash
# 1. Create and activate a Python virtual environment
python3 -m venv ~/nuwa/.venv
source ~/nuwa/.venv/bin/activate

# 2. Install west
pip install west

# 3. Get the SDK
cd ~/nuwa
west init -m https://github.com/Ameba-AIoT/nuwa.git
west update

# 4. Create the nuwa.py shortcut
ln -sf tools/meta_tools/nuwa.py nuwa.py
```

## 🏗️ Build

```bash
./nuwa.py build -b <BOARD> <SOURCE_DIR>

# e.g.
./nuwa.py build -b rtl872xda_evb zephyr/samples/hello_world
```

Update all repositories to the latest:

```bash
./nuwa.py update
```

Other commands:

```bash
west build -t clean      # Partial clean (keeps configuration)
west build -t pristine   # Full clean
west build -t menuconfig # Open Kconfig menuconfig UI
```

## ⚡ Flash

**On Windows** — connect the board via serial cable, then:

```bash
./nuwa.py flash --port <PORT>
```

**On Linux** — download and launch [AmebaRemoteService](https://aiot.realmcu.com/download/misc/AmebaRemoteService_v2.0.2.exe) on a Windows PC connected to the board, then run on the Linux host:

```bash
./nuwa.py flash --port <PORT> --remote-server <WINDOWS_IP>
```

## 🖥️ Monitor

**On Windows** — connect the board via serial cable, then:

```bash
./nuwa.py monitor --port <PORT> -b 1500000 [--reset]
```

**On Linux** — with [AmebaRemoteService](https://aiot.realmcu.com/download/misc/AmebaRemoteService_v2.0.2.exe) running on the Windows PC connected to the board:

```bash
./nuwa.py monitor --port <PORT> -b 1500000 --remote-server <WINDOWS_IP> [--reset]
```

`--reset` reboots the board automatically when the monitor starts.

## 💬 Feedback

- **Bug reports / suggestions**: log in to [RealMCU](https://www.realmcu.com/en/Account/Login) and submit feedback.
- **Code issues**: open a Pull Request or Issue directly on GitHub.
