**Welcome to Magisk Delta - the unofficial third-party Magisk with extra feature. Please uninstall Magisk Delta if you don't trust it**

## 886fdde8-delta

- Always patch selinux if installing Magisk into system partition

### HAPPY NEW YEAR 2023 🎆🎆
There might be a few updates before it is released as 25.2-delta-6 with highlight changes:

- [MagicMount]: Recreate all mounts under mirrors to make magic mount more compatible, especially devices which use overlayfs to modify some system folder
- [General] Support Bluestacks, needs [app_process wrapper](https://github.com/HuskyDG/app_process_wrapper/releases) to run Zygisk, overwise it will be bootloop
- [Module] Live patch `sepolicy.rule` if it is not found in sepolicy.rules directory, especially `magiskinit` on some old devices cannot mount partition that stores `sepolicy.rule`

Remember to join discussion group to feedback and report bugs

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
- [Modules] Support magic mount more partitions (`my_*`, `odm`, `optics`, `prism`)
- [MagiskHide] Introduce SuList feature
- [Zygisk]: Switch to use native bridge
- [Zygisk]: Replace xhook with lsplt hook api
- [MagicMount]: Recreate all mounts under mirrors
- [General] Support Bluestacks, needs [app_process wrapper](https://github.com/HuskyDG/app_process_wrapper/releases) to run Zygisk, overwise it will be bootloop
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
