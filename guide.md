# Bring Up SHRP

1. Add device specific properties. `BoardConfig.mk`
```bash
SHRP_PATH := device/brand/codename
# Maintainer name
SHRP_MAINTAINER := epicX
# Device codename
SHRP_DEVICE_CODE := c103
# put this 0 if device has no EDL mode
SHRP_EDL_MODE := 1
SHRP_EXTERNAL := /external_sd
SHRP_INTERNAL := /sdcard
SHRP_OTG := /usb_otg
# Put 0 to disable flashlight
SHRP_FLASH := 1
# These are led paths, find yours then put here
SHRP_FONP_1 := /sys/class/leds/led:torch_0/brightness
SHRP_FONP_2 := /sys/class/leds/led:torch_1/brightness
SHRP_FONP_3 := /sys/class/leds/led:switch/brightness
# Max Brightness of LED
SHRP_FLASH_MAX_BRIGHTNESS := 200
# Check your device's recovery path, dont use blindly
SHRP_REC := /dev/block/bootdevice/by-name/recovery
# Use this flag only if your device is A/B
SHRP_AB := true
```

 *** Don't remove any line , just leave it blank ! ***

# Build SHRP


* To initialize your local repository using the OMNIROM trees to build SHRP, use a command like this:

```bash
repo init -u git://github.com/SKYHAWK-Recovery-Project/platform_manifest_twrp_omni.git -b 9.0
```
* Then to sync up:

```bash
repo sync
```

* Then to build for a device with recovery partition:

```bash
cd <source-dir>

export ALLOW_MISSING_DEPENDENCIES=true

 . build/envsetup.sh

 lunch omni_<device>-eng

 mka recoveryimage
```

* or in one line
```
export ALLOW_MISSING_DEPENDENCIES=true; source build/envsetup.sh; lunch omni_<device>-eng; mka recoveryimage
```
