Local manifests to build TWRP for [Raspberry Pi 3](http://konstakang.com/devices/rpi3/TWRP) and [Raspberry Pi 4](http://konstakang.com/devices/rpi4/TWRP).

How to build:
-------------

1. Set up [Android build environment](https://source.android.com/setup/initializing).

2. Initialize repo:

```
repo init -u git://github.com/LineageOS/android.git -b lineage-16.0
curl --create-dirs -L -o .repo/local_manifests/manifest_brcm_rpi.xml -O -L https://raw.githubusercontent.com/lineage-rpi/android_local_manifest/lineage-16.0-twrp/manifest_brcm_rpi.xml
repo sync
```

3. Apply [patches](https://github.com/lineage-rpi/android_local_manifest/tree/lineage-16.0-twrp/patches):

```
cd path/to/project
git am patchname.patch
```

4. Compile:

```
. build/envsetup.sh
lunch lineage_rpi3-userdebug
mka ramdisk-recovery
```

5. Copy ramdisk-recovery.img to LineageOS 16.0 boot partition (/dev/block/mmcblk0p1).
