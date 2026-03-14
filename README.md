# Windows Deployment Services PXE Deployment Lab

## Overview

This project demonstrates the installation and configuration of **Windows Deployment Services (WDS)** to support network-based operating system deployment using **PXE boot**.

The environment integrates several enterprise infrastructure services including:

- Active Directory
- DHCP
- Windows Deployment Services
- Windows Preinstallation Environment (WinPE)
- PXE Boot infrastructure
- Windows image capture and deployment

The project consists of two major assignments:

- **Assignment 1.1** – Installing and Configuring Windows Deployment Services
- **Assignment 1.2** – Creating Windows Deployment Boot Images for Image Capture

---

# Technologies Used

- Windows Server
- Windows Deployment Services (WDS)
- PXE Boot
- Active Directory
- DHCP
- Windows Preinstallation Environment (WinPE)
- Hyper-V Virtualization

---

# Lab Environment

| Role | Hostname | Operating System |
|-----|-----|-----|
| Domain Controller | DC1 | Windows Server |
| DHCP Server | DHCP | Windows Server |
| WDS Server | WDS | Windows Server |
| Reference Machine | WIN10-REF | Windows 10 |

---

# Infrastructure Workflow

The deployment process follows this sequence:

Client Computer  
⬇  
PXE Boot Request  
⬇  
DHCP Assigns IP Address  
⬇  
WDS Server Responds  
⬇  
WinPE Boot Image Loads  
⬇  
Deployment or Image Capture Begins

---

# Assignment 1.1 — Installing and Configuring Windows Deployment Services

## Objective

Install and configure **Windows Deployment Services (WDS)** to support network-based operating system deployment.

---

## Creating the WDS Server

![WDS Server Created](screenshots/A1_S01_WDS_Server_Created.png)

---

## Creating a Snapshot

![WDS Snapshot](screenshots/A1_S02_WDS_Snapshot.png)

---

## Joining the Domain

![Domain Joined](screenshots/A1_S03_WDS_Domain_Joined.png)

![Domain Join Confirmation](screenshots/A1_S04_Domain_Join_Confirmation.png)

---

## Configuring Static IP Address

![Static IP](screenshots/A1_S05_Static_IP_Config.png)

---

## Preparing Deployment Disk

![Disk Formatted](screenshots/A1_S06_WDS_Images_Disk_Formatted.png)

---

## Creating RemoteInstall Folder

![RemoteInstall Folder](screenshots/A1_S07_RemoteInstall_Folder.png)

---

## Installing WDS Role

![WDS Installation](screenshots/A1_S08_WDS_Role_Installation.png)

---

## Configuring RemoteInstall Location

![RemoteInstall Location](screenshots/A1_S09_RemoteInstall_Location.png)

---

## Configuring PXE Server

![PXE Server Settings](screenshots/A1_S10_PXE_Server_Settings.png)

---

## WDS Server Properties

![WDS Properties](screenshots/A1_S11_WDS_Server_Properties.png)

---

## PXE Boot Policy

![PXE Boot Policy](screenshots/A1_S12_PXE_Boot_Policy.png)

---

# Assignment 1.2 — Creating Windows Deployment Boot Images for Image Capture

## Objective

Configure **Windows Deployment Services** to support operating system image capture by importing a **WinPE boot image** and creating a capture image.

---

## Creating the Software Share

A folder named **Software** was created on the WDS server to store installation media.

![Software Folder](screenshots/A12_S01_E-Software-Folder-Created.png)

![Share Permissions](screenshots/A12_S02_E-Software-Share-Permissions.png)

---

## Copying and Mounting Windows Installation Media

The Windows 10 ISO was copied to the Software share and mounted.

![ISO Copied](screenshots/A12_S03_Win10ISO-Copied-to-Software.png)

![ISO Mounted](screenshots/A12_S04_Win10ISO-Mounted-Sources.png)

---

## Opening the WDS Console

![Boot Images Empty](screenshots/A12_S05_WDS-Console-BootImages-Empty.png)

---

## Adding the Windows Boot Image

Boot image imported from:


E:\Sources\boot.wim


![Select boot.wim](screenshots/A12_S06_AddBootImage-Select-bootwim.png)

![Boot Image Metadata](screenshots/A12_S07_AddBootImage-Metadata-Windows10Boot.png)

![Boot Image Added](screenshots/A12_S08_Windows10Boot-Added.png)

---

## Creating the Capture Boot Image

![Create Capture Image](screenshots/A12_S09_CreateCaptureImage-ContextMenu.png)

![Capture Metadata](screenshots/A12_S10_CaptureImage-Metadata-Location.png)

![Capture Progress](screenshots/A12_S11_CaptureImage-Progress.png)

---

## Adding the Capture Image to WDS

![Select Capture WIM](screenshots/A12_S13_AddBootImage-Select-CaptureWIM.png)

![Capture Complete](screenshots/A12_S13_CaptureImage-Complete.png)

![Wizard Summary](screenshots/A12_S14_AddImageWizard-Summary.png)

---

## Verification of Boot Images

![Boot Images Final](screenshots/A12_S16_BootImages-Final.png)

---

# Important Notes

- Windows Server 2025 WDS does **not support Windows 11 boot images for capture**
- Windows 10 boot images must be used
- Capture images must be added to WDS to be available for PXE boot

---

# Outcome

The Windows Deployment Services server was successfully prepared for **network-based operating system capture and deployment**.

A **WinPE capture image** named **Win10ITCapture** was created to capture a reference Windows installation and deploy standardized images across multiple systems.

---

# Conclusion

This project demonstrates how **Windows Deployment Services enables centralized operating system deployment** using PXE boot and capture images.

Using WDS significantly reduces manual installation time and ensures consistent operating system deployment across enterprise environments.

---

# Author

Zeyad Almahmoudi  
BCIT — Technology Support Professional (TSP)
