# Bring Up SHRP

Configure SHRP in `BoardConfig.mk`

```bash
# NOTE:
# Don't use '-' or blank spaces in flag values!
# These will create build errors or other bugs in recovery (Excluding SHRP_PATH,SHRP_REC).
#
# NOTE-2:
# all values within these brackets: "<" ">" showing choice values and need to be
# replaced by you with the correct values!
# Example: if the codename of your device is "gtexslte" <device-codename> becomes:
# SHRP_DEVICE_CODE := gtexslte
# (so without any brackets ofc!)

################### ############################################
# MANDATORY FLAGS # These flags HAVE TO be set/changed by you! #
################### ############################################

# Device codename
# Default (if not set): N/A
SHRP_DEVICE_CODE := <device-codename>

# Path of your SHRP device tree
# Replace <device-brand> with the device brand name
# (SHRP_DEVICE_CODE will expand to the above variable so check if that is correct)
SHRP_PATH := device/<device-brand>/$(SHRP_DEVICE_CODE)

# Maintainer name
# Default (if not set): N/A
SHRP_MAINTAINER := <your-nick-name-here>

# Recovery Type (for "About" section only)
# Default (if not set): N/A
SHRP_REC_TYPE := <Treble|Normal|SAR>

# Device Type (for "About" section only)
# Default (if not set): N/A
SHRP_DEVICE_TYPE := <A_Only|A/B>

# Your device's recovery path, dont use blindly
# No default
SHRP_REC := </dev/block/bootdevice/by-name/recovery>

################### ################################################################################
# IMPORTANT FLAGS # These are usually good to check - at least if the defaults are what you expect #
################### ################################################################################

# Emergency DownLoad mode (0 = no EDL mode, 1 = EDL mode available)
# Default (if not set): 0
SHRP_EDL_MODE := <0|1>

# internal storage path
# Default (if not set): /sdcard
SHRP_INTERNAL := /sdcard

# If your device has an external sdcard
# Default (if not set): /
SHRP_EXTERNAL := /external_sd

# USB OTG path
# Default (if not set): /
SHRP_OTG := /usb_otg

# Flashlight: (0 = disable, 1 = enable)
# Default (if not set): 0
SHRP_FLASH := <0|1>

################## #########################################################################
# OPTIONAL FLAGS # Stuff which highly depends on your device and / or personal preferences #
################## #########################################################################

# Use this flag only if your device is A/B.
# Default (if not set) is no A/B device
# Set this variable when true ONLY (do not use "false" or similiar)
SHRP_AB := true

# SHRP padding flag (for rounded corner devices only)
# You have to change these values according to your device's roundness.
SHRP_STATUSBAR_RIGHT_PADDING := <1-XXX>
# Default (for LEFT): 20
SHRP_STATUSBAR_LEFT_PADDING := <1-XXX>

# For notch devices
# Default (if not set) is no notch
# Set this variable when true ONLY (do not use "false" or similiar)
SHRP_NOTCH := true

# SHRP Express, enables on-the-fly theme patching (also persistent) + persistent lock
# Default (if not set) is not using Express
# Set this variable when true ONLY (do not use "false" or similiar)
SHRP_EXPRESS := true

# SHRP Express use Data save shrp files inside /data instead of /system
# Note - SHRP_EXPRESS must be true to use this flag otherwise it won't work.
# Default (if not set) will use /system if SHRP_EXPRESS true otherwise will use legacy method of patching
# Set this variable when true ONLY (do not use "false" or similiar)
SHRP_EXPRESS_USE_DATA := true

# SHRP Dark mode, use this flag to have dark theme set by default
# Default (if not set) is not using DARK mode
# Set this variable when true ONLY (do not use "false" or similiar)
SHRP_DARK := true

# custom led paths for flashlight
# find yours then replace the examples here
SHRP_CUSTOM_FLASHLIGHT := true
SHRP_FONP_1 := /sys/class/leds/led:torch_0/brightness
SHRP_FONP_2 := /sys/class/leds/led:torch_1/brightness
SHRP_FONP_3 := /sys/class/leds/led:switch/brightness

# Max brightness of flashlight
# you can also check the above led paths in Android when you turn on flashlight
SHRP_FLASH_MAX_BRIGHTNESS := 200

# Force mount system in /system despite SAR policy
# useful for maintaining backwards compatibility and/or Samsung devices
# Default (if not set) is to follow the SAR policy
# Set this variable when true ONLY (do not use "false" or similiar)
SHRP_NO_SAR_AUTOMOUNT := true

# Do not include the SHRP theming system
# Useful to save space for devices with a smaller recovery partition
# Default (if not set) is full theming support
# Set this variable when true ONLY (do not use "false" or similiar)
SHRP_LITE := true

################################## ##############################################
# SHRP DEFAULT ADDONS - OPTIONAL # Default SHRP addon behavior - fully optional #
################################## ##############################################

# SHRP comes with a set of default addons.
# This section allows to disable some or all of them, e.g. to save a little space
# or when a device does not support / need them.

#####
# DEFAULT behavior if neither
# - SHRP_SKIP_DEFAULT_ADDON_X nor
# - INC_IN_REC_ADDON_X
# are set:
# the addon will be added to the build and saved into the internal storage
# on flashing (i.e: $(SHRP_INTERNAL)/SHRP/addons)
#
# SHRP_SKIP_DEFAULT_ADDON_X := true
# --> will not add this addon
#
# INC_IN_REC_ADDON_X := true
# --> will add this addon & store it within the recovery ramdisk (i.e. NOT in the internal storage!)
#
# If SHRP_SKIP_DEFAULT_ADDON_X is set INC_IN_REC_ADDON_X will be ignored!
#
######

# Addon - Substratum Overlay (OMS -Normal- disabler)
# Default (if not set) is not skipping this addon (i.e. add it)
# Ensure you understood the above note on the default behavior!
SHRP_SKIP_DEFAULT_ADDON_1 := true
# Default (if not set) is NOT adding it to the ramdisk but internal storage.
# To store this addon into the recovery ramdisk instead set to "true" here.
# Ensure you understood the above note on the default behavior!
INC_IN_REC_ADDON_1 := true

# Addon - Substratum Overlay (OMS -legacy- disabler)
# Default (if not set) is not skipping this addon (i.e. add it)
# Ensure you understood the above note on the default behavior!
SHRP_SKIP_DEFAULT_ADDON_2 := true
# Default (if not set) is NOT adding it to the ramdisk but internal storage.
# To store this addon into the recovery ramdisk instead set to "true" here.
# Ensure you understood the above note on the default behavior!
INC_IN_REC_ADDON_2 := true

# Addon - Clear Fingerprint (remove fingerprint lock from system)
# Default (if not set) is not skipping this addon (i.e. add it)
# Ensure you understood the above note on the default behavior!
SHRP_SKIP_DEFAULT_ADDON_3 := true
# Default (if not set) is NOT adding it to the ramdisk but internal storage.
# To store this addon into the recovery ramdisk instead set to "true" here.
# Ensure you understood the above note on the default behavior!
INC_IN_REC_ADDON_3 := true

# Addon - Force Encryption (remove force encryption from your device)
# Default (if not set) is not skipping this addon (i.e. add it)
# Ensure you understood the above note on the default behavior!
SHRP_SKIP_DEFAULT_ADDON_4 := true
# Default (if not set) is NOT adding it to the ramdisk but internal storage.
# To store this addon into the recovery ramdisk instead set to "true" here.
# Ensure you understood the above note on the default behavior!
INC_IN_REC_ADDON_4 := true


# Default (if not set) is NOT adding it to the ramdisk but internal storage.
# To store magisk zip into the recovery ramdisk instead set to "true" here.
# Ensure you understood the above note on the default behavior!
INC_IN_REC_MAGISK := true

# Default (if not set) will show magisk root and unroot option inside the recovery.
# To hide the prebuilt magisk flash option from recovery, set value to "true".
# Ensure you understood the above note on the default behavior!
SHRP_EXCLUDE_MAGISK_FLASH := true

############################ #########################################################
# CUSTOM ADDONS - OPTIONAL # Custom addons! Yea fully optional but.. GREAT STUFF! :) #
############################ #########################################################

# SHRP can be extended as YOU wish! You can add whatever you can think of
# e.g patching a ROM, adding stuff, apps, there is no limit ;)
# Addons will be shown in the "Tweaks" section of SHRP.

# Custom addon folder. Do not forget to put a "/" at the end of the path!
SHRP_EXTERNAL_ADDON_PATH := "device/<device-brand>/$(SHRP_DEVICE_CODE)/<AddonFolderName>/"

# Addon #1 - Name
SHRP_EXTERNAL_ADDON_1_NAME := "LOS Recorder"
# Addon #1 - Description
SHRP_EXTERNAL_ADDON_1_INFO := "A magisk module which add lineageOS recorder into your system"
# Addon #1 - Addon file name as ZIP (zip format is required)
SHRP_EXTERNAL_ADDON_1_FILENAME := "los_recorder.zip"
# Addon #1 - Free defineable button text the user need to press to actually install that addon
# (Examples: Ok, Install, Flask, Enable, Disable, etc)
SHRP_EXTERNAL_ADDON_1_BTN_TEXT := "Install"
# Addon #1 - Text beeing shown when the installation was successful
SHRP_EXTERNAL_ADDON_1_SUCCESSFUL_TEXT := "Installed"
# Addon #1 - Inject the addon into the recovery (if so: be sure that it will fit into the partition)
# Default (if not set) is NOT adding this addon into the recovery ramdisk. That means:
# If you do NOT set this the addon will be saved into the internal storage (i.e: $(SHRP_INTERNAL)/SHRP/addons)
# Set this variable when true ONLY (do not use "false" or similiar)
SHRP_INC_IN_REC_EXTERNAL_ADDON_1 := true

# As you might already guess from the naming scheme:
# You can add multiple custom addons (max amount is 6)!
#
# just add the above flags again and replace:
# SHRP_EXTERNAL_ADDON_1_XXXX
# with
# SHRP_EXTERNAL_ADDON_2_XXXX for the second addon
# and for the third up to the sixth change it accordingly:
# SHRP_EXTERNAL_ADDON_3_XXXX, SHRP_EXTERNAL_ADDON_4_XXXX, SHRP_EXTERNAL_ADDON_5_XXXX, SHRP_EXTERNAL_ADDON_6_XXXX
```

# Reference Configuration

```bash
https://raw.githubusercontent.com/epicX67/twrp_device_coolpad_c103/treble/BoardConfig.mk
```

# Build SHRP

- To initialize your local repository using the OMNIROM trees to build SHRP, use a command like this:

**Available Branches**

| android versions | branch  |
| :--------------: | :-----: |
|        9         | v3_9.0  |
|        10        | v3_10.0 |
|        11        | v3_11.0 |

```bash
repo init -u git://github.com/SHRP/manifest.git -b v3_9.0
```

- Then to sync up:

```bash
repo sync
```

- Then to build for a device with recovery partition:

```bash
cd <source-dir>

export ALLOW_MISSING_DEPENDENCIES=true

 . build/envsetup.sh

 lunch omni_<device>-eng

 mka recoveryimage
```

- or in one line

```
export ALLOW_MISSING_DEPENDENCIES=true; source build/envsetup.sh; lunch omni_<device>-eng; mka recoveryimage
```
