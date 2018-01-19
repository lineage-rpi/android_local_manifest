Local manifests to build LineageOS 14.1 for [Raspberry Pi 3](http://konstakang.com/devices/rpi3/CM14.1).

How to build:
-------------

1. Set up [Android build environment](https://source.android.com/setup/initializing).

2. Install additional packages:

```
sudo apt-get install kpartx python-mako
```

3. Initialize repo:

```
repo init -u git://github.com/LineageOS/android.git -b cm-14.1
curl --create-dirs -L -o .repo/local_manifests/manifest_brcm_rpi3.xml -O -L https://raw.githubusercontent.com/lineage-rpi/android_local_manifest/cm-14.1/manifest_brcm_rpi3.xml
repo sync
```

4. Apply [patches](https://github.com/lineage-rpi/android_local_manifest/tree/cm-14.1/patches):

```
cd path/to/project
git am patchname.patch
```

5. Compile:

```
. build/envsetup.sh
lunch lineage_rpi3-userdebug
mka kernel ramdisk systemimage
```

6. Create writable image:

```
cd device/brcm/rpi3
sudo ./mkimg.sh
```
