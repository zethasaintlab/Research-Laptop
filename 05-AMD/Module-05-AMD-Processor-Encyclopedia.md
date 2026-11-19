# Module 05 — AMD Processor Encyclopedia (Ensiklopedia Prosesor AMD)

## 5.1 Evolusi Arsitektur Laptop AMD (2023–2026)

```
[2023: Transisi Zen 4]               [2024: Era AI & Zen 5]               [2025–2026: Diversifikasi Penuh]
  Ryzen 7040 (Phoenix)                 Ryzen 8040 (Hawk Point)              Ryzen AI 300 (Strix & Krackan Point)
  • Monolitik TSMC 4nm (Zen 4)         • Refresh Zen 4 + XDNA 1 (16 TOPS)   • Hibrida Zen 5 + Zen 5c + XDNA 2 (50 TOPS)
  • Radeon 780M (RDNA 3, 12 CU)        • Penamaan ulang jadi Ryzen 200      • Radeon 890M / 880M / 860M (RDNA 3.5)
  • XDNA 1 NPU (10 TOPS)                 Series pada 2025                   
                                                                            Ryzen AI Max+ 300 (Strix Halo)
  Ryzen 7045HX (Dragon Range)          Ryzen AI 9 HX 370 (Strix Point)      • Chiplet Mega-APU: 16C Zen 5 + 40 CU RDNA 3.5
  • Chiplet Desktop (2x CCD + IOD)     • Debut Zen 5 + XDNA 2 (50 TOPS)     • Bus Memori 256-bit LPDDR5X (256 GB/s)
  • Varian 7945HX3D (3D V-Cache)                                            
                                                                            Ryzen 9000HX (Fire Range)
                                                                            • 16C Zen 5 Chiplet + 9955HX3D (Gen-2 V-Cache)
```

## 5.2 Klasifikasi Keluarga Prosesor Laptop AMD

1. **AMD Ryzen AI Max & Ryzen AI Max+ Series — *Strix Halo* (Workstation & Mega-APU, 2025–2026)**:
   * Paket chiplet TSMC N4P dengan hingga **16 core penuh Zen 5 / 32 thread** (`AI Max+ 395`, 64 MB L3), iGPU raksasa **Radeon 8060S (40 CU RDNA 3.5)** setara dGPU RTX 4060/4070 Laptop, antarmuka memori **quad-channel 256-bit LPDDR5X-8000 (256 GB/s)** hingga 128 GB UMA (alokasi VRAM dinamis hingga 96 GB), dan NPU **XDNA 2 (50 TOPS)**.
2. **AMD Ryzen AI 300 Series — *Strix Point* & *Krackan Point* (2024–2026)**:
   * *Strix Point (`AI 9 HX 375 / HX 370 / 365`)*: Monolitik TSMC N4P dengan hingga **4× Zen 5 + 8× Zen 5c = 12 core / 24 thread**, iGPU **Radeon 890M (16 CU)** / **880M (12 CU)**, dan NPU **XDNA 2 (50–55 TOPS)**.
   * *Krackan Point (`AI 7 350 / AI 5 340 / 330`)*: 6 hingga 8 core Zen 5/5c, iGPU **Radeon 860M / 840M**, tetap mempertahankan NPU **XDNA 2 (50 TOPS)** untuk kelas harga terjangkau.
3. **AMD Ryzen 9000HX Series — *Fire Range* (Flagship Gaming & Workstation, 2025–2026)**:
   * Chiplet desktop Zen 5 hingga **16 core / 32 thread** (`Ryzen 9 9955HX` dan `9955HX3D` dengan **144 MB total cache** menggunakan 2nd-Gen 3D V-Cache yang ditempatkan di bawah CCD agar inti CPU bersentuhan langsung dengan heatsink). Tanpa NPU terintegrasi.
4. **Ryzen 7000, 8000, Ryzen 200 Series, Ryzen PRO, & Ryzen Z-Series**:
   * *Ryzen 200 Series (2025–2026)* (`Ryzen 9 270, Ryzen 7 260, Ryzen 5 240`): Penyegaran dari *Ryzen 8040 Hawk Point (Zen 4 + Radeon 780M + XDNA 1 16 TOPS)*.
   * *Ryzen PRO*: Varian bisnis dengan enkripsi memori penuh *AMD Memory Guard*, *AMD Shadow Stack*, dan pengelolaan *DASH*.
   * *Ryzen Z-Series (`Z1 Extreme, Z2 Extreme`)*: Ditala pada 9W–30W untuk *handheld PC* dan *UMPC hybrid*.

---

## 5.3 Dekode Penamaan & Teknologi Ekosistem AMD

* **Aturan Skema 4-Digit (`Ryzen 7 7840HS` vs. `7730U` vs. `7520U`)**: Digit pertama (`7` atau `8`) adalah tahun rilis; **digit ketiga menentukan arsitektur Zen sebenarnya** (`2` = Zen 2 lawas, `3` = Zen 3/3+, `4` = Zen 4).
* **Skema Modern**: `Ryzen AI [Tier] [HX] [3xx]` menandakan arsitektur **Zen 5 + XDNA 2 (50+ TOPS)**; `Ryzen AI Max+ 395` menandakan **Strix Halo 256-bit**; sedangkan `Ryzen 7 260` (tanpa kata *AI*) menandakan **Zen 4 refresh**.
* **Sufiks Daya**: `e` (~9W fanless), `U` (15W–28W), `HS` (35W–54W monolitik performa tinggi), `HX` pada `7045HX/9000HX` (55W+ chiplet desktop), sedangkan `HX` pada `Ryzen AI 9 HX 370` menandakan SKU monolitik tertinggi (12C + 16 CU).
* **Teknologi Kunci**: *Zen 5 IPC (+16% atas Zen 4, AVX-512 512-bit penuh)*, kesetaraan instruksi *Zen 5 + Zen 5c*, *XDNA 2 Spatial Dataflow (Block FP16)*, *Precision Boost 2 & Curve Optimizer*, *AMD SmartShift*, *Smart Access Memory (SAM)*, dan *STAPM*.
