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

**Note: For every release, latest YAAP source code is synced. Changelogs here are from device-side only**

**YAAP-HOMEMADE 5th Release - 20260211**

**ROM (includes custom changes, added by Tashar02):**
* Do not ship LineageOS's Camelot (PDF viewer), Glimpse (Gallery) and Twelve (Music player).
* Add support for window ignore secure.
* Implement screenshot sound effect from NothingOS.
* Erase more cache upon flashing.
* Select the proper request list size for high speed session during video recording.
* Add support for receiving dataCallback with fd/buffer as frame buffer in camera.
* Fix deadlock in binder death cleanup of CameraService.
* Avoid waiting on results once flush is completed in camera.
* Import Xiaomi Image Tags defenitions.
* Fix some memory leaks.
* Remove unnecessary HashMap instantiation.
* Avoid needless Integer.valueOf() object allocation.
* Keep recent tasks for more time in memory.
* Prevent ANRs by offloading dumps to a dedicated thread.
* Optimize the response speed of recents animations.
* Fix an upstream race condition in handling of system error files.
* Fix an upstream infinite loop bug in ProtoFieldFilter.skipBytes().
* Optimize writeToParcel performance.
* Switch to low ram policy for bitmaps and apply ImageView's CenterCrop style of cropping.
* Further reduce notifications bitmap resource usage.
* Limit auto restricted bucket delay.
* Reduce concurrency limit.
* Disable lookaside allocator.
* Reduce buffer size bytes for PackageUtils.
* Reduce max running broadcast limits.
* Reduce dropbox max files.
* Reduce input history ring buffer size.
* Disallow max cached processes above 128.
* Reduce logging size for NetworkPolicyLogger and BroadcastResponseStatsLogger.
* Be conservative when loading snapshot config.
* Use getPackagesForOps instead of iterating packages by checkOperation.
* Further optimize snapshotAndMonitorLegacyStorageAppOp.
* Opportunistically create views directly for performance.
* Fix split shade missing issue.
* Avoid using deriveStateOf for media translation.
* Optimize home to desktop transition.
* Remove expensive compression for app icons.
* Optimize pin sizes for pinner service.
* Pin critical files for I/O latency.
* Reduce icons memory usage for ShortcutService.
* Fix wrong volume drawable.
* Reduce blocking operation on display thread.
* Fix flickering issue in streaming video cases.
* Remove jobs for non-existent system packages.
* Reduce screenshot dismiss delay to 3 seconds.
* Set scroll friction to 0.012.
* Use -O3 for libhwui and compile for performance.
* Use -O3 for core/jni.
* Use -O3 for aapt2.
* Use -O3 for androidfw.
* Use -O3 and LTO with 100% instrumentation for hardware display HAL.
* Use -O3 for renderengine.
* Use -O3 for binder.
* Use -O3 for SurfaceFlinger and disable debugging.
* Reduce thread scheduling overhead in SurfaceFlinger
* Import arter97's VRR implementation in SurfaceFlinger.
* Enable mirror blur for notification shade and app drawer.
* Remove blue tint on white theme.
* Prevent Launcher3 crash on boot.
* Fix and bring back option to customize blur radius for Launcher3.
* Set default enhanced blur radius for Launcher3 to 15dp.
* Increase dalvik heap growth limit for 6gb ram targets to 384 MB.
* Disable event writing in production builds.
* Optimize the DateTimeView logic time consumption when updating the UI main thread time.
* Remove ScrollCache when activity is destroyed.
* Do not pin non-existent libraries.
* Return early in BootReceiver if trace_pipe doesn't exist.

**Device:**
* Kernel state at Scarlet-v4.0-beta4.
* Update unpinned blobs to redwood OS2.0.17.0.UMSMIXM.
* Update public.libraries.txt to redwood OS2.0.17.0.UMSMIXM.
* Whitelist libmialgoengine.so to load dynamically.
* Update auto brightness nits to redwood OS2.0.17.0.UMSMIXM.
* Update Dolby Media blobs from OnePlus 11 CPH2447_16.0.1.300(EX01).
* Apply Expressive theme globally for Dolby Atmos.
* Optimize and shrink resources for Dolby Atmos.
* Use new method to listen for preference changes in Dolby Atmos.
* Raise freq of little+big CPUs and GPU for expensive rendering.
* Bring back MIUI color mode options.
* Re-enable GL backpressure.
* Disable high performance transitions.
* Stop shipping 32-bit Zygote.
* Set market name for redwood.
* Label missing sysfs node for IPA fw subsystem.
* Add sepolicy for diag-router on user build only.
* Fix rounded_corner_content_padding placement.
* Refine statusbar padding.
* Remove some problematic and duplicated pinned files.
* Specify ambient color temperature sensor.

**YAAP-HOMEMADE 4th Release - 20260110-hotfix**
* Correctly override enhanced blur radius for Launcher3 and set it to 20dp.

**YAAP-HOMEMADE 4th Release - 20260110**
* Update unpinned blobs to redwood OS2.0.16.0.UMSMIXM.
* Update WFD system blobs to dada OS3.0.3.0.WOCMIXM.
* Update CarrierConfig to LA.QSSI.16.0.r1-06700-qssi.0.
* Transition back to stock time_daemon from Sony's TimeKeep.
* Boost CPU and GPU to max freq for expensive rendering, particularly for background blur.
* Set background blur radius for Launcher3 to 23.
* Switch back from expensive mirror blur to clamp blur.
* Fix dlopen failures for mialgoengine camera lib.
* Fix soft reboot caused by BPF check failure to detect GpuMem tracing in libmeminfo.

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
