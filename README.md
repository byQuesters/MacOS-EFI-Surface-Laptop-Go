# macOS Sequoia on Microsoft Surface Laptop Go (M1943)

This repository contains the OpenCore configuration required to run macOS Sequoia on the Microsoft Surface Laptop Go (Model 1943). This EFI is optimized to deliver a near-MacBook-like experience, with a focus on the stability of Continuity and Widgets services.

---

## 💻 Hardware Specifications
| Componente | Detalle |
| :--- | :--- |
| **CPU** | Intel Core i5-1035G1 (Ice Lake) |
| **GPU** | Intel UHD Graphics |
| **RAM** | 4GB / 8GB LPDDR4x |
| **Almacenamiento** | SSD NVMe / eMMC |
| **Pantalla** | 12.4" PixelSense (1536 x 1024) |
| **Bootloader** | OpenCore 

---

## ✅ What Works?

* **Apple Services:** iPhone widgets (via itlwm + HeliPort), iCloud, iMessage, and App Store.
* **Network:** Wi-Fi (via itlwm + HeliPort) and native Bluetooth with Sequoia patches.
* **Peripherals:** Keyboard, Trackpad (multi-touch gestures), and TouchScreen (10-point).
* **Multimedia:** Audio (Layout 35), Native Brightness, and Webcam.
* **Power:** Advanced power management, Battery, Fan, and Sleep/Wake.
* **Ports:** USB-A, USB-C (Data/Charging), Surface Connect, and 3.5mm headphone jack.
* **System:** Recovery, Physical Buttons Volume and power buttons.

* **Hibernation:** Deep Sleep (macOS Hibernation `Hibernatemode=25`).

---

## ⚠️ Special Requirements

### 📶 iPhone WiFi & Widgets
Due to Sequoia's restrictions with the AWDL protocol on Intel chips, to recover the **iPhone Widgets** and maintain a stable connection:
1. This EFI uses **itlwm.kext** instead of AirportItlwm.

2. It is mandatory to use the **HeliPort** app to manage WiFi networks.

3. This method prevents Bluetooth from conflicting with WiFi, enabling the iPhone to be visible in the Notification Center.

👉 **[Download HeliPort.app](https://github.com/OpenIntelWireless/HeliPort/releases)**

### 🔑 Identity (SMBIOS)
For the services For Apple devices to work, you must generate your own serial numbers:
1. Open the `config.plist` file with **OCAuxiliaryTools**.

2. Go to **PlatformInfo > Generic** and generate data for `MacBookAir9,1`.

3. Save and perform a **NVRAM Reset** upon restarting.

### 🌙 Deep Sleep (Hibernation)
To prevent battery drain when closing the lid, it is recommended to enable true hibernation by running the following command in the terminal:
```bash
`sudo pmset -a hibernatemode 25
```

## 📄 Credits
* [Acidanthera](https://github.com/acidanthera) for OpenCore and base Kexts.

* [BigSurface](https://github.com/Xiashangning/BigSurface) for the specific support for Microsoft Surface devices.

* [OpenIntelWireless](https://github.com/OpenIntelWireless) for the itlwm and Bluetooth drivers.

* [EliteMacx86](https://www.youtube.com/watch?v=kNXrugg25u0) for the WiFi and Bluetooth tutorial on macOS Sequoia.

* [Dortania](https://dortania.github.io/OpenCore-Install-Guide/) for the main OpenCore guide.
