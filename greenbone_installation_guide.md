# Greenbone OPENVAS Community Edition Installation Guide

## Overview
This guide explains how to download, verify, import, and run the Greenbone OPENVAS Community Edition virtual appliance using either VMware Workstation Player/Pro or Oracle VirtualBox.

---

# Option 1: VMware Workstation Player / Pro

## Download the Appliance
Download the VMware OVA image:

```text
https://files.greenbone.net/download/delivery/website-free/OPENVAS-FREE-24.10.9-VMware-Workstation.ova
```

## SHA256 Checksum

```text
2fbbd7ffec7124111d7dba0f6474630ac231bd309b8c8bc17d67d698609433c6
```

---

# Option 2: Oracle VirtualBox

## Download the Appliance
Download the VirtualBox OVA image:

```text
https://files.greenbone.net/download/delivery/website-free/OPENVAS-FREE-24.10.9-VirtualBox.ova
```

## SHA256 Checksum

```text
(Add the official SHA256 checksum here)
```

---

# Verify the Downloaded File

It is recommended to verify the SHA256 checksum after downloading the OVA file.

## Windows (PowerShell)

```powershell
Get-FileHash .\OPENVAS-FREE-24.10.9-VMware-Workstation.ova -Algorithm SHA256
```

or

```powershell
Get-FileHash .\OPENVAS-FREE-24.10.9-VirtualBox.ova -Algorithm SHA256
```

Compare the output hash with the official checksum.

---

# Install on VMware Workstation Player / Pro

## Step 1 — Open VMware Workstation
Launch VMware Workstation Player or VMware Workstation Pro.

## Step 2 — Import the OVA Appliance
1. Click **File** → **Open**.
2. Select the downloaded `.ova` file.
3. Click **Import**.
4. Choose a name and storage location for the VM.
5. Wait for the import process to complete.

## Step 3 — Configure VM Settings (Optional)
Recommended minimum resources:

- CPU: 2 vCPUs
- RAM: 4 GB minimum (8 GB recommended)
- Disk: Default provided virtual disk
- Network Adapter: NAT or Bridged

## Step 4 — Start the Virtual Machine
Click **Power On this virtual machine**.

---

# Install on Oracle VirtualBox

## Step 1 — Open VirtualBox
Launch Oracle VirtualBox.

## Step 2 — Import Appliance
1. Click **File** → **Import Appliance**.
2. Browse and select the downloaded `.ova` file.
3. Click **Next**.
4. Review appliance settings.
5. Click **Import**.
6. Accept license terms if prompted.

## Step 3 — Adjust VM Resources (Optional)
Recommended minimum resources:

- CPU: 2 vCPUs
- RAM: 4 GB minimum (8 GB recommended)
- Network: NAT or Bridged Adapter

## Step 4 — Start the VM
Select the imported VM and click **Start**.

---

# Initial Greenbone Setup

After booting:

1. Wait for the appliance initialization to complete.
2. The VM console will display the assigned IP address.
3. Open a web browser on your host machine.
4. Navigate to:

```text
https://<GREENBONE_IP_ADDRESS>
```

Example:

```text
https://192.168.1.100
```

5. Ignore the self-signed certificate warning if prompted.
6. Log in using the default credentials provided by Greenbone.

---

# Update Feeds

After the first login:

1. Go to the Greenbone Security Assistant (GSA).
2. Allow feed synchronization to complete.
3. Feed updates may take time during the first startup.

---

# Basic Network Recommendations

## NAT Mode
Recommended for:

- Testing environments
- Isolated lab environments

## Bridged Mode
Recommended for:

- Scanning devices on the same physical network
- Internal vulnerability assessments

---

# Troubleshooting

## Cannot Access Web Interface
- Verify the VM has obtained an IP address.
- Ensure the host firewall allows HTTPS traffic.
- Confirm the VM network adapter is connected.

## Slow Performance
- Increase RAM allocation.
- Increase CPU cores.
- Ensure virtualization support (VT-x/AMD-V) is enabled in BIOS.

## Feed Sync Takes Too Long
- Initial synchronization can take several hours depending on internet speed.
- Leave the VM running until synchronization completes.

---

# Useful Commands

## Check IP Address

```bash
ip addr
```

## Restart Greenbone Services

```bash
sudo systemctl restart gvmd
sudo systemctl restart gsad
```

## Check Service Status

```bash
sudo systemctl status gvmd
sudo systemctl status gsad
```

---

# Notes

- Use snapshots before major configuration changes.
- Keep feeds updated regularly.
- Ensure the VM clock and timezone are correct.
- Use strong passwords after the first login.

---

# References

Greenbone Official Website:

```text
https://www.greenbone.net/
```

Greenbone Community Documentation:

```text
https://greenbone.github.io/docs/latest/
```
