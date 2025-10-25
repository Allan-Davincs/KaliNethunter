# Kali NetHunter — Rootless Install (Android 12+ / Android 15 tested)

![status: draft](https://img.shields.io/badge/status-draft-yellow)
![platform: android](https://img.shields.io/badge/platform-android-brightgreen)
![termux](https://img.shields.io/badge/termux-required-blue)

> Educational guide to install Kali NetHunter in **rootless** mode on Android devices (Android 12 and newer).
> **Only for educational and lawful use.** The author and repository owner are not responsible for misuse.

---

## Table of Contents
- [About](#about)
- [Requirements](#requirements)
- [Quick Install (copy & paste)](#quick-install-copy--paste)
- [Full Step-by-Step](#full-step-by-step)
- [Start & Use NetHunter](#start--use-nethunter)
- [Fix: Android 12+ child-process killing](#fix-android-12-child-process-killing)
- [Install NetHunter Store & KeX (GUI)](#install-nethunter-store--kex-gui)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [Credits & Resources](#credits--resources)

---

## About
This repository contains a concise, copy-friendly README to install **Kali NetHunter Rootless** using **Termux** on Android devices (recommended Android 12+ / tested with Android 15). The instructions are adapted from public NetHunter documentation and community tutorials and aim to be beginner-friendly.

**Important:** This guide does _not_ cover rooting devices, bypassing security controls, or illegal activity. Only proceed on devices you own or have explicit permission to use for testing.

---

## Requirements
- Physical Android device (Android 12, 13, 14, or 15 recommended)
- Termux (install from F-Droid or the Termux GitHub releases; **do not** use the Play Store build)
  - F-Droid: https://f-droid.org/packages/com.termux/
  - GitHub: https://github.com/termux/termux-app/releases
- Internet connection
- ~10+ GB free storage (image sizes vary)
- Basic familiarity with command-line (Termux)
- Optionally: a computer and VNC client (to connect to KeX GUI)

---

## Quick Install (copy & paste)
> Open Termux and paste these commands (one-by-one). Read prompts and answer as described in the Full Step-by-Step section.
```bash
pkg update -y
termux-setup-storage
pkg install wget -y
wget -O install-nethunter-termux https://offs.ec/2MceZWr
chmod +x install-nethunter-termux
./install-nethunter-termux
# When prompted choose image "1" for Kali NetHunter Lite
# If download completes, re-run ./install-nethunter-termux to perform install
```

---

## Full Step-by-Step
1. **Download & install Termux**
   - Use F‑Droid or Termux GitHub releases. Avoid the Play Store package — it is outdated.
2. **Open Termux** and update packages:
   ```bash
   pkg update -y
   ```
3. **Grant storage permission** (for shared storage access):
   ```bash
   termux-setup-storage
   ```
4. **Install `wget`** (used to fetch installer script):
   ```bash
   pkg install wget -y
   ```
5. **Download the NetHunter installer script** (ensure the URL is correct):
   ```bash
   wget -O install-nethunter-termux https://offs.ec/2MceZWr
   ```
6. **Make the script executable**:
   ```bash
   chmod +x install-nethunter-termux
   ```
7. **Run the installer**:
   ```bash
   ./install-nethunter-termux
   ```
   - When prompted to choose an image, enter `1` (Kali NetHunter Lite) or select your preferred image.
8. **If the script only downloads the image, re-run**:
   ```bash
   ./install-nethunter-termux
   ```
9. **When asked whether to delete downloaded image or rootfs, answer `N`** unless you want a fresh download.
10. **Wait** for installation to finish — this may take several minutes depending on your network and device.

---

## Start & Use NetHunter
- Start the NetHunter CLI:
  ```bash
  nethunter
  # or
  nh
  ```
- To set KeX (VNC) password (first-time only):
  ```bash
  nethunter kex passwd
  ```
- To start KeX GUI (VNC server):
  ```bash
  nethunter kex
  ```
  - On first run you will be asked to set a password and remember the port number (e.g., 5901).
- To stop KeX GUI:
  ```bash
  nethunter kex stop
  ```
- To get a root shell (if available in this image):
  ```bash
  nethunter -r
  ```

---

## Fix: Android 12+ child-process killing
Android 12+ enforces stricter process management which may kill forked child processes used by Termux + NetHunter. To reduce unwanted kills:
1. Open **Settings** → **About phone** → tap **Build number** 7 times to enable Developer options.
2. Open **Developer options** → enable **Disable child process restrictions**.

> Note: Exact wording of the option may differ by OEM/Android vendor.

---

## Install NetHunter Store & KeX (GUI)
1. Visit NetHunter Store (from device browser):
   - https://store.nethunter.com/packages/com.offsec.nethunter.store/
2. Download the NetHunter Store APK and install (you may need to authorize installing unknown apps).
3. Open NetHunter Store → locate **KeX** and install.
4. Open KeX app → create a new connection:
   - **Port**: `5901` (or the port shown by `nethunter kex`)
   - **Password**: the KeX password you set earlier
5. Save and connect via the KeX entry to see the Kali GUI on your device.

---

## Troubleshooting
- **Installer link fails or file missing**: Double-check the URL or download the script manually from a trusted source. Use a reliable network.
- **Permission denied on script**: Ensure you ran `chmod +x install-nethunter-termux` and that the file exists in the current directory (`ls -l`).
- **Termux says “command not found” for `nethunter`**: Re-open Termux or ensure the NetHunter rootfs finished installing. Re-run the installer to complete installation.
- **VNC/KeX won’t connect**: Verify port (5901), correct password, and that the `nethunter kex` session is running.
- **Child processes are killed (Android 12+)**: Enable **Disable child process restrictions** in Developer options.
- **Downloads fail repeatedly**: Try switching to a different network or use a computer to download and transfer the image to the device.

If you hit a specific error, paste the exact message here and I’ll help you debug it.

---

## Contributing
Contributions welcome — open an issue or PR with improvements, clarifications, or updated links. Keep content lawful and respectful of device security and privacy.

---

## License
This repository is released under the MIT License. See `LICENSE` for details.

---

## Credits & Resources
- Official NetHunter rootless docs: https://www.kali.org/docs/nethunter/nethunter-rootless/
- NetHunter Store: https://store.nethunter.com/
- Termux: https://f-droid.org/packages/com.termux/
- Community tutorials and videos (e.g., David Bombal)

---
