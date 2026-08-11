# 第三方组件声明

[English](THIRD_PARTY_NOTICES.md) | [简体中文](THIRD_PARTY_NOTICES_CN.md)

最后核对时间：2026 年 8 月 12 日

本仓库重新分发了第三方引导文件、固件驱动、内核扩展、资源及补丁数据。这些内容
**不属于**本仓库 MIT 许可证的授权范围。其版权归各自作者所有，并继续遵循上游
许可证或其他适用条款。

下方链接是查阅许可证正文、源代码及版权声明的权威来源。使用者和再次分发者应
自行阅读并遵守相关条款。本文件仅用于署名和组件清单，不能替代上游许可证。

## 引导程序、驱动、资源及补丁

| 仓库内组件 | 上游项目 | 许可证或状态 |
|---|---|---|
| OpenCore 1.0.7、OpenRuntime、OpenCanopy、ResetNvramEntry | [Acidanthera/OpenCorePkg](https://github.com/acidanthera/OpenCorePkg) | [BSD 3-Clause](https://github.com/acidanthera/OpenCorePkg/blob/master/LICENSE.txt) |
| HFSPlus 驱动及 OpenCore 音频、字体和图像资源 | [Acidanthera/OcBinaryData](https://github.com/acidanthera/OcBinaryData) | 上游仓库没有单独的许可证文件；再次分发前请查阅上游条款 |
| `config.plist` 内的 AMD Vanilla 内核补丁 | [AMD-OSX/AMD_Vanilla](https://github.com/AMD-OSX/AMD_Vanilla) | 上游仓库没有单独的许可证文件；再次分发前请查阅上游条款 |

## 内核扩展

| 仓库内组件 | 版本 | 上游项目 | 许可证或状态 |
|---|---:|---|---|
| AMDRyzenCPUPowerManagement、SMCAMDProcessor | 0.7.2 / 1.0.1 | [trulyspinach/SMCAMDProcessor](https://github.com/trulyspinach/SMCAMDProcessor) | BSD 3-Clause |
| AMFIPass | 1.4.1 | Dhinak G.；配合 [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher) 使用 | 保留上游版权和条款；原独立仓库目前已不可访问 |
| AppleALC | 1.9.8 | [Acidanthera/AppleALC](https://github.com/acidanthera/AppleALC) | BSD 3-Clause |
| AppleMCEReporterDisabler | 1.2 | AMD 黑苹果社区组件，见 [Dortania](https://github.com/dortania/OpenCore-Install-Guide) | 未找到单独的上游许可证，本项目不对其重新授权 |
| BlueToolFixup、BrcmFirmwareData、BrcmPatchRAM3 | 2.6.9 | [Acidanthera/BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM) | GPL-2.0 |
| IO80211FamilyLegacy、IOSkywalkFamily | 12.0 / 1.0 | [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher) 使用的 Apple 组件 | Apple 版权所有并遵循适用的 Apple 条款；不属于本项目 MIT 许可证范围 |
| Lilu | 1.7.3 | [Acidanthera/Lilu](https://github.com/acidanthera/Lilu) | BSD 3-Clause |
| NVMeFix | 1.1.2 | [Acidanthera/NVMeFix](https://github.com/acidanthera/NVMeFix) | [BSD 3-Clause](https://github.com/acidanthera/NVMeFix/blob/master/LICENSE.txt) |
| RealtekRTL8111 | 2.4.2 | [Mieze/RTL8111_driver_for_OS_X](https://github.com/Mieze/RTL8111_driver_for_OS_X) | GPL-2.0 |
| RestrictEvents | 1.1.7 | [Acidanthera/RestrictEvents](https://github.com/acidanthera/RestrictEvents) | BSD 3-Clause |
| SMCRadeonSensors | 2.0.0 | [ChefKiss](https://chefkiss.dev/) | 保留上游版权和条款，本项目不对其重新授权 |
| SMCProcessor、SMCSuperIO、VirtualSMC | 1.3.4 / 1.3.4 / 1.3.8 | [Acidanthera/VirtualSMC](https://github.com/acidanthera/VirtualSMC) | BSD 3-Clause |
| USBToolBox | 1.1.1 | [USBToolBox/kext](https://github.com/USBToolBox/kext) | 上游仓库没有单独的许可证文件；再次分发前请查阅上游条款 |
| UTBMap | 1.1 | 针对本机生成的 USB 映射 | 仓库专属配置，参阅 [LICENSE](LICENSE) |
| WhateverGreen | 1.7.1 | [Acidanthera/WhateverGreen](https://github.com/acidanthera/WhateverGreen) | BSD 3-Clause |

## 补充说明

OpenCore Legacy Patcher 具有自己的
[许可证条款](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/LICENSE.txt)。
Apple 品牌的二进制文件和组件版权归 Apple Inc. 所有。它们出现在本仓库中，并不
代表本项目授予了 Apple 条款或适用法律以外的其他权利。

如果本声明中的来源、版本、署名或许可证状态存在错误，欢迎提交 Issue 以便修正。
