# Module 06 — ARM & Alternative Processor Platforms (Platform Prosesor ARM & Arsitektur Alternatif)

## 6.1 Paradigma Arsitektur ARM64 dalam Komputasi Laptop

```
====================================================================================
          PERBANDINGAN FUNDAMENTAL EKSEKUSI INSTRUKSI: x86-64 vs. ARM64
====================================================================================
  [x86-64 (Intel / AMD)]                        [ARM64 / AArch64 (Apple / Qualcomm)]
  Instruksi Panjang Variabel (1–15 Byte)        Instruksi Panjang Tetap (Tepat 4 Byte)
                 │                                              │
                 ▼                                              ▼
  ┌─────────────────────────────┐                ┌─────────────────────────────┐
  │   Complex Length Decoder    │                │   Parallel Fixed Decoder    │
  │ (Harus mencari batas akhir  │                │ (Batas tiap instruksi pasti │
  │  tiap instruksi secara      │                │  setiap 32-bit; mudah       │
  │  berurutan — boros daya)    │                │  diperlebar 8–10 wide)      │
  └──────────────┬──────────────┘                └──────────────┬──────────────┘
                 │ (Diterjemahkan ke micro-ops)                 │
                 ▼                                              ▼
  ┌─────────────────────────────┐                ┌─────────────────────────────┐
  │ Out-of-Order Execution Core │                │ Out-of-Order Execution Core │
  │ (ALU, FPU/SIMD, ROB, Cache) │                │ (ALU, NEON/SME, ROB, Cache) │
  └─────────────────────────────┘                └─────────────────────────────┘
```

Instruksi panjang tetap 32-bit pada **ARM64 (AArch64)** memungkinkan dekoder *front-end* diperlebar hingga 8–10 instruksi per siklus dengan daya jauh lebih rendah daripada x86-64, disertai 31 register tujuan umum. Keunggulan efisiensi ini terwujud penuh pada kode native ARM64, sedangkan aplikasi x86-64 memerlukan lapisan translasi biner (*Rosetta 2* atau *Windows Prism*).

---

## 6.2 Ekosistem Qualcomm Snapdragon Laptop (*Windows on ARM*)

| Keluarga Produk | Status Siklus Hidup | Arsitektur & Litografi | Susunan Core CPU (Oryon) | GPU Terintegrasi (Adreno) | NPU (Hexagon) | Memori & Lebar Pita |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Snapdragon X Elite** (`X1E-84-100`, `80-100`, `78-100`, `00-1DE`) | Current / Recent-Gen (2024–2026) | ARM64 (ARMv8.7-A), **TSMC N4P** (4nm) | **12 core Oryon** (3 kluster × 4 core), total cache **42 MB**, *Dual-Core Boost* hingga 4,2–4,3 GHz (kecuali `78-100`). | **Adreno X1-85** (hingga **4,6 TFLOPS** FP32 pada `84/80`, **3,8 TFLOPS** pada `78`). | **Hexagon NPU (45 TOPS INT8)** | **128-bit LPDDR5X-8448**, bandwidth **135 GB/s**, maks. 64 GB. |
| **Snapdragon X Plus** (`X1P-64-100`, `46-100`, `42-100`) | Current / Recent-Gen (2024–2026) | ARM64, **TSMC N4P** (4nm) | **10 core Oryon** (42 MB cache, maks. 3,4 GHz) atau **8 core Oryon** (30 MB cache). Tanpa *Dual-Core Boost*. | **Adreno X1-85** (3,8 TFLOPS) atau **Adreno X1-45** (2,1 / 1,7 TFLOPS). | **Hexagon NPU (45 TOPS INT8)** | **128-bit LPDDR5X-8448** (135 GB/s), maks. 64 GB. |
| **Snapdragon X (Entry)** (`X1-26-100`) | Current-Gen Value (2025–2026) | ARM64, **TSMC N4P** (4nm) | **8 core Oryon** (30 MB cache, maks. 3,0 GHz). | **Adreno X1-45** (1,7 TFLOPS FP32). | **Hexagon NPU (45 TOPS INT8)** | **128-bit LPDDR5X-8448** (135 GB/s). |
| **Snapdragon X2 Elite / X2 Series** | Announced / Emerging (2025–2026) | ARM64 (Oryon Gen-2/3), **TSMC N3P** (3nm) | Peningkatan jumlah core, IPC, dan efisiensi daya. | Arsitektur **Adreno generasi baru**. | **Hexagon NPU (~80 TOPS)** | Ditingkatkan untuk beban AI lokal generasi berikutnya. |

