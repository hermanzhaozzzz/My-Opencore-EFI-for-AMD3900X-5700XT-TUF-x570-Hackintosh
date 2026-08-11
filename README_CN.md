# AMD Ryzen 9 3900X、RX 5700 XT 与 ASUS TUF X570 的 OpenCore EFI

[English](README.md) | [简体中文](README_CN.md)

作者及维护者：Herman ZHAO

联系邮箱：hermanzhaozzzz@gmail.com

本 EFI 最新维护时间：2026 年 8 月 12 日

## 当前版本

| 项目 | 版本或状态 |
|---|---|
| OpenCore | **1.0.7 RELEASE**（`REL-107-2026-03-20`） |
| 实际测试的 macOS | **macOS Sequoia 15.2** |
| 必须使用的 SMBIOS | **`MacPro7,1`** |

这套 EFI 适用于与本机相同或非常接近的硬件配置。

## 硬件配置

| 硬件 | 型号 |
|---|---|
| CPU | AMD Ryzen 9 3900X 3.8 GHz |
| GPU | 蓝宝石 Radeon RX 5700 XT 8 GB 超白金极光特别版 |
| 主板 | ASUS TUF Gaming X570，无 Wi-Fi 版 |
| 电源 | 海韵 GX750 750 W，金牌全模组 |
| 机箱 | 恩杰 NZXT H710i 黑红版 |
| CPU 水冷 | 恩杰 NZXT Kraken X73 360 mm |
| 内存 | 金士顿 DDR4，共 64 GB，16 GB × 4，2666 MHz |
| Windows 固态硬盘 | 西部数据 SN550 500 GB NVMe |
| macOS 固态硬盘 | 三星 970 EVO Plus |
| Wi-Fi / 蓝牙 | 奋威 FV-T919 |
| 声音 | 显示器通过 HDMI/DisplayPort 外接音频；主板音频接口已测试可用 |

## 使用前必读

- 正常启动请使用 `config.plist`。
- 推荐使用 OCAuxiliaryTools 编辑 `config.plist`。
- 第一次启动前必须生成自己的 SMBIOS 身份信息。

