# Module 17 — Glossary & Technical Reference (Glosarium & Referensi Teknis Terpadu)

## 17.1 Glosarium Arsitektur Silikon, CPU, & Pemaketan Chip
- **3D V-Cache**: Penumpukan vertikal cache SRAM L3 tambahan (64 MB per CCD) dengan ikatan tembaga langsung pada prosesor AMD Ryzen `X3D` untuk memangkas latensi memori gim.
- **Branch Prediction**: Sirkuit prediktor di *front-end* CPU yang menebak arah percabangan logika (`if/else`) sebelum evaluasi selesai guna mencegah *pipeline stall*.
- **Cache Hierarchy (`L1`, `L2`, `L3`, `SLC`)**: Tingkatan memori SRAM cepat di dalam chip dari pribadi tiap core (`L1`, `L2`) hingga bersama antar-core (`L3/LLC`) dan antar-subsistem SoC (`SLC`).
- **Chiplet / Multi-Tile Architecture**: Pemisahan fungsi silikon ke beberapa *die* terpisah dalam satu paket menggunakan *Intel Foveros/EMIB* atau *AMD Infinity Fabric*.
- **CPPC (Collaborative Processor Performance Control)**: Antarmuka ACPI untuk komunikasi peringkat efisiensi core dari firmware prosesor ke penjadwal kernel Linux (`amd_pstate`) dan Windows.
- **DVFS (Dynamic Voltage and Frequency Scaling)**: Penyesuaian tegangan dan frekuensi CPU ribuan kali per detik sesuai kebutuhan beban kerja.
- **Embedded Controller (EC)**: Mikrokontroler terpisah di *motherboard* yang mengatur keyboard, kurva kipas, pengisian baterai, dan sensor suhu sasis.
- **IPC (Instructions Per Clock)**: Rata-rata jumlah instruksi yang diselesaikan satu core CPU dalam satu siklus *clock*.
- **ISA vs. Microarchitecture**: **ISA** adalah kontrak set instruksi biner (*x86-64, ARM64, LoongArch64, RISC-V*), sedangkan **Microarchitecture** adalah rancangan fisik sirkuit eksekusinya (*Zen 5, Lion Cove, Cougar Cove, Oryon*).
- **NUMA (Non-Uniform Memory Access)**: Topologi di mana latensi akses memori bergantung pada jarak fisik antar-*chiplet* (CCD).
- **Out-of-Order Execution (OoOE)**: Eksekusi instruksi di urutan belakang lebih dulu saat instruksi di depan menunggu data memori.
- **P-Core, E-Core, & LP-E Core**: Pembagian inti hibrida antara performa latensi rendah (*P-Core*), efisiensi multi-thread (*E-Core*), dan pulau daya rendah terisolasi (*LP-E Core*).
- **RibbonFET & PowerVia**: Transistor *Gate-All-Around* dan penghantaran daya sisi belakang wafer pada node **Intel 18A**.
- **SMT / Hyper-Threading**: Eksekusi dua utas instruksi (*logical threads*) secara simultan pada satu inti CPU fisik.
- **Zen 5c**: Varian padat (*compact*) dari mikroarsitektur AMD Zen 5 dengan sel berkerapatan tinggi yang mempertahankan **100% kesetaraan set instruksi dan IPC** dengan Zen 5 standar.

