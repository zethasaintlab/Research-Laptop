# Module 14 — Specification Interpretation (Panduan Membaca & Membedah Lembar Spesifikasi Laptop)

## 14.1 Anatomi Audit 15 Parameter Lembar Spesifikasi
1. **Processor Name**: Dekode keluarga arsitektur, generasi silikon, SKU, dan sufiks (`Core Ultra 7 258V` = Lunar Lake 32GB MoP vs `Core 7 240H` = Raptor Lake tanpa NPU vs `Ryzen 7 7730U` = Zen 3).
2. **Core & Thread Count**: Periksa komposisi P/E/LP-E core serta apakah *Hyper-Threading/SMT* aktif (`Threads = 2 × Cores`) atau dinonaktifkan (`Threads = Cores`).
3. **GPU & TGP**: Untuk dGPU, wajib verifikasi kapasitas **VRAM**, tipe memori (**GDDR6 vs GDDR7**), dan batas daya **TGP (Watt)**.
4. **RAM**: Periksa kapasitas, kecepatan (MT/s), kanal (*dual/quad-channel*), dan faktor bentuk (*SO-DIMM / CSODIMM / LPCAMM2* vs *Soldered / MoP*).
5. **Storage**: Antarmuka (*PCIe 4.0/5.0 NVMe*), ukuran (*M.2 2280 vs 2242/2230*), dan jumlah slot ekspansi.
6. **Display**: Ukuran, rasio aspek (**16:10**), resolusi, panel (*IPS / Mini-LED / OLED*), cakupan warna (**100% sRGB / DCI-P3**), kecerahan (*nits*), *refresh rate*, dan VRR.
7. **Battery & Charging**: Kapasitas energi **Watt-hour (`Wh`)** dan daya adaptor (*USB-C PD* vs *Proprietary*).
8. **Weight & Dimensions**: Hitung bobot total perjalanan ($\text{Laptop} + \text{Adaptor}$).
9. **Ports & Wireless**: Protokol di balik USB-C (*USB4 40Gbps vs Thunderbolt 5 80/120Gbps*), **HDMI 2.1 FRL vs TMDS**, dan **Wi-Fi 7**.
10. **Thermal, MUX Switch, & Firmware**: Keberadaan *MUX Switch / Advanced Optimus*, material TIM (*PTM7950 / Liquid Metal*), dan chip keamanan *TPM 2.0 / vPro / PRO*.

---

## 14.2 Kamus Istilah Pemasaran yang Menyesatkan

| Istilah Pemasaran di Katalog / Toko | Realitas Teknis Sebenarnya | Dampak Nyata bagi Pembeli |
| :--- | :--- | :--- |
| **"AI-Powered / AI PC Ready"** *(kelas hemat)* | NPU lama 10–16 TOPS atau tanpa NPU sama sekali. | **Tidak memenuhi standar Copilot+ PC (40+ TOPS)**. |
| **"Up to 5.4 GHz Max Turbo Boost"** | Kecepatan puncak sesaat pada **1 inti CPU tunggal** (*Burst*). | Frekuensi beban penuh berkelanjutan turun ke 2,6–3,8 GHz. |
| **"NVIDIA GeForce RTX 5060 / 4070"** *(tanpa Watt)* | Pabrikan menyembunyikan nilai **TGP rendah (45W–65W)**. | Performa nyata **25%–35% lebih lambat** dibanding TGP penuh 115W–140W. |
| **"FHD Anti-Glare IPS-Level Display"** | Sering kali panel **TN/VA murah** dengan gamut **45% NTSC (~62% sRGB)**. | Warna kusam dan pudar; tidak layak untuk pekerjaan visual. |
| **"1 ms Response Time"** *(LCD murah)* | Mengacu pada **1 ms MPRT** via kedipan lampu latar (*backlight strobing*). | Kecerahan turun drastis dan tetap menyisakan *ghosting* fisik. |
| **"HDMI 2.1 Port"** *(tanpa keterangan FRL)* | Mengacu pada **HDMI 2.1 TMDS (18 Gbps / HDMI 2.0 lama)**. | Terbatas 4K 60Hz atau 4K 120Hz dengan kompresi warna 4:2:0. |
| **"MIL-STD-810H Military-Grade"** | Pabrikan memilih beberapa sub-uji ringan tanpa sertifikasi IP. | Tidak tahan air atau jatuh ke beton seperti laptop *fully-rugged* IP66. |

---

## 14.3 Empat Studi Kasus Bedah Spesifikasi Nyata (2025–2026)

1. **ASUS Zenbook S 14 (`UX5406` — Ultrabook Premium)**: *Core Ultra 7 258V (Lunar Lake, 32GB LPDDR5X-8533 MoP, Arc 140V, NPU 47 TOPS), 14" 3K 120Hz OLED, 72 Wh, 1,20 kg*. Unggul di baterai dan layar tajam 242 PPI; kompromi pada RAM tersolder permanen, batas termal sasis 1,19 cm (~17–22W), dan port `HDMI 2.1 TMDS` 18 Gbps (wajib pakai Thunderbolt 4 untuk monitor eksternal high-refresh).
2. **Lenovo Legion 5 / Pro 5 Gen 10 (Gaming Mainstream)**: *Ryzen 7 260 / Core Ultra 7 255HX, RTX 5060 8GB GDDR7 (TGP 115W penuh), 2× SO-DIMM DDR5, M.2 2242 + slot M.2 2280 kosong, 16" WQXGA 165–240Hz G-SYNC, 80 Wh, adaptor 245W*. Kinerja GPU penuh tanpa cekikan daya; SSD bawaan M.2 2242 berpotensi QLC sehingga slot kedua M.2 2280 ideal diisi SSD TLC.
3. **Lenovo ThinkPad P1 Gen 7 (Mobile Workstation Tipis)**: *Core Ultra 7 165H vPro, NVIDIA RTX 2000 Ada 8GB, 32GB LPCAMM2 LPDDR5X-7467 (upgradeable hingga 64GB), 16" WQXGA IPS 500nits, 90 Wh, 1,82 kg*. Memadukan modul RAM *LPCAMM2* cepat yang dapat di-upgrade dengan sertifikasi ISV dalam bobot ringan; menggunakan memori non-ECC dan TGP konservatif (~35W–60W).
4. **Laptop Budget Entry-Level Pasar Indonesia (Rp 6,5 – 8,5 Juta)**: *Ryzen 5 7520U (Zen 2 lawas 4-core), Radeon 610M, 8GB LPDDR5 tersolder, 14" TN 250nits 45% NTSC, 42 Wh*. Contoh jebakan penamaan: digit ketiga `2` menandakan silikon tahun 2019 dan RAM 8 GB tersolder membatasi umur pakai.
