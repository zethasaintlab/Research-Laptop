# Module 15 — Cross-Platform Comparison & Decision Framework

## 15.1 Matriks Komparasi Enam Arsitektur Platform Laptop (2026)

| Dimensi Evaluasi | 1. x86-64 Ultraportable SoC *(Core Ultra 200V/S3, Ryzen AI 300)* | 2. x86-64 High-TDP + dGPU *(Core Ultra HX, Ryzen 9000HX + RTX 50)* | 3. x86-64 High-Bandwidth UMA *(AMD Ryzen AI Max+ / Strix Halo)* | 4. Apple Silicon UMA *(Apple M3 / M4 / M5 Base, Pro, Max — macOS)* | 5. Windows on ARM64 *(Qualcomm Snapdragon X / X2 — WoA)* | 6. Open-Hardware & ChromeOS *(Framework, System76, Chromebook)* |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **ISA & Topologi** | x86-64 Monolitik / Multi-Tile Efisiensi (15W–35W). | x86-64 Chiplet/Hibrida (45W–175W) + PCIe dGPU. | x86-64 Chiplet Mega-APU (45W–120W) + Bus 256-bit. | ARM64 Monolitik SoC + UMA 128-bit hingga 512-bit. | ARM64 Monolitik SoC + Bus 128-bit LPDDR5X. | x86-64 Modular (*Framework/Linux*) atau ARM64/x86 (*ChromeOS*). |
| **Performa Burst vs. Sustained** | Burst cepat; *sustained* dibatasi termal sasis (18W–28W). | *Sustained* tertinggi di industri bila pendingin memadai. | *Sustained* sangat kuat di sasis ringkas 13–16 inci. | Konsisten antara *burst* dan *sustained* (kecuali MacBook Air *fanless*). | Sangat responsif untuk tugas harian & kompilasi native ARM. | Bergantung penuh pada desain sasis (sangat tinggi pada *Framework 16*). |
| **Kinerja Grafis & AI Lokal** | iGPU kuat (*Arc 140V/B390*, *Radeon 890M*); NPU 45–50 TOPS. | **Tertinggi mutlak** untuk 3D, Ray Tracing, CUDA, & difusi AI. | iGPU *Radeon 8060S* setara RTX 4060/4070 + hingga **96 GB VRAM UMA**. | Akselerasi Metal/ProRes luar biasa; hingga **128 GB UMA** untuk LLM besar. | GPU Adreno memadai untuk produktivitas; NPU 45–80 TOPS efisien. | *Framework 16* mendukung modul GPU RTX 5070 / RX 7700S yang dapat diganti. |
| **Daya Tahan Baterai & Mode Baterai** | **10 – 16 jam**; performa mode baterai sangat terjaga. | **3 – 6 jam**; performa turun **40%–70%** saat kabel dicabut. | **7 – 11 jam**; penurunan mode baterai jauh lebih moderat. | **14 – 22 jam**; performa mode baterai **100% identik** dengan mode AC. | **12 – 18 jam**; performa mode baterai sangat konsisten. | 8–12 jam (*Framework 13*); 10–15 jam (*Chromebook*). |
| **Kompatibilitas Software & Gaming** | **100% Native** seluruh aplikasi x86 Windows/Linux & gim *anti-cheat*. | **100% Native** seluruh ekosistem gim PC, CAD, dan CUDA. | **100% Native** seluruh aplikasi x86 dan gim PC. | Native macOS + **Rosetta 2** sangat matang; katalog gim Windows terbatas. | Native ARM64 + emulasi **Prism**; kendala pada *kernel anti-cheat* & driver lama. | **100% Native Linux** (*Framework/System76*); *ChromeOS* terbatas aplikasi web/Android/Crostini. |
| **Kematangan Ekosistem Linux** | **Sangat Baik** (upstream `amd_pstate`/`intel_pstate`, Mesa/Xe). | **Baik–Sangat Baik** (membutuhkan pengelolaan PRIME/RTD3 pada dGPU NVIDIA). | **Sangat Baik** (100% stack terbuka `amdgpu` + Mesa RADV + ROCm). | Terbatas (*Asahi Linux* matang di M1/M2; M3–M5 belum lengkap). | Parsial (kernel 6.11+ mendukung model tertentu; akselerasi media belum penuh). | **Terbaik di Industri** (dukungan resmi vendor, skema terbuka, & LVFS). |
| **Upgradeability & Repairability** | Rendah–Menengah (RAM umumnya tersolder; SSD M.2 dapat diganti). | **Tinggi** (2–4 slot SO-DIMM/CSODIMM, 2–4 slot SSD, Wi-Fi modular). | Rendah pada RAM (256-bit wajib tersolder); SSD M.2 dapat diganti. | **Nol** (RAM & SSD tersolder permanen; biaya perbaikan tinggi). | Rendah (RAM tersolder; beberapa model memakai SSD M.2 2230). | **Skor 10/10** (*Framework*: mainboard, GPU, RAM, SSD, dan port dapat ditukar). |

---

## 15.2 Corong Keputusan Empat Tahap & 18 Dimensi Evaluasi