* **Ekosistem Windows on ARM**: Emulasi **Prism** menjalankan aplikasi x86-64 dengan cepat untuk produktivitas, tetapi tidak dapat memuat driver kernel x86 maupun sistem *kernel-level anti-cheat* gim kompetitif. Mendukung Hyper-V/WSL2 Linux ARM64 secara native. Di Linux, dukungan *Device Tree* upstream aktif pada kernel 6.11–6.18+ untuk model seperti *ThinkPad T14s Gen 6* dan *Dell XPS 13 9345*.

---

## 6.3 Ekosistem Apple Silicon (*macOS Unified Architecture*)

| Varian Tingkat Chip | Target Perangkat | Filosofi Arsitektur & Konfigurasi Core | Arsitektur Memori Terpadu (UMA) | Media Engine & Konektivitas |
| :--- | :--- | :--- | :--- | :--- |
| **Base (`M3`, `M4`, `M5`)** | *MacBook Air 13/15*, *MacBook Pro 14 (entry)* | Fokus efisiensi ekstrem & sasis tipis/fanless. **8–10 core CPU** (4P + 4–6E) dan **8–10 core GPU**. | Bus **128-bit LPDDR5 / LPDDR5X**; bandwidth **100–153 GB/s**; kapasitas **16–32 GB**. | 1× Video Encode/Decode Engine + 1× ProRes Engine; Thunderbolt 4. |
| **Pro (`M3 Pro`, `M4 Pro`, `M5 Pro`)** | *MacBook Pro 14 & 16* | Fokus throughput multi-core & portabilitas. Hingga **12–14 core CPU** (8–10P + 4E) dan **16–20 core GPU**. | Bus **192-bit** (M3 Pro, 150 GB/s) diperlebar menjadi **256-bit** pada M4/M5 Pro (**273 GB/s+**); kapasitas **24–64 GB**. | 1× Video Engine + 1× ProRes Engine; **Thunderbolt 5 (120 Gbps)** mulai M4 Pro. |
| **Max (`M3 Max`, `M4 Max`, `M5 Max`)** | *MacBook Pro 14 & 16* | Workstation mobile penuh. Hingga **16 core CPU** (12P + 4E) dan **32–40 core GPU**. | Bus **384-bit hingga 512-bit LPDDR5X**; bandwidth **400–546 GB/s+**; kapasitas **36–128 GB**. | **2× Video Encode Engine + 2× ProRes Engine**; **Thunderbolt 5**. |
| **Ultra (`M2 Ultra`, `M3 Ultra`)** | *Mac Studio / Mac Pro* *(Desktop)* | Menggabungkan dua die *Max* via **UltraFusion** (2,5 TB/s). Tidak digunakan di laptop. | Bus **1024-bit** (**800+ GB/s**); hingga **192–512 GB**. | **4× Video & ProRes Engines**. |

* **Teknologi Inti**: *Unified Memory Architecture (UMA)* (hingga 75%–85% RAM dapat dialokasikan ke GPU untuk LLM lokal), GPU *Dynamic Caching + Ray Tracing + Mesh Shading*, akselerator matriks CPU **ARM SME** (M4/M5), *Media Engines* ProRes/AV1, dan *Rosetta 2* (didukung mode pengurutan memori *TSO* x86 di perangkat keras).

---

## 6.4 MediaTek & Platform Prosesor Laptop Alternatif Global

1. **MediaTek Kompanio (`520, 838, 1380, Kompanio Ultra`)**: Produk ritel matang khusus ekosistem **ChromeOS / Chromebook Plus** berbasis inti ARM Cortex dan GPU Mali/Immortalis.
2. **Huawei HiSilicon Kirin PC (`Kirin 9006C / Kirin X90`)**: Produk komersial regional Tiongkok dengan inti kustom *Taishan* dan GPU *Maleoon* untuk sistem operasi **HarmonyOS Next for PC** dan Linux domestik (UOS/Kylin).
3. **Inisiatif SoC Laptop NVIDIA + MediaTek**: Platform ARM64 + GPU Blackwell + Tensor NPU (*Announced / Emerging 2025–2026*).
4. **Ekosistem Domestik Tiongkok**: **Loongson `3A6000`** (*LoongArch64*, 4C/8T *LA664*, emulasi biner x86 *LATX*), **Zhaoxin `KX-6000G / KX-7000`** (*x86-64*, hingga 8 core kompatibel native Windows/Linux), dan **Phytium `Tengrui D2000/D3000`** (*ARM64*).
5. **RISC-V Laptop Platforms (*DeepComputing DC-ROMA II* & *Framework Laptop 13 RISC-V Mainboard*)**: Perangkat pengembang/riset menggunakan SoC *SpacemiT K1* (8 core RV64GC + RVV 1.0) untuk pengujian Linux dan kompiler RISC-V native.
