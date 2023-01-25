# Magisk Delta Internal Documentation

## Early-init mount

- Some files requires to be mounted earliest in the boot process, Magisk Delta has provided the way to mount files in `pre-init` stage, before `init` is executed
- The one of following location is used as place to store files for early-mount.d (`$PREINITDIR/early-mount.d`):
  - `/data/adb/early-mount.d` (Ext4, Data encryption is disabled)
  - `/data/unencrypted/early-mount.d` (Ext4, File based Encryption)
  - `/cache/early-mount.d`
  - `/metadata/early-mount.d` (*)
  - `/persist/early-mount.d` (*)

> The location is decided by magiskinit: magiskinit will check each location in the top-down list if it's usable (is it on the ext4 partition or mountable in preinit?)

> (*) Be careful when device can only use persist or metadata for early-mount, these partitions are very limited in size. Filling up them might cause device unable to boot.

- You can place your files into the corresponding location under `early-mount.d` directory. For example, you want to replace `/vendor/etc/vintf/manifest.xml` and your mount directory is `/data/unencrypted/early-mount.d`, copy your `manifest.xml` to `/data/unencrypted/early-mount.d/system/vendor/etc/vintf/manifest.xml` , Magisk Delta will mount your files in the next reboot​
- Other files are not in `$PREINITDIR/early-mount.d/system` will be ignored.
- For module developers, you can use this path:
```
$(magisk --path)/.magisk/mirror/early-mount
```


**Early-init mount only support simple mount, which means it can replace files but cannot add new files, folders or replace folders**

## init.rc inject

- Feel annoying when you must repack boot image to inject custom `*.rc` script by using `overlay.d`? Magisk Delta has provide the way to inject custom `*.rc` script systemlessly!
- The chose location of custom `*.rc` script is `$PRENITDIR/early-mount.d/initrc.d`. Magisk Delta will inject all scripts in this folder into `init.rc` every boot.
- You can use `${MAGISKTMP}` to refer to Magisk tmpfs folder. Every occurrence of the pattern `${MAGISKTMP}` in your `*.rc` scripts will be replaced with the Magisk tmpfs folder when magiskinit injects it into `init.rc`.
- Magisk's mirror will not be available while booting, in order to access to the copy of `early-mount.d` directory. You can use this pattern `${MAGISKTMP}/.magisk/early-mount.d`.
- For module developers, you can use this path:
```
$(magisk --path)/.magisk/mirror/early-mount/initrc.d
```
- Here is an example of the `custom.rc` if you use `initrc.d`:

```
# Use ${MAGISKTMP} to refer to Magisk's tmpfs directory

on early-init
    setprop sys.example.foo bar
    insmod ${MAGISKTMP}/.magisk/early-mount.d/libfoo.ko
    start myservice

service myservice ${MAGISKTMP}/.magisk/early-mount.d/myscript.sh
    oneshot
```


## Remove files and folders

- Magisk has module feature which allows users to add and replace files in system without making actual changes to system partitions, so you still can receive OTA,... However, Magisk module does not allow users to make some files in system become invisible.

- In Magisk documentation:

> It is complicated to actually remove a file (possible, not worth the effort). Replacing it with a dummy file should be good enough

> It is complicated to actually remove a folder (possible, not worth the effort). Replacing it with an empty folder should be good enough. Add the folder to the replace list in "config.sh" in the module template, it will replace the folder with an empty one

- In some case, replace file or folder with blank one is not enough and might cause issue. And some modding require files to be disappeared in order to take effect. So Magisk Delta has added removal support for modules. Replacing the target which you want to be deleted with the broken symlink point to `/xxxxx`. When Magic mount happened and detected this symlink, the target will be ignored and disappeared.

- Example creating symbolic link as `/data/adb/modules/mymodule_id/system/vendor/etc/thermal-engine-normal.conf`, the target `/vendor/etc/thermal-engine-normal.conf` will be ignored and disappeared:

```
ln -s "/xxxxx" /data/adb/modules/mymodule_id/system/vendor/etc/thermal-engine-normal.conf
```

## MagiskHide 

- Hide Magisk and its modifications from chosen apps on hidelist.
- The principal implementation: Mounted by default, Unmount if listed

## MagiskHide SuList

- Magisk is hidden by default. Chosen apps on sulist will be able to see Magisk.
- The principal implementation: Unmount by default, Mounted if whitelisted

