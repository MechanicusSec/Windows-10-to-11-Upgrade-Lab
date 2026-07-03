# Windows 10 to Windows 11 Upgrade Lab

## Overview

Windows 10 to Windows 11 Upgrade Lab is a beginner-friendly IT support and sysadmin portfolio project focused on practicing a Windows 10 to Windows 11 in-place upgrade in VMware.

The lab covers virtual machine preparation, Windows installation, TPM and Secure Boot readiness, Windows Update checks, VMware snapshots, Windows 11 upgrade execution, post-upgrade verification, troubleshooting notes and documentation.

This project uses a safe local lab environment only. No real user data, production systems, passwords, private files or company devices are used.

---

## Scenario

A company is preparing to upgrade Windows 10 client computers to Windows 11.

The goal of this lab is to act as an IT support technician and practice the upgrade process safely in VMware before performing similar work on real devices.

The lab starts with a clean Windows 10 Pro installation, prepares the VM for Windows 11, performs an in-place upgrade and verifies the upgraded Windows 11 system.

---

## Lab goals

* Create a clean project structure for documentation.
* Prepare a VMware virtual machine for Windows 10.
* Download and verify Windows ISO files.
* Install Windows 10 Pro in VMware.
* Configure UEFI, Secure Boot and virtual TPM.
* Verify Windows 10 baseline status.
* Install VMware Tools.
* Run Windows Update checks before upgrading.
* Create a VMware snapshot before upgrading.
* Upgrade Windows 10 Pro to Windows 11 Pro.
* Verify Windows 11 after upgrade.
* Document the process with screenshots and notes.

---

## Planned parts

| Part | Topic | Status |
| --- | --- | --- |
| Part 1 | Project setup | Complete |
| Part 2 | Windows 10 ISO preparation | Complete |
| Part 3 | VMware VM creation | Complete |
| Part 4 | Windows 10 installation | Complete |
| Part 5 | Windows 10 baseline verification | Complete |
| Part 6 | VMware Tools installation | Complete |
| Part 7 | Windows Update preparation | Complete |
| Part 8 | Pre-upgrade snapshot | Complete |
| Part 9 | Windows 11 upgrade and verification | Complete |
| Part 10 | Upgrade troubleshooting notes | Planned |
| Part 11 | Final report and GitHub polish | Planned |

---

## Current VM configuration

