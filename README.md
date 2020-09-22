# Hackintosh configuration for Lenovo ThinkPad E580

Tested on 20KS003AXS model with macOS Catalina (10.15.6)

**BIOS Settings**
* BIOS version 1.34
* Disable Secure Boot option

**Not Supported Hardware**
* Stock NVMe SSD (Samsung PM981)
* Discrete graphics card (ATI Radeon RX 550)
* Line/Mic Input (3,5")
* Card reader
* Fingerprint sensor
* Trackpad supports up to 3-finger gestures. Cannot rotate, pinch, etc

**Wi-Fi Fix**

Native Wi-Fi adapter was replaced with Broadcom BCM94352Z

While it is possible to make the AC3165 card work now, it is adviced to replace it with a better card that is supported.

**Known Issues**
* Lid close and FN keys stop working after sleep (fixed after reboot)
* External monitor need to be re-plugged after sleep
* Minor glitches for battery status is observed from time to time (empty or red battery icon, etc)

## Optional configuration

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
