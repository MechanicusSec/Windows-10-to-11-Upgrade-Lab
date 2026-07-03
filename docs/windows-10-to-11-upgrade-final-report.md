# Windows 10 to Windows 11 Upgrade Lab — Final Report

## Report metadata

| Field | Detail |
| --- | --- |
| Project | Windows 10 to Windows 11 Upgrade Lab |
| Environment | Local VMware lab |
| Source OS | Windows 10 Pro |
| Target OS | Windows 11 Pro |
| Upgrade type | In-place upgrade |
| VM name | Win10-to-Win11-Upgrade-Lab |
| Lab user | LabUser |
| Report type | Final upgrade report |
| Date | 2026-07-03 |

---

## Purpose

This report summarizes a safe local lab upgrade from Windows 10 Pro to Windows 11 Pro.

The goal was to practice the type of work an IT support technician or junior sysadmin may perform when preparing client devices for a Windows 11 migration.

The lab focused on preparation, compatibility checks, update checks, snapshot safety, in-place upgrade execution and post-upgrade verification.

---

## Scope

The lab included:

* Windows 10 ISO preparation.
* VMware virtual machine creation.
* Windows 10 Pro installation.
* UEFI, Secure Boot and virtual TPM configuration.
* Windows 10 baseline verification.
* VMware Tools installation.
* Windows Update review before upgrade.
* VMware snapshot creation before upgrade.
* Windows 11 ISO attachment.
* Windows 11 in-place upgrade.
* Post-upgrade verification.
* Troubleshooting notes.
* GitHub documentation.

The lab did not use real company devices, production systems, personal Microsoft accounts, real user data, license keys, passwords or private files.

---

## Lab environment

| Component | Value |
| --- | --- |
| Virtualization platform | VMware Workstation |
| VM name | Win10-to-Win11-Upgrade-Lab |
| VM storage location | `C:\VirtualMachines` |
| Network mode | NAT |
| Memory | 8 GB |
| CPU | 2 cores |
| Disk | 80 GB |
| Firmware | UEFI |
| Secure Boot | Enabled |
| TPM | Present |
| Account type | Local lab account |
| Lab account | LabUser |

---

## Source operating system

| Item | Value |
| --- | --- |
| Operating system | Windows 10 Pro |
| Version | 22H2 |
| OS build | 19045.3803 |
| Installation type | Clean Windows 10 installation |
| VMware Tools | Installed and running |
| Windows Update | Checked before upgrade |

---

## Target operating system

| Item | Value |
| --- | --- |
| Operating system | Windows 11 Pro |
| Upgrade method | In-place upgrade |
| Setup method | `setup.exe` launched from mounted Windows 11 ISO |
| Files and apps | Kept |
| OS build shown in PowerShell | 26200 |
| TPM after upgrade | Present and ready |
| Secure Boot after upgrade | Enabled |
| Windows Update after upgrade | Required updates completed |
| Device Manager after upgrade | Checked |

---

## Preparation summary

Before upgrading, the VM was configured to meet Windows 11 requirements.

The VM used UEFI firmware, Secure Boot and a virtual TPM.

The virtual machine was assigned 8 GB of memory, 2 CPU cores and an 80 GB virtual disk.

VMware Tools was installed and verified with the `VMTools` Windows service.

Windows Update was checked before the upgrade. Windows 10 later showed an end-of-support or missing-fixes status, which supported the business reason for moving to Windows 11.

A VMware snapshot named `Before Windows 11 Upgrade` was created before beginning the upgrade. This provided a rollback point if the upgrade failed.

---

## Upgrade process summary

The Windows 11 ISO was attached to the VMware virtual CD/DVD drive.

The upgrade was started from inside Windows 10 by opening the mounted ISO and running:

```text
setup.exe
```

Windows Setup confirmed the intended upgrade path:

| Item | Selection |
| --- | --- |
| Target operating system | Windows 11 Pro |
| Files and apps | Keep personal files and apps |

The upgrade was then started and allowed to complete without interruption.

The VM rebooted during the upgrade process and returned to the upgraded Windows desktop.

---

## Verification summary

After the upgrade, the system was verified with Windows graphical tools and PowerShell commands.

### Commands used

```powershell
winver

Get-ComputerInfo | Select-Object WindowsProductName,WindowsVersion,OsBuildNumber

Get-Tpm

Confirm-SecureBootUEFI

Get-Service VMTools
```

### Command purpose

