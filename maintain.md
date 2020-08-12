# About

You want to become an **official maintainer** of a device? Good! Then this guide is for you!

Before starting you should have read the [Build Guide][build] and so having a working port for the device you want to maintain.

Another hard requirement is the use of [Telegram][tg]: it's free, available on all platforms and nice so have that installed before doing anything else.

# Steps

## Join the main SHRP Telegram groups
1. [SHRP community][community]
1. [SHRP releases][releases]

## Build
- Read and *follow* the [Build Guide][build]
- Build locally on your pc and test with at least 1 or 2 other users (the more the better of course). 
- Do not proceed until you have a **fully working build** (see next topic) - if needed ask for help in [SHRP community][community]

## Requirements
### Mandatory
The following are hard requirements in order to make you a maintainer of a device and adding your device to official builds:

1. You must own the device. **We don't accept blind builds!**
1. Test *normal* operations - at least these:
   - full **backup** of all partitions
   - full **restore** of all partitions
   - execute a **factory reset**
   - **mount/unmount** partitions manually
   - **flash** a ROM
   - Test the **file manager**
   - Test the **terminal** app
1. Theme - at least these:
   - Change **theme color**
   - Change **dashboard icons** 
1. Change SHRP to another **language**
1. ADB **sideload** must work
1. Security:
   - set **pattern** lock, reboot, test if **ADB + MTP is NOT accessible**, unlock, test if ADB + MTP **is accessible now**
   - set **password** lock, reboot, test if **ADB + MTP is NOT accessible**, unlock, test if ADB + MTP **is accessible now**
1. **Magisk:**
   - install by the SHRP menu
   - boot to Android twice (if magisk manager do not show up on the first boot)
   - check magisk manager - was rooting succesful?
   - UnRoot in SHRP
   - boot to Android - Magisk / root really gone?
1. **Decrypting*** (custom ROMs like LOS etc)
1. Test an **external sdcard** (obviously for devices with an external sdcard slot only)
   - must have: **vFAT** and/or **exFAT** support ([tech details][fatwp])
   - nice to have: ntfs, ext2/3/4, f2fs support


' * as long as your STOCK ROM generally supports encryption. Decryption support is focused on custom ROMs only while having it working for STOCK gives you a bonus ;)

### Optional

1. Flashlight
1. Decrypting* (STOCK)
1. OTG support
1. SHRP_EXPRESS

' * as long as your STOCK ROM generally supports encryption. If not you can skip that step but let us know about it.


## Formals
If you walked through all the above CONGRATS!! Great job :) Now let's go on with making it real!

Fill out this little [request form][form] to request becoming a maintainer.

## Request access (TG group)
1. In [SHRP community][community] let the [SHRP team][team] know that you filled out the form (use the `@` before the nickname to notify)
1. In [SHRP community][community] request access to become a member of the **maintainers Telegram group** (you will be invited then).

## Request access (github) 
In the **maintainers TG group** request access to the [device-tree repo][dt] if not given already.

## Upload your tree(s)
Import your device tree to the [device-tree repo][dt]

## CI automation scripts
Add a new *CI script* for your device by 
- *forking* this [CI repo][ci-repo]
- adding your *own* script: filename = device *codename*
- and finally create a *pull request* for that change

## Post your build
- In the **maintainers TG group** write `/get post` to get the TG post template.
- Fill out that template and post it back in the TG group



[team]: https://skyhawk-recovery-project.github.io/#/contact?id=team
[dt]: https://github.com/SHRP-Devices
[build]: guide.md
[community]: https://t.me/sky_hawk
[releases]: https://t.me/shrp_official
[form]: https://forms.gle/ifsMN2hCV3Z5wPFDA
[ci-repo]: https://github.com/SHRP-Devices/ci_scripts
[tg]: https://telegram.org/
[fatwp]: https://en.wikipedia.org/wiki/File_Allocation_Table#Types
