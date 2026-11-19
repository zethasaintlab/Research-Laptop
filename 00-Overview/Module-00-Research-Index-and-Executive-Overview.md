# Module 00 — Research Index & Executive Overview

## 1. Validasi Ruang Lingkup & Dimensi Tambahan (2023–2026)

Berdasarkan perkembangan nyata ekosistem komputasi bergerak hingga **November 2026**, ensiklopedia ini mengintegrasikan **tujuh dimensi kategori dan rekayasa teknis tambahan** di luar kerangka dasar:

1. **Handheld-Laptop Hybrids & Ultra-Mobile PCs (UMPC) Berkeyboard Fisik**: Perangkat seperti *GPD Win Max 2*, *GPD Pocket 4*, dan *OneXPlayer G1* yang memadukan layar 8–11 inci, kontroler gim terintegrasi, dan keyboard fisik penuh di atas APU x86-64 kelas laptop. Kategori ini mengaburkan batas antara konsol genggam (*handheld*) dan subnotebook.
2. **Workstation Inferensi AI Lokal Berbasis Memori Terpadu Kapasitas Masif (High-Capacity UMA AI Workstations)**: Munculnya perangkat berkapasitas RAM terpadu 64 GB hingga 192 GB (seperti *Apple MacBook Pro M-Max* dan sistem berbasis *AMD Ryzen AI Max+ / Strix Halo* dengan antarmuka memori 256-bit) yang secara khusus dirancang untuk memuat model bahasa besar (*Large Language Models* / LLM) lokal berparameter puluhan miliar secara penuh di memori tanpa bergantung pada VRAM GPU diskrit tradisional.
3. **Ekosistem Laptop Native-Linux & Open-Firmware OEM**: Produsen spesialis seperti *System76*, *TUXEDO Computers*, *Slimbook*, dan *Star Labs* yang merancang perangkat keras dengan dukungan *upstream kernel*, integrasi pembaruan firmware melalui *LVFS (Linux Vendor Firmware Service / fwupd)*, serta implementasi *coreboot* / *open-source Embedded Controller (EC)*.
4. **Arsitektur Keamanan Firmware & Hardware Root-of-Trust**: Implementasi *Intel Boot Guard*, *AMD Platform Security Processor (PSP)*, *Microsoft Pluton*, *Apple Secure Enclave*, serta implikasinya terhadap verifikasi integritas boot (*Secure Boot*), enkripsi disk penuh (*LUKS/BitLocker*), dan kemampuan pemasangan sistem operasi alternatif.
5. **Rekayasa Subpiksel Layar & Ergonomi Visual (Eye-Strain Engineering)**: Perbedaan struktur fisik subpiksel antara panel LCD *RGB Stripe* dan panel OLED laptop (*Diamond Pentile* vs *RGB Tandem OLED*), frekuensi *Pulse-Width Modulation (PWM)*, serta teknik *Frame Rate Control (FRC)* (8-bit + FRC vs 10-bit sejati) yang berdampak langsung pada ketajaman rendering teks pemrograman dan kelelahan mata.
6. **Standar Memori Modular Generasi Baru (JEDEC CAMM2 & LPCAMM2)**: Transisi industri dari modul *SO-DIMM* tradisional dan RAM tersolder (*soldered LPDDR5X*) menuju modul kompresi tipis *LPCAMM2* yang menggabungkan efisiensi daya dan lebar pita LPDDR5X dengan kemampuan penggantian oleh pengguna.
7. **Interkoneksi Eksternal Berlatensi Rendah (OCuLink & USB4 v2 / Thunderbolt 5)**: Penggunaan antarmuka *OCuLink (PCIe 4.0 x4, 64 Gbps)* pada laptop tipis dan *mini-workstation* untuk menghubungkan GPU eksternal (eGPU) tanpa hambatan *overhead* enkapsulasi protokol yang ditemukan pada Thunderbolt 3/4 dan USB4 40 Gbps.

---

## 2. Pemetaan Global Industri Laptop (Global Industry Mapping)

Peta ekosistem industri laptop global per **November 2026** diklasifikasikan ke dalam delapan domain utama:

