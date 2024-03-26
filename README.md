**This build is highly experimental, you should only use it when you know what you are doing.**

This repository hosts a custom Linux kernel that merges unRAID's kernel configuration with the versatile features of a distro Linux's kernel. Initially derived from an Unraid kernel configuration, this kernel has been extensively modified and optimized by incorporating settings and features from Arch Linux kernel, aiming to create a kernel that combines the best of both worlds.

The core idea behind this project was to enhance the unRAID kernel by integrating the  features and optimizations found in Arch Linux's kernel. This hybrid approach aims to deliver a kernel that is not only stable and efficient but also equipped with the latest advancements in Linux kernel development, making it suitable for a broader range of applications and hardware support.

Key features:
- Unraid Compatibility: Maintains core functionalities and compatibility with unRAID.
- Enhanced Hardware Support: By aligning closer with Arch Linux's kernel configuration, this kernel extends its compatibility with a wider array of hardware features.
- Modern Features: Incorporates the latest kernel features and optimizations from Arch Linux, ensuring users benefit from recent advancements.
- Security and Performance: Prioritizes security and performance enhancements, ensuring that the kernel is secure and efficient for various use case. 
- Kernel hardening is enabled to minimize the risk of data corruption.

Notes:
- This build has SR-IOV (hardware virtualisation) support for i915 adapters. You can enable it with the kernel command line parameters:
```
i915.enable_guc=3 i915.max_vfs=7
```
  The virtual i915 adapters should be enabled from cli:
```
echo 2 > /sys/devices/pci0000:00/0000:00:02.0/sriov_numvfs
```
  You can see the addition adapters with the lspci command.
-  This build includes the r8125 (for 2.5 GbE RTL8125, RTL8126 chips) and r8168 (for 1 GbE RTL8168, RTL8411 chips) drivers from the Realtek site. You can enable them with disabling the built-in kernel driver:
```
echo "blacklist r8169" > /boot/config/modprobe.d/r8169.conf
```
-  AppArmor is included in this build but needs to be enabled from user space.	
