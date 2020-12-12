Device configuration for Sony Xperia XZ Premium (maple)
========================================================

Description
-----------

This repository is for ArrowOS 11 on Sony Xperia XZ Premium (maple).

How to build ArrowOS
----------------------

* Make a workspace:

        mkdir -p ~/arrowos
        cd ~/arrowos

* Initialize the repo:

        repo init -u git://github.com/ArrowOS/android_manifest.git -b arrow-11.0

* Create a local manifest:

        vim .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <!-- SONY -->
            <project name="whatawurst/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="lineage-18.1" />
            <project name="kgvarunkanth/android_device_sony_yoshino-common1" path="device/sony/yoshino-common" remote="github" revision="arrow-11.0" />
            <project name="kgvarunkanth/android_device_sony_maple1" path="device/sony/maple" remote="github" revision="arrow-11.0" />

            <!-- Pinned blobs for maple -->
            <project name="kgvarunkanth/proprietary_vendor_sony_maple" path="vendor/sony/maple" remote="github" revision="ten" />
        </manifest>

* Sync the repo:

        repo sync

* Extract vendor blobs

        cd device/sony/maple
        ./extract-files.sh

* Setup the environment

        source build/envsetup.sh
        lunch arrow_maple-userdebug

* Build arrowOS

        make -j8 bacon
