# Hackintosh configuration for Lenovo ThinkPad E580

Tested on 20KS003AXS model with macOS Big Sur (11.1)

**IMPORTANT**

This repo migrated to OpenCore bootloader. You still can find the last Clover files in 'EFI-Clover' folder.
Be aware that Big Sur+OpenCore combination may require some/significant time for initial setup. I experienced number of annoying issues that lead to few re-installs and admin permissions recovery.
Also make sure to replace PlatformInfo parameters with your own unique values:
```
Generic -> MLB
Generic -> ROM
Generic -> SystemSerialNumber
Generic -> SystemUUID
```

**BIOS Settings**
* BIOS version 1.34
* Controller should be set to AHCI
* Disabled options: Secure Boot; CSM Support; Internal Storage Tamper Detection
* To prevent instant wake also disable: Wake On Lan; Network Stack; Always On USB

**Not Supported Hardware**
* Following stock NVMe SSDs reported as not supported: Samsung PM981
* Discrete graphics card (ATI Radeon RX 550)
* Line/Mic Input (3,5")
* Card reader
* Fingerprint sensor
* Trackpad supports up to 3-finger gestures. Cannot rotate, pinch, etc

**Wi-Fi Adapter**

While it is possible to make the stock Wi-Fi card (Intel AC3165) work now, it is still adviced to replace it with a better card that is supported.
I've replaced mine with Broadcom BCM94352Z, so this repo contains kexts for it.

**Known Issues**
* Lid close and FN keys stop working after sleep (fixed after reboot)
* External monitor connected to HDMI need to be re-plugged after sleep

## Optional configuration
**Possible fixes**
* Some users reported that they failed to boot. That can possibly be fixed by adding **npci=0x3000** to bootflags.
* If you want to try make Intel AC3165 WiFi work, check following repos: https://github.com/OpenIntelWireless/itlwm, https://github.com/AppleIntelWifi/adapter
* Working SSDs: Toshiba XG5 (stock), ADATA SX8200

**Disable Hibernation**

Run following commands:
```
sudo pmset -a hibernatemode 0
sudo rm /var/vm/sleepimage
sudo mkdir /var/vm/sleepimage
sudo pmset -a standby 0
sudo pmset -a autopoweroff 0
```