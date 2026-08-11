# Third-Party Notices

[English](THIRD_PARTY_NOTICES.md) | [简体中文](THIRD_PARTY_NOTICES_CN.md)

Last reviewed: August 12, 2026

This repository redistributes third-party bootloader files, firmware drivers,
kernel extensions, resources and patch data. They are **not** covered by this
repository's MIT license. Copyright remains with the respective authors, and
each item remains subject to its upstream license or other applicable terms.

The links below are the authoritative sources for license text, source code and
notices. Users and redistributors are responsible for reviewing and complying
with those terms. This file is an attribution and inventory; it does not replace
the upstream licenses.

## Bootloader, drivers, resources and patches

| Bundled material | Upstream project | License or status |
|---|---|---|
| OpenCore 1.0.7, OpenRuntime, OpenCanopy and ResetNvramEntry | [Acidanthera/OpenCorePkg](https://github.com/acidanthera/OpenCorePkg) | [BSD 3-Clause](https://github.com/acidanthera/OpenCorePkg/blob/master/LICENSE.txt) |
| HFSPlus driver and OpenCore audio/font/image resources | [Acidanthera/OcBinaryData](https://github.com/acidanthera/OcBinaryData) | Upstream repository publishes no standalone license file; consult upstream before redistribution |
| AMD Vanilla kernel patches embedded in `config.plist` | [AMD-OSX/AMD_Vanilla](https://github.com/AMD-OSX/AMD_Vanilla) | Upstream repository publishes no standalone license file; consult upstream before redistribution |

## Kernel extensions

| Bundled component | Version | Upstream project | License or status |
|---|---:|---|---|
| AMDRyzenCPUPowerManagement, SMCAMDProcessor | 0.7.2 / 1.0.1 | [trulyspinach/SMCAMDProcessor](https://github.com/trulyspinach/SMCAMDProcessor) | BSD 3-Clause |
| AMFIPass | 1.4.1 | Dhinak G.; distributed for use with [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher) | Retains upstream copyright and terms; original standalone repository is no longer available |
| AppleALC | 1.9.8 | [Acidanthera/AppleALC](https://github.com/acidanthera/AppleALC) | BSD 3-Clause |
| AppleMCEReporterDisabler | 1.2 | AMD Hackintosh community component referenced by [Dortania](https://github.com/dortania/OpenCore-Install-Guide) | No standalone upstream license identified; not relicensed here |
| BlueToolFixup, BrcmFirmwareData, BrcmPatchRAM3 | 2.6.9 | [Acidanthera/BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM) | GPL-2.0 |
| IO80211FamilyLegacy, IOSkywalkFamily | 12.0 / 1.0 | Apple components used by [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher) | Apple copyright and applicable Apple terms; not covered by this project's MIT license |
| Lilu | 1.7.3 | [Acidanthera/Lilu](https://github.com/acidanthera/Lilu) | BSD 3-Clause |
| NVMeFix | 1.1.2 | [Acidanthera/NVMeFix](https://github.com/acidanthera/NVMeFix) | [BSD 3-Clause](https://github.com/acidanthera/NVMeFix/blob/master/LICENSE.txt) |
| RealtekRTL8111 | 2.4.2 | [Mieze/RTL8111_driver_for_OS_X](https://github.com/Mieze/RTL8111_driver_for_OS_X) | GPL-2.0 |
| RestrictEvents | 1.1.7 | [Acidanthera/RestrictEvents](https://github.com/acidanthera/RestrictEvents) | BSD 3-Clause |
| SMCRadeonSensors | 2.0.0 | [ChefKiss](https://chefkiss.dev/) | Retains upstream copyright and terms; not relicensed here |
| SMCProcessor, SMCSuperIO, VirtualSMC | 1.3.4 / 1.3.4 / 1.3.8 | [Acidanthera/VirtualSMC](https://github.com/acidanthera/VirtualSMC) | BSD 3-Clause |
| USBToolBox | 1.1.1 | [USBToolBox/kext](https://github.com/USBToolBox/kext) | Upstream repository publishes no standalone license file; consult upstream before redistribution |
| UTBMap | 1.1 | Generated USB map specific to this machine | Repository-specific configuration; see [LICENSE](LICENSE) |
| WhateverGreen | 1.7.1 | [Acidanthera/WhateverGreen](https://github.com/acidanthera/WhateverGreen) | BSD 3-Clause |

## Additional notice

OpenCore Legacy Patcher has its own
[license terms](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/LICENSE.txt).
Apple-branded binaries and components remain copyrighted by Apple Inc. Their
presence in this repository does not grant any license beyond the rights, if
any, supplied by Apple or applicable law.

If an attribution, source link, version or license status is inaccurate, please
open an issue so the notice can be corrected.
