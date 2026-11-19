# Module 04 — Intel Processor Encyclopedia (Ensiklopedia Prosesor Intel)

## 4.1 Evolusi Arsitektur Laptop Intel (2023–2026)

```
[2023–2024: Monolitik Intel 7]         [Akhir 2023–2024: Multi-Tile]       [Akhir 2024–2025: Split Era]        [2025–2026: Unifikasi 18A]
  Core Gen 13 & Gen 14                   Core Ultra Series 1                 Core Ultra Series 2                 Core Ultra Series 3
  (Raptor Lake / Refresh)                (Meteor Lake)                       (Lunar Lake vs Arrow Lake)          (Panther Lake)
  • 1 Die Monolitik (Intel 7)            • 4 Tile via Foveros 3D             • 200V: Memory-on-Package (N3B)     • Intel 18A (RibbonFET+PowerVia)
  • P-Core (HT) + E-Core                 • Compute (Intel 4) + SoC (N6)      • 200H/HX: Chiplet Performa (N3B)   • Menggabungkan efisiensi 200V
  • Tanpa NPU (0 TOPS)                   • NPU 3 (~11 TOPS) + Arc Xe-LPG     • Tanpa Hyper-Threading di P-Core     + skalabilitas RAM 200H
                                                                                                                 • NPU 5 (50 TOPS) + Arc Xe3
```

## 4.2 Klasifikasi Keluarga Prosesor Laptop Intel

1. **Intel Core Ultra Series 3 — *Panther Lake* (Current-Generation Flagship, Akhir 2025–2026)**:
   * Desain *multi-tile* **Foveros 2.5D** menggunakan node **Intel 18A** (*RibbonFET + PowerVia*) pada *Compute Tile*.
   * Hingga **16 core / 16 thread**: 4× *Cougar Cove* P-core (tanpa HT) + 8× *Darkmont* E-core + 4× *Darkmont* LP-E core.
   * iGPU **Intel Arc Xe3-LPG** (*Celestial*, hingga 12 Xe3-cores pada *Arc B390*), **NPU 5 (50 TOPS INT8, mendukung FP8/INT4)**, dan kembali mendukung memori eksternal papan utama (**LPDDR5X hingga 9600 MT/s** atau **DDR5/LPCAMM2 hingga 7200 MT/s**).
2. **Intel Core Ultra Series 2 — *Lunar Lake (200V)* vs. *Arrow Lake (200H / 200HX / 200U)* (2024–2026)**:

| Dimensi Teknis | Core Ultra 200V (*Lunar Lake*) | Core Ultra 200H (*Arrow Lake-H*) | Core Ultra 200HX (*Arrow Lake-HX*) | Core Ultra 200U (*Arrow Lake-U*) |
| :--- | :--- | :--- | :--- | :--- |
| **Segmen Target** | Ultrabook ultra-tipis & *Copilot+ PC* (17W–30W). | Laptop kreator, tipis-gaming & performa (28W–45W). | Gaming *flagship* & *mobile workstation* (55W–160W+). | Laptop bisnis & produktivitas arus utama (15W–28W). |
| **Node Fabrikasi** | TSMC N3B + TSMC N6. | TSMC N3B + TSMC N5 + N6. | TSMC N3B + TSMC N6. | **Intel 3** (Arsitektur berbeda dari N3B). |
| **Susunan Core** | **4P** (Lion Cove, tanpa HT) + **4 LP-E** (Skymont) = **8C / 8T**. | Hingga **6P** + **8E** + **2 LP-E** = **16C / 16T**. | Hingga **8P** + **16E** = **24C / 24T**. | **2P** (Redwood Cove+, **dengan HT**) + **8E** + **2 LP-E** = **12C / 14T**. |
| **Arsitektur Memori** | **Memory-on-Package (MoP)**: 16 GB (`xx6V`) atau 32 GB (`xx8V`) LPDDR5X-8533 tersolder di paket chip. | Eksternal: DDR5-6400 atau LPDDR5X-8400 hingga 96–128 GB. | Eksternal: hingga 4 slot DDR5-6400 (maks. 192–256 GB), mendukung **ECC** (WM880). | Eksternal: DDR5-6400 atau LPDDR5X-8400 hingga 64–96 GB. |
| **iGPU & NPU** | **Arc 140V / 130V (Xe2)**; **NPU 4 (40–48 TOPS)** — Lolos Copilot+ PC. | **Arc 140T / 130T (Xe-LPG+)**; NPU 3 (13 TOPS). | Intel Graphics (4 Xe); NPU 3 (13 TOPS). | Intel Graphics (4 Xe); NPU 3 (12 TOPS). |

3. **Intel Core Ultra Series 1 — *Meteor Lake* (Akhir 2023–2024)**: Debut *Foveros 3D*, Intel 4 + TSMC N5/N6, hingga 6P + 8E + 2 LP-E (dengan HT), iGPU Arc Xe-LPG, NPU 3 (~11 TOPS).
4. **Intel Core (Non-Ultra) Series 1 & Series 2 (`120U, 150U, 210H, 240H, 270H`)**: Pembaruan (*refresh*) dari arsitektur monolitik **Raptor Lake (Intel 7)** tahun 2023 **tanpa NPU**.
5. **Intel Core Gen 13 & Gen 14 (`13xxx / 14xxx`, terutama seri `HX`) & N-Series (`N100, N200, Core i3-N305`)**: Seri `HX` membawa die desktop hingga 24 core / 32 thread ke laptop gaming/workstation; *N-Series* hanya berisi E-core hemat daya dengan memori *single-channel* untuk Chromebook dan laptop edukasi.

---

## 4.3 Dekode Penamaan & Kamus Sufiks Intel (2020–2026)

* **`V`**: Eksklusif untuk *Core Ultra 200V (Lunar Lake)* **Memory-on-Package** (`6V` = 16 GB RAM, `8V` = 32 GB RAM).
* **`U`**: *Ultra-low power* (9W–15W base) untuk ultraportabel dan bisnis harian.
* **`H`**: *High-performance* (28W–45W base) untuk laptop kreator dan gaming menengah.
* **`HX`**: *Desktop-in-Laptop* (55W+ base, turbo >130W) untuk gaming berat dan workstation ECC.
* **`HK` / `P` / `Y` / `G1-G7`**: Sufiks historis (*Legacy / Discontinued*) yang telah digantikan oleh skema modern.

## 4.4 Teknologi Silikon vs. Program Platform Intel
* **Fitur Silikon**: *Intel Hybrid Architecture & Thread Director*, *Turbo Boost Max 3.0 & Thermal Velocity Boost (TVB)*, *Intel Quick Sync Video* (akselerasi perangkat keras **10-bit 4:2:2** dan AV1), *Intel Arc Xe/Xe2/Xe3 + XMX*, *Intel AI Boost NPU*, *Dynamic Tuning (DTT)*, dan *Intel Boot Guard*.
* **Program Sertifikasi Platform**: **Intel Evo Edition** (standar pengalaman bangun instan <1,5 detik, baterai nyata, Thunderbolt, Wi-Fi 6E/7), **Intel vPro Enterprise/Essentials** (kombinasi CPU + PCH + Wi-Fi Intel yang mengaktifkan pengelolaan jarak jauh *out-of-band* **Intel AMT**), dan **Thunderbolt 4 (40 Gbps) / Thunderbolt 5 (80 Gbps simetris, 120 Gbps Bandwidth Boost)**.