| Domain Ekosistem | Entitas, Arsitektur & Klasifikasi Kunci | Status & Posisi Industri (2023–2026) |
| :--- | :--- | :--- |
| **1. Kategori Produk Utama** | Clamshell Tradisional, Ultrabook / Thin-and-Light, Gaming (Thin & Full-Power), Creator, Mobile Workstation, Business / Enterprise, Education / Chromebook, 2-in-1 Convertible, Detachable, Dual-Screen, Foldable Display, Rollable Display, Modular / Repairable, Rugged / Industrial, ARM-based Laptop, AI PC, UMPC / Handheld Hybrid. | Multidimensi; satu SKU fisik umumnya melintasi 2–4 kategori sekaligus. |
| **2. Arsitektur Set Instruksi (ISA)** | **x86-64** (CISC-front-end / RISC-like micro-ops), **ARM64 / AArch64** (RISC), **LoongArch64** (RISC independen Tiongkok), **RISC-V** (RV64GC — tahap pengembang). | x86-64 mendominasi segmen korporasi & gaming; ARM64 tumbuh pesat di ultraportabel & efisiensi baterai. |
| **3. Vendor Prosesor (CPU / SoC)** | **Intel** (Core, Core Ultra Series 1/2/3), **AMD** (Ryzen 7000/8000/9000HX, Ryzen AI 300, Ryzen AI Max), **Apple** (M3, M4, M5 series), **Qualcomm** (Snapdragon X, X Plus, X Elite, X2), **MediaTek** (Kompanio), **Huawei HiSilicon** (Kirin seri PC), **Zhaoxin** (KX-7000), **Loongson** (3A6000). | Kompetisi arsitektur heterogen (P-core + E-core) dan desain berbasis *chiplet/tile* menjadi standar utama. |
| **4. Vendor Grafis (iGPU & dGPU)** | **NVIDIA** (GeForce RTX 40 & RTX 50 Laptop, RTX Ada & Blackwell Workstation), **AMD** (Radeon 700M/800M/8060S iGPU, Radeon RX 7000M/S & Radeon Pro), **Intel** (Arc Xe-LPG, Xe2-LPG, Xe3 iGPU & Arc Pro), **Apple** (Custom GPU), **Qualcomm** (Adreno), **ARM** (Mali/Immortalis). | iGPU kelas atas (Radeon 890M/8060S, Arc 140V/B390) mulai menggantikan dGPU kelas pemula (entry-level). |
| **5. Akselerator AI (NPU & Tensor)** | **Intel AI Boost**, **AMD XDNA / XDNA 2**, **Qualcomm Hexagon NPU**, **Apple Neural Engine**, **NVIDIA Tensor Cores** (FP8/FP4), **MediaTek APU**. | Terjadi pemisahan fungsi: NPU untuk inferensi latar belakang hemat daya, GPU/UMA untuk LLM & difusi berat. |
| **6. Manufaktur Merek (OEM)** | **Global Tier-1**: Lenovo, HP, Dell, Apple, ASUS, Acer, MSI, Gigabyte, Razer, Samsung, LG, Microsoft.<br>**Regional & Spesialis**: Framework, Huawei, Xiaomi, Honor, Dynabook, Panasonic, Getac, System76, TUXEDO, Mechrevo, XMG/Schenker, Axioo, Advan, Zyrex. | Konsolidasi desain premium di Tier-1, sementara inovasi modularitas dan harga agresif dipimpin OEM spesialis & regional. |
| **7. Manufaktur Desain Asli (ODM)** | **Volume Utama**: Quanta Computer, Compal Electronics, Wistron, Pegatron, Inventec, Huaqin, Wingtech.<br>**Enthusiast / White-Label**: Clevo, Tongfang (Uniwill), Emdoor. | Sebagian besar laptop global dirancang dan dirakit oleh ODM di Taiwan dan Tiongkok sebelum diberi merek oleh OEM. |
| **8. Teknologi Kunci 2023–2026** | Litografi EUV 3nm/4nm/Intel 18A, pengemasan *Foveros* / *EMIB* / *CoWoS*, layar *Tandem OLED* & *Rollable OLED*, *LPCAMM2*, *Vapor Chamber + Liquid Metal / PTM7950*, Wi-Fi 7, Thunderbolt 5 / USB4 v2. | Fokus bergeser dari sekadar peningkatan frekuensi *clock* menuju efisiensi *performance-per-watt* dan kepadatan termal. |

---

## 3. Tujuan dan Filosofi Riset
Ensiklopedia teknis ini dirancang untuk menjembatani kesenjangan antara **terminologi pemasaran konsumen** dan **realitas rekayasa perangkat keras komputer bergerak**. Dalam industri laptop modern, label seperti *"Core i7"*, *"Ryzen 9"*, *"RTX 4070"*, atau *"AI PC"* tidak lagi merujuk pada satu tingkat performa yang seragam. Dua laptop dengan label prosesor dan GPU yang identik di atas kertas dapat menunjukkan selisih performa berkelanjutan (*sustained performance*) hingga **35%–55%** akibat perbedaan batas daya termal (*TDP/TGP*), desain pendingin, konfigurasi lebar pita memori, dan manajemen daya firmware (*Embedded Controller*).

