## Build Information

```
ROM: YAAP
Type: HOMEMADE (UNOFFICIAL)
Devices: POCO X5 Pro / Redmi Note 12 Pro Speed (redwood)
Device trees:
1. https://github.com/Tashar02/device_xiaomi_redwood/tree/yaap-sixteen
2. https://github.com/Tashar02/device_xiaomi_sm8350-common/tree/yaap-sixteen

Vendor trees:
1. https://github.com/Tashar02/vendor_xiaomi_redwood/tree/sixteen
2. https://github.com/Tashar02/vendor_xiaomi_sm8350-common/tree/sixteen
3. https://github.com/Tashar02/vendor_xiaomi_redwood-miuicamera/tree/yaap-sixteen
4. https://github.com/Tashar02/vendor_oneplus_dolby/tree/main

Kernel tree: https://github.com/Atom-X-Devs/scarlet_xiaomi_sm7325/tree/staging
```

## Flashing Process

* Reboot to recovery
* Format data (Only if you want to do a clean flash)
* Connect to adb and run `adb sideload YAAP-*.zip` from platform-tools.
* Reboot to recovery.
* Reboot to system.
* After flashing, unlock the device and let it idle for 2-3 minutes to allow Android processes to properly initialize before using it.

## Changelogs

**YAAP-HOMEMADE Initial Release - 20250913**
* Initial unofficial build.
