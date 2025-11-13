# 2 - Data Backup & ROM Recovery

## Prerequisites
- [1 - Install OrangeFox Recovery](https://github.com/Narayana108/-CR-Droid-install-guide/blob/main/1-flash-orangefox-recovery.md) Guide completed.
**Things break easily ! Always have backups !**

POCO F5 (Marble) has two slots, Slot A and Slot B, these work like partitions. User Data is separated from the OS, Kernel and Firmware Data as it is stored on a separate Slot.

- Check for multiple slots:
       `fastboot getvar current-slot`
  
      fastboot getvar current-slot  
    	# Output:
    	# current-slot: b
		
_Only A/B devices report `current-slot`. This shows the phone has 2 slots_
_This is only for educational purpose, it wont be used later._

## OrangeFox Recovery ROM Backup 
- I don't use OrangeFox Recovery backups as a primary means, as I don't understand exactly how it works. 

- User data( media, contacts, etc ) cannot be backup'd from OrangeFox Recovery for POCO F5, as it requires an external storage( e.g SD card ).


## Backup tips
Encrypted backups work with only with the same ROM and Major version.

This is crucial for understanding ROM installs and updates as well.
Extracts from the [Official OrangeFox backup guide](https://wiki.orangefox.tech/en/guides/backups):

    * Creating backups of encrypted data is fraught with risks. If you want to backup the data partition of an encrypted device, _you would be very well advised to first delete the lockscreen password/pin in the ROM before booting to recovery to create the backup_. If you do not do this, you might have issues when trying to restore the data backup. ( - I am not sure how applicable this is, as mentioned above it should work, the ROM's encryption method and version should just match the backup's encryption format ).

    * Always take a backup of your user data (to an external storage device or the cloud) every time you want to flash something (anything - ROMs, recovery, kernels, mods, OTA updates, or whatever else). `Ignore this advice at your own peril`.

    * Do not try to restore a backed-up data partition from one ROM to another ROM.

    * Do not try to restore a backup of an encrypted device to a device that is not encrypted, or to a device that is encrypted with a different encryption protocol (eg, by a different ROM).
    
    * Do not try to restore a backup of one ROM on top of another ROM. First flash the ROM zip of the ROM whose backup you want to restore (the _precise version_ that was backed up) before restoring its backup.
    
    * Do not try to restore a backup of a partition that currently contains data which you want to retain. Restoring a backup of a partition necessarily involves automatic wiping of its current contents, and replacing them with the contents of the backup. So anything already there before restoring the backup will be _irretrievably_ lost.
    
    * With Android 12 and higher there can be potential fscrypt policy problems that can make the system unbootable after restoring a data backup. Make sure that the ROM you are restoring the backup to is _exactly_ the same as the one that you took the backup from.



## ROM Roll Back & Recovery
- My ROM roll back technique is to simply keep the current ROM version with its corresponding kernel and firmware versions stored on my computer.
- If anything go's wrong with the new update or installation, I just flash the backup ROM, etc from my computer.

## User Data Backup
_There are much better backup solutions, Such as: [Neo-Backup](https://github.com/NeoApplications/Neo-Backup)_
_This is just what I used when I did my upgrade._
 
### Copy Data from phone to PC
```bash
adb pull /sdcard/DCIM/         ~/Phone/backups/media/DCIM/
adb pull /sdcard/Download/      ~/Phone/backups/media/Download/
adb pull /sdcard/Documents/     ~/Phone/backups/media/Documents/
adb pull /sdcard/Music/         ~/Phone/backups/media/Music/
adb pull /sdcard/Pictures/      ~/Phone/backups/media/Pictures/
adb pull /sdcard/Recordings/    ~/Phone/backups/media/Pictures/
adb pull /sdcard/Movies/        ~/Phone/backups/media/Movies/
adb pull /sdcard/contacts.vcf   ~/Phone/backups/media/
adb pull /sdcard/PipePipeData.zip ~/Phone/backups/media/
```

### Copy Data from PC to phone
```bash
adb push ~/Phone/backups/media/DCIM/         /sdcard/
adb push ~/Phone/backups/media/Download/      /sdcard/
adb push ~/Phone/backups/media/Documents/     /sdcard/
adb push ~/Phone/backups/media/Music/         /sdcard/
adb push ~/Phone/backups/media/Pictures/      /sdcard/
adb push ~/Phone/backups/media/Pictures/Recordings/ /sdcard/Recordings/
adb push ~/Phone/backups/media/Movies/        /sdcard/
adb push ~/Phone/backups/media/contacts.vcf   /sdcard/
adb push ~/Phone/backups/media/PipePipeData.zip /sdcard/
```

### Save App List
```bash
adb shell "pm list packages -3" | awk -F: '{gsub(/\r$/,"",$2); print $2}' | sort > ~/Phone/backups/apps/installed_apps.txt
```

#### Verify
```bash
wc -l ~/Phone/backups/apps/installed_apps.txt    # → 86 (or your count)
head -n5 ~/Phone/backups/apps/installed_apps.txt
```

---
➡️ Next Guide: [3 - Install CRDroid 12.2](https://github.com/Narayana108/-CR-Droid-install-guide/blob/main/3-flash-crdroid-12.md)