## 17.2 Glosarium GPU, Tampilan, NPU, Memori, & Termal
- **MUX Switch & Advanced Optimus**: Sakelar perangkat keras yang menghubungkan output dGPU langsung ke layar internal tanpa melewati frame buffer iGPU (+5%–15% FPS).
- **TGP (Total Graphics Power) & Dynamic Boost**: Batas daya listrik maksimum (Watt) untuk subsistem dGPU, termasuk pergeseran daya dinamis 15W–25W dari CPU ke GPU.
- **UMA (Unified Memory Architecture)**: Satu kolam memori fisik bersama berkecepatan tinggi untuk CPU, GPU, dan NPU (*Apple Silicon, AMD Strix Halo*).
- **Tandem OLED & Mini-LED FALD**: Teknologi layar kontras tinggi; *Tandem OLED* menumpuk dua lapisan emisi organik untuk kecerahan ganda dan umur panjang, sedangkan *Mini-LED FALD* memakai ratusan-ribuan zona peredupan lokal LCD tanpa risiko *burn-in*.
- **PWM Dimming vs. DC Dimming**: Peredupan layar via kedipan cepat (*PWM*) vs penurunan arus halus (*DC*).
- **Roofline Model (`Compute-Bound` vs. `Memory-Bandwidth-Bound`)**: Kerangka analisis yang menunjukkan bahwa pengetikan token LLM lokal dibatasi oleh **lebar pita memori (GB/s)**, bukan angka TOPS NPU.
- **Quantization (`INT4`, `FP4`, `INT8`, `FP8`, `Block FP16`)**: Kompresi bobot model AI ke presisi bit lebih rendah agar muat di RAM/VRAM laptop.
- **CAMM2 & LPCAMM2 (`JEDEC JESD318`)**: Modul memori kompresi datar tipis yang menggabungkan kecepatan/efisiensi LPDDR5X dengan modularitas ganti-pengguna.
- **Memory Rank (`1Rx8` vs. `1Rx16`)**: Organisasi blok sel memori 64-bit; modul `1Rx16` memangkas paralelisme internal dan menurunkan performa 10%–15%.
- **TLC vs. QLC NAND & HMB**: Sel 3-bit (*TLC*, tahan lama & cepat kontinu) vs sel 4-bit (*QLC*, kecepatan anjlok setelah *pseudo-SLC cache* habis); *HMB* meminjam RAM sistem untuk tabel peta SSD *DRAM-less*.
- **Thunderbolt 5 / USB4 v2 (`PAM3`) & OCuLink**: *TB5/USB4 v2* menyediakan 80 Gbps dua arah (120 Gbps *Bandwidth Boost*) melalui USB-C; *OCuLink* menyediakan jalur mentah PCIe 4.0 x4 (64 Gbps) tanpa *hot-plug* dan tanpa daya.
- **Vapor Chamber, Liquid Metal, & PTM7950**: *Vapor chamber* menyebarkan panas 3D; *PTM7950* adalah material perubahan fase (~45°C) yang aman dari korsleting dan bebas *pump-out effect*.
- **Linux Stack (`amdgpu`, `xe`, `nvidia-open`, `Mesa RADV/ANV`, `DXVK`, `VKD3D-Proton`, `LVFS/fwupd`, `RTD3`, `s2idle`)**: Komponen inti kernel, driver vulkan ruang pengguna, lapisan translasi gim Windows, dan manajemen daya/firmware Linux.

## 17.3 Tabel Referensi Cepat Rumus Rekayasa Laptop

| Parameter yang Dihitung | Rumus Matematis Praktis | Contoh Perhitungan Nyata |
| :--- | :--- | :--- |
| **Kapasitas Energi Baterai (Wh)** | $\text{Wh} = \frac{\text{Kapasitas (mAh)} \times \text{Tegangan Nominal (V)}}{1000}$ | Baterai 4.500 mAh pada 15,4V (4-cell) = $\mathbf{69,3\text{ Wh}}$. |
| **Estimasi Daya Tahan Baterai (Jam)** | $\text{Jam} = \frac{\text{Kapasitas Baterai (Wh)}}{\text{Rata-rata Konsumsi Daya Sistem (W)}}$ | Baterai 72 Wh pada konsumsi rata-rata 5,5W $\approx \mathbf{13,1\text{ jam}}$. |
| **Lebar Pita Memori (GB/s)** | $\text{Bandwidth (GB/s)} = \frac{\text{Transfer Rate (MT/s)} \times \text{Lebar Bus (bit)}}{8000}$ | LPDDR5X-8533 pada bus 128-bit $\approx \mathbf{136,5\text{ GB/s}}$. |
| **Batas Kecepatan Token LLM (tok/s)** | $\text{Max tok/s} \approx \frac{\text{Memory Bandwidth (GB/s)}}{\text{Ukuran Model di Memori (GB)}}$ | Model 8B 4-bit (4,8 GB) di RTX 5080 (896 GB/s) $\approx \mathbf{186\text{ tok/s}}$ teoretis. |
| **Kerapatan Piksel Layar (PPI)** | $\text{PPI} = \frac{\sqrt{W_{\text{px}}^2 + H_{\text{px}}^2}}{\text{Ukuran Diagonal (inci)}}$ | Layar 14 inci `2880×1800` = $\mathbf{242,6\text{ PPI}}$. |
| **Jeda Antar-Frame Layar (ms)** | $\text{Frame Time (ms)} = \frac{1000}{\text{Refresh Rate (Hz)}}$ | Layar 120 Hz = **8,33 ms** per frame; 240 Hz = **4,17 ms**. |
