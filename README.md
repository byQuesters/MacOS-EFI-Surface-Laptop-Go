# macOS Sequoia on Microsoft Surface Laptop Go (M1943)

Este repositorio contiene la configuración de **OpenCore** necesaria para ejecutar macOS Sequoia en la Microsoft Surface Laptop Go (Modelo 1943). Esta EFI está optimizada para ofrecer una experiencia cercana a una MacBook real.

---

## 💻 Especificaciones de Hardware
| Componente | Detalle |
| :--- | :--- |
| **CPU** | Intel Core i5-1035G1 (Ice Lake) |
| **GPU** | Intel UHD Graphics |
| **RAM** | 4GB / 8GB LPDDR4x |
| **Almacenamiento** | SSD NVMe / eMMC |
| **Pantalla** | 12.4" PixelSense (1536 x 1024) |
| **Bootloader** | OpenCore |

---

## ✅ ¿Qué funciona?

* **Red:** WiFi nativo (vía AirportItlwm + OCLP) y Bluetooth nativo.
* **Periféricos:** Teclado (con Hot Plug), Trackpad y TouchScreen.
* **Multimedia:** Audio, Brillo (teclas de función) y Cámara.
* **Energía:** Gestión de energía, Batería, Ventilador (Fan) y Reposo (Sleep/Wake).
* **Puertos:** USB, Surface Dock, SD Card y salida mDP.
* **Seguridad:** UEFI Secure Boot **ON** y FileVault.
* **Sistema:** Recovery, Botones de volumen y encendido.
* **Hibernación:** Deep Sleep (macOS Hibernation `Hibernatemode=25`).
* **Multi-Boot:** Windows, Linux y chromeOS.

---

## ⚠️ Requisitos Especiales

### 📶 WiFi & OCLP
Debido a que macOS Sequoia eliminó ciertos drivers de red, para obtener WiFi nativo con **AirportItlwm**:
1. Instalar la kext correspondiente.
3. Usar **OpenCore Legacy Patcher (OCLP)** para aplicar los "Root Patches" de red una vez instalado el sistema.
Para que el WiFi y Bluetooth funcionen correctamente en macOS Sequoia utilizando el método de **AirportItlwm + OCLP**, sigue este tutorial detallado:
👉 **[Guía Paso a Paso: Intel WiFi & BT en Sequoia](https://www.youtube.com/watch?v=kNXrugg25u0)**

*Nota: Es necesario aplicar los "Root Patches" desde OpenCore Legacy Patcher después de cada actualización de macOS para mantener el soporte de red.*

### 🌙 Deep Sleep
Para una gestión óptima de la batería al cerrar la tapa, se recomienda activar la hibernación real ejecutando:
```bash
sudo pmset -a hibernatemode 25
```


## 📄 Créditos
* [Acidanthera](https://github.com/acidanthera) por OpenCore y Kexts base.
* [BigSurface](https://github.com/Xiashangning/BigSurface) por el soporte específico para dispositivos Microsoft Surface.
* [OpenIntelWireless](https://github.com/OpenIntelWireless) por los drivers itlwm y Bluetooth.
* [EliteMacx86](https://www.youtube.com/watch?v=kNXrugg25u0) por el tutorial de WiFi y Bluetooth en macOS Sequoia.
* [Dortania](https://dortania.github.io/OpenCore-Install-Guide/) por la guía principal de OpenCore.
