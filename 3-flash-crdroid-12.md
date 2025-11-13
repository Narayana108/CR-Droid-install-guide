# 3 - Flash CRDroid 12
_Guide is for: CRDroid 12.2 - 31 October 2025_

## Prerequisites
- Phone model: POCO F5 Marble
- [2 - Data Backup & ROM Recovery](https://github.com/Narayana108/-CR-Droid-install-guide/blob/main/2-data-backup-and-rom-recovery.md) Guide completed.

## Good to know
    - CRDoid 12.2 is stable and amazing !
    - CRDroid can run all you apps and Google Playstore.
    - I don't use Google or Google Playstore, so that is not included in this Guide.
    - CRDroid can run apps with strong security/integrity checks such as Bank apps, but that requires modifications.

## Important info
[Blog changelog for each version](https://crdroid.net/blog/). 

**Never use the updater from your mobile phone running CRDroid !**
As this cannot run kernel and firmware updates, and often the kernel or firmware needs to also be updated with the new ROM version.

Very important to read this [Changelog](https://crdroid.net/marble/12) !
As you may see a line like this in there:
`    - use 30_october ksu file from install documents`
**This means that the new minor ROM version requires a kernel upgrade !**
If you update from the CRDroid ROM or flash to the new ROM, you will get stuck in a bootloop of death.
But it is recoverable by flashing the correct kernel and or firmware.

[All Support Links and Channels](https://crdroid.net/marble/12/support) 

Use @Chaitanyabuilds telegram channel as the primary means to getting updates, kernel links, change log, etc. This will always have the latest most up to date files and information.

### Download the required files
With correct versions for the specific device, as per the [cr-droids official site](https://crdroid.net/marble/12) or telegram groups instructions.
My directory structure is as follows with the required downloaded files:

    ~/Phone/cr-droid-12.2-2025-10-31                                    
    ❯ tree                                                                                   
    .
    ├── 1.recovery
    │   └── OFRP-R11.1_7_RECOVERY-Beta-marble.img
    ├── 2.firmware`
    │   └── fw_marble_marble_in_global-ota_full-OS2.0.206.0.VMRINXM-user-15.0-439b7fd3c5.zip
    ├── 3.kernel
    │   └── LosKsu_30_October.zip
    └── 4.rom
        └── crDroidAndroid-16.0-20251031-marble-v12.2.zip

Copy the firmware, kernel and ROM to your phone:

	~/Phone/cr-droid-12.2-2025-10-31
  	❯ tree 
    
	❯ adb push 2.firmware /sdcard/                                                                                 
 	                                                                                                             
	❯ adb push 3.kernel /sdcard/

	❯ adb push 4.rom /sdcard/

Files in `/sdcard/` = `/` within the phone( root directly / highest level directly).
## Boot into recovery
       adb reboot recovery

## Flash Firmware, Kernel and Rom

_If you are installing a different ROM or upgrading a major version of the same ROM, you may need to wipe(format) your entire phone_

### Flash from Computers CLI
Initially I used the CLI when I first installed CR Droid.

Old notes for KernelSU Flash via 'adb sideload':
` adb sideload kernelsu_next_20240810.zip`

_I put this hear only for reference, and if someone wants to update this section of the guide_

###  Flash in OrangeFox Recovery
**Recommended method**

You should be in booted into Recovery mode now.

#### 1. Flash the Firmware
- In Files (First tab) navigate to '2.firmware'.
- Select the zip file.
- Make sure 'Reflash OrangeFox after flashing a ROM' is ticked
- Swipe to install
- Wipe Dalvik/Art Cache,cache, FRP, metadata
- Make sure no errors occurred, if not move on to the next step.
  
#### 2. Flash the Kernel
_I am not sure if this should maybe be Step 3 instead, 
but you may just flash the kernel again after flashing the ROM, if the ROM doesn't boot._

- In Files (First tab) navigate to '3.kernel'
- Select the zip file
- Make sure 'Reflash OrangeFox after flashing a ROM' is ticked
- Swipe to install
- Make sure no errors occured, if not move on to the next step.

#### 3. Flash the ROM
- In Files (First tab) navigate to '4.rom'
- Select the zip file
- Make sure 'Reflash OrangeFox after flashing a ROM' is ticked
- Swipe to install
- Make sure no errors occurred,
- Reboot to system  ! And you should be now booted into the newly installed CRDroid version !

#### 4. Extra - Install Nikgapps (Google)

- Reboot to recovery
- Flash the Nikgapps
- Make sure no errors occurred,
- Wipe Dalvik/ArtCache and Cache
- Make sure no errors occurred,
- Reboot to system !

## Restore your backups

### Push all backed-up media & data back to phone once
```bash
adb push ~/Phone/backups/media/DCIM/         /sdcard/
adb push ~/Phone/backups/media/Download/      /sdcard/
adb push ~/Phone/backups/media/Documents/     /sdcard/
adb push ~/Phone/backups/media/Music/         /sdcard/
adb push ~/Phone/backups/media/Pictures/      /sdcard/
adb push ~/Phone/backups/media/Pictures/Recordings/ /sdcard/
adb push ~/Phone/backups/media/Movies/        /sdcard/
adb push ~/Phone/backups/media/contacts.vcf   /sdcard/
adb push ~/Phone/backups/media/PipePipeData.zip /sdcard/
```

## Extra
### Fix Banking Apps not working

1. Download [KernelSU APK - V1.0.5](https://github.com/tiann/KernelSU/releases/download/v1.0.5/KernelSU_v1.0.5_12081-release.apk)
    from: https://github.com/tiann/KernelSU/

	_The KernelSU app should just be working out the box, nothing extra needs to be installed. This App solely depends on the correct KernelSU version being installed._

2. You will then need to install certain kernel modules in KernelSU depending on what is patches are required to get the banking apps working.

3. Join a telegram group to get full guides on how to proceed:

I only used the information in this group as a secondary means to fix a certain problem I had. 
I am not that familiar with what software is being used at share. 
But these are the best guides I have seen on the internet till date.

**Again, use at own risk !**
**For education purposes only**

	👨‍💻 Yuri Root Channel:
    📚 All methods for: Root, Hide Root, By Pass Ingegrity, root dection, etc.
    🎯 Channel: t.me/yuriiroot
---

✅ All Done.
🙏 Hari Om Tat Sat.
