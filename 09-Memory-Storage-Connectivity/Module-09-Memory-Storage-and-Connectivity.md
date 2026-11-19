# Module 09 — Memory, Storage & Connectivity (Memori, Penyimpanan & Konektivitas)

## 9.1 Arsitektur RAM & Faktor Bentuk Fisik

```
====================================================================================
               EVOLUSI FAKTOR BENTUK FISIK RAM LAPTOP (JEDEC STANDARDS)
====================================================================================
  [1. SO-DIMM / CSODIMM]           [2. LPCAMM2 / CAMM2]          [3. Soldered / MoP]
  ┌─────────────────────┐          ┌─────────────────────┐       ┌─────────────────┐
  │  Slot Miring/Tumpuk │          │ Modul Datar Sekrup  │       │ Chip BGA di PCB │
  │  (Tinggi ~3.8-4 mm) │          │  (Tinggi ~1.5 mm)   │       │  atau Paket CPU │
  └─────────────────────┘          └─────────────────────┘       └─────────────────┘
  • Upgradeable (2 slot)           • Upgradeable (1 modul)       • Tidak bisa upgrade
  • Jalur tembaga panjang          • Jalur pendek = 8533+ MT/s   • Jalur terpendek
  • CSODIMM tambah chip CKD        • Efisiensi daya LPDDR5X      • Daya paling irit
```

* **Generasi Memori**: Transisi dari **DDR4** (3200 MT/s) ke **DDR5** (4800–6400+ MT/s dengan sub-kanal ganda 2×32-bit per modul dan **CSODIMM** berchip *Client Clock Driver* untuk kecepatan 6400 MT/s) serta **LPDDR5X** (7467–9600 MT/s) menuju standar masa depan **LPDDR6**.
* **Standar Modular Baru JEDEC `JESD318` (CAMM2 & LPCAMM2)**: Modul kompresi datar yang memangkas ketebalan vertikal 57% dibanding SO-DIMM sekaligus menyatukan lebar bus 128-bit penuh dan kecepatan LPDDR5X dengan kemampuan penggantian oleh pengguna.
* **Jebakan Memory Rank (`1Rx8` vs. `1Rx16`)**: Modul murah `1Rx16` (4 chip DRAM 16-bit per keping) memiliki jumlah *bank groups* internal setengah dari modul `1Rx8` (8 chip 8-bit), menurunkan performa CPU/iGPU dalam gim dan beban sensitif memori sebesar **10%–15%**.

---

## 9.2 Subsistem Penyimpanan (Storage Architecture)

* **Antarmuka & Ukuran**: **PCIe 4.0 x4 NVMe** (~7.400 MB/s) sebagai standar emas dan **PCIe 5.0 x4 NVMe** (~14.000+ MB/s) pada kelas flagship; ukuran fisik **M.2 2280**, **M.2 2242 / 2230**, serta penyimpanan tersolder **BGA NAND** (pada Apple MacBook).
* **Teknologi Sel NAND (`SLC`, `MLC`, `TLC`, `QLC`)**: **TLC** (3 bit/sel) menawarkan daya tahan tulis tinggi (600–1.200 TBW per 1 TB) dan kecepatan tulis berkelanjutan stabil (1.000–3.500+ MB/s). Sebaliknya, SSD **QLC** (4 bit/sel, 16 tingkat tegangan) mengandalkan *pseudo-SLC cache* sementara; begitu menyalin file besar atau kapasitas terisi >75%, kecepatan tulisnya anjlok ke **80–160 MB/s**.
* **DRAM Cache vs. HMB (*Host Memory Buffer*) & SSD Thermal Throttling**: SSD *DRAM-less* modern meminjam 32–64 MB RAM sistem via PCIe (HMB) untuk menyimpan peta alamat FTL. SSD PCIe 4.0/5.0 kencang membutuhkan *thermal pad* ke sasis agar pengendali tidak mengalami *thermal throttling*.

---

## 9.3 Konektivitas, Ekspansi Eksternal, & Jaringan Nirkabel

| Parameter Teknis | Thunderbolt 4 / USB4 (40 Gbps) | Thunderbolt 5 / USB4 v2 (80 Gbps) | OCuLink (*SFF-8611 / SFF-8612*) |
| :--- | :--- | :--- | :--- |
| **Arsitektur Sinyal** | Protokol terenkapsulasi di atas lapisan fisik USB-C. | Sinyal **PAM3** terenkapsulasi di atas lapisan fisik USB-C (hingga **120 Gbps Bandwidth Boost**). | **Koneksi PCIe 4.0 x4 mentah langsung (*raw PCIe*)** tanpa lapisan enkapsulasi protokol. |
| **Lebar Pita PCIe Nyata** | Dibatasi efektif pada **~22–32 Gbps** (~2,8–3,8 GB/s). | Hingga **~64 Gbps** lebar pita data PCIe. | **64 Gbps penuh** (~7,8 GB/s dengan latensi sangat rendah). |
| **Penalti Performa eGPU** | Kehilangan kinerja GPU kelas atas sebesar **20%–35%**. | Penalti berkurang signifikan menjadi **8%–15%**. | Penalti minimal (**5%–10%**). |
| **Hot-Plug & Daya** | Mendukung *hot-plug* penuh & pengisian daya hingga **100W–240W**. | Mendukung *hot-plug* penuh & pengisian daya hingga **240W**. | **Tidak mendukung hot-plug** (wajib mati/tidur saat cabut-pasang) & **0 Watt** daya. |

* **Konektor Fisik vs. Protokol**: **USB-C** hanyalah bentuk colokan 24-pin; periksa dukungan **DisplayPort Alt Mode**, **USB Power Delivery**, dan **USB4 / Thunderbolt**. Demikian pula bedakan **HDMI 2.1 FRL (48 Gbps sejati)** dari **HDMI 2.1 TMDS (18 Gbps / HDMI 2.0 lama)**.
* **Wi-Fi 7 (IEEE 802.11be) & CNVi**: Mendukung kanal **320 MHz** (pita 6 GHz), **4096-QAM**, dan **MLO (Multi-Link Operation)**. Waspadai kartu Wi-Fi Intel berkode **CNVi (`AX201, AX211, BE201`)** yang hanya berfungsi pada prosesor Intel, berbeda dengan kartu PCIe standar (`BE200, AX210, MT7925, NCM865`).
