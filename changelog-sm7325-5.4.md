## Build Information

```
Kernel: Scarlet
Type: Stable
Devices: POCO X5 Pro / Redmi Note 12 Pro Speed (redwood), Xiaomi 11 Lite 5G NE (lisa)
Compiler: Neutron clang 24.0.0 with Neutron LLD 24.0.0
Compiler specific optimization: DCE and Clang Full LTO
Kernel Source: https://github.com/Atom-X-Devs/scarlet_xiaomi_sm7325.git
Kernel Branch: main
```
## Instructions for using the kernel source

### Branch
```
main: Includes the stable release of each update.
staging: An experimental branch that is NOT recommended for use until it has been merged into the 'main' branch.
```

### Defconfig
```
For redwood: xiaomi-qgki_defconfig and redwood.config
For lisa: xiaomi-qgki_defconfig and lisa.config
```

## Flashing Process

* Reboot to recovery, connect to adb and `adb sideload Scarlet-*.zip` from platform-tools.
* Alternatively, use Franco Kernel Manager's built-in flasher to flash the kernel (requires root). 
* After flashing, unlock the device and let it idle for 2-3 minutes to allow Android processes to properly initialize before using it.

## Credits
* All rightful commit authors, especially @Divyanshu-Modi at GitHub.
* My testers, especially @c7c9d5, @Megagangar, @mehuldekate205, @soumyadip_69, @ongenesis, @paganminkombaung at Telegram.

