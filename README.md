# My-Opencore-EFI-for-AMD3900X-5700XT-TUF-x570-Hackintosh
> This EFI is created by Herman ZHAO
>
> E-mail: hermanzhaozzzz@gmail.com
>

---

Opencore version: 0.5.9

---

When you use the same computer parts as me, you can gain a perfect AMD Mac OS machine by using my EFI.

---

CPU: AMD Ryzen-9 3900X 3.8GHz

GPU: 蓝宝石5700XT 8G 超白金极光特别版

Motherboard/主板: ASUS TUF Gaming X570 (without WIFI edition, there is no need to buy the WIFI edition if you want to hack into sh! We need another driver free net card)

Power: 海韵/SEASONIC GX750 750W 金牌全模

机箱: 恩杰NZXT H710i 黑红

CPU一体式水冷: 恩杰NZXT Kraken 海妖X73 360mm

内存: 芝奇G. SKILL 焰光戟 8G*2 F4-3600C16D-16GTZNC （预算有限，后面会升级64G）

SSD/固态硬盘: 

- Windows10-西部数据 SN550 500G NVMe协议

- Mac OS(Catalina10.15.5)-海康威视E2000L NVMe协议

Wireless card/无线网卡+Bluetooth/蓝牙: 奋威 FV-T919 - 1750M 



For debug, please use the **config-debug-model.plist** to see the boot log

For normal work, please use the **config.plist**

DO NOT edit the plist file **without** using Xcode or propertree!

REMEMBER to update your SMBIOS info.

![](pictures/SMBIOSinfo.jpg)

Works fine:

- AMD CPU
- 5700XT GPU
- Wireless network card
- Bluetooth
- Sleep wake

Not work:

- Sidecar(Because this CPU do not have Core graphics)