| Command | Purpose |
| --- | --- |
| `winver` | Shows the installed Windows version and build information. |
| `Get-ComputerInfo` | Displays Windows system and OS information. |
| `Select-Object` | Filters PowerShell output to selected fields. |
| `Get-Tpm` | Verifies TPM presence and readiness. |
| `Confirm-SecureBootUEFI` | Confirms Secure Boot is enabled. |
| `Get-Service VMTools` | Confirms VMware Tools is installed and running. |

---

## Evidence collected

| Screenshot | Purpose |
| --- | --- |
| `screenshot-01-project-structure.png` | Project folder and documentation structure |
| `screenshot-02-windows-10-winver.png` | Windows 10 version verification |
| `screenshot-03a-windows-10-systeminfo.png` | Windows 10 system information baseline |
| `screenshot-03b-windows-10-tpm-secureboot-check.png` | TPM and Secure Boot before upgrade |
| `screenshot-03c-windows-10-disk-memory-check.png` | Disk, memory and CPU verification |
| `screenshot-03d-windows-10-network-check.png` | Network connectivity verification |
| `screenshot-04a-vmware-tools-installation.png` | VMware Tools installation evidence |
| `screenshot-04b-vmware-tools-installed.png` | VMware Tools service verification |
| `screenshot-05a-windows-update-before-check.png` | Windows Update before manual check |
| `screenshot-05b-windows-update-checking.png` | Windows Update downloading updates |
| `screenshot-05c-windows-update-end-of-support-status.png` | Windows 10 end-of-support/update status |
| `screenshot-06a-pre-upgrade-snapshot-created.png` | Pre-upgrade snapshot evidence |
| `screenshot-06b-snapshot-manager-before-upgrade.png` | Snapshot Manager rollback point |
| `screenshot-07a-windows-11-iso-attached.png` | Windows 11 ISO attached in VMware |
| `screenshot-07b-windows-11-setup-files.png` | Windows 11 setup files inside Windows 10 |
| `screenshot-08a-windows-11-setup-start.png` | Windows 11 Setup start |
| `screenshot-08b-windows-11-license-or-readiness-check.png` | Windows 11 readiness check |
| `screenshot-08c-windows-11-ready-to-install-keep-files-apps.png` | Ready to install and keep files/apps |
| `screenshot-08d-windows-11-upgrade-installing.png` | Upgrade installation progress |
| `screenshot-09a-windows-11-winver.png` | Windows 11 version verification |
| `screenshot-09b-windows-11-powershell-version-check.png` | Windows version/build PowerShell check |
| `screenshot-09c-windows-11-tpm-secureboot-check.png` | TPM and Secure Boot after upgrade |
| `screenshot-09d-windows-11-tpm-secureboot-check.png` | Additional TPM/Secure Boot evidence |
| `screenshot-09e-windows-11-device-manager-clean.png` | Device Manager after upgrade |
| `screenshot-09f-windows-11-update-final-status.png` | Final Windows Update status |

---

## Troubleshooting observations

During the lab, `ping microsoft.com` timed out. This did not mean that network access was broken.

Connectivity was instead verified with:

```powershell
Test-NetConnection microsoft.com -CommonTCPPort HTTP
```

The result showed successful TCP connectivity.

PowerShell also showed `WindowsProductName` as `Windows 10 Pro` while showing a Windows 11 build number. This can happen because some compatibility fields may still use older naming internally. For version evidence, `winver` and OS build information were treated as the stronger indicators.

Windows Update later showed the system as up to date while offering an optional preview update. The optional preview update was not required for this lab.

---

## Result

The Windows 10 Pro VM was successfully upgraded to Windows 11 Pro.

The upgrade preserved the local lab account and kept personal files and apps.

Post-upgrade checks confirmed that TPM, Secure Boot, VMware Tools, Device Manager and Windows Update were functioning after the upgrade.

The lab successfully demonstrates a safe, documented Windows 10 to Windows 11 upgrade workflow in VMware.

---

## Skills demonstrated

This lab demonstrates:

* Windows client installation.
* Windows 10 to Windows 11 upgrade preparation.
* VMware Workstation administration.
* Virtual TPM configuration.
* Secure Boot and UEFI verification.
* Windows Update review.
* VMware snapshot usage.
* In-place upgrade execution.
* Post-upgrade validation.
* PowerShell verification.
* Troubleshooting documentation.
* Git and GitHub documentation workflow.

---

## Final conclusion

The lab met its goal.

The Windows 10 VM was prepared, verified, snapshotted, upgraded to Windows 11 and checked after the upgrade.

The project is suitable as a portfolio lab for IT support, desktop support and junior sysadmin learning.
