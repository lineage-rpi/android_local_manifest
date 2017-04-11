Local manifests to build LineageOS 14.1 for [Raspberry Pi 3](http://konstakang.com/devices/rpi3/CM14.1).

How to build:
-------------

Initialize repo:

    repo init -u git://github.com/LineageOS/android.git -b cm-14.1
    curl --create-dirs -L -o .repo/local_manifests/manifest_brcm_rpi3.xml -O -L https://raw.githubusercontent.com/lineage-rpi/android_local_manifest/cm-14.1/manifest_brcm_rpi3.xml
    repo sync

Compile:

    . build/envsetup.sh
    lunch lineage_rpi3-userdebug
    mka ramdisk systemimage
