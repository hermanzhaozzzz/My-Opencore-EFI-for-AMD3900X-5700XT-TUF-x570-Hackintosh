# Ryzen 9 3900X + RX 5700 XT 黑苹果 EFI

[English](README.md) | **简体中文**

这是我目前正在使用的一套 OpenCore EFI，适用于 Ryzen 9 3900X、RX 5700 XT
和 ASUS TUF Gaming X570 这套硬件，或配置非常接近的电脑。

| OpenCore | 实测系统 | SMBIOS |
|---|---|---|
| **1.0.7 RELEASE** | **macOS Sequoia 15.2** | **必须使用 `MacPro7,1`** |

最新的可用版本请从 [Releases](https://github.com/hermanzhaozzzz/My-Opencore-EFI-for-AMD3900X-5700XT-TUF-x570-Hackintosh/releases)
下载。

## 使用前先看这里

1. 先备份你现在能够正常启动的 EFI。
2. 使用 [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) 生成一套
   **`MacPro7,1`** 的 Serial、MLB、SystemUUID 和 ROM，替换仓库中的演示值。
3. 正常启动使用 `config.plist`；修改配置推荐使用
   [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools)。
4. 这套 USB 映射是按照我的主板和设备制作的。如果你的接口布局不同，请重新检查
   USB 映射。

> [!WARNING]
> 不要直接使用公开仓库中的 SMBIOS 身份，也不要为这套配置选择 `iMac20,2`。

## 为什么一定要用 `MacPro7,1`

我最初使用 `iMac20,2`，系统可以启动，但 Bilibili 视频和屏幕共享会明显卡顿。
Ryzen 9 3900X 没有核显，切换到 `MacPro7,1` 后，相关任务能够正常交给
RX 5700 XT，卡顿随即消失。

切换后，我同时播放了 **8 路 4K 视频**，画面依然非常流畅；使用 PyTorch MPS
对 RX 5700 XT 进行持续压力测试也一切正常。测试代码和结果见
[PyTorch MPS 教程](tutorial_pytorch-via-this_AMD5700xtGPU/README_CN.md)。

![SMBIOS 信息](pictures/SMBIOSinfo.jpg)

## 硬件配置

| 硬件 | 型号 |
|---|---|
| CPU | AMD Ryzen 9 3900X 3.8 GHz |
| GPU | 蓝宝石 Radeon RX 5700 XT 8 GB 超白金极光特别版 |
| 主板 | ASUS TUF Gaming X570，无 Wi-Fi 版 |
| 内存 | 金士顿 DDR4，16 GB × 4，共 64 GB，2666 MHz |
| macOS 固态硬盘 | 三星 970 EVO Plus |
| Windows 固态硬盘 | 西部数据 SN550 500 GB NVMe |
| Wi-Fi / 蓝牙 | 奋威 FV-T919 |
| 声音 | 显示器通过 HDMI/DisplayPort 外接音频；主板音频接口也已测试可用 |
| 机箱 | 恩杰 NZXT H710i 黑红版 |
| CPU 水冷 | 恩杰 NZXT Kraken X73 360 mm |
| 电源 | 海韵 GX750 750 W，金牌全模组 |

## 已测试功能

- macOS 与 Windows 双系统启动
- RX 5700 XT 图形加速
- Bilibili 视频、8 路 4K 视频同时播放和屏幕共享
- PyTorch 通过 MPS/Metal 调用 RX 5700 XT
- Wi-Fi、蓝牙和 AirDrop
- USB 2.0、USB 3.0、睡眠与唤醒
- HDMI/DisplayPort 音频和主板音频接口

本轮测试使用 Wi-Fi，没有重新测试 Realtek 有线网卡。

### 已知限制

- Sidecar 无法使用。
- iPhone 镜像无法使用。

## Wi-Fi 与蓝牙

如果第一次进入 macOS 后奋威 FV-T919 无法使用，请安装
[OpenCore Legacy Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/)，
执行 **Post-Install Root Patch**，然后重启。

系统更新可能会清除 Root Patch；遇到 Wi-Fi 或蓝牙消失时，重新执行一次即可。

## 系统升级建议

这套 EFI 理论上覆盖 macOS 10.13 High Sierra 至 macOS 26 Tahoe，但我实际完整
测试的是 **macOS Sequoia 15.2**，日常使用建议以 Sonoma 或 Sequoia 为主。

- 同一大版本内的小版本更新可以尝试，但请先备份 EFI。
- 不建议直接升级 macOS 大版本；OpenCore、Kext 和 OCLP 都可能需要同步更新。
- 推荐使用 [`macupdatectl`](https://github.com/hermanzhaozzzz/.my_shell_envs/blob/main/bin/macupdatectl)
  屏蔽大版本升级，同时保留安全更新。

## 额外教程福利

- [LiquidBar](https://github.com/hermanzhaozzzz/LiquidBar)：我开发的 NZXT 机箱风扇、
  水冷泵功率和温度监控工具。强烈建议使用同款机箱和水冷的用户安装。
- [通过 MPS/Metal 在 PyTorch 中调用 RX 5700 XT](tutorial_pytorch-via-this_AMD5700xtGPU/README_CN.md)：
  包含 `uv` 和 Conda 安装方法、最小验证代码、压力测试和本机实测结果。

## 联系与赞助

- 作者：Herman ZHAO
- 邮箱：hermanzhaozzzz@gmail.com
- 最近维护：2026 年 8 月 12 日

整理 EFI、反复重启测试和编写教程都需要不少时间。如果这个项目帮你少走了一些
弯路，欢迎请我喝杯咖啡。赞助完全自愿，也感谢你的使用和反馈。

| 支付宝 | 微信支付 |
|:---:|:---:|
| <img src="pictures/sponsor-alipay.jpg" alt="支付宝赞助二维码" width="280"> | <img src="pictures/sponsor-wechat-pay.jpg" alt="微信支付赞助二维码" width="280"> |
