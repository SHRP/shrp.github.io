# Build SHRP

**Available Branches**

| android versions | branch  |
| :--------------: | :-----: |
|        9         | v3_9.0  |
|        10        | v3_10.0 |
|        11        | v3_11.0 |
|        12        | shrp-12.1|

<br />

# Android 9

- To initialize your local repository using the OMNIROM trees to build SHRP, use a command like this:

```bash
repo init -u https://github.com/SHRP/manifest.git -b v3_9.0
```

- Then to sync up:

```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

- Then to build for a device with recovery partition:

```bash
cd <source-dir>
. build/envsetup.sh
lunch omni_<device>-eng
mka recoveryimage
```

- or in one line

```
source build/envsetup.sh; lunch omni_<device>-eng; mka recoveryimage
```

<br /><br />

# Android 10

- To initialize your local repository using the OMNIROM trees to build SHRP, use a command like this:

```bash
repo init -u https://github.com/SHRP/manifest.git -b v3_10.0
```

- Then to sync up:

```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

- Then to build for a device with recovery partition:

```bash
cd <source-dir>
. build/envsetup.sh
lunch omni_<device>-eng
mka recoveryimage
```

- or in one line

```
source build/envsetup.sh; lunch omni_<device>-eng; mka recoveryimage
```

<br /><br />

# Android 11

- To initialize your local repository using the TWRP trees to build SHRP, use a command like this:

```bash
repo init -u https://github.com/SHRP/manifest.git -b v3_11.0
```

- Then to sync up:

```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

- Then to build for a device with recovery partition:

```bash
cd <source-dir>
. build/envsetup.sh
lunch twrp_<device>-eng
mka recoveryimage
```

- or in one line

```
source build/envsetup.sh; lunch twrp_<device>-eng; mka recoveryimage
```

- Otherwise to build for a device without a recovery partition use:

```
mka bootimage
```

<br /><br />

# Android 12.1

- To initialize your local repository using the TWRP trees to build SHRP, use a command like this:

```bash
repo init -u https://github.com/SHRP/manifest.git -b shrp-12.1
```

- Then to sync up:

```bash
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```
- Then to setup the build:
```bash
cd <source-dir>; export ALLOW_MISSING_DEPENDENCIES=true; . build/envsetup.sh; lunch twrp_<device>-eng
```

- The build target is dependent on the device, and should reflect the location of stock recovery on the device. Issue the build command that applies to your device:
- Recovery partition: ```bash mka recoveryimage``` or ```bash source build/envsetup.sh; lunch twrp_<device>-eng; mka recoveryimage```
- Boot image: ```bash mka bootimage``` or ```bash source build/envsetup.sh; lunch twrp_<device>-eng; mka bootimage```
- Vendor_boot image: ```bash mka vendorbootimage``` or ```bash source build/envsetup.sh; lunch twrp_<device>-eng; mka vendorbootimage```
