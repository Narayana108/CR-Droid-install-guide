# 1 - Flash OrangeFox Recovery

⚠️ Before you start, make sure you’ve **deleted every Google account** from the device on a fresh install. This will prevent “Factory Reset Protection” (FRP) from kicking in during the setup steps.
    
## Terminologies
    - 'ROM' means 'Android Operating system'.
    - 'To flash' means 'to install'.
    - Sideloading is the same as flashing.
    
## Important information
    - Always refer to the official website and telegram channels for most accurate up to date information.
    - CR Droid ROMs are very delicate, one requires to have the exact kernel and firmware version for the specific ROM version.
    - Follow each step precisely.
    - If one step fails or gives errors, do not move onto the next step.
    - If you are a beginner - read all the guides to have the full picture before starting.

## About this guide
    - File names(versions) used are for CRDroid 12.2. File names should be adjusted according to versions. 
    - I tried my best to give as much information for a smooth and clear install or upgrade process.
    - But there are no guarantees in life, use at own risk.
    - The guides on the internet (websites, github, etc) are generally outdated and or are not clear, which will lead one down a rabbit hole of frustration, difficulties and waste a lot of time.
    - The useful updated information and guides are found in Telegram channels.
    - This is supposed to be a useful guide, and hopefully up to date as well.
    - The version numbers are given to easily see if guide is up to date and still still valid.
    - But even if in the future it becomes outdated, a lot of good fundamentals can be found here.


## What is OrangeFox Recovery?

- It is an isolated mini ROM that lives in its own partition and it can be booted into via Recovery Mode.
- If the custom ROM gets corrupt (i.e from installs, upgrades, etc), you have a method to Recover your ROM.
- It is used for: backups, recovery and flashing ROM's, kernels and firmware.
- It can also: remove installed apps, kernelsu modules, boot into various states, check active slot and other things.

### Access Recovery Mode
- Press and hold: 'power + volume up' to access Recovery Mode.

Only the default Recovery ROM should be there, we still need to flash OrangeFox Recovery.

## Prerequisites

    - Phone model: POCO F5 Marble (India)
    - ROM: CR-Droid (Install or upgrade)
    - PC OS: Debian / Ubuntu
    - Phone:
      - Boot loader unlocked
      - Developer mode enabled
      - USB debugging enabled
      - Maybe more things, I cant remember.

### Downloaded correct OrangeFox Recovery version
As per the instructions from the [CR-Droid official site](https://crdroid.net/marble/12)

## 1. Install tools
        sudo apt update && sudo apt install adb fastboot -y

## 2. Verify device and boot to fastboot

Your mobile should be:
- Switched on.
- Screen is unlocked.
- USB debugging allowed.

Now start the process:
- Verify device from your CLI on your computer:
       `adb devices`
- Reboot to fastboot:
    `adb reboot bootloader`
    
_You should see the fastboot screen on your mobile phone now_

- Verify connection 
       `fastboot devices`

## 3. Flash OrangeFox Recovery
You should now be booted into fastboot.
- Now flash the OrangeFox unto your phone.
 `fastboot flash recovery OFRP-R11.1_7_RECOVERY-Beta-marble.img`

## 4. Reboot into Recovery
        fastboot reboot recovery
---

➡️ Next: [2 - Data Backup & ROM Recovery](https://github.com/Narayana108/-CR-Droid-install-guide/blob/main/2-data-backup-and-rom-recovery.md)
