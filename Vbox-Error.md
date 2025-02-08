# Fixing "VirtualBox Kernel Driver Not Installed (rc=-1908)" Error on Kali Linux

## ERROR : [[ Result code: NS_ERROR_FAILURE(0x80004005) ]]

If you're encountering the "VirtualBox Kernel Driver Not Installed (rc=-1908)" error on Kali Linux, follow the steps below to resolve the issue.

### Steps to Resolve the Error

**1. Update Your System**
  - Ensure your system is up-to-date to prevent compatibility issues.
      - ***$***  `sudo apt update && sudo apt upgrade -y`

**2. Install Required Packages**
- Install the necessary packages for building kernel modules.
      - ***$*** `sudo apt install -y build-essential dkms linux-headers-$(uname -r)`

**3. Reinstall VirtualBox DKMS**
- Reinstall the VirtualBox Dynamic Kernel Module Support to ensure kernel modules are correctly built and installed.
     - ***$*** `sudo apt install --reinstall virtualbox-dkms`

**4. Installs the libelf-dev package on your system**
- This package provides development libraries and header files for libelf1, a shared library that allows for high-level reading and writing of ELF (Executable and Linkable Format) files. ELF is a common standard file format for executables, object code, shared libraries, and core dumps in Unix-like operating systems. 
     - ***$*** `sudo apt install libelf-dev`

**5. Load the VirtualBox Kernel Module**
- Manually load the vboxdrv kernel module.
     - ***$*** `sudo modprobe vboxdrv`





### Link to a video tutorial:
[![How to fix errors in VirtualBox - modprobe vboxdrv, Kernel driver not installed](https://img.youtube.com/vi/AKAq2LGu_zs/0.jpg)](https://www.youtube.com/watch?v=AKAq2LGu_zs)
 
