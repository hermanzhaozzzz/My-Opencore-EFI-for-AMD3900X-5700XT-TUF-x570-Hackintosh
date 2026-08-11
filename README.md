# My-Opencore-EFI-for-AMD3900X-5700XT-TUF-x570-Hackintosh
> This EFI is created by Herman ZHAO
>
> E-mail: hermanzhaozzzz@gmail.com
>

---

-   OpenCore version: **1.0.7 RELEASE** (`REL-107-2026-03-20`)

-   Tested macOS version: **macOS Sequoia 15.2**

-   Required SMBIOS: **MacPro7,1**

---

When you use the same computer parts as me, you can gain a perfect AMD Mac OS machine by using my EFI.

---

CPU: AMD Ryzen-9 3900X 3.8GHz

GPU: 蓝宝石5700XT 8G 超白金极光特别版

Motherboard/主板: ASUS TUF Gaming X570 (without WIFI edition, there is no need to buy the WIFI edition if you want to hack into sh! We need another driver free net card)

Power: 海韵/SEASONIC GX750 750W 金牌全模

机箱: 恩杰NZXT H710i 黑红

CPU一体式水冷: 恩杰NZXT Kraken 海妖X73 360mm

内存: 芝奇G. SKILL 焰光戟 8G*4 F4-3600C16D-16GTZNC

SSD/固态硬盘: 

- Windows10-西部数据 SN550 500G NVMe协议

- macOS（当前实测 Sequoia 15.2）- 三星 970 EVO Plus

Wireless card/无线网卡+Bluetooth/蓝牙: 奋威 FV-T919 - 1750M 

Audio card: a USB audio card is used

For normal work, please use the **config.plist**

DO NOT edit the plist file **without** using Xcode or propertree!

REMEMBER to update your SMBIOS info.

