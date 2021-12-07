# Build SHRP

SHRP is now available for a11 native devices (Beta)

**Available Branches**

| android versions | branch  |
| :--------------: | :-----: |
|        9         | v3_9.0  |
|        10        | v3_10.0 |
|        11        | v3_11.0 |

<br />

# Android 9

- To initialize your local repository using the OMNIROM trees to build SHRP, use a command like this:

```bash
repo init -u git://github.com/SHRP/manifest.git -b v3_9.0
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
repo init -u git://github.com/SHRP/manifest.git -b v3_10.0
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

- To initialize your local repository using the OMNIROM trees to build SHRP, use a command like this:

```bash
repo init -u git://github.com/SHRP/manifest.git -b v3_11.0
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
source build/envsetup.sh; lunch omni_<device>-eng; mka recoveryimage
```
