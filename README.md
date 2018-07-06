Manifests to build TWRP for [Raspberry Pi 3](http://konstakang.com/devices/rpi3/TWRP).

How to build:
-------------

1. Set up [Android build environment](https://source.android.com/setup/initializing).

2. Initialize repo:

```
repo init -u git://github.com/lineage-rpi/android_local_manifest.git -b twrp-8.1
curl --create-dirs -L -o .repo/local_manifests/manifest_brcm_rpi3.xml -O -L https://raw.githubusercontent.com/lineage-rpi/android_local_manifest/twrp-8.1/manifest_brcm_rpi3.xml
repo sync
```

3. Apply [patches](https://github.com/lineage-rpi/android_local_manifest/tree/twrp-8.1/patches):

```
cd path/to/project
git am patchname.patch
```

4. Compile:

```
export ALLOW_MISSING_DEPENDENCIES=true
. build/envsetup.sh
lunch omni_rpi3-userdebug
mka ramdisk-recovery
```

5. Copy ramdisk-recovery.img as ramdisk.img in [LineageOS 15.1](http://konstakang.com/devices/rpi3/LineageOS15.1) boot partition (/dev/block/mmcblk0p1).
