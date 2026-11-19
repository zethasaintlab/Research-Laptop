# Module 16 — Personalized Scenario Analysis (Analisis Skenario Personal & Konfigurasi All-AMD)

## 16.1 Protokol Evaluasi Skenario 15 Langkah
1. Ekstraksi kebutuhan aktual (*workload* terukur) $\rightarrow$ 2. Identifikasi batasan mutlak (*hard constraints*) $\rightarrow$ 3. Identifikasi preferensi $\rightarrow$ 4. Identifikasi kompromi yang dapat diterima $\rightarrow$ 5. Penentuan kategori laptop $\rightarrow$ 6. Penentuan arsitektur perangkat keras $\rightarrow$ 7. Kebutuhan CPU $\rightarrow$ 8. Kebutuhan GPU $\rightarrow$ 9. Kebutuhan RAM & Storage $\rightarrow$ 10. Kebutuhan Layar $\rightarrow$ 11. Evaluasi Desain Termal $\rightarrow$ 12. Evaluasi Baterai & Portabilitas $\rightarrow$ 13. Evaluasi OS & Driver $\rightarrow$ 14. Identifikasi keterbatasan tersembunyi $\rightarrow$ 15. Perbandingan produsen & SKU nyata di pasar target.

---

## 16.2 Bedah Mendalam Konfigurasi *All-AMD*

| Tipe Konfigurasi | Arsitektur Silikon Nyata | Contoh Produk Representatif | Apakah Benar-Benar *All-AMD*? |
| :--- | :--- | :--- | :--- |
| **1. Monolithic APU-Only** | Satu keping silikon monolitik (*Ryzen AI 300* atau *Ryzen 8040*) berisi inti Zen 4/5, iGPU **Radeon 780M / 880M / 890M**, dan NPU XDNA. | *ASUS Zenbook S 16 (UM5606)*, *ThinkPad T14 / P14s AMD*, *Framework Laptop 13 (Ryzen AI 300)*. | **Ya (100% All-AMD)**. Paling matang untuk ultrabook, pemrograman, dan Linux harian. |
| **2. High-Bandwidth Mega-APU** | Paket chiplet **AMD Ryzen AI Max+ (*Strix Halo*)** memadukan hingga 16 core Zen 5 dengan iGPU **Radeon 8060S (40 CU)** di atas bus 256-bit LPDDR5X (256 GB/s). | *HP ZBook Ultra G1a 14*, *ASUS ROG Flow Z13 (GZ302)*. | **Ya (100% All-AMD)**. Puncak rekayasa laptop All-AMD untuk AI lokal & workstation ringkas. |
| **3. AMD CPU + AMD dGPU** | Prosesor AMD Ryzen dipasangkan dengan kartu grafis diskrit **AMD Radeon RX 7000M / 7000S Series** dan protokol **AMD SmartShift**. | *ASUS TUF Gaming A16 Advantage Edition (FA617NS — Ryzen 7 7735HS + RX 7600S)*, *Framework Laptop 16 (RX 7700S)*. | **Ya (100% All-AMD)**. Ditujukan untuk gaming penuh dengan tumpukan grafis murni AMD. |
| **4. AMD CPU + Non-AMD dGPU** | Prosesor AMD Ryzen dipasangkan dengan GPU diskrit **NVIDIA GeForce RTX 40/50 Series**. | *Lenovo Legion 5 / Pro 5 (Ryzen + RTX 5060/5070)*, *ASUS ROG Zephyrus G14/G16*. | **Tidak (Hibrida)**. Beban grafis 3D dan AI berat dikendalikan oleh silikon & driver NVIDIA. |

* **Audit Teknis All-AMD di Linux**: Memberikan kenyamanan kernel dan Wayland terbaik di industri (**100% open-source `amdgpu` + Mesa RADV + `amd_pstate=active`** tanpa friksi DKMS), namun memiliki kompromi pada ekosistem pelatihan AI **CUDA** (*ROCm* resmi terbatas pada GPU/Strix Halo tertentu) serta ketiadaan dekode video perangkat keras native **10-bit 4:2:2**.

---

## 16.3 Demonstrasi Skenario Teknis & Konteks Pasar Indonesia (IDR, November 2026)

**Profil Skenario**: *Pengembang perangkat lunak & insinyur jaringan/AI pengguna Linux (Wayland/Hyprland/Fedora/Arch) yang menjalankan kontainer/VM, AI lokal (LLM 7B–32B), dan gaming via Steam Proton.*

