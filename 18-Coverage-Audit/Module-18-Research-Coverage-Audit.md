# Module 18 — Research Coverage Audit (Audit Cakupan Riset & Dokumentasi Penutup)

## 18.1 Audit Status Penyelesaian Seluruh Modul (`Module 00` – `Module 18`)
Seluruh **19 modul** dalam peta jalan *Global Laptop Industry Research* telah diselesaikan 100% dan diverifikasi silang terhadap sumber primer per **November 2026**. Rincian status lengkap tercatat pada `RESEARCH_STATUS.md` dan `RESEARCH_INDEX.md`.

## 18.2 Inventaris Entitas yang Telah Diselidiki
- **22 Klasifikasi Kategori & Faktor Bentuk**: Mulai dari *Everyday/Consumer*, *Ultrabook (Intel Evo)*, *Gaming* (4 sub-kelas), *Creator*, *Mobile Workstation (ISV/ECC)*, *Business/Enterprise*, *Chromebook Plus*, *Fully-Rugged (IP66)*, *AI PC / Copilot+ PC*, *High-Capacity UMA AI Workstation*, hingga faktor bentuk *Convertible, Detachable, Dual-Screen, Foldable, Rollable, Modular, Fanless, Liquid-Cooled,* dan *UMPC Handheld-Laptop Hybrid*.
- **25+ Entitas ODM & OEM Global/Regional**: *Quanta, Compal, Wistron, Pegatron, Inventec, Huaqin, Wingtech, Clevo, Tongfang (Uniwill), Emdoor*, serta *Lenovo, ASUS, Dell (rebrand Dell/Pro/Pro Max), HP (konsolidasi OmniBook), Acer, Apple, MSI, Gigabyte, Razer, Samsung, LG, Microsoft, Framework, System76, TUXEDO, Slimbook, Star Labs, Panasonic, Getac, Huawei, Xiaomi, Honor, Mechrevo, XMG, GPD, OneXPlayer, DeepComputing, Axioo, Advan,* dan *Zyrex*.
- **12 Keluarga Platform Silikon**: *Intel Core Gen 13/14, Core Series 1/2, Core Ultra Series 1/2/3 (Panther Lake 18A), N-Series*; *AMD Ryzen 7000/8000/200, 7045HX, 9000HX (Fire Range), Ryzen AI 300 (Strix/Krackan Point), Ryzen AI Max+ (Strix Halo), Ryzen PRO, Z-Series*; *Apple Silicon M3–M5*; *Qualcomm Snapdragon X / X2*; *MediaTek Kompanio*; *HiSilicon Kirin PC*; *NVIDIA+MediaTek*; *Loongson, Zhaoxin, Phytium, RISC-V*; serta GPU *NVIDIA RTX 40/50 Laptop & RTX PRO Blackwell*, *AMD Radeon 700M/800M/8060S & RX 7000M/S*, dan *Intel Arc Xe/Xe2/Xe3 & Arc Pro*.

## 18.3 Transparansi Keterbatasan Data (`[INSUFFICIENT DATA]`)
1. **Ketersediaan Ritel & Harga IDR Pasca-Peluncuran Platform Terbaru Akhir 2026 (`[INSUFFICIENT DATA]`)**: Daftar SKU ritel final di Indonesia untuk *Core Ultra Series 3 (Panther Lake)* lini korporasi tertentu, *Snapdragon X2*, dan SoC *NVIDIA + MediaTek* masih menunggu rilis resmi distributor lokal.
2. **Component Lottery OEM**: Variasi pemasok SSD (*TLC vs QLC*), RAM (*1Rx8 vs 1Rx16*), kartu Wi-Fi, dan panel layar di dalam satu nomor model laptop mewajibkan verifikasi nomor bagian (*Part Number*) atau utilitas diagnostik (`hwinfo64` / `nvme-cli` / `dmidecode`).
3. **Peta Register Embedded Controller (EC) & ACPI Proprietari**: Dukungan kontrol kipas/profil daya pada kernel Linux untuk laptop konsumen yang berusia < 3 bulan berstatus *Unknown / Insufficient Evidence* hingga tabel DSDT/SSDT diaudit.
4. **Kematangan Driver Linux pada Apple M3–M5 & Snapdragon X Generasi Baru**: Masih dalam pengembangan aktif di *Asahi Linux* dan upstream *Device Tree* kernel.
5. **Fluktuasi Kurs & Pajak Impor Indonesia**: Seluruh referensi harga IDR mencerminkan kondisi pasar per **November 2026**.
6. **Tolok Ukur RDNA 4 Mobile Diskrit (`[INSUFFICIENT DATA]`)**: AMD memfokuskan RDNA 4 pada desktop dan mengandalkan *Strix Halo (Radeon 8060S)* pada laptop tipis-menengah selama 2025–2026.

## 18.4 Area Riset Lanjutan
1. Rekayasa balik firmware *Embedded Controller (EC)* dan protokol *open-firmware* (`coreboot` / `Chromium EC`).
2. Standar memori *JEDEC LPDDR6* dan pengendali *PCIe 6.0* berdaya rendah pada laptop generasi berikutnya.
3. Topologi bus audio *Sound Open Firmware (SOF)* dan ekstraksi koefisien kalibrasi *Smart Amplifier* di Linux.
4. Diagnostik telemetri residensi tidur paket `S0ix` (`PC10` / `S0i3`) pada desain multi-tile/chiplet.
5. Studi degradasi longitudinal baterai Li-Po dan material antarmuka termal (*PTM7950* vs *liquid metal*).
