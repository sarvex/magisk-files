## 249e0d8a-delta

### Diffs to official Magisk

- [General] MagiskHide is rewritten, rely on system logcat
- [App] Add support for install Magisk into system partition
- [General] Copy required files to `/system` for `addon.d`
- [Manager] Show all supported languages in Language settings for Chinese ROM
- [Modules] Support systemless deleting files or folders for modules
- [General] Built-in Bootloop Protection to protect system from bootloop by Modules
- [General] Tune F2FS for unencrypted devices
- [MagiskInit] Support Pre-Init mount, replace system files before init process starts
- [MagiskInit] Support loading custom rc script from pre-init directory
- [App] Wait for service to bind before accessing
- [Modules] Support magic mount more partitions (`my_*`, `odm`, `optics`, `prism`)
- [MagiskHide] Introduce [SuList feature](https://huskydg.github.io/magisk-files/docs/sulist)
- [Zygisk]: Switch to use native bridge
- [Zygisk]: Replace xhook with lsplt hook api
- [MagicMount]: Recreate all mounts under mirrors to make magic mount more compatible
- [General] Support Bluestacks
- [Zygisk] Create a holder with clean mount namespace, `setns` to holder then `unshare` for process on hidelist.

### About Canary and Debug?

- They are built from the same source code
- Debug has more detailed logs than Canary

## Magisk (c3b4678f) (25204)

- Make hiding the Magisk app 100% offline
- Cleanups and minor refactoring of Zygisk

## Magisk (831a398b) (25206)

Fix support on Linux < 3.6

Several minor under-the-hood improvements

## Diffs to v25.2

[General] Fix minor bug in module files mounting implementation

[MagiskPolicy] Fix minor bug in command line argument parsing

[Zygisk] Prevent crashing daemon in error

[Zygisk] Rewrite zygote code injection with new loader library approach

[App] Make stub patching 100% offline