| Komponen | Rekomendasi Spesifikasi | Alasan Teknis (*Technical Reason*) |
| :--- | :--- | :--- |
| **Laptop Category** | *Creator / Thin-and-Light Performance Laptop* atau *Compact Workstation* | Keseimbangan pendinginan dua kipas dan mobilitas tanpa bobot >3 kg. |
| **CPU Platform** | **x86-64 Monolithic APU atau High-Bandwidth Chiplet APU (AMD Ryzen AI 300 / AI Max+)** | Kompatibilitas x86-64 penuh, virtualisasi KVM cepat, dan dukungan `amd_pstate=active`. |
| **CPU Class** | **8–16 Core Fisik Zen 5 / Zen 5c** (TDP 28W–54W+, mis. *Ryzen AI 9 HX 370* / *AI Max+ 395*) | *Single-core IPC* tinggi untuk IDE/kompilasi dan 24–32 thread untuk kontainer/VM. |
| **GPU** | **All-AMD iGPU Tinggi (*Radeon 890M* / *Radeon 8060S*)** atau ***Radeon RX 7600S/7700S*** *(Alternatif Hybrid: NVIDIA RTX 5060/5070 Ti)* | Stack `amdgpu` + Mesa RADV mulus di Wayland dan VKD3D-Proton; *Radeon 8060S* setara dGPU kelas menengah. |
| **RAM** | **Minimal 32 GB** (ideal **64 GB**) **LPDDR5X-7500/8000** atau **DDR5-5600 Dual-Channel** | Mencegah *swapping* pada Docker/VM dan memberi alokasi UMA memadai untuk LLM lokal. |
| **Storage** | **1 TB – 2 TB PCIe Gen 4.0 x4 NVMe SSD (Sel NAND TLC)** + slot M.2 kedua | Kecepatan baca/tulis acak tinggi tanpa degradasi khas QLC. |
| **Display** | **14–16 inci 16:10, WQXGA / 2.8K (2560×1600 / 2880×1800), 120 Hz+, 100% sRGB/DCI-P3** | Ruang vertikal luas untuk kode dan kepadatan piksel >215 PPI. |
| **Cooling & Battery** | **Dual-Fan + Vapor Chamber / PTM7950**; Baterai **70–90 Wh** + **USB-C PD 100W** | Performa berkelanjutan stabil dan daya tahan baterai portabel 8–12 jam. |
| **Operating System** | **Linux Modern (Fedora Workstation / Arch Linux / CachyOS)** kernel ≥ 6.12 & Mesa terkini | Dukungan penuh Zen 5, RDNA 3.5, dan protokol Wayland modern. |

### Lima Varian Produk & Realitas Distribusi Indonesia (IDR)
1. **Best Overall**: **ASUS Zenbook S 16 OLED (`UM5606WA` Ryzen AI 9 HX 370 / Radeon 890M / 32GB / 1TB / 16" 3K 120Hz OLED)** — *Marketplace/Distributor Ritel Indonesia*: **Rp 28.499.000 – Rp 32.199.900** (*ASUS Online Store Indonesia* untuk varian penyegaran `UM5606GA` Ryzen AI 9 465: **Rp 42.999.000**).
2. **Best Performance (All-AMD Mega-APU AI Lokal)**: **HP ZBook Ultra G1a 14 (`AY8J9AV` — Ryzen AI Max+ PRO 395 / Radeon 8060S / 256-bit UMA)** — *Katalog Pengadaan B2B/Indent Indonesia*: **Rp 64.400.000 – Rp 71.484.000**. *(Alternatif gaming hybrid AMD+NVIDIA resmi: **Lenovo Legion 5 15AKP10/15AGP11** Ryzen AI 7 + RTX 5060 115W OLED di kisaran **Rp 32.149.000 – Rp 34.089.000**)*.
3. **Best Value (All-AMD dGPU Gaming)**: **ASUS TUF Gaming A16 Advantage Edition (`FA617NS` — Ryzen 7 7735HS / RX 7600S 95W / 16GB / 512GB / 16" 165Hz 100% sRGB / 90 Wh)** — *Ritel Resmi Indonesia*: **Rp 17.999.000 – Rp 19.998.960**. *(Peringatan SKU: hindari varian `FA617NSR` dengan `Ryzen 7 7435HS` apabila membutuhkan daya baterai panjang karena chip `7435HS` tidak memiliki iGPU sehingga dGPU selalu menyala)*.
4. **Best Portability**: **GPD Pocket 4 (Ryzen AI 9 HX 370 / 32–64GB / 8,8" 144Hz / 770 g + modul KVM/RS-232)** — *Impor Paralel Marketplace Indonesia*: mulai **Rp 23.119.000** (tanpa garansi prinsipal lokal).
5. **Best Long-Term Ownership**: **Framework Laptop 13 / 16 (Ryzen AI 300)** (*impor mandiri*) atau **Lenovo ThinkPad T14 / P14s AMD** (*jalur B2B resmi Indonesia* kisaran Rp 22–32 juta; unit bekas ex-corporate Gen 1 Ryzen 5 PRO 4650U beredar di kisaran **Rp 6.300.000**).