> [!WARNING]
> The SMBIOS identifiers included in this public repository are demonstration
> values only. Generate your own Serial, MLB, SystemUUID, and ROM with
> [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) before booting this EFI.
> Do not reuse the included identifiers.
>
> 本公开仓库内的 SMBIOS 身份仅用于示例。使用此 EFI 前，请通过
> [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 生成自己的 Serial、MLB、
> SystemUUID 和 ROM，不要直接使用仓库内的身份信息。

## Compatibility and tested scope / 理论支持与实测范围

### Theoretical coverage / 理论覆盖

- The bundled AMD Vanilla kernel patches cover Darwin 17 through Darwin 25,
  corresponding to macOS 10.13 High Sierra through macOS 26 Tahoe. This only
  describes the kernel-patch range and is **not** a guarantee that every macOS
  release in that range has been tested with this complete EFI.
- Considering the `MacPro7,1` SMBIOS, RX 5700 XT support, and the bundled
  Broadcom/OCLP wireless stack, this repository is maintained primarily for
  macOS 14 Sonoma and macOS 15 Sequoia.
- macOS 26 Tahoe is covered by the AMD patch limits, but the complete EFI,
  wireless root patches, USB stack, and third-party Kexts have not been
  validated together. A direct major-version upgrade is therefore not
  recommended.

- 当前 AMD Vanilla 内核补丁理论覆盖 Darwin 17–25，即 macOS 10.13 High
  Sierra 至 macOS 26 Tahoe。该范围只代表内核补丁的匹配范围，**不代表这套完整
  EFI 已经在所有这些系统版本上测试通过**。
- 结合 `MacPro7,1`、RX 5700 XT 以及当前 Broadcom/OCLP 无线方案，本仓库主要
  面向 macOS 14 Sonoma 和 macOS 15 Sequoia。
- AMD 补丁虽然已经覆盖 macOS 26 Tahoe，但完整 EFI、无线 Root Patch、USB 和
  第三方 Kext 尚未组合验证，因此不建议直接进行大版本升级。

### Actually validated / 实际测试

This OpenCore 1.0.7 release was booted and tested on **macOS Sequoia 15.2**.
The following items were verified after the upgrade:

- macOS and Windows boot correctly from the OpenCore picker
- No duplicate `NO NAME` boot entry
- Wi-Fi, Bluetooth, USB 2.0/3.0, and audio
- RX 5700 XT graphics acceleration
- Smooth Bilibili video playback and screen sharing

The wired Realtek interface was not retested for this release because the
machine currently uses Wi-Fi. Other macOS versions remain unverified unless
explicitly documented here.

本次 OpenCore 1.0.7 已在 **macOS Sequoia 15.2** 实际启动并完成测试：macOS 与
Windows 双系统引导、无重复 `NO NAME` 启动项、Wi-Fi、蓝牙、USB 2.0/3.0、声音、
RX 5700 XT 图形加速、Bilibili 视频播放和屏幕共享均正常。由于当前使用 Wi-Fi，
本次没有重新测试 Realtek 有线网卡。未在此明确列出的系统版本均视为未实测。

## macOS update policy / 系统更新策略

- Minor updates within the currently validated major version, such as macOS
  15.x updates, can normally be installed manually after making a working EFI
  backup. OCLP root patches may be removed by the macOS update and must be
  reinstalled afterward to restore Broadcom Wi-Fi support.
- Major upgrades, especially macOS 15 to macOS 26, are not recommended until
  OpenCore, AMD patches, Kexts, USB mapping, and OCLP wireless patches have all
  been reviewed and tested together.
- Do not leave automatic macOS upgrades enabled on this Hackintosh. The
  recommended tool is
  [`macupdatectl`](https://github.com/hermanzhaozzzz/.my_shell_envs/blob/main/bin/macupdatectl).
  Run `macupdatectl` and choose **“只屏蔽大版本，保留安全更新”**. The tool also
  provides restore and full-block modes; full blocking also pauses system
  security-data updates, so it is not the default recommendation here.

- 当前已验证大版本内的小版本更新（例如 macOS 15.x）通常可以在备份 EFI 后手动
  安装。系统更新会清除 OCLP Root Patch，更新完成后需要重新执行 Root Patch，
  才能恢复 Broadcom Wi-Fi。
- 不建议直接进行大版本升级，尤其不要直接从 macOS 15 升级 macOS 26；应先重新
  审核并组合测试 OpenCore、AMD 补丁、Kext、USB 映射和 OCLP 无线补丁。
- 推荐使用
  [`macupdatectl`](https://github.com/hermanzhaozzzz/.my_shell_envs/blob/main/bin/macupdatectl)
  管理更新。运行 `macupdatectl` 后选择 **“只屏蔽大版本，保留安全更新”**。如果选择
  “屏蔽所有系统更新”，系统安全数据更新也会暂停，因此这里不将其作为默认方案。

## Required SMBIOS: `MacPro7,1` / 必须仿冒的机型

This Ryzen 9 3900X + RX 5700 XT build must use the **`MacPro7,1`** SMBIOS.
Do not use `iMac20,2`: the Ryzen 9 3900X has no integrated GPU, while an iMac
SMBIOS expects an iGPU to handle some background graphics and video workloads.
On macOS 15.2, using `iMac20,2` caused observable stuttering during Bilibili
video playback and screen sharing. Switching to `MacPro7,1` allowed the RX 5700
XT to handle those workloads and removed the stuttering in testing. See
[Dortania's SMBIOS guidance](https://dortania.github.io/OpenCore-Install-Guide/extras/smbios-support.html)
for the rationale behind using an iMac Pro or Mac Pro SMBIOS on CPUs without an
iGPU.

这套 Ryzen 9 3900X + RX 5700 XT 配置必须仿冒 **`MacPro7,1`**，不要使用
`iMac20,2`。Ryzen 9 3900X 没有核显，而普通 iMac 的 SMBIOS 会假定系统存在核显，
并可能把部分后台图形和视频任务交给核显路径。在 macOS 15.2 的实际测试中，
`iMac20,2` 会导致 Bilibili 视频播放及屏幕共享出现卡顿；切换为 `MacPro7,1`
后，这些任务由 RX 5700 XT 承担，卡顿消失。这里的关键是准确使用
**`MacPro7,1`**，而不是任意 Mac Pro 或 iMac 机型。

![image](pictures/SMBIOSinfo.jpg)

Works fine:

- AMD CPU
- 5700XT GPU
- Wireless network card
- Bluetooth
- Sleep wake
- Audio card

Not work:

- Sidecar(Because this CPU do not have Core graphics)

Tips:
- Modify the BIOS setting to turn on the Virtual function of AMD cpu(for VMWare)
- BIOS Overclocking reference:
    - Recommend `flck frequency` ≤1800 MHz (I use 1800 MHz)
    - Recommend`memory frequency`≤3600 Mhz (I use 3333 MHz)

<u>Please update your SMbios info!</u>


AFTER you successfully login the system, you may find that WIFI and bluetooth can not work, you should install [OpenCore-Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/) and run the "Post-Install Root Patch" protocol and reboot. Then, you will make it!

## Companion tool / 配套工具

[LiquidBar](https://github.com/hermanzhaozzzz/LiquidBar) is a lightweight native
macOS menu-bar app built and tested with this EFI setup. It reads the Ryzen CPU
temperature through VirtualSMC/SMCAMDProcessor and monitors or controls the NZXT
Kraken X73 and Smart Device V2 through liquidctl.

[LiquidBar](https://github.com/hermanzhaozzzz/LiquidBar) 是针对本 EFI 配置开发并测试的
轻量原生 macOS 菜单栏工具。它通过 VirtualSMC/SMCAMDProcessor 读取 Ryzen CPU 温度，
并通过 liquidctl 监控及控制 NZXT Kraken X73 与 Smart Device V2。
