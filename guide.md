# Build SHRP

*To get started with OMNI sources to build TWRP, you'll need to get familiar with [Git & Repo](https://source.android.com/source/using-repo.html)*

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
cd <source-dir>;

export ALLOW_MISSING_DEPENDENCIES=true;

 . build/envsetup.sh;

 lunch omni_<device>-eng;

 . <shrp_device_tree_path>/shrp_env.sh;

 mka recoveryimage
```
