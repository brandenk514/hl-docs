---
layout: post
title: "Installing Proxmox"
date: 2025-06-11
categories: virtualization
tags: proxmox virtualization
image:
   path: /assets/headers/proxmox-logo-stacked-color.svg
---

## Why Proxmox?

I chose Proxmox for a variety of reasons, but mostly because Broadcom decided to buy VMware and gut ESXi, the product I loved. I was a full supporter of VMUG (VMware User Group), and when Broadcom brought VMware, I could see the writing on the wall. It wasn't long after I migrated off of ESXi that VMUG became untenable for the average person to use.

That being said, I have been presently surprised by Proxmox’s robustness and flexibility. It is a rock-solid KVM platform that allows you to run and maintain highly available virtual machines and containers. Its basic backup integrations and dedicated backup software (Proxmox Backup Server) have made it a go-to for myself and many others. That only scratches the surface so with that let’s get it installed!

## Prerequisites

- A dedicated server or bare-metal machine
- At least 2GB RAM (4GB+ recommended)
- 64-bit processor with virtualization support (Intel VT/AMD-V)
- Reliable internet connection
- Backup any important data (installation will erase the disk)

## Step 1: Download Proxmox VE ISO

1. Go to the [Proxmox Downloads page](https://www.proxmox.com/en/downloads).
2. Download the latest Proxmox VE ISO Installer.

## Step 2: Create a Bootable USB Drive

- Use tools like [Rufus](https://rufus.ie/) (Windows), [balenaEtcher](https://www.balena.io/etcher/) (Linux/macOS/Windows), or `dd` (Linux/macOS) to write the ISO to a USB drive.

Example using `dd`:
```sh
sudo dd if=proxmox-ve_*.iso of=/dev/sdX bs=4M status=progress
```
Replace `/dev/sdX` with your USB device.

## Step 3: Boot from USB

1. Insert the USB drive into your server.
2. Reboot and enter the BIOS/UEFI settings.
3. Set the USB drive as the primary boot device.
4. Save and reboot.

## Step 4: Install Proxmox VE

1. When the Proxmox installer loads, select **Install Proxmox VE**.
2. Accept the license agreement.
3. Select the target hard disk for installation.
4. Configure country, time zone, and keyboard layout.
5. Set a strong password and provide an email address.
6. Configure network settings (hostname, IP, gateway, DNS).
7. Confirm and start the installation.

## Step 5: First Boot and Web Interface

1. After installation, remove the USB drive and reboot.
2. Access the Proxmox web interface from another computer:
   ```
   https://<your-server-ip>:8006
   ```
3. Log in with the `root` user and the password you set during installation.

## Step 6: Update Proxmox VE

After logging in, update your system:
```sh
apt update && apt full-upgrade
```

## Additional Resources

- [Proxmox VE Documentation](https://pve.proxmox.com/pve-docs/)
- [Proxmox Community Forum](https://forum.proxmox.com/)

---