## Pull Request Contributions
1. [Wiktor Józwiak](https://github.com/Atom-X-Devs/scarlet_xiaomi_sm7325/issues/10)

## Changelogs

**v7.0 - 30/10/2026**
* Fix LSM session leak in msm_lsm_close() that caused soundtrigger failures and audio HAL crash loops.
* Merge CLO tag `LA.UM.9.14.1.r1-21700-QCM6490.QISI15.0`.
* Update qcacld-3.0, fw-api, and camera-kernel to CLO tag `LA.UM.9.14.1.r1-21700-QCM6490.QISI15.0`.
* Merge branch `linux-5.4.y` of openela/kernel-lts.
* Pick relevant commits from CLO tag `LA.UM.9.14.7.r1-03700-QCM6490.QISI15.0` across UFS, ADSPRPC, USB DWC3, and KGSL instead of merging the tag directly due to divergences from lahaina msm-5.4.
* Avoid UAF memory access in exit path, handle delayed Rx cancel cmd interrupt, reduce the interrupt wait time for SE IRQ in msm_geni_serial.
* Revert "serial: msm_geni_serial: Use correct condition for device suspend check" to fix a very rare kernel panic.
* Fix [CVE-2026-43037](https://github.com/advisories/GHSA-p2wf-qj6m-x5fg), [CVE-2026-31504](https://github.com/advisories/GHSA-5v9p-3rfc-6rw2), [CVE-2025-38617](https://github.com/advisories/GHSA-g6xr-fxvq-ffp4), [CVE-2026-52943](https://github.com/advisories/GHSA-vwrr-994w-h832), [CVE-2026-43038](https://github.com/advisories/GHSA-78m7-4xgc-xrrq), [CVE-2026-23455](https://github.com/advisories/GHSA-gm78-p64f-gx97), [CVE-2026-31662](https://github.com/advisories/GHSA-895h-4xx6-r95p), [CVE-2026-64306](https://github.com/advisories/GHSA-9h5h-wjm4-4jqg), [CVE-2026-64313](https://github.com/advisories/GHSA-x49g-5fpg-2qxf), [CVE-2026-80590](https://github.com/advisories/GHSA-m48g-6cv9-p3rh), and [CVE-2026-81000](https://github.com/advisories/GHSA-32hf-vhcc-85c2).
* Fix use-after-free read of tail->len in unix_stream_data_wait().
* Pick stable kernel fixes from mainline across networking, IPv4/IPv6, netfilter, TUN/TAP, procfs, genirq, and ptrace.
* Import various filesystem fixes for ext4, f2fs, and fat.
* Fix verifier bypass in fuse_prog_is_valid_access for fuse-bpf.
* Add support for EROFS.
* Enable per-CPU high-priority kthreads for EROFS decompression.
* Fix write failure in block crypto fallback.
* Import remaining commits missed from the inline crypto encryption update to upstream patchset (including fscrypt, skcipher API transition, and casefolding sync).
* Pull kallsyms improvements and cleanups from mainline.
* Pull some SPS, QCEDEV, and USB interconnect patches from msm-5.15.
* Bring irqchip, pinctrl, and genirq updates from upstream as dependencies to land Qualcomm PDC driver.
* Re-implement Qualcomm PDC irqchip with upstream architecture and modular support.
* Add implementation of Qualcomm IPCC mailbox from mainline, dropping downstream driver.
* Pause memlat monitor sampling timer when the CPU cluster is idle to avoid unnecessary wakeups.
* Revert applying thermal pressure when frequency dips below non-boost frequency in qcom-cpufreq-hw since the yupik doesn't have boost frequencies.
* Route LMh thermal pressure through Frequency Invariance Engine (FIE) in qcom-cpufreq-hw and skip redundant thermal pressure updates when frequency limits are unchanged.
* Remove CONFIG_SCHED_DEBUG and make sched debug functionality unconditional.
* Drop legacy Android max frequency capping to eliminate conflicting CPU capacity reporting with upstream thermal pressure.
* Upstream EEVDF to mainline.
* Re-enable PLACE_DEADLINE_INITIAL and PLACE_REL_DEADLINE sched features for better initial task placement and relative deadline preservation across migrations.
* Bring some general scheduler improvements from mainline.
* Fix some use-after-free in binder.
* Migrate to rcu_hurry in key areas to resolve lazy RCU performance regression and improve app launch performance.
* Add support for POSIX_FADV_NOREUSE in memory management.
* Apply micro-optimizations to hot page allocation path and refine atomic/RT reserve access handling.
* Move zram lockmap to be per-zram instead of per table and use custom keys per zram object.
* Fix race in accessing memory_section->usage in sparsemem and missing barrier in anon_vma init.
* Tune SSG I/O scheduler default expiration values and disable front merges to reduce latency on UFS workloads.
* Free perms_list on every bridge exit path in smcinvoke.
* Add 1ms sleep in wda_qmi of datarmnet to avoid circular wait.
* Unlock mutex lock before returning for non-custom waveforms in haptic_hv vibrator driver.
* Make directory locking killable in do_last() of VFS.
* Silence false-positive page allocation failure warnings in qdf_nbuf of qcacmn.
* Clear xrun state before sending buffer in msm-compress audio driver.
* Use freezable wait for forced requests in fuse request_wait_answer().
* Use freezable wait in dcache d_wait_lookup().
* Update snapshot of MMC crypto from msm-5.10.
* Update AW882XX audio driver to v2.0.13.
* Update Goodix touch driver to v1.4.17 with IC name lookup simplification and memory deallocation order fix.
* Fix IRQ depth imbalance on resume from gesture and prevent destroying workqueues during shutdown in Goodix touch driver.
* Implement charging status check for GT9897T touch driver, disable capacitance data for production, and optimize panel check delay.
* Import missing lisa changes for apr_mius.
* Import FPC fingerprint driver from ingres-s-oss for lisa.
* Properly guard redwood-specific changes in qti_battery_charger and camera driver.
* Fix xm_property_id sequence for lisa in qti_battery_charger.
* Disable pm8008j PMIC and LDO on Xiaomi sm7325 platform.
* Import missing camera clock settings, fix regulator table, and use suspend MCLK pinctrl for front sensor of lisa.
* Introduce tsens_chipinfo nvmem cells property on yupik.
* Move SDE IB bandwidth voting from DISP RSC to APPS RSC and factor in AB for IB vote calculation.
* Fix uninitialized `display` variable in `*_bridge_[enable|disable]` in SDE display driver.
* Enable all configs required by kernel FCM 7 in xiaomi_stock_defconfig.
* Stop calling do_execve_file in umh and remove the now unused do_execve_file from exec.
* Upstream KernelSU to `v32799`.

**v6.0 - 10/07/2025**
* Merge CLO tag `LA.UM.9.14.1.r1-21200-QCM6490.QISI15.0` (Linux tag is at v5.4.302 state).
* Add support for checkpoint restore capability that is required for Android 17 (for Chrome-based browsers to work).
* Fix [CVE-2026-43499](https://github.com/advisories/GHSA-cqc6-9f34-295v).
* Update DTC to upstream version `v1.8.1-15-g66e1201`.
* Update CFI from upstream (Thanks to Alex Winkowski).
* Bring some more scheduler improvements from mainline.
* Upstream EEVDF to linux tip/master.
* Use actual object size to detect spans in zsmalloc.
* Simplify read begin/end logic in zsmalloc.
* Return -EBUSY for zspage migration lock contention in zsmalloc.
* Fix vmstat_shepherd double-scheduling vmstat_update.
* Avoid unmap after kgsl system suspend.
* Return success for cmo of dummy clients in ion dma-buf.
* Nullify display modes after kfree.
* Fix division by zero during ESD recovery.
* Disable capacitance data support of goodix touchscreen for production.
* Fix accuracy of bsl_vol_default for AW8692X haptics.
* Add support for AW869X haptics.
* Upstream KernelSU to `v32579`. Only official KernelSU manager and KowSU manager is usable now.
* Get rid of manual KernelSU hooks in kernel in favor of syscall table tampering from within KernelSU.
* Enable RCU boost.
* Re-enable Polly optimizer since we've switched to Neutron Clang 23.0.0 which has Polly optimizer fixed for zstd.

**v5.0 - 16/05/2025**
* Upstream RCU to android14-5.15-lts.
* Pull fixes to lazy RCU from mainline.
* Implement fuse-bpf from android12-5.4-lts.
* Pull fixes to fuse-bpf from android15-6.1.
* Add support for seccomp architecture tracking from android12-5.4-lts.
* Add UBSAN trap instrumentation for my own debugging purpose (disabled in production).
* Replace zero-length array with flexible-array member across many drivers.
* Fix kernel stack corruption from af_unix by rejecting oversized sockaddr_un in unix_bind().
* Fix some array-bounds warnings.
* Simplify implementations of {READ,WRITE}_ONCE().
* Enforce atomicity for {READ,WRITE}_ONCE() memory accesses.
* Enforce that READ_ONCE_NOCHECK() access size is sizeof(long).
* Fix tons of data races.
* Fix array-index-out-of-bounds warnings generated by UBSAN.
* Fix an infinite loop in filemap.
* Fix possible endless loop in BPF map iteration.
* Don't take ->pi_lock unconditionally in task_work.
* Make chmod_common(), chown_common(), do_truncate(), default_llseek() killable.
* Fix lockdep warnings in fuse.
* Go back to using hardcoded static transmit buffer for ir-spi driver since we hit page allocation failure with the dynamic memory allocation method.
* Implement proper wake IRQ tracking in swr-mstr-ctrl audio driver.
* Set max available ratio of SSG to 25 again since capping queue depth saves power.
* Reduce synchronize_rcu() latency by reporting GP kthread's CPU QS early.
* Add buffer overflow check for perfcounter dynamic list in kgsl.
* Prevent sign extension on alignments in kgsl.
* Avoid a use-after-free in kgsl.
* Fix rampant inaccuracies of vmpressure data caused by stale data usage.
* Use statically allocated zram compression algorithm names.
* Do not permit zram params change after init.
* Optimize LZ4 dictionary compression performance for zram.
* Do not forget to endio for partial discard requests in zram.
* Switch to kvzalloc() for dictionary streams in backend_lz4.
* Fix runnable_sum clamp units mismatch.
* Reduce UTIL_EST_WEIGHT_SHIFT to 4 for better race-to-sleep.
* Make finish_task_switch() and its subfunctions always inline.
* Disable entity eligibility check, lag placement and run to parity for EEVDF to get better schbench results on Android.
* Upstream EEVDF to mainline.
* Reserve DL bandwidth only for root-domain moves in cpuset.
* Rdesign the entire DVFS headroom of schedutil with better dynamic logic for improved headroom predictability.
* Backport thermal pressure logic to qcom cpufreq driver from msm-6.1.
* Introduce frequency invariance engine (FIE) based on Tensor AIO.
* Port hardware throttle detection and thermal pressure to FIE from Tensor AIO.
* Migrate sampling work of memlat to dedicated kthread.
* Upstream KernelSU to v32486.
* Implement selinux_hide KernelSU hooks.
* Disable Polly optimizer since it breaks zstd compilation with Google's prebuilt Android Clang 22.0.2 based on r596125.

**v4.1 - 21/03/2025 [Eid Mubarak]**
* Improve transmit buffer handling in ir-spi driver.
* Fix pelt clock sync when entering idle.
* Drop Oneplus 3 fingerprintd thaw hack.
* Do not allow KernelSU manager built with a dummy keystore since it poses a security vulnerability.

**v4.0 - 13/03/2025**
* Merge CLO tag `LA.UM.9.14.r1-26700-LAHAINA.QSSI16.0`.
* Drop incomplete backport of a PSI patchset.
* Upstream BPF to msm-5.10.
* Fix USB debugging and WiFi hotspot on Android 16 QPR2.
* Add support for ZSTD compression algorithm v1.5.8 by Facebook.
* Apply optimizations from Samsung to ZSTD.
* Allow zram compression algorithm to be changed by users again.
* Add support for BBR v3 TCP congestion control.
* Restrict 8-channel audio capture to non-Xiaomi platforms to fix microphone while using speaker mode on social media apps.
* Fix UAF in dataipa and vidc.
* Enable hybrid mode only for HFR usecase in vidc.
* Fix kernel panic caused by mailbox.
* Handle spurious interrupt in pmic-arb spmi driver.
* Upstream smcinvoke to msm-5.15.
* Use threaded interrupts for glink.
* Ignore rpm-glink irq for suspend wake-up.
* Upstream EEVDF to mainline.
* Bring-in various general scheduler improvements from mainline.
* Optimize LLC cache affinity tiebreaker in CASS.
* Apply piecewise linear boosting to DVFS headroom in schedutil.
* Fully fix-up and bring back support for thermal pressure to make more accurate scheduler decisions.
* Switch to non deferrable work in qcom-cpufreq-hw.
* Fix spinlock initialization order in qcom-cpufreq-hw.
* Reduce limits polling delay to 1ms in qcom-cpufreq-hw.
* Set each CPU clock to its max when waking up in qcom-cpufreq-hw.
* Retain disable depth for managed interrupts across CPU hotplug.
* Rebalance managed interrupts across multi-CPU hotplug.
* Improve exFAT performance and bring-in several upstream fixes to the driver.
* Fix I/O error on fsync() in detached loop devices.
* Fix a directory corruption in ext4.
* Drop deprecated garbage collection logic from f2fs.
* avoid always making PTE dirty in pte_mkwrite().
* Fix reference counting in ovl_mmap error path.
* Protect free_pgtables with mmap_lock write lock in exit_mmap.
* Fix UAF when mm->mmap is reused after being freed.
* Set default vmpressure threshold of Simple LMK to 95.
* Wait 30ms in Simple LMK before starting killing victim processes again.
* Thaw the entire victim process in Simple LMK.
* Skip reclaim throttle on critical processes.
* Hardcode dirty_expire_centisecs to 30s.
* Fix double-free in dbitmap of binder.
* Fix a memory leak in the UFS driver.
* Add AOP rx queue len defense check in aoss driver to prevent potential kernel panic.
* Fix race between runtime PM suspend and MMIO read in qcacmn's hal_reo.
* Stop filtering out unavailable userspace logs.
* Improve eventpoll logging to stop indicting timerfd.
* Do not set 3V to voltage regulator of goodix fingerprint driver.
* Fix some compiler warnings.
* Remove CONFIG_USB_LAN78XX.
* Drop RKSU (KernelSU-legacy) by github.com/rsuntk in favor of XXKSU by github.com/Backslashxx to integrate scope-minimized manual KernelSU hooks v1.9.
* Pass netd_integration_test.
* Compile kernel using Android (AOSP) clang 22.0.0, based on r584948..

**v3.1 - 19/10/2025**
* Upstream zram to mainline.
* Increase zRAM size to 5GB.
* Report correct key code of headset buttons.
* Remove explicit warning on NULL pointer from fpsimd.
* Upstream KernelSU to rsuntk/KernelSU at commit 9a7c84bfbc1 which includes fix to kernel panic coming from fpsimd.
* Compile kernel using Android (AOSP) clang 20.0.0, based on r547379.

**v3.0 - 26/09/2025**
* Merge branch `upstream/rcu-5.10` into `redwood`.
* Merge branch `upstream/sched-6.1` into `redwood`.
* Upstream USB, mm, timer, ext4, f2fs to `linux v5.4.299`.
* Migrate to kmap_local_page() from kmap_atomic().
* Fix incorrect backport that made zram asynchronous.
* Upstream zsmalloc to mainline.
* Add Kcompressd for accelerated memory compression.
* Revert "mm: mmap: merge vma after call_mmap() if possible" patchset to fix potential memory corruption.
* Fix memory corruption in madvise caused by stale pte.
* Import various madvise fixes from mainline.
* Backport some GPU rice from msm-5.10.
* Upstream EEVDF to mainline.
* Enable fair group sched to minimize cold app launch time.
* Increase DVFS headroom boost multiplier to 1/4.
* Restore tasks affinity while moving across cpusets.
* Improve runtime of cpufreq_stats_create_table().
* Fix buffer overflow detection in trans_stats().
* Recalculate energy model for better accuracy.
* Partially upstream rtc-pm8xxx to msm-5.15 and mainline.
* Fix illegal RCU lock usage in handle_sepolicy() of KernelSU.
* Remove unnecessary RCU dereference in get_policydb() of KernelSU.
* Fix uninitialized mutex lock in ion.
* Fix uninitialized mutex lock in qcom-i2c-pmic.
* Fix various lockdep warnings.
* Fix a false-positive "RCU lock not being held" warning in sched.
* Fix illegal spinlock usage in camera.
* Enable various memory sensitive qcom loggers to mitigate potential memory corruption.
* Defer enabling IRQ in AOSS driver until QMP link is ready to prevent kernel panic caused by synchronous external abort.
* Switch to kvzalloc() for encoding and decodign QMI message to fix order-4 page allocation failures during modem restart.
* Switch to kvzalloc() for tethering stats collection to fix order-3 page allocation failure during prolonged period of USB tethering usage.
* Switch to kvzalloc() for read log ring buffer to fix a rare order-5 page allocation failure.
* Fix false-positive warning for device endpoint command timeouts from USB.
* Fix use-after-free in USB, ext4, f2fs, and crypto-qti.
* Replace collect_mounts()/drop_collected_mounts() with a safer variant.
* Fix OOB read in ext4, and qti-battery-charger.
* Partially upstream Incremental fs to android-mainline.
* Fix link startup failure for single-lane operation in ufs.
* Fix wild-memory-access in iommu.
* Fix PMD offset calculation for non-2M aligned start aperture in dma-mapping-fast.
* Fix various potential NULL pointer dereferences.
* Fix memory leak in USB dwc3-msm.
* Fix various warnings by smatch and clang.
* Add kernel-enforced timeout option for fuse server requests.
* Use freezable wait in fuse_get_req() and request_wait_answer().
* Implement charging status check in goodix touchscreen driver using querying USB_ONLINE property.
* Remove obsolete charging status check in focaltech 3680 touchscreen driver.
* Enable transition to LP2 for display since it's used by our video-mode panels.
* Disable LLVM's new noisy `builtin-wcslen` and `default-const-init-unsafe` warnings.
* Bring cosmetic changes to commit hash for localversion auto.
* Upstream KernelSU to rsuntk/KernelSU at commit 05b256639c3.
* Allow hardware updates of Access and Dirty page.
* Warn on NULL pointer before panicking from fpsimd.

**v2.1 - 17/07/2025**

* Fix kernel panic caused by kshrinkd by temporarily moving slab shrinkers out of kshrinkd and getting rid of it (until we get a solution).

**v2.0 - 16/07/2025**

* Rebase kernel on `LA.UM.9.14.r1-26100-LAHAINA.QSSI15.0` with wifi, audio, camera, dataipa, datarmnet, display, video driver from `LA.UM.9.14.r1-26000-LAHAINA.QSSI15.0`.
* Fix broken VoWiFi originating from fw-api.
* Redo old mm patchset.
* Fix build with GCC LTO that requires 4-way interleave using PMULL for crc32.
* Switch back to deep suspend since s2idle causes black screen of death and reboot when device enters deep sleep when battery is less than 5%.
* Set ssg's max available ratio back to 100 again.
* Enable UFS clock scaling.
* Fix timestamps on panic logs.
* Fix console-ramoops generation.
* Fix kernel panic caused by a race in __power_supply_changed_work().
* Fix kernel panic caused by subsystem crash.
* Fix stack depot reaching limit capacity by set __exception_irq_entry with __irq_entry as a default.
* Update lz4 to v1.10.0.
* Backport zsmalloc from mainline.
* Backport zram from mainline.
* Backport timer from linux-6.7.
* Upstream binder to android-mainline.
* Upstream EEVDF to mainline.
* Upstream scheduler to `android14-6.1`.
* Fix the usage of CPUFREQ_NEED_UPDATE_LIMITS in sched.
* Port tapered DVFS headroom from gs201 and fine-tune it.
* Disable big tasks rotation since it negatively affects the active load balancer.
* Fix tons of uninitialized variables, NULL pointer dereferences and OOB accesses in qcacld-3.0 and qcacmn.
* Add support for NCM USB tethering.
* Fix clkgating for ufs.
* Fix refount leaks in of/irq.
* Fix a deadlock in USB dwc3 core.
* Discard contiguous clusters in batches in exfat.
* Increase priority of glink worker thread.
* Avoid race for intent lock in glink.
* Fix various data races in swap code.
* Introduce __cma_alloc API to avoid prolonged stalls resulting from blocking pages.
* Remove __GFP_NORETRY flag from kgsl_system_alloc_pages.
* Fix system crash caused by KASAN with a dirty hack.
* Introduce Simple Low Memory Killer, fine-tune it and disable PSI.
* Rewrite goodix fingerprint driver to improve clarity and performance.
* Update rq stats way less frequently.
* Rework GPU target frequency calculation for high refresh rates to reduce overly aggresive frequency requests in some games.
* Use pipes rather than temporary files for intermediate steps.
* Disable cleancache since we don't have a proper backened or any usability.
* Upstream KernelSU to rsuntk/KernelSU at commit fea6b79743809.

**v1.1 - 14/03/2025**

* Reset CLO tag for fw-api to `LA.UM.9.14.r1-25500-LAHAINA.QSSI15.0` to fix VoWiFi.
* Add back necessary input listeners for Goodix touchscreen driver.
* Fix some GCC warnings.
* Disable unused L2TP.
* Upstream KernelSU to rsuntk/KernelSU.
* Switch to scope-minimized manual KernelSU hooks.
* Implement an LTO-specific version of READ_ONCE() that provides acquire semantics.
* Disable wakeup_irq if port is closed for msm_geni_serial.
* Add some missing mm reverts for PSI.
* Add support for Userfaultfd GC (ROM requires `ro.dalvik.vm.enable_uffd_gc=True` in system.prop).

**v1.0 - 04/03/2025**

* Rebase the kernel on the CLO tag `LA.UM.9.14.r1-25800-LAHAINA.QSSI15.0`.
* Add exFAT driver.
* Add a custom haptic_hv driver (thanks to Divyanshu-Modi).
* Debloat Wi-Fi drivers.
* Import Xiaomi changes while minimizing unnecessary code.
* Port the FocalTech 3680 touchscreen driver from ruby-s-oss.
* Debloat defconfig.
* Set Westwood as the default TCP congestion control algorithm.
* Set LZ4 as the default zram compression algorithm.
* Update dtc to upstream version `v1.7.0-60-g95c74d7`.
* Optimize various compiler-specific instructions.
* Fix all KASAN warnings.
* Fix multiple memory leaks.
* Optimize memory and string utility functions.
* Fix various compiler warnings.
* Improve graphics rendering performance.
* Switch to SBalance instead of msm_irqbalance.
* Backport Binder from msm-5.15.
* Add support for Fuse Passthrough.
* Set the default I/O scheduler to SSG.
* Add HPB driver for SK Hynix UFS variants (8/256 GB).
* Upstream UFS to msm-5.10.
* Update LZ4 to v1.9.4 with V8 ASM decompression acceleration.
* Upstream multiple Qualcomm OSS drivers (thanks to Divyanshu-Modi).
* Align inline encryption for UFS with the upstream version.
* Backport zsmalloc from mainline.
* Backport zram from mainline.
* Hardcode zram size to 4GB.
* Upstream uid_sys_stats to android-mainline.
* Optimize F2FS's garbage collector.
* Remove excessive debugging bloat.
* Fix and silence excessive spam in dmesg.
* Remove CAF's tracing from EXT4 and F2FS.
* Switch to stack memory and kmem cache usage in multiple drivers to minimize dynamic memory allocation.
* Mitigate msm-5.4's memory management issues.
* Backport scheduler from msm-5.15.
* Backport RCU from msm-5.10.
* Recalculate the energy model manually using CoreMark.
* Add Capacity Aware Superset Scheduler.
* Backport EEVDF from mainline.
* Set s2idle as the default sleep state instead of deep suspend.
* Enforce WFI idle state when the screen is on.
* Enable threaded NAPI for IPA.
* Add KernelSU-Legacy (fork by rsuntk), which is disabled by default in the repository.
