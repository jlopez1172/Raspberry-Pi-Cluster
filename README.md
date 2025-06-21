🌐 Raspberry Pi Cluster: Build Your Own Mini Supercomputer

This project is based on the official Raspberry Pi Cluster Tutorial. It documents the setup of a Raspberry Pi cluster used for experimenting with distributed computing, centralized file systems, and network booting. It uses Power over Ethernet (PoE) to streamline power and connectivity. Video captured the fully assembled cluster. Unfortunately, the file is too large to upload to the repository.

🧠 Project Goals
Build a functional and modular Raspberry Pi cluster

Set up network communication between nodes.

🧰 Hardware Requirements
8x Raspberry Pi 4 boards (1 master node + 7 worker nodes)

8x microSD cards

1x 8-Port Power over Ethernet (PoE) Network Switch

8x Ethernet cables

No power hubs (all devices powered via PoE switch)

8-Bay Cluster Case from C4Labs

🔧 Software Stack
Raspberry Pi OS Lite (on master node only)

OpenSSH (for remote access)

nfs-kernel-server (for shared filesystem)

PXE Boot setup for worker nodes

🚀 Getting Started
1. Flash Raspberry Pi OS to Master Node
Use the Raspberry Pi Imager to install Raspberry Pi OS Lite on the master node’s SD card. Enable SSH and assign it a static IP.

2. Configure Network and Hostnames
Connect all Pis to the PoE switch

Configure static/reserved IPs via your router or local DHCP

Set distinct hostnames for easy access (e.g., master, worker1, ..., worker7)

3. Set Up Shared File System
Install and configure NFS-kernel-server on the master node to host the bootable filesystem for worker nodes.

bash
sudo apt update
sudo apt install nfs-kernel-server
Export a shared directory (e.g., /nfs/rootfs) via /etc/exports.

4. PXE Boot Configuration for Worker Nodes
Configure the TFTP and DHCP settings on the master node to enable the worker nodes to boot over the network without local storage.

Enable PXE boot on Raspberry Pi 4s (if not already enabled)

Set up a TFTP server.

Serve the operating system (OS) and root filesystem from the master node.

Refer to Raspberry Pi's Netbooting Guide for exact setup steps.

📚 Resources
Official Raspberry Pi Cluster Tutorial
(https://www.raspberrypi.com/tutorials/cluster-raspberry-pi-tutorial/)

Netbooting Raspberry Pi 4

NFS Server Setup Guide