## 4. Prinsip Pemisahan Fakta Teknis vs Pemasaran
Sepanjang seluruh modul dalam ensiklopedia ini, setiap evaluasi perangkat keras menerapkan lima aturan pemisahan analitis:
1. **Branding vs Desain Silikon (Silicon Die)**: Nama seri pemasaran dipisahkan secara tegas dari arsitektur mikro inti (*microarchitecture*) dan node fabrikasi yang digunakan di dalam kemasan chip.
2. **Performa Puncak Sesaat (Burst) vs Performa Berkelanjutan (Sustained)**: Performa dalam 10–30 detik pertama (*PL2/Tau* pada Intel atau *PPT Slow/Fast* pada AMD) dipisahkan dari kemampuan sasis membuang panas secara kontinu selama beban kerja berjam-jam.
3. **Spesifikasi Nominal GPU vs Batas Daya TGP**: Model GPU diskrit mobile dievaluasi bersama alokasi daya listriknya (*Total Graphics Power*), lebar bus memori, dan jalur koneksi layar (*MUX Switch / Advanced Optimus*).
4. **Kapasitas Baterai (Wh) vs Efisiensi Sistem Idle/Beban Ringan**: Daya tahan baterai tidak ditentukan oleh kapasitas *Watt-hour* semata, melainkan oleh konsumsi daya terendah pada kondisi beban ringan (*C-states*, efisiensi *display self-refresh*, dan daya *uncore/SoC*).
5. **Angka NPU TOPS vs Kinerja Beban Kerja AI Nyata**: Kemampuan akselerasi AI lokal dibedakan antara tugas inferensi ringan berdaya rendah di NPU dengan tugas berat yang dibatasi oleh *memory bandwidth* (seperti eksekusi LLM lokal dan generasi gambar).

## 5. Status Ketersediaan Produk dalam Kerangka Temporal (2023–2026)
Setiap produk dan teknologi yang dibahas diklasifikasikan ke dalam enam status siklus hidup:
* **Current-Generation (Generasi Aktif 2025–2026)**: Produk yang aktif dipasarkan pada periode riset (mis. *Intel Core Ultra Series 2 & Series 3*, *AMD Ryzen AI 300 / AI Max 300 / 9000HX*, *Apple M4 & M5*, *Qualcomm Snapdragon X / X2*, *NVIDIA RTX 50 Series Laptop*).
* **Recent-Generation (Generasi Terkini 2023–2024)**: Produk yang masih beredar luas di pasar ritel maupun pasar sekunder dan tetap relevan secara teknis (mis. *Intel Core Gen 13/14*, *Core Ultra Series 1*, *AMD Ryzen 7000/8000*, *Apple M3*, *NVIDIA RTX 40 Series Laptop*).
* **Legacy (Generasi Terdahulu Pra-2023)**: Arsitektur acuan untuk memahami evolusi sejarah (mis. debut arsitektur hibrida *Intel Alder Lake Gen 12*, *AMD Ryzen 5000/6000*, *Apple M1/M2*).
* **Announced / Paper-Launched**: Platform yang telah diumumkan secara resmi oleh vendor semikonduktor atau OEM, namun unit ritelnya belum tersedia secara luas untuk konsumen.
* **Experimental / Proof-of-Concept**: Prototipe pameran teknologi (seperti konsep layar gulung awal sebelum komersialisasi atau laptop berbasis RISC-V tahap awal).
* **Discontinued**: Lini produk yang produksinya telah dihentikan oleh pabrikan.

## 6. Konteks Pasar Global vs Ekosistem Indonesia
Analisis pasar tidak hanya mengacu pada ketersediaan di Amerika Utara, Eropa, atau Tiongkok, tetapi juga menyertakan realitas distribusi di **Indonesia**:
* **Diferensiasi SKU Regional**: Produsen global sering memasukkan konfigurasi layar, kapasitas baterai, atau kapasitas RAM yang berbeda untuk pasar Asia Tenggara dibandingkan pasar Amerika Utara (misalnya varian dengan panel NTSC 45% pada lini *entry-level/budget* yang tidak dijual di Eropa Barat).
* **Struktur Distribusi & Garansi**: Di Indonesia, produk terbagi menjadi **unit resmi bergaransi prinsipal** (memiliki sertifikasi Postel/Kominfo dan layanan purnajual lokal seperti *ASUS Indonesia, Lenovo Indonesia, Acer Indonesia, HP Indonesia, Apple Authorized Reseller*) dan **unit impor non-resmi / distributor paralel** (sering ditemukan pada merek seperti *Framework, Razer, System76, Mechrevo*, atau konfigurasi RAM/GPU tertinggi yang tidak dimasukkan secara resmi oleh distributor lokal).
