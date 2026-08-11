# My-Opencore-EFI-for-AMD3900X-5700XT-TUF-x570-Hackintosh
> This EFI is created by Herman ZHAO
>
> E-mail: hermanzhaozzzz@gmail.com
>

---

-   Opencore version: 1.0.3

-   Mac OS version: 15.2

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

- Mac OS(Catalina10.15.5)-三星 970 EVO Plus

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
