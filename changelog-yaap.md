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

**YAAP-HOMEMADE 3rd Release - 20251229**
* Add support for OTA updates using YAAP's OpenDelta updater.

**YAAP-HOMEMADE 2nd Release - 20251228**
* Update all unpinned blobs to redwood OS2.0.13.0.UMSMIXM.
* Update WiFiDisplay system blobs to dada OS2.0.217.0.WOCMIXM.
* Override kernel BPF version to 5.10.239.
* Fix compilation, hotspot, boot failure with Android 16 QPR2.
* Enable support for background blur.
* Enable Graphics Acceleration.
* Disable GL Backpressure.
* Remove overlay for Aperture.
* Set GMS INTENT for QR code scanner to fix the QR code scanner QS tile.
* Remove vendor-defined color profiles since it causes yellow tint on Instagram reels.
* Fix "Phone doesn't ring through the earbuds but only the phone speaker when receiving incoming call" bug.
* Avoid access of deprecated LocUnorderedSetMap entry in gps.

**YAAP-HOMEMADE Initial Release - 20250913**
* Initial unofficial build.
