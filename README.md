#DirtyUnicorns tree for Moto G (2015)
* Based off https://github.com/Motorola-CyanogenMod/android_device_motorola_surnia

##Dependencies:
````
sudo apt-get install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop openjdk-6-jdk openjdk-6-jre pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev
sudo apt-get install g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev schedtool libc6-i386 lib32stdc++6 lib32gcc1 lib32ncurses5 zlib1g lib32z1 lib32bz2-1.0
````
You also need the repo tool for cloning Android source trees.

##Set up and get the repo:
````
repo init -u https://github.com/DirtyUnicorns/android_manifest.git -b lollipop-caf
mkdir -p .repo/local_manifests
````

Create a file .repo/local_manifests/osprey.xml and paste this in:
````
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
    <project name="Vachounet/android_device_motorola_osprey" path="device/motorola/osprey" remote="github" revision="du-5.1" />
    <project name="MotoG3/android_vendor_motorola_osprey" path="vendor/motorola/osprey" remote="github" revision="cm-12.1" />
    <project name="MotoG3/android_kernel_motorola_msm8916" path="kernel/motorola/msm8916" remote="github" revision="cm-12.1" />
    <project name="CyanogenMod/android_external_mm-dash" path="external/mm-dash" remote="github" />
    <project name="CyanogenMod/android_hardware_qcom_fm" path="hardware/qcom/fm" remote="github" />
    <project name="CyanogenMod/android_device_qcom_common" path="device/qcom/common" remote="github" />
    <project name="CyanogenMod/android_hardware_qcom_audio" path="hardware/qcom/audio-caf/msm8916" remote="github" revision="cm-12.1-caf-8916" />
    <project name="CyanogenMod/android_hardware_qcom_display" path="hardware/qcom/display-caf/msm8916" remote="github" revision="cm-12.1-caf-8916" />
    <project name="CyanogenMod/android_hardware_qcom_media" path="hardware/qcom/media-caf/msm8916" remote="github" revision="cm-12.1-caf-8916" />	
</manifest>
````

Then fetch the repositories
````
repo sync
````

##Building:
````
source build/envsetup.sh
breakfast osprey
make clean
brunch osprey
````