1. **Tahap 1 — Filter Mutlak (*Hard Constraints*)**: (1) *Workload*, (2) *Operating System*, (3) *Software & Driver Compatibility*.
2. **Tahap 2 — Arsitektur Komputasi & Memori**: (4) *CPU Architecture*, (5) *GPU Requirements*, (6) *Memory Requirements*, (7) *Storage Requirements*.
3. **Tahap 3 — Rekayasa Fisik, Ergonomi, & Ekosistem**: (8) *Display*, (9) *Cooling*, (10) *Battery Life*, (11) *Portability*, (14) *Driver Support*, (15) *Firmware Support*.
4. **Tahap 4 — Ekonomi & Siklus Hidup**: (12) *Upgradeability*, (13) *Repairability*, (16) *Budget*, (17) *Regional Availability*, (18) *Long-Term Ownership (5–7 Tahun)*.

---

## 15.3 Cetak Biru Konfigurasi untuk 18 Persona Pengguna

1. **Students**: 14" 16:10 IPS 100% sRGB, *Ryzen 5/7 U/HS / Core Ultra 5 / MacBook Air*, RAM **16 GB**, SSD 512 GB, baterai 55–65 Wh.
2. **Developers**: 14–16" 16:10/3:2, *Ryzen AI 7/9 / Core Ultra 7 H/S3 / M4-M5 Pro*, RAM **32 GB**, SSD 1 TB TLC, keyboard nyaman.
3. **Linux Enthusiasts**: *ThinkPad T14/P14s AMD, Framework 13/16, System76, TUXEDO*; iGPU AMD/Intel upstream + LVFS (`fwupd`) + kamera USB UVC.
4. **Linux Gaming Users**: *All-AMD (Radeon 890M/8060S/RX 7700S)* atau *NVIDIA RTX 5070 Ti (12GB) / 5080 (16GB)* dengan Mesa RADV / NVIDIA 560+ Explicit Sync.
5. **Windows Gaming Users**: *RTX 5060 / 5070 Ti / 5080 Laptop* ber-TGP penuh (115W–175W), MUX Switch / Advanced Optimus, layar 165–240 Hz VRR.
6. **Content Creators**: Layar terkalibrasi $\Delta E < 2$ (100% sRGB & DCI-P3/AdobeRGB), pembaca kartu SD UHS-II, RAM 32 GB, *ProArt P16 / MacBook Pro / Yoga Pro 9i*.
7. **Video Editors**: *Hardware Media Engine* dengan dekode/enkode **10-bit 4:2:2** (*MacBook Pro M-Max, Intel Quick Sync, NVIDIA RTX 50 9th-Gen NVENC*), dua SSD NVMe.
8. **3D Artists**: *NVIDIA RTX 5070 Ti / 5080 / RTX PRO Blackwell* (RT Cores + OptiX), VRAM ≥ 12–16 GB, RAM 64 GB, pendingin workstation.
9. **AI Developers (LLM Lokal)**: *MacBook Pro M4/M5 Max (64–128 GB UMA, 546 GB/s)*, *AMD Ryzen AI Max+ 395 (64–128 GB UMA, 256 GB/s)*, atau *RTX 5090 Laptop (24 GB GDDR7)*.
10. **Machine Learning Engineers**: *NVIDIA RTX 5080 (16 GB) / 5090 (24 GB)* (ekosistem CUDA/PyTorch/TensorRT), RAM 64 GB, SSD 2–4 TB TLC, Linux/WSL2.
11. **Researchers**: *AMD Ryzen 9 9955HX / AI Max+ 395* atau *Intel Core Ultra 9 285HX vPro* (instruksi **AVX-512 penuh** + opsi memori **ECC** 64–128 GB).
12. **Business Professionals**: *ThinkPad T14s/X1 Carbon, HP EliteBook, Dell Pro*; **Intel vPro / AMD PRO**, Discrete TPM 2.0, layar IPS matte 400 nits, garansi *on-site*.
13. **Frequent Travelers**: Bobot **0,95–1,25 kg**, charger universal USB-C PD GaN, baterai 60–75 Wh (*Zenbook S 14, ThinkPad X1 Carbon/X9, MacBook Air 13, LG Gram 14*).
14. **General-Purpose Users**: *IdeaPad Slim 5, Vivobook S, Swift Go*; RAM 16 GB, SSD 512 GB–1 TB, layar IPS/OLED 16:10.
15. **Battery Life Priority**: *MacBook Pro 14/16 (M4/M5), MacBook Air 15, Intel Core Ultra 200V (Lunar Lake), Qualcomm Snapdragon X* dengan baterai ≥ 70 Wh.
16. **Performance Priority**: *Desktop replacement* 16–18 inci (*Legion Pro 7i, ROG Strix SCAR 18, MSI Titan 18 HX, ThinkPad P16*), total daya 200W–250W+.
17. **Portability Priority**: *Acer Swift Blade 14 (799 g), ExpertBook B9 (990 g), ThinkPad X1 Carbon (~986 g), GPD Pocket 4 (770 g)*.
18. **Repairability Priority**: *Framework Laptop 13 / 16* (skor 10/10), *ThinkPad T14 / L14*, *HP EliteBook 840/860* (sekrup standar, RAM & Wi-Fi modular).