> [!WARNING]
> 公开仓库中的 SMBIOS 身份仅为演示值。请使用
> [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 生成自己的 Serial、MLB、
> SystemUUID 和 ROM，**并且在 GenSMBIOS 中必须选择 `MacPro7,1` 机型**。
> 不要选择其他 Mac 机型，也不要直接使用仓库中的身份信息。

## 理论支持与实测范围

### 理论覆盖

- 当前 AMD Vanilla 内核补丁覆盖 Darwin 17–25，即 macOS 10.13 High Sierra
  至 macOS 26 Tahoe。这个范围只代表内核补丁能够匹配，不能保证整套 EFI 已在
  每个系统版本上测试通过。
- 结合 `MacPro7,1`、RX 5700 XT 及当前 Broadcom/OCLP 无线方案，本仓库主要
  面向 macOS 14 Sonoma 和 macOS 15 Sequoia。
- AMD 补丁虽然包含 macOS 26 Tahoe，但完整 EFI、无线 Root Patch、USB 和
  第三方 Kext 尚未在 Tahoe 上完成组合验证，因此不建议直接进行大版本升级。

### 实际验证

OpenCore 1.0.7 已在 **macOS Sequoia 15.2** 实际启动并验证以下功能：

- 从 OpenCore 选择器正常启动 macOS 和 Windows；
- Wi-Fi 和蓝牙；
- USB 2.0 和 USB 3.0；
- 显示器通过 HDMI/DisplayPort 外接音频，主板音频接口可用；
- RX 5700 XT 图形加速；
- Bilibili 视频流畅播放及屏幕共享。

由于本机目前使用 Wi-Fi，本次没有重新测试 Realtek 有线网卡。未在上面明确
列出的 macOS 版本均应视为未经测试。

## macOS 更新策略

- 当前已验证大版本内的小版本更新，例如 macOS 15.x，通常可以在完整备份一份
  已知正常的 EFI 后手动安装。
- macOS 更新可能清除 OCLP Root Patch。更新后需要重新执行 Post-Install Root
  Patch，才能恢复 Broadcom Wi-Fi。
- 不建议直接进行大版本升级，尤其不要直接从 macOS 15 升级 macOS 26。升级前
  应重新检查并组合测试 OpenCore、AMD 补丁、Kext、USB 映射和 OCLP 无线补丁。
- 不要在黑苹果上保持大版本自动升级。推荐使用
  [`macupdatectl`](https://github.com/hermanzhaozzzz/.my_shell_envs/blob/main/bin/macupdatectl)，
  运行后选择 **“只屏蔽大版本，保留安全更新”**。完全屏蔽会同时暂停系统安全
  数据更新，因此不作为默认建议。

## 必须使用的 SMBIOS：`MacPro7,1`

这套 Ryzen 9 3900X + RX 5700 XT 配置必须使用 **`MacPro7,1`**，不要使用
`iMac20,2`。Ryzen 9 3900X 没有核显，而普通 iMac 的 SMBIOS 可能会假定系统
存在核显，并把部分后台图形和视频任务交给核显路径。

在 macOS 15.2 的实际测试中，`iMac20,2` 会导致 Bilibili 视频播放及屏幕共享
出现明显卡顿；切换为 `MacPro7,1` 后，这些工作由 RX 5700 XT 承担，卡顿消失。
关于无核显 CPU 为什么应使用 iMac Pro 或 Mac Pro SMBIOS，可参阅
[Dortania 的 SMBIOS 指南](https://dortania.github.io/OpenCore-Install-Guide/extras/smbios-support.html)。

![SMBIOS 信息](pictures/SMBIOSinfo.jpg)

## 已正常工作的功能

- AMD CPU
- RX 5700 XT 图形加速
- Wi-Fi
- 蓝牙
- AirDrop
- 睡眠与唤醒
- 显示器通过 HDMI/DisplayPort 外接音频，主板音频接口可用

## 已知限制

- 由于 CPU 没有核显，Sidecar 无法使用。
- iPhone 镜像无法使用。

## BIOS 提示

- 如果需要使用 VMware，请开启 AMD CPU 虚拟化。
- FCLK 建议不超过 1800 MHz；本机使用 1800 MHz。
- 内存频率建议不超过 3600 MHz；本机目前使用 2666 MHz。

## 安装后的 Wi-Fi 与蓝牙

第一次成功进入 macOS 后，Wi-Fi 和蓝牙可能仍然无法使用。请安装
[OpenCore Legacy Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/)，
执行 **Post-Install Root Patch**，然后重启。

## 额外教程福利

- [LiquidBar](https://github.com/hermanzhaozzzz/LiquidBar) — 我开发的一套用于控制
  恩杰 NZXT 机箱风扇和水冷泵功率、监控温度的程序。强烈建议使用同款机箱和
  水冷的用户安装。

- [通过 MPS/Metal 在 PyTorch 中调用 RX 5700 XT](tutorial_pytorch-via-this_AMD5700xtGPU/README_CN.md) —
  包含经过验证的 `uv` 和 Conda 安装方法、最小 GPU 验证、性能测试及本机实测结果。

## 支持与赞助

整理、升级并实际测试这套 EFI 和相关教程需要投入不少时间与精力。如果本项目
对您有所帮助，欢迎请我喝杯咖啡。赞助完全自愿，您的认可与支持就是我继续维护
和分享的动力，非常感谢！

| 支付宝 | 微信支付 |
|:---:|:---:|
| <img src="pictures/sponsor-alipay.jpg" alt="支付宝赞助二维码" width="280"> | <img src="pictures/sponsor-wechat-pay.jpg" alt="微信支付赞助二维码" width="280"> |
