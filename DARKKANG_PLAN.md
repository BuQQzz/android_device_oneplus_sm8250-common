# DarkKangOS 16.01 Development Plan

## Project Overview
**ROM Name:** DarkKangOS  
**Version:** 16.01  
**Base:** LineageOS 23.0 (Android 16)  
**Device:** OnePlus 8T (kebab)  
**Chipset:** Qualcomm SM8250 (Snapdragon 865)  
**GitHub:** BuQQzz/darkkang-* repositories  

## Design Philosophy
- **Performance First:** Evolution X performance optimizations as foundation
- **Smart Customization:** crDroid features for power users
- **Refined UI/UX:** Paranoid Android polish and aesthetics
- **Stability:** LineageOS 23.0 proven stable base

---

## Phase 1: Foundation (Current)
### 1.1 LineageOS Base Build ✅ In Progress
- [x] Sync LineageOS 23.0 source (1127 repos)
- [x] Configure OnePlus 8T device tree
- [x] Extract proprietary blobs via ADB
- [x] Fix Android.bp dependencies
- [x] Push vendor repos to GitHub
- [ ] Complete first successful LineageOS build
- [ ] Validate boot, basic functionality

### 1.2 Repository Setup
- [ ] Create vendor/darkkang directory structure
- [ ] Set up DarkKangOS branding files
- [ ] Create GitHub repos:
  - `BuQQzz/darkkang_vendor_darkkang`
  - `BuQQzz/darkkang_device_oneplus_kebab`
  - `BuQQzz/darkkang_kernel_oneplus_sm8250`

---

## Phase 2: Performance Base (Evolution X)
### 2.1 Research & Analysis
- [ ] Clone Evolution-X/vendor_evolution repository
- [ ] Analyze sm8250-specific optimizations
- [ ] Identify CPU governor tweaks
- [ ] Review memory management improvements
- [ ] Document Qualcomm-specific patches

### 2.2 Kernel Selection & Optimization
**Options:**
- **Kirisakura Kernel:** Known for balanced performance/battery
- **Clarity Kernel:** Aggressive performance tuning

**Tasks:**
- [ ] Test both kernels with LineageOS base
- [ ] Benchmark performance (AnTuTu, Geekbench)
- [ ] Monitor thermal behavior
- [ ] Select winner and fork to BuQQzz/darkkang_kernel_oneplus_sm8250
- [ ] Apply additional performance patches

### 2.3 Integration
- [ ] Cherry-pick Evolution X CPU optimizations
- [ ] Port memory management tweaks
- [ ] Integrate I/O scheduler improvements
- [ ] Add Qualcomm performance hints
- [ ] Configure build flags for performance

---

## Phase 3: Customization (crDroid)
### 3.1 Feature Analysis
**Target Features:**
- [ ] Status bar customizations
- [ ] Quick settings tiles management
- [ ] Lock screen options
- [ ] Navigation gestures
- [ ] Button remapping
- [ ] Display color profiles
- [ ] Sound customizations

### 3.2 Implementation
- [ ] Clone crdroid/android_vendor_crdroid
- [ ] Cherry-pick customization frameworks
- [ ] Adapt for DarkKangOS branding
- [ ] Test feature stability
- [ ] Document user-facing options

---

## Phase 4: UI/UX Refinement (Paranoid Android)
### 4.1 Visual Polish
- [ ] Clone AOSPA/android_vendor_aospa
- [ ] Analyze UI/UX improvements
- [ ] Port smooth animations
- [ ] Integrate refined color schemes
- [ ] Add custom fonts support

### 4.2 DarkKangOS Identity
- [ ] Design custom boot animation (dark theme)
- [ ] Create wallpaper pack
- [ ] Design system icons
- [ ] Set up custom sounds
- [ ] Configure default theme

---

## Phase 5: Integration & Testing
### 5.1 Vendor Configuration
**File Structure:**
```
vendor/darkkang/
├── config/
│   ├── common.mk
│   ├── version.mk
│   ├── packages.mk
│   └── props.mk
├── overlay/
│   ├── frameworks/
│   └── packages/
├── prebuilt/
│   ├── bootanimation/
│   ├── fonts/
│   └── media/
└── darkkang.mk
```

### 5.2 Build System
- [ ] Create `darkkang_kebab.mk` lunch combo
- [ ] Configure version string: "DarkKangOS 16.01"
- [ ] Set up OTA update framework
- [ ] Configure build properties

### 5.3 Testing Matrix
- [ ] Boot test
- [ ] WiFi/Bluetooth/NFC
- [ ] Camera (all sensors)
- [ ] Audio (speaker/headphone/mic)
- [ ] Display (refresh rate, color)
- [ ] Performance benchmarks
- [ ] Battery life test
- [ ] Thermal testing
- [ ] OTA update test

---

## Phase 6: Release Preparation
### 6.1 Documentation
- [ ] Create installation guide
- [ ] Write feature documentation
- [ ] Prepare changelog
- [ ] Set up bug reporting template
- [ ] Create XDA thread

### 6.2 Release Assets
- [ ] Build release version
- [ ] Generate recovery flashable ZIP
- [ ] Create fastboot images
- [ ] Calculate checksums (MD5/SHA256)
- [ ] Upload to GitHub releases

### 6.3 Community
- [ ] Post on XDA Forums
- [ ] Create Telegram group
- [ ] Set up GitHub Discussions
- [ ] Prepare support documentation

---

## Technical Specifications
### Build Environment
- **OS:** Ubuntu 24.04
- **CPU:** AMD Ryzen 3900X (24 threads)
- **RAM:** 31GB (upgrade to 64GB recommended)
- **Swap:** 47GB
- **Storage:** ~500GB for source + builds

### Device Support (Initial)
- OnePlus 8T (kebab)
- Future: OnePlus 8 Pro, 8, Nord series

### Version Strategy
- **16.01** - Initial release (Android 16, Jan 2025)
- **16.02** - February security + features
- **16.03** - March security + features
- Major updates follow Android version (17.01, etc.)

---

## Resource Links
### Source Repositories
- LineageOS: https://github.com/LineageOS
- Evolution X: https://github.com/Evolution-X
- crDroid: https://github.com/crdroidandroid
- Paranoid Android: https://github.com/AOSPA

### Device Resources
- OnePlus 8T Wiki: https://wiki.lineageos.org/devices/kebab/
- XDA Forums: https://xda-developers.com/c/oneplus-8t.11579/
- Kernel Sources: https://github.com/OnePlusOSS/android_kernel_oneplus_sm8250

### Build Resources
- AOSP Documentation: https://source.android.com/
- Soong Build System: https://android.googlesource.com/platform/build/soong/
- Repo Tool: https://gerrit.googlesource.com/git-repo/

---

## Current Status
**Last Updated:** October 30, 2025  
**Phase:** 1.1 - LineageOS Base Build  
**Blockers:** None  
**Next Steps:** Complete LineageOS base build, validate boot and functionality

---

## Notes
- RAM pressure during Soong analysis (~30GB/31GB) - consider incremental builds
- Some vendor blobs require manual ADB extraction (extract-files.sh incomplete for Android 16)
- GitHub repos use `lineage-23.0` branch for vendor blobs, will create `darkkang-16.01` branches for custom code
- Consider using `ccache` for faster incremental builds (requires ~100GB additional storage)
