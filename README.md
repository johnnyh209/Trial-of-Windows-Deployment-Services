# Trialing Windows Deployment Services
My first attempt at using Windows Deployment Services (WDS).

All of this is done in virtual machines. I have opted to use Hyper-V as the hypervisor, along with VMs of Windows Server and Windows 10.

Goal is to set up WDS on an install of Windows Server, and spin up a second VM that downloads an image of Windows 10 using PXE boot.

# Chapters

This directory will be broken up into several parts. The name of each file in this repository will correlate to the names below:

1. Part 1: Hyper-V and Windows Server Setup
2. Part 2: Installing and Using WDS
3. Part 3: PXE Boot On a New VM Instance
