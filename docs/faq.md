## FAQ

### How to install Magisk Delta from start?

- Process like installing Magisk: <https://topjohnwu.github.io/Magisk/install.html>

### How to switch from current Magisk to Magisk Delta and vice versa?

Just do like when you update Magisk!

#### Direct Install (Recommended)

1. Install, open and then grant root acccess to Magisk Delta.
2. In **Magisk** section, tap "Install" and then "Direct Install". If you don't see this, try close and open the app.

#### Just flash Magisk Delta from current Magisk app

1. Rename the extension `magisk.apk` to `magisk.zip`
2. Open Magisk app, click "Modules" tab -> "Install from storage" and choose `magisk.zip`

#### Install Magisk directly to `/system` (Not recommended)

For some reasons, you don't want to install Magisk in regular way (patch boot imge), you can install Magisk directly to `/system`. Make sure you have a backup of your ROM in case system can't boot and do not use broken Custom Recovery. Your ROM must be able to mount read-write and your kernel must support dynamic SeLinux rules patch. Process this method at your own risk!

1. Restore to stock boot image if you already have Magisk installed
2. Boot to recovery, rename `magisk.apk` to `systemmagisk.zip` and flash it.
3. If you want to update Magisk, please use **Direct Install into system partition** instead of **Direct Install**

### How to install Magisk into emulator (such as NoxPlayer, LDPlayer, etc...)?

#### Before start:

1. Only Magisk Delta support Magisk installation into system partition. 
2. Although emulator has ramdisk image, patching ramdisk is not used because ramdisk is stored in seperate partition with very SMALL disk size that is not enough to store Magisk binaries.
3. MumuPlayer X will not be supported
4. Latest Magisk Delta Canary has been adopted to support Bluestacks, but need [app_process wrapper](https://github.com/HuskyDG/app_process_wrapper/releases) to run Zygisk.

#### Step to step to install Magisk into emulator like NoxPlayer, LDPlayer, MemuPlayer,...

1. Enable Root access in emulator settings
2. Install and open Magisk Delta
3. Grant root access to Magisk Delta, click "Install" under Magisk field and use "Direct Install into system partition" option instead of "Direct Install" option (If you don't see this option, close and re-open Magisk Delta app) Don't restart now!
4. ~~Disable Root access in emulator settings.~~ Backup built-in `su` (`/system/bin/su` and `/system/xbin/su`) and delete them (in case you want to uninstall Magisk and restore to built-in `su`), then reboot. Because emulators like LDPlayer will remove all `su` after disable ROOT from settings, **DO NOT** disable Root access in emulator settings.
5. Enjoy Magisk!

#### Step to step to install Magisk into Bluestacks

1. Download Bluestacks Tweaker from [here](https://bstweaker.tk/)
2. Use Bluestacks Tweaker and click "Unlock" to unlock Bluestacks instance and then launch it, overwise you can't install Magisk
3. When the instance starts up successfully, click "Patch" to open root access, install Magisk Delta and execute "Direct Install into system partition" action
4. When you are done, click "UnPatch" and then relanch the instance.
5. Enjoy Magisk!

### After enabling MagiskHide, why my app/game can still detect emulator?

MagiskHide is not emulator-detection bypass

### How to manually trigger Core-only mode from Recovery?

Create a empty file named `.disable_magisk` in these location: `/cache`, `/persist` or `/metadata`

### How to pass Play Integrity (Device Integrity)

1. Enable Zygisk or install Riru core
2. Enable MagiskHide and install [Safetynet Fix Mod](https://github.com/HuskyDG/safetynet-integrity-fix/releases/latest)
3. Reboot your device

### Why not restore Magisk modules online repo?

The official Magisk modules repository is dead and no longer maintained. Due to that, add them back is meanless. However, [Fox2Code](https://github.com/Fox2Code) has developed [Magisk Modules Manager](https://github.com/Fox2Code/FoxMagiskModuleManager)  app which allows you to download Magisk modules online.
