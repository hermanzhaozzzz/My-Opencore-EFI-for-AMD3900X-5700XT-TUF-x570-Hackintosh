# Hackintosh EFI for Ryzen 9 3900X and RX 5700 XT

**English** | [简体中文](README_CN.md)

This is the OpenCore EFI currently running on my Ryzen 9 3900X, RX 5700 XT and
ASUS TUF Gaming X570 desktop. It is intended for the same hardware or systems
with a very similar configuration.

| OpenCore | Tested macOS | SMBIOS |
|---|---|---|
| **1.0.7 RELEASE** | **macOS Sequoia 15.2** | **`MacPro7,1` is required** |

Download the latest usable build from
[Releases](https://github.com/hermanzhaozzzz/My-Opencore-EFI-for-AMD3900X-5700XT-TUF-x570-Hackintosh/releases).

## Before you use it

1. Back up your current bootable EFI.
2. Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate Serial,
   MLB, SystemUUID and ROM values for **`MacPro7,1`**, then replace the example
   values in this repository.
3. Use `config.plist` for normal booting. I recommend
   [OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools) for editing it.
4. The included USB map was made for my motherboard and devices. Check it again
   if your port layout is different.

> [!WARNING]
> Do not reuse the public SMBIOS identity, and do not select `iMac20,2` for this build.

## Why `MacPro7,1` matters

I originally used `iMac20,2`. The system booted, but Bilibili video and screen
sharing stuttered badly. The Ryzen 9 3900X has no integrated GPU. After changing
the SMBIOS to `MacPro7,1`, those workloads were handled correctly by the
RX 5700 XT and the stuttering disappeared.

I then played **eight 4K videos simultaneously** without visible stuttering and
ran a sustained PyTorch MPS stress test on the RX 5700 XT without issues. The
test code and results are available in the
[PyTorch MPS tutorial](tutorial_pytorch-via-this_AMD5700xtGPU/README.md).

![SMBIOS information](pictures/SMBIOSinfo.jpg)

## Hardware

| Component | Model |
|---|---|
| CPU | AMD Ryzen 9 3900X 3.8 GHz |
| GPU | Sapphire Radeon RX 5700 XT 8 GB NITRO+ Special Edition |
| Motherboard | ASUS TUF Gaming X570, non-Wi-Fi edition |
| Memory | Kingston DDR4, 16 GB × 4, 64 GB total, 2666 MHz |
| macOS SSD | Samsung 970 EVO Plus |
| Windows SSD | Western Digital SN550 500 GB NVMe |
| Wi-Fi / Bluetooth | Fenvi FV-T919 |
| Audio | Monitor audio over HDMI/DisplayPort; motherboard audio jacks also tested working |
| Case | NZXT H710i, black/red |
| CPU cooler | NZXT Kraken X73 360 mm AIO |
| Power supply | Seasonic GX750 750 W, 80 Plus Gold, fully modular |

## Tested features

- macOS and Windows dual boot
- RX 5700 XT graphics acceleration
- Bilibili playback, eight simultaneous 4K videos and screen sharing
- PyTorch on the RX 5700 XT through MPS/Metal
- Wi-Fi, Bluetooth and AirDrop
- USB 2.0, USB 3.0, sleep and wake
- HDMI/DisplayPort audio and motherboard audio jacks

I used Wi-Fi during this round of testing and did not retest the Realtek wired
network interface.

### Known limitations

- Sidecar is unavailable.
- iPhone Mirroring is unavailable.

## Wi-Fi and Bluetooth

If the Fenvi FV-T919 does not work after the first macOS login, install
[OpenCore Legacy Patcher](https://dortania.github.io/OpenCore-Legacy-Patcher/),
run **Post-Install Root Patch**, and reboot.

A system update may remove the root patches. If Wi-Fi or Bluetooth disappears,
apply them again.

## macOS updates

This EFI theoretically covers macOS 10.13 High Sierra through macOS 26 Tahoe,
but the version I have fully tested is **macOS Sequoia 15.2**. For daily use, I
recommend staying with Sonoma or Sequoia.

- Minor updates within the same macOS release are reasonable to try after
  backing up the EFI.
- A direct major-version upgrade is not recommended; OpenCore, Kexts and OCLP
  may all need to be updated together.
- I recommend [`macupdatectl`](https://github.com/hermanzhaozzzz/.my_shell_envs/blob/main/bin/macupdatectl)
  to block major upgrades while keeping security updates enabled.

## Extra tutorials and tools

- [LiquidBar](https://github.com/hermanzhaozzzz/LiquidBar): my utility for
  controlling NZXT case fans and liquid-cooling pump power while monitoring
  temperatures. I strongly recommend it for the same case and cooler.
- [Use the RX 5700 XT from PyTorch through MPS/Metal](tutorial_pytorch-via-this_AMD5700xtGPU/README.md):
  `uv` and Conda setup, minimal verification code, a stress test and measured
  results from this machine.

## Contact and support

- Maintainer: Herman ZHAO
- Email: hermanzhaozzzz@gmail.com
- Last updated: August 12, 2026

Maintaining the EFI, testing it through repeated reboots and writing the related
tutorials all take time. If this project saved you some trouble, you are welcome
to buy me a coffee. Support is entirely optional, and feedback is always welcome.

| Alipay | WeChat Pay |
|:---:|:---:|
| <img src="pictures/sponsor-alipay.jpg" alt="Alipay support QR code" width="280"> | <img src="pictures/sponsor-wechat-pay.jpg" alt="WeChat Pay support QR code" width="280"> |
