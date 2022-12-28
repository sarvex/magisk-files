**Welcome to Magisk Delta - the unofficial third-party Magisk with extra feature**

## 7f89a94f-delta

- Minor script changes

NOTE: 

- Since Magisk Delta 25206+, Bootloop Protector is triggered not only when `zygote` keeps restarting for many times but also when system failed to boot for 3 times, which is useful for some module that cause system crashing.

### Diffs to official Magisk

- [General] MagiskHide is rewritten, rely on system logcat
- [App] Support installing into system partition
- [General] Copy required files to `/system` for `addon.d`
- [Manager] Show all supported languages in Language settings for Chinese ROM
- [Module] Support systemless deleting files or folders for modules
- [General] Built-in Bootloop Protection to protect system from bootloop by magisk module
- [General] Tune F2FS driver
- [MagiskInit] Support Pre-Init mount, replace system files before `init` starts
- [MagiskInit] Support loading custom rc script from pre-init directory
- [App] Wait for service to bind before accessing
- [Modules] Support magic mount more partitions (`my_*`, `odm`, `optics`, `prism`)
- [MagiskHide] Introduce [SuList feature](https://huskydg.github.io/magisk-files/docs/sulist)
- [Zygisk]: Switch to use native bridge
- [Zygisk]: Replace xhook with lsplt hook api
- [MagicMount]: Recreate all mounts under mirrors
- [General] Support Bluestacks
- [Module] Live patch `sepolicy.rule` if it is not found in `sepolicy.rules` directory

### About Canary and Debug?

- They are built from the same source code
- Debug has more detailed logs than Canary

## Magisk (831a398b) (25206)

- Fix support on Linux < 3.6
- Several minor under-the-hood improvements

## Diffs to v25.2

- [General] Fix minor bug in module files mounting implementation
- [MagiskPolicy] Fix minor bug in command line argument parsing
- [Zygisk] Prevent crashing daemon in error
- [Zygisk] Rewrite zygote code injection with new loader library approach
- [App] Make stub patching 100% offline
