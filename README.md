Manifest to build TWRP for [Raspberry Pi 4](http://konstakang.com/devices/rpi4/TWRP).

How to build:
-------------

1. Set up [Android build environment](https://source.android.com/setup/initializing).

2. Initialize repo:

```
repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-11 --depth=1
curl --create-dirs -L -o .repo/local_manifests/manifest_brcm_rpi4.xml -O -L https://raw.githubusercontent.com/lineage-rpi/android_local_manifest/twrp-11/manifest_brcm_rpi4.xml
repo sync
```

3. Apply [patches](https://github.com/lineage-rpi/android_local_manifest/tree/twrp-11/patches):

```
cd path/to/project
git am patchname.patch
```

4. Compile:

```
. build/envsetup.sh
lunch twrp_rpi4-eng
make ramdisk-recovery -jX
```

5. Copy ramdisk-recovery.img to [LineageOS 19](http://konstakang.com/devices/rpi4/LineageOS19) boot partition (/dev/block/mmcblk0p1).