| Setting | Value |
| --- | --- |
| VM name | Win10-to-Win11-Upgrade-Lab |
| VM location | `C:\VirtualMachines` |
| Upgrade path | Windows 10 Pro to Windows 11 Pro |
| Firmware | UEFI |
| Secure Boot | Enabled |
| TPM | Present |
| Memory | 8 GB |
| CPU | 2 cores |
| Disk | 80 GB |
| Network | NAT |
| Original Windows edition | Windows 10 Pro |
| Original Windows version | 22H2 |
| Original Windows build | 19045.3803 |
| Upgraded Windows edition | Windows 11 Pro |
| Upgraded Windows build shown in PowerShell | 26200 |
| Lab user | LabUser |
| VMware Tools | Installed and running |

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
│   ├── screenshot-02-windows-10-winver.png
│   ├── screenshot-03a-windows-10-systeminfo.png
│   ├── screenshot-03b-windows-10-tpm-secureboot-check.png
│   ├── screenshot-03c-windows-10-disk-memory-check.png
│   ├── screenshot-03d-windows-10-network-check.png
│   ├── screenshot-04a-vmware-tools-installation.png
│   ├── screenshot-04b-vmware-tools-installed.png
│   ├── screenshot-05a-windows-update-before-check.png
│   ├── screenshot-05b-windows-update-checking.png
│   ├── screenshot-05c-windows-update-end-of-support-status.png
│   ├── screenshot-06a-pre-upgrade-snapshot-created.png
│   ├── screenshot-06b-snapshot-manager-before-upgrade.png
│   ├── screenshot-07a-windows-11-iso-attached.png
│   ├── screenshot-07b-windows-11-setup-files.png
│   ├── screenshot-08a-windows-11-setup-start.png
│   ├── screenshot-08b-windows-11-license-or-readiness-check.png
│   ├── screenshot-08c-windows-11-ready-to-install-keep-files-apps.png
│   ├── screenshot-08d-windows-11-upgrade-installing.png
│   ├── screenshot-09a-windows-11-winver.png
│   ├── screenshot-09b-windows-11-powershell-version-check.png
│   ├── screenshot-09c-windows-11-tpm-secureboot-check.png
│   ├── screenshot-09d-windows-11-tpm-secureboot-check.png
│   ├── screenshot-09e-windows-11-device-manager-clean.png
│   └── screenshot-09f-windows-11-update-final-status.png
├── logbook.md
└── README.md
```

---

## Documentation and evidence

| File or folder | Purpose |
| --- | --- |
| `README.md` | Main GitHub project overview |
| `logbook.md` | Step-by-step project notes |
| `screenshots/` | Screenshot evidence |
| `results/` | Command output and verification results |
| `notes/` | Troubleshooting notes |

---

## Current screenshot evidence

| Screenshot | Purpose |
| --- | --- |
| `screenshot-01-project-structure.png` | Project folder and documentation structure |
| `screenshot-02-windows-10-winver.png` | Windows 10 Pro version and build verification |
| `screenshot-03a-windows-10-systeminfo.png` | Windows 10 system information baseline |
| `screenshot-03b-windows-10-tpm-secureboot-check.png` | TPM and Secure Boot verification before upgrade |
| `screenshot-03c-windows-10-disk-memory-check.png` | Disk, CPU and memory verification |
| `screenshot-03d-windows-10-network-check.png` | Network connectivity verification |
| `screenshot-04a-vmware-tools-installation.png` | VMware Tools installation evidence |
| `screenshot-04b-vmware-tools-installed.png` | VMware Tools running service verification |
| `screenshot-05a-windows-update-before-check.png` | Windows Update state before manual check |
| `screenshot-05b-windows-update-checking.png` | Windows Update downloading updates |
| `screenshot-05c-windows-update-end-of-support-status.png` | Windows 10 end-of-support/update status |
| `screenshot-06a-pre-upgrade-snapshot-created.png` | Pre-upgrade snapshot evidence |
| `screenshot-06b-snapshot-manager-before-upgrade.png` | Snapshot Manager showing rollback point |
| `screenshot-07a-windows-11-iso-attached.png` | Windows 11 ISO attached in VMware |
| `screenshot-07b-windows-11-setup-files.png` | Windows 11 setup files shown inside Windows 10 |
| `screenshot-08a-windows-11-setup-start.png` | Windows 11 Setup started |
| `screenshot-08b-windows-11-license-or-readiness-check.png` | Windows 11 readiness check |
| `screenshot-08c-windows-11-ready-to-install-keep-files-apps.png` | Ready to install with personal files and apps kept |
| `screenshot-08d-windows-11-upgrade-installing.png` | Windows 11 upgrade installation progress |
| `screenshot-09a-windows-11-winver.png` | Windows 11 version verification |
| `screenshot-09b-windows-11-powershell-version-check.png` | Windows 11 version/build check in PowerShell |
| `screenshot-09c-windows-11-tpm-secureboot-check.png` | TPM and Secure Boot verification after upgrade |
| `screenshot-09d-windows-11-tpm-secureboot-check.png` | Additional TPM and Secure Boot verification after upgrade |
| `screenshot-09e-windows-11-device-manager-clean.png` | Device Manager check after upgrade |
| `screenshot-09f-windows-11-update-final-status.png` | Final Windows 11 update status |

---

## Current progress

The Windows 10 ISO was prepared, copied away from OneDrive and renamed with a clear lab filename.

A new VMware VM was created with 8 GB RAM, 2 CPU cores, 80 GB disk, NAT networking, UEFI firmware, Secure Boot and virtual TPM.

Windows 10 Pro 22H2 was installed and verified with `winver`.

Windows 10 baseline checks were completed, including disk space, CPU, memory, TPM, Secure Boot and network connectivity.

VMware Tools was installed and verified with the `VMTools` service running.

Windows Update was checked before upgrade. Updates were detected, and Windows 10 later showed an end-of-support/missing-fixes status, supporting the business reason for upgrading.

A VMware snapshot named `Before Windows 11 Upgrade` was created before starting the upgrade.

The Windows 11 ISO was attached to the VM and launched from inside Windows 10 using `setup.exe`.

Windows Setup confirmed the in-place upgrade path as Windows 11 Pro while keeping personal files and apps.

The in-place upgrade completed successfully.

Post-upgrade checks confirmed Windows 11 build information, TPM, Secure Boot, Device Manager status and Windows Update status.

---

## Skills demonstrated

* VMware virtual machine setup
* Windows ISO preparation
* Windows 10 installation
* Windows 10 baseline verification
* UEFI configuration
* Secure Boot configuration
* Virtual TPM configuration
* VM encryption for TPM support
* NAT network configuration
* VMware Tools installation
* Windows service verification
* Windows Update review
* VMware snapshot creation
* Windows 11 in-place upgrade
* Post-upgrade validation
* Device Manager review
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

Windows may report some compatibility fields using Windows 10 naming even after upgrade, but `winver` and OS build information are used as the primary version evidence.
