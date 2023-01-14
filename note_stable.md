## Magisk v25.2-delta-5 by HuskyDG

### Diffs to official Magisk

- [General] Restore MagiskHide, uses system logcat to monitor app processes startup: disabled or abnormal logcat can't use MagiskHide.
- [App] The package name is `io.github.huskydg.magisk`
- [App] Support Magisk installation without boot image for emulators
- [General] Copy required files to `/system` for `addon.d`, like Lygisk
- [Manager] Show all supported languages in Language settings for Chinese ROM
- [Modules] Support systemless deleting files or folders for modules
- [General] Built-in Bootloop Protection to protect system from bootloop by Modules
- [General] Tune F2FS for unencrypted devices
- [MagiskInit] Support Pre-Init mount, replace system files before `init` starts
- [MagiskInit] Support loading custom rc script from pre-init directory
- [App] Wait for service to bind before accessing  [topjohnwu/Magisk#6268](https://github.com/topjohnwu/Magisk/pull/6268)
- [Modules] Support magic mount more partitions (`my_*`, `odm`, `optics`, `prism`)
- [MagiskInit] Use stable random number seed [topjohnwu/Magisk#6340](https://github.com/topjohnwu/Magisk/pull/6340)
- [MagiskHide] Introduce [SuList feature](https://huskydg.github.io/magisk-files/docs/sulist): Sulist apps are granted root, Magisk remain invisible for other processes
- [Zygisk]: Change to Native bridge method (Credit @5ec1cff for [Maru](https://github.com/topjohnwu/Magisk/tree/940a3862a4b0868ebe02ae035bcb7fefa6985bc2), [chinese post about it](https://github.com/5ec1cff/my-notes/blob/master/maru.md))

## Magisk (c3b4678f) (25204)

- Make hiding the Magisk app 100% offline
- Cleanups and minor refactoring of Zygisk

## Diffs to v25.2

- [General] Fix minor bug in module files mounting implementation
- [MagiskPolicy] Fix minor bug in command line argument parsing
- [Zygisk] Prevent crashing daemon in error
- [Zygisk] Rewrite zygote code injection with new loader library approach