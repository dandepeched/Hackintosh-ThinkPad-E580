# Hackintosh configuration for Lenovo ThinkPad E580

Tested on 20KS003AXS model with macOS Mojave (10.14)

**Not Supported Hardware**
* Native Wi-Fi (Intel AC 3165)
* Discrete graphics card (ATI Radeon RX 550)
* Card reader
* Fingerprint sensor

**Wi-Fi Fix**
Native Wi-Fi adapter (Intel AC 3165) was replaced with Broadcom BCM94352Z

**Disable Hibernation**
Run following commands:
```
sudo pmset -a hibernatemode 0
sudo rm /var/vm/sleepimage
sudo mkdir /var/vm/sleepimage
sudo pmset -a standby 0
sudo pmset -a autopoweroff 0
```

**Power Management**
Proper FrequencyVectors was added to IOPlatformPluginFamily.kext

**Known Issues**
* Lid close and FN keys stop working after sleep (fixed after reboot)
* Minor glitches for battery status is observed from time to time (empty or red battery icon while 100% charge)
