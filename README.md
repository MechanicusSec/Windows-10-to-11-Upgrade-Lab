# Windows 10 to Windows 11 Upgrade Lab

## Overview

Windows 10 to Windows 11 Upgrade Lab is a beginner-friendly IT support and sysadmin portfolio project focused on practicing a Windows 10 to Windows 11 upgrade in VMware.

The lab is designed to practice virtual machine preparation, Windows installation, hardware compatibility checks, TPM and Secure Boot verification, Windows 10 baseline verification, Windows 11 upgrade preparation, basic troubleshooting and documentation.

This project uses a safe local lab environment only.

No real user data, production systems, passwords, private files or company devices are used.

---

## Scenario

A company is preparing to upgrade Windows 10 client computers to Windows 11.

The goal of this lab is to act as an IT support technician and practice the upgrade process safely in VMware before performing similar work on real devices.

The lab starts with a clean Windows 10 Pro installation and prepares the virtual machine for a later Windows 11 upgrade.

---

## Lab goals

The goals of this lab are to:

* Create a clean project structure for documentation.
* Prepare a VMware virtual machine for Windows 10.
* Download and verify a Windows 10 ISO.
* Install Windows 10 Pro in VMware.
* Configure the VM with Windows 11-compatible settings.
* Verify Windows 10 version and build.
* Verify UEFI, Secure Boot, TPM, CPU, memory and disk configuration.
* Install VMware Tools.
* Run Windows Update.
* Create a snapshot before upgrading.
* Upgrade Windows 10 to Windows 11.
* Troubleshoot common upgrade problems.
* Document the process with screenshots and notes.

---

## Planned parts

| Part | Topic | Status |
| --- | --- | --- |
| Part 1 | Project setup | Complete |
| Part 2 | Windows 10 ISO preparation | Complete |
| Part 3 | VMware VM creation | Complete |
| Part 4 | Windows 10 installation | Complete |
| Part 5 | Windows 10 baseline verification | Started |
| Part 6 | VMware Tools installation | Planned |
| Part 7 | Windows Update preparation | Planned |
| Part 8 | Pre-upgrade snapshot | Planned |
| Part 9 | Windows 11 upgrade | Planned |
| Part 10 | Upgrade troubleshooting | Planned |
| Part 11 | Final report and GitHub polish | Planned |

---

## Current VM configuration

| Setting | Value |
| --- | --- |
| VM name | Win10-to-Win11-Upgrade-Lab |
| VM location | `C:\VirtualMachines` |
| Operating system | Windows 10 x64 |
| Firmware | UEFI |
| Secure Boot | Enabled |
| TPM | Present |
| Memory | 8 GB |
| CPU | 2 cores |
| Disk | 80 GB |
| Network | NAT |
| Windows 10 edition | Windows 10 Pro |
| Windows 10 version | 22H2 |
| Windows build | 19045.3803 |
| Lab user | LabUser |

---

## Project structure

```text
Windows-10-to-11-Upgrade-Lab/
├── docs/
│   └── .gitkeep
├── notes/
│   └── .gitkeep
├── results/
│   └── .gitkeep
├── screenshots/
│   ├── .gitkeep
│   ├── screenshot-01-project-structure.png
│   └── screenshot-02-windows-10-winver.png
├── logbook.md
└── README.md
```

---

## Documentation and evidence

Main documentation files:

| File | Purpose |
| --- | --- |
| `README.md` | Main GitHub project overview |
| `logbook.md` | Step-by-step project notes |

Screenshot evidence is stored in:

```text
screenshots/
```

Command outputs and verification results may be stored in:

```text
results/
```

Troubleshooting notes may be stored in:

```text
notes/
```

---

## Current screenshot evidence

| Screenshot | Purpose |
| --- | --- |
| `screenshot-01-project-structure.png` | Project folder and documentation structure |
| `screenshot-02-windows-10-winver.png` | Windows 10 Pro version and build verification |

---

## Current progress

The documentation project structure has been created.

The Windows 10 ISO was downloaded with the Microsoft Media Creation Tool.

The ISO was located, copied away from OneDrive and renamed with a clear lab filename.

A new VMware virtual machine was created for the upgrade lab.

The VM was configured with 8 GB RAM, 2 CPU cores, 80 GB disk, NAT networking, UEFI firmware, Secure Boot and a virtual TPM.

Windows 10 Pro was installed successfully.

The Windows version was verified with `winver`.

The current confirmed Windows version is Windows 10 Pro 22H2, OS Build 19045.3803.

---

## Skills demonstrated

This project demonstrates:

* VMware virtual machine setup
* Windows ISO preparation
* Windows 10 installation
* Windows 10 baseline verification
* UEFI configuration
* Secure Boot configuration
* Virtual TPM configuration
* VM encryption for TPM support
* NAT network configuration
* Windows version verification
* Local account setup
* IT support documentation
* Screenshot-based evidence collection
* Markdown documentation
* Git and GitHub workflow

---

## Notes

This is a local lab project for learning and portfolio demonstration.

Do not include real passwords, private account names, real company data, license keys, production information or sensitive IP addresses in public documentation.

Local paths should be anonymized in written documentation, for example:

```text
C:\Users\*****\Documents\ISO
```

The VM location used in this lab is:

```text
C:\VirtualMachines
```

This path does not expose a personal username and is suitable for documentation.
