# TWRP device tree for Lenovo Smart Tab M10 FHD Plus (TB-X606F)

## Release info
This is an unofficial build.  Install at your own risk.

Build with [minimal AOSP TWRP for Android 12.1](https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp/tree/twrp-12.1).

This branch was created when Android 13 removed support for FDE (full disk encryption).  It will work with any ROMs/GSIs that use FBE (file-based encryption) with aes-256-xts:aes-256-cts.

Stock ROMs use FDE, so this branch will **not** work with stock ROMs.  For stock ROM support, use branch [android-11.0](https://github.com/Yahoo-Mike/recovery_device_lenovo_X606FA/tree/android-11.0).

Support Thread on [XDA](https://forum.xda-developers.com/t/4222887/).

### About Device

![Lenovo Smart Tab M10 HD](https://download.lenovo.com/images/ProdImageSmart/amazon_alexa.jpg "Lenovo Smart Tab M10 FHD Plus (TB-X606F)")

Recovery Device Tree for Lenovo Smart Tab M10 FHD Plus wifi (TB-X606F)
=======================================================================
Component   | Specs
-------:|:-------------------------
Chipset| MediaTek Helio P22T
CPU | ARM Cortex-A53, Octo-Core, 2.3 GHz
GPU     | IMG PowerVR GE8320, 650 MHz
Memory  | 2GB or 4GB (soldered)
Shipped Android Version | 9.0 (Pie), upgrade to 10.0
Storage | 32GB or 64GB eMMC
MicroSD | Up to 256 GB
Battery | 5000 mAh, Li-Po (non-removable)
Display | 1920x1200 pixels, 10.3"
Front Camera | 5.0 MP
Rear Camera  | 8.0 MP
Wifi | dual band, 802.11a/b/g/n/ac
WLAN | 4G LTE   (TB-X606X only)
Bluetooth | v5
USB | USB-C (micro USB)
Release Date | August 2020


## To build
```
. build/envsetup.sh
lunch twrp_X606FA-eng
mka recoveryimage
```

## Android 12: patch for FBE decryption
There was a change in the data structure for Keymaster in Android 12.  It is incompatible with vendor blobs prior to A12 (like this device).

To make FBE decryption work, you will need to apply [this patch](https://github.com/Yahoo-Mike/recovery_device_lenovo_X606FA/tree/android-12.1-fbe/patch/system/vold) to TWRP before compiling.
