---
title: "CloudStack: Kernel upgrade on Ubuntu-based and Debian-based instances"
slug: cloudstack-kernel-upgrade-on-ubuntu-debian
---


### To upgrade kernel to version 4.4 on an Ubuntu 14.04.x instance:

- On the required Virtual Machine, login via console or ssh.
- Confirm the running kernel is 3.13.x.  Run : `uname -a`
- To install new kernel, run : `'`sudo apt-get update && sudo apt-get install linux-generic-lts-xenial`
   - NB. While installing package, you may be prompted to keep or install new file from package maintainer's; select *Install the package maintainer's version*
- Reboot instance. Run : `sudo shutdown -r now`
- Verify instance is running kernel version 4.x. Run : `uname -a`
- Remove old kernel version.
   - Run : `sudo apt-get autoremove --purge -y`
   - Verify remaining packages. Run : `sudo dpkg -l |grep linux-image`
   - If there are remaining packages that need un-installation, run : `sudo apt-get remove packagename --purge`

### To upgrade kernel to version 3.16 on a Debian 8.x instance:

- On the required Virtual Machine, login via console or ssh.
- Confirm the running kernel is 3.13.x.  Run :  `uname -a`. If already running version 3.16, nothing more is required.
- To install new kernel, run : `sudo apt-get update && sudo apt-get linux-image-amd64 -y`
   - NB. While installing package, you may be prompted to keep or install new file from package maintainer's; select *Install the package maintainer's version*
- Reboot instance. Run : `sudo shutdown -r now`
- Verify instance is running kernel version 3.16. Run : `uname -a`
- Remove old kernel version.
   - Run : `sudo apt-get autoremove --purge -y`
   - Verify remaining packages. Run : `sudo dpkg -l |grep linux-image`
   - If there are remaining packages that need un-installation, run : `sudo apt-get remove packagename --purge`
