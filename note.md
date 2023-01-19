**Welcome to Magisk Delta - the unofficial third-party Magisk with extra feature. Please uninstall Magisk Delta if you don't trust it**

## fd48f87f-delta

### Diffs to 25.2-delta-6

- [MagiskHide] Allow SuList apps to load magisk module mounts. Example, if you want systemless hosts load for Chrome, you need to add Chrome to SuList to let systemless hosts work!
- [General] Fix MagiskHide and Zygisk become non-functional after enable Core-only mode
- [General] Trim mountinfo before mounting mirrors
- [MagiskInit] Inject `magiskd` by init `exec`, no longer register magisk as service
- [MagiskHide] Refactor logcat-based hide (it might not work properly with Zygote Preforking enabled)
- [MagiskHide] No longer spoof/alter/manipulate any non-Magisk related signals or traces to circumvent any device state detection
- [SuList] No longer automatically grant root access for SuList apps
- [SuList] Only unmounts after system server start, số module like systemize apps and debloat should work (you also need to add apps that is systemized by Magisk module to SuList)

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
- [MagiskInit] Inject `magiskd` by init `exec`, no longer register magisk as service

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
