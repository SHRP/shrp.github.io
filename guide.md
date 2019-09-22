# Bring Up SHRP

1. First create a file in root of your device tree `shrp_env.sh` and add device specific properties.

```bash
# !/bin/bash
export SHRP_MAINTAINER="epicX"  # Maintainer name
export SHRP_DEVICE_CODE="c103"  # Device codename
export SHRP_EDL_MODE="1"  # put this 0 if device has no EDL mode
export SHRP_EXTERNAL="/external_sd"
export SHRP_INTERNAL="/sdcard"
export SHRP_OTG="/usb-otg"
export SHRP_FLASH="1"  # Put 0 to disable flashlight
export SHRP_FLASH_MAX_BRIGHTNESS="200"

# These are led paths, find yours then put here
export SHRP_FONP_1="/sys/class/leds/led:torch_0/brightness"
export SHRP_FONP_2="/sys/class/leds/led:torch_1/brightness"
export SHRP_FONP_3="/sys/class/leds/led:switch/brightness"
export SHRP_REC="/dev/block/bootdevice/by-name/recovery"  # Check your device's recovery path, dont use blindly
```
 *** Don't remove any line , just leave it blank ! ***

2. Add this to `BoardConfig.mk`
```bash
SHRP_PATH := device/brand/codename
```

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
