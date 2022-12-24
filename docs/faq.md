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

### How do I run magisk on devices with exploit/temporarily root?

Occasionally, there would be exploits in certain devices that could lead to full fledged root. On modern Android, it is possible to use MagiskSU if you can gain a shell with the following conditions:

- Effective UID should be privileged (root, or euid=0)
- Have the ability to reload sepolicy (which 99.9% of the time means SELinux permissive)
- Have full Linux capabilities

If you meet all requirement above (after running exploit root tool):

- Push `magisk.apk` and `busybox` binary to `/data/local/tmp` and run [this script](https://huskydg.github.io/script/temp-magisk.sh) with root access

Note that these changes are not persistent, and you will need to find ways to rerun the whole process every boot.

### How to install Magisk into emulator (such as NoxPlayer, LDPlayer, etc...)?

- Before start:

1. Only Magisk Delta support Magisk installation into system partition. 
2. Although emulator has ramdisk image, patching ramdisk is not used because ramdisk is stored in seperate partition with very SMALL disk size that is not enough to store Magisk binaries.
3. MumuPlayer X will not be supported
4. Latest Magisk Delta Canary has been adopted to support Bluestacks, but enabling Zygisk will cause bootloop.

- Step to step to install Magisk into emulator:

1. Enable Root access in emulator settings
2. Install and open Magisk Delta
3. Grant root access to Magisk Delta, click "Install" under Magisk field and use "Direct Install into system partition" option instead of "Direct Install" option. If you don't see this option, close and re-open Magisk Delta app.
4. Disable Root access in emulator settings.
    *Some emulators delete `su` executable after disabling root access, accidentally remove magisk's `su` so backup and delete `/system/xbin/su` instead.*

### Pass Safetynet / Play Integrity (Device Integrity)

1. Enable Zygisk or install Riru core
2. Enable MagiskHide and install [Safetynet Fix Mod](https://github.com/HuskyDG/safetynet-integrity-fix/releases/latest)
3. Reboot your device

### Why not restore Magisk modules online repo?

The official Magisk modules repository is dead and no longer maintained. Due to that, add them back is meanless. However, [Fox2Code](https://github.com/Fox2Code) has developed [Magisk Modules Manager](https://github.com/Fox2Code/FoxMagiskModuleManager)  app which allows you to download Magisk modules online.
