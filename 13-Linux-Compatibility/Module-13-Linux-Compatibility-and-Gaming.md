# Module 13 — Linux Compatibility & Gaming (Kompatibilitas Perangkat Keras & Gaming di Linux)

## 13.1 Kompatibilitas CPU, Manajemen Daya, & Firmware Platform
* **Intel (`x86-64`)**: *Upstream First-Class Support* melalui `intel_pstate`, penjadwal hibrida `EEVDF` + *Intel Thread Director*, dan daemon termal `thermald`.
* **AMD (`x86-64`)**: Standar emas komunitas Linux melalui **`amd_pstate=active` (EPP/CPPC)** dan **`amd-pmf`**.
* **Qualcomm Snapdragon X (`ARM64`)**: Dukungan aktif via berkas **Device Tree (`.dtb`)** pada kernel 6.11–6.18+ (*ThinkPad T14s Gen 6, Dell XPS 13 9345*), namun akselerasi dekode video (*VPU*), audio *smart-amp*, dan tidur mendalam masih berkembang.
* **Apple Silicon (`ARM64`)**: Proyek **Asahi Linux** matang pada **M1 dan M2** (mendukung OpenGL 4.6 & Vulkan 1.3 via *Mesa Honeykrisp*), sementara generasi **M3, M4, dan M5** masih dalam pengembangan bertahap.
* **Suspend (`s2idle / S0ix` vs. `S3`) & Firmware (`LVFS / fwupd`)**: Laptop modern mengandalkan `s2idle` yang bergantung pada kebersihan tabel **ACPI DSDT/SSDT** agar seluruh perangkat masuk ke status `D3cold`. Gunakan satu daemon profil daya (`power-profiles-daemon`, `tuned`, atau `TLP`), pastikan `intel-ucode`/`amd-ucode` terpasang, dan utamakan laptop yang mendukung **LVFS (`fwupd`)**.

---

## 13.2 Tumpukan Grafis Linux & Subsistem Khusus Laptop

```
====================================================================================
             TUMPUKAN PERANGKAT LUNAK GRAFIS LINUX (LINUX GRAPHICS STACK)
====================================================================================
  [Aplikasi Desktop / Compositor Wayland (Hyprland, KWin, Mutter) / Gim Vulkan]
                                       │
         ┌─────────────────────────────┼─────────────────────────────┐
         ▼ (Jalur Sumber Terbuka Mesa) │                             ▼ (Jalur NVIDIA)
┌─────────────────────────┐            │            ┌─────────────────────────────┐
│   Mesa 3D User-Space    │            │            │  NVIDIA Proprietary User-   │
│ • RADV (AMD Vulkan)     │            │            │  Space (CUDA, OptiX, NVENC, │
│ • ANV (Intel Vulkan)    │            │            │  Vulkan, OpenGL, DLSS)      │
│ • NVK (NVIDIA Open VK)  │            │            └──────────────┬──────────────┘
│ • RadeonSI / Iris (GL)  │            │                           │
└────────────┬────────────┘            │            ┌──────────────┴──────────────┐
             │ (DRM / KMS / GBM)       │            ▼ (Open Kernel)               ▼ (Legacy)
┌────────────▼────────────┐ ┌──────────▼──────────┐ ┌──────────────────┐ ┌────────────────┐
│  amdgpu (Kernel Module) │ │ xe / i915 (Kernel)  │ │ nvidia-open.ko   │ │ nouveau.ko     │
└────────────┬────────────┘ └──────────┬──────────┘ └────────┬─────────┘ └───────┬────────┘
             ▼                         ▼                     ▼                   ▼
       [AMD Radeon]              [Intel Arc]              [NVIDIA GeForce / RTX PRO]
```

* **PRIME Render Offload, RTD3 (`D3cold`), & Wayland Explicit Sync**: Pada laptop hibrida NVIDIA, iGPU merender desktop sementara variabel `__NV_PRIME_RENDER_OFFLOAD=1` mendelegasikan gim ke dGPU. Pastikan **RTD3** mematikan dGPU (0W) saat tidak terpakai (hindari polling `nvidia-smi` terus-menerus). Protokol **Wayland Explicit Sync (`linux-drm-syncobj-v1`)** pada driver NVIDIA 555/560/570+ menghilangkan kedipan frame di XWayland.
* **Subsistem Papan Utama (*The Last Mile*)**:
  1. *Wi-Fi*: Intel (`iwlwifi` — AX210/BE200) paling stabil; Qualcomm (`ath11k/ath12k`) baik; MediaTek (`mt7921e/mt7925e`) & Realtek (`rtw89`) terkadang peka terhadap PCIe ASPM.
  2. *Audio Smart Amplifiers*: Chip penguat digital (*Cirrus Logic CS35L41*, *TI TAS2781*) membutuhkan *quirk* ACPI spesifik model di kernel Linux agar woofer menyala dan suara tidak cempreng.
  3. *Kamera Web*: Antarmuka **USB UVC** bekerja 100% *out-of-the-box*, sedangkan sensor **MIPI CSI-2 (`Intel IPU6/IPU7`)** memerlukan tumpukan `ipu6-drivers` + `libcamera` + `v4l2-relayd`.
  4. *Kontrol EC/WMI*: `thinkpad_acpi` / `LenovoLegionLinux`, `asusctl` (`asus-nb-wmi`), `acer-wmi` / `ec_sys`, dan `tuxedo-drivers`.

---

## 13.3 Ekosistem Linux Gaming & Kerangka Evaluasi 6 Tingkat

* **Steam Play / Proton, DXVK, & VKD3D-Proton**: *DXVK* menerjemahkan DirectX 8–11 ke Vulkan; *VKD3D-Proton* menerjemahkan DirectX 12 ke Vulkan (membutuhkan tambahan ~400 MB – 1 GB VRAM ekstra dibanding Windows). *Steam Shader Pre-Caching (Fossilize)* dan ekstensi Vulkan `VK_EXT_graphics_pipeline_library` (GPL) menghilangkan *shader stutter*, didukung **Gamescope**, **MangoHud**, dan **Feral GameMode**.
* **Batas Anti-Cheat Ring-0**: Modul *Easy Anti-Cheat (EAC)* dan *BattlEye* berjalan jika pengembang mengaktifkan dukungan runtime Linux; gim dengan driver anti-cheat kernel Windows Ring-0 (*Riot Vanguard, Ricochet, EA Javelin*) tidak dapat berjalan di Linux.
* **Kerangka Evaluasi 6 Tingkat**: (1) **Excellent** (*ThinkPad AMD, Framework, System76, Dell Developer Edition* — upstream penuh + LVFS), (2) **Good** (*ROG Zephyrus/Legion* dengan `asusctl`/`LenovoLegionLinux`), (3) **Partial** (*Snapdragon X* atau laptop kamera *IPU6*), (4) **Poor** (ACPI `s2idle` cacat & Wi-Fi tertutup), (5) **Unsupported** (bootloader terkunci), dan (6) **Unknown / Insufficient Evidence** (rilis baru < 3 bulan tanpa laporan `linux-hardware.org`).
