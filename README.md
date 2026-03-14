# Windows Deployment Services PXE Deployment Lab

## Overview

This lab demonstrates the installation and configuration of **Windows Deployment Services (WDS)** to support network-based operating system deployment using **PXE boot**.

The WDS server was integrated with **Active Directory** and configured to respond to both known and unknown client computers, allowing centralized operating system deployment in an enterprise environment.

---

# Lab Objective

The objective of this lab was to:

- Install Windows Deployment Services
- Configure a dedicated storage location for deployment images
- Integrate WDS with Active Directory
- Enable PXE boot deployment
- Configure PXE boot policies for automated OS installation

---

# Lab Environment

| Role | Hostname | Operating System |
|-----|-----|-----|
| Domain Controller | DC1 | Windows Server |
| WDS Server | WDS | Windows Server |
| DHCP Server | DHCP1 | Windows Server |
| Hyper-V Host | Physical | Windows |

---

# Infrastructure Overview

Windows Deployment Services enables administrators to deploy operating systems across the network without requiring physical installation media.

The deployment workflow is:

Client Computer  
⬇  
PXE Boot  
⬇  
DHCP Provides IP Address  
⬇  
WDS Server Responds  
⬇  
Boot Image Loaded  
⬇  
Operating System Deployment Begins

---

# Lab Implementation Steps

## 1 — Create WDS Server

A new virtual machine named **WDS** was created and joined to the domain.

![WDS Server Created](screenshots/A1_S01_WDS_Server_Created.png)

---

## 2 — Create Snapshot

A checkpoint snapshot was created to allow rollback if configuration changes fail.

![WDS Snapshot](screenshots/A1_S02_WDS_Snapshot.png)

---

## 3 — Join Server to Domain

The WDS server was joined to the Active Directory domain.

![Domain Join](screenshots/A1_S03_WDS_Domain_Joined.png)

![Domain Join Confirmation](screenshots/A1_S04_Domain_Join_Confirmation.png)

---

## 4 — Configure Static IP Address

The WDS server was assigned a static IP address and reserved in DHCP.

![Static IP](screenshots/A1_S05_Static_IP_Config.png)

---

## 5 — Attach Secondary Disk for Deployment Images

A 40GB disk was attached to store operating system deployment images.

The disk was formatted as **NTFS**.

![Disk Formatted](screenshots/A1_S06_WDS_Images_Disk_Formatted.png)

---

## 6 — Create RemoteInstall Folder

A folder named **RemoteInstall** was created on the secondary disk.

```
E:\RemoteInstall
```

![RemoteInstall Folder](screenshots/A1_S07_RemoteInstall_Folder_Created.png)

---

# Installing Windows Deployment Services

WDS was installed using **Server Manager**.

Steps:

1. Open Server Manager
2. Add Roles and Features
3. Select Role-based Installation
4. Choose Windows Deployment Services
5. Select Role Services:

- Deployment Server
- Transport Server

![WDS Installation](screenshots/A1_S08_WDS_Role_Installation.png)

---

# Configuring Windows Deployment Services

After installation, the WDS server was configured using the **Configure Server Wizard**.

The deployment folder was set to:

```
E:\RemoteInstall
```

![RemoteInstall Location](screenshots/A1_S09_RemoteInstall_Location_Config.png)

---

# PXE Server Configuration

The PXE server was configured to respond to both known and unknown client computers.

![PXE Server Settings](screenshots/A1_S10_PXE_Server_Settings.png)

---

# PXE Boot Policy

PXE boot behavior was configured under **Server Properties → Boot Tab**.

Policy used:

```
Continue the PXE boot unless the user presses ESC
```

This allows automated network boot while still providing a manual exit option.

![WDS Server Properties](screenshots/A1_S11_WDS_Server_Properties.png)

![PXE Boot Policy](screenshots/A1_S12_PXE_Boot_Policy_Configured.png)

---

# Skills Demonstrated

- Windows Server Administration
- Windows Deployment Services
- PXE Boot Deployment
- Active Directory Integration
- DHCP Coordination
- Enterprise OS Deployment Infrastructure

---

# Conclusion

This lab demonstrates how to deploy and configure **Windows Deployment Services** to support centralized operating system deployment across a network.

Using PXE boot and Active Directory integration significantly simplifies operating system provisioning in enterprise environments.

---

# Author

Zeyad Almahmoudi  
BCIT — Technology Support Professional (TSP)
