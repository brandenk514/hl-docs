---
layout: post
title: "Let's rack it all up!"
date: 2025-06-20
categories: architecture 
tags: Compute Dell PowerEdge
image:
   path: /assets/headers/uac-rack-diagram.png
---

## 📦 What's the inside that box?
While you definitely don't need to have a rack in your garage, basement, or even bedroom (I am not kidding), it feels great to have piece of professional computing equipment that is all tidy up and looks straight out of a data center. So let's run down the hardware from top to bottom!

## 🖥️ The hardware

### Networking 

#### [Ubiquiti UDM-SE](https://store.ui.com/us/en/category/all-cloud-gateways/products/udm-se)

This is my router and firewall. It is responisble for protecting my network from the internet as well as my inter-vlan routing. It is a Cloud key as well so it can control all my other Unifi devices. Unifi Network version 9 is an amazing upgrade from version 8 and allows me to see all my networking devices in one place. It also provides insights into networking connectivtiy and performance issues. 

🔧 Hardware & Performance
- **Port Layout:**
    * 8x 1 GbE RJ45 (1G/100M/10M)
    * 1x 2.5 GbE RJ45 (2.5G/1G/100M/10M)
    * 2x 10G SFP+ (10G/1G)
- **IDS/IPS Throughput:** 3.5 Gbps

#### [Ubiquiti USW-Pro-Aggregation](https://store.ui.com/us/en/category/all-switching/products/usw-pro-aggregation)

This is my core switch or spine. I don't technically have a spine and leaf topology, but hey it's a homelab 🤷‍♂️. It's rock solid switch and holds all my SFP+ 10G connections. Also, it's nice to have those 25G for Hyperconverged applications or faster backups. 

🔧 Hardware & Performance
- **Port Layout:**
    * 4x 25G SFP28
    * 28x 10G SFP+
- **Switching Capacity:** 760 Gbps
- **Total Non-Blocking Throughput:** 380 Gbps
- **Forwarding Rate:** 565 Mpps

#### [Ubiquiti USW-Pro-24](https://store.ui.com/us/en/category/all-switching/products/usw-pro-24)

This is my leaf for all my base-t connections. If it is a management interface or out-of-band IPMI, it's connected here. It's not impressive, but it does it's job perfectly.

🔧 Hardware & Performance
- **Port Layout:**
    * 24x 1 GbE RJ45 (1G/100M/10M)
    * 2x 10G SFP+
- **Switching Capacity:** 88 Gbps
- **Total Non-Blocking Throughput:** 44 Gbps
- **Forwarding Rate:** 65 Mpps

### Compute

#### [TerraMaster F4‑424 Max](https://www.terra-master.com/us/f4-424-max.html)

This is my second backup server. I use ZFS replication to backup my most important files from my primary storage. I love this machine. It's compact, quiet, and has an impressive CPU. I am defintely not using it to it's max in any way. My only complaint is that TOS is not great. It's getting better and better, but it can't compete with TrueNAS or Unraid. Mine has 2x NVMe for TrueNAS OS and 4x 16TB HDDs.

🔧 Hardware & Performance
 - **CPU:** Intel Core i5‑1235U (10 cores/12 threads, up to 4.4 GHz) with integrated Iris Xe graphics
- **Memory:** 32GB of DDR5 5600MT/s 
- **Storage Bays:**
    * 4x 16TB HDDs
    * 2x 512GB NVMe
- **Networking:** Dual 10GbE RJ‑45 ports
- **USB Ports:** Two USB‑A and one USB‑C (Gen 2, 10 Gbps) on the rear for external drives or accessories 

#### Dell PowerEdge R440

This my bare metal docker host. It runs Ubuntu 24.04 

🔧 Hardware & Performance

**Chassis:** 1U, dual-socket rack server
**CPU:** Dual Intel Xeon Gold 6138
**Memory:** 256GB of ECC DDR4
**Storage:** 4×2.5″ 400GB SAS SSDs
**Networking:**
    - 2× 1 GbE RJ-45
    - 2x SFP28 via ConnectX4

