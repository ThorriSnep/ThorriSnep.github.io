---
title: My home server (host OS and pfSense)
author: ThorriSnep
date: 2022-02-18 12:00:00 +0100
categories: [linux]
tags: [linux, pfSense, homeserver]
---
In this post I want to show you how you can set up a pfSense VM as your firewall and router and my first step in upgrading my home network and server.

A quick overview of the steps we are going to take:

1. Set up Ubuntu as host system
2. Configure network bridges with netplan
3. Set up a KVM VM with libvert for pfSense
4. Install pfSense

# 1. Set up Ubuntu as host system

For my host OS I'm using Ubuntu Server 20.04 LTS.

If you want to remotely manage your host OS, during the tnstall you should choose the option to install OpenSSH.

After your host OS is intalled lets start installing all the packages we need:

### 1. Lets get you up to date:

```bash
sudo apt update
sudo apt upgrade

```
### 2. Now get everything we might need installed:

```bash
sudo apt install qemu bridge-utils libosinfo-bin virtinst libvirt-clients libvirt-deamon libvirt-deamon-system libvirt-sock libvirt-deamon-driver-qemu libvirt-deamon-driver-lxc

```

# 2. Configure network bridges with netplan

To use the pfSense system we need to set up 2 bridges one for the WAN connection and one for the LAN.

```bash
cd /etc/
sudo cp -r netplan netplan.bu
cd netplan
```

In the netplan directory you should find the installer-config file. In this file we are going to add the bridges with the following steps:

First you should deaktivate dhcp on your interfaces.
We don't need the physical LAN interfaces to have an IP, because we want to connect directly to the bridge.
The physical WAN interface can't have an IP because the only device that should get an IP is the WAN interface of the pfSense mashine.




```yaml

```
