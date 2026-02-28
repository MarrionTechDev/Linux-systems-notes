# Device Specifications and Modifications

This folder documents the hardware I used to experiment with the Linux system
Since it is important to break things as you are learn Linux, I decided to revive an old laptop I had lying around.

## Device Info
- Device: Dell Latitude D630
- CPU: Intel Core 2 Duo
- RAM: TWO 1 GB DDR2 SRAM
- Storage: 120 GB HDD
- Other Notes: Battery removed during testing, external keyboard used.

## Modification
- RAM Increase: TWO 2 GB DDR2 SODIMM (Motoeagle)
- Storage: 256 GB SATA SSD (Raoyi)
- Other Notes: A cheap 8 GB flash drive. 

## Debian Installation Plan
Using lightweight DE to get the most out of memory and storage.
- Target OS: Debian 12.0.0 amd64 netinst.iso (Bookworm)
- Partitioning: Guided - use entire disk, All files in one partition 
- Desktop Environment: XFCE
- Package selection: 
  - build-essential, git, python3, python3-pip
  - net-tools, ssh, vim
  - utilities for networking and server exploration

## Goals
- Document a reproducible setup
- Track installation steps
- Note hardware limitations and configurations

## Note To Self
- When making a bootable drive, use a small flash drive (8GB, 16GB).
  Old laptops sometimes find it hard to unpack the iso
