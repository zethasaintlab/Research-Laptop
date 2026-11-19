# Module 10 — Display, Battery & Thermal Engineering (Rekayasa Layar, Baterai & Termal)

## 10.1 Rekayasa Teknologi Layar (Display Engineering)

```
====================================================================================
           PERBANDINGAN ARSITEKTUR FISIK PANEL LAYAR LAPTOP MODERN
====================================================================================
  [1. LCD Konvensional (IPS/VA/TN)]    [2. Mini-LED LCD]          [3. Self-Emissive OLED]
  ┌───────────────────────────────┐  ┌─────────────────────────┐  ┌─────────────────────────┐
  │    Filter Warna (R / G / B)   │  │  Filter Warna (R/G/B)   │  │ Lapisan Emisi Organik   │
  ├───────────────────────────────┤  ├─────────────────────────┤  │ (Tiap Piksel Menyala &  │
  │   Kristal Cair (Liquid Crystal│  │  Kristal Cair (LC)      │  │  Mati Secara Mandiri —  │
  │   Shutter — Mengatur Cahaya)  │  ├─────────────────────────┤  │  Kontras ∞:1, 0.0005 nit│
  ├───────────────────────────────┤  │ Ribuan Zona Mini-LED    │  └─────────────────────────┘
  │ Diffuser & Lampu Latar Edge   │  │ (Local Dimming Aktif    │  • Subpiksel: Diamond
  │ LED Tunggal (Selalu Menyala)  │  │  Meredup di Area Gelap) │    Pentile atau RGB Tandem
  └───────────────────────────────┘  └─────────────────────────┘
```

* **Teknologi Panel**: **TN** (*legacy/entry*, kontras & sudut pandang buruk), **VA** (kontras tinggi tapi *black smearing* lambat), **IPS / Fast IPS / IPS Black** (kontras 2.000:1, sudut pandang 178°, subpiksel **RGB Stripe** tajam untuk teks), **Mini-LED FALD** (500–2.500+ zona *local dimming*, kecerahan HDR 1.000–1.600 nits tanpa risiko *burn-in*), serta **OLED / AMOLED / Tandem OLED** (kontras $\infty:1$, waktu respons 0,2 ms, lapisan ganda *Tandem OLED* melipatgandakan kecerahan dan umur pakai).
* **Parameter Optik & Ergonomi**:
  * Hindari jebakan gamut warna **45% NTSC (~62% sRGB)**; pilih minimal **100% sRGB** atau **100% DCI-P3** dengan akurasi **$\Delta E < 2$**.
  * Bedakan panel **10-bit sejati** dari **8-bit + FRC**.
  * **PWM Dimming vs. DC Dimming**: Layar OLED menggunakan kedipan PWM; frekuensi rendah (240–480 Hz) dapat memicu ketegangan mata (*eye strain*), sedangkan panel OLED modern kelas atas memakai **High-Frequency PWM (1.920–3.840 Hz)** atau mode *DC-like*.
  * **VRR (Adaptive Sync / G-SYNC / FreeSync / LTPO 1–120 Hz)** dan lapisan permukaan (*Matte Anti-Glare* vs *Glossy Anti-Reflective / Nano-texture*).

---

## 10.2 Rekayasa Baterai, Penghantaran Daya, & Manajemen Energi

* **Watt-Hour (Wh) vs. mAh**: $\text{Wh} = \frac{\text{mAh} \times \text{V}}{1000}$. Batas maksimum regulasi kabin pesawat (FAA/IATA) adalah **100 Wh** (sehingga laptop besar memakai kapasitas **99,9 Wh**).
* **USB Power Delivery 3.1 EPR**: Memperluas standar USB-C dari 100W (20V/5A) menjadi **140W (28V)**, **180W (36V)**, hingga **240W (48V/5A)** dengan kabel *e-Marker*, sementara laptop gaming/workstation penuh tetap mengandalkan adaptor proprietari **180W–330W+** dan sirkuit **Battery Bypass**.
* **Faktor Penentu Daya Tahan Nyata**: Daya *idle* paket SoC (*Package C-States*), pencegahan bangun liar dGPU (*rogue wake-ups*), konsumsi layar (PSR), manajemen tidur **Modern Standby (`S0ix`) vs. `S3`**, serta pembatasan pengisian **75%–80% Charge Limit** oleh BMS untuk memperpanjang umur sel Li-Po.

---

## 10.3 Rekayasa Termal, Akustik, & Mekanis Sasis

* **Heat Pipe Sinter vs. Vapor Chamber 3D**: *Vapor chamber* menyebarkan panas secara dua/tiga dimensi di seluruh area CPU, GPU, VRM, dan VRAM untuk mencegah titik panas (*hotspot*).
* **Material Antarmuka Termal (TIM)**:
  * *Thermal Paste Standar*: Rentan mengalami **pump-out effect** pada *bare-die* laptop setelah 1–2 tahun.
  * *Liquid Metal (~73 W/m·K)*: Konduktivitas ekstrem namun konduktif listrik (berisiko korsleting dan membutuhkan heatsink berlapis nikel).
  * *Phase-Change Material (**Honeywell PTM7950**, ~8,5 W/m·K)*: Padat pada suhu ruang dan mencair pada **~45°C**; 100% non-konduktif listrik, bebas *pump-out*, dan menjadi standar emas keandalan jangka panjang.
* **Sasis & MIL-STD-810H**: Material berjenjang dari plastik polikarbonat, aluminium CNC, paduan **magnesium-lithium** (30%–35% lebih ringan dari aluminium), **serat karbon**, hingga **Ceraluminum**. Label **MIL-STD-810H** merupakan kumpulan metode uji selektif oleh OEM dan **tidak setara** dengan sertifikasi ketahanan air/debu **IP65/IP66**.
