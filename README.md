# Hackintosh configuration for Lenovo ThinkPad E580

Tested on 20KS003AXS model with macOS Big Sur (11.1)

**NOTICE**
Clover version of Big Sur is not stable, so I cannot recommend this update.
I have a plan to migrate to OpenCore bootloader, so this commit is the last one for Clover.
Be aware that Big Sur installation can only be boot from **Preboot** partition.


**BIOS Settings**
* BIOS version 1.34
* Disable Secure Boot option

**Not Supported Hardware**
* Following stock NVMe SSDs reported as not supported: Samsung PM981
* Discrete graphics card (ATI Radeon RX 550)
* Line/Mic Input (3,5")
* Card reader
* Fingerprint sensor
* Trackpad supports up to 3-finger gestures. Cannot rotate, pinch, etc

**Wi-Fi Adapter**

While it is possible to make the stock Wi-Fi card (Intel AC3165) work now, it is still adviced to replace it with a better card that is supported.
I've replaced mine with Broadcom BCM94352Z.

**Known Issues**
* Lid close and FN keys stop working after sleep (fixed after reboot)
* External monitor need to be re-plugged after sleep
* Minor glitches for battery status is observed from time to time (empty or red battery icon, etc)

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

**Kexts Location**

If you prefer to keep all kexts in */Library/Extensions* directory, you can use those from *Non-EFI Files* folder
