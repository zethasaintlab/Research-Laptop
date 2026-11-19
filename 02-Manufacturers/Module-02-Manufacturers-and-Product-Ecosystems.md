# Module 02 — Manufacturers & Product Ecosystems (Ekosistem Manufaktur & Lini Produk Global)

## 2.1 Arsitektur Rantai Pasok Global: OEM vs. ODM

```
[Vendor Silikon: Intel, AMD, Apple, Qualcomm, NVIDIA]
                       │
                       ▼ (Desain Referensi & BSP / Board Support Package)
       ┌───────────────┴───────────────┐
       ▼                               ▼
[ODM Volume Tier-1]             [ODM Enthusiast / White-Label]
• Quanta Computer               • Clevo
• Compal Electronics            • Tongfang (Uniwill)
• Wistron / Pegatron            • Emdoor / Huaqin
• Inventec / Huaqin             
       │                               │
       ▼ (Desain Kustom Eksklusif)     ▼ (Sasis Barebone Standar + Rebranding)
[OEM Global Tier-1]             [OEM Regional & Spesialis]
• Apple, Lenovo, Dell, HP,      • Mechrevo, XMG/Schenker, TUXEDO,
  ASUS, Acer, MSI, Samsung        System76 (sebagian), Axioo Pongo, Advan
```

* **Model ODM Kustom (*Joint Design Manufacturing* / JDM)**: OEM Tier-1 seperti Apple, Lenovo (lini ThinkPad), Dell (lini XPS/Pro), dan HP (lini EliteBook) merancang sendiri papan utama, sistem engsel, dan *Embedded Controller* (EC), lalu menyerahkan produksi massalnya kepada ODM raksasa (**Quanta Computer, Compal Electronics, Wistron, Pegatron, Inventec**).
* **Model ODM Barebone / White-Label**: Perusahaan seperti **Clevo** dan **Tongfang (Uniwill)** merancang sasis lengkap beserta papan utama, sistem pendingin, dan firmware BIOS/EC dasar. Merek regional maupun spesialis (*XMG, TUXEDO, Mechrevo, Eluktronics, Axioo Pongo*) membeli desain *barebone* tersebut dan memasang komponen serta merek mereka sendiri.

---

## 2.2 Ekosistem Manufaktur Global Tier-1

### 1. Lenovo
* **ThinkPad (Komersial & Enterprise)**: *X1 Series (X1 Carbon, X1 2-in-1)*; *X9 Aura Edition (Gen 1, 2025–2026)* (desain aluminium *engine-hub* ultra-tipis tanpa TrackPoint klasik); *T-Series (T14, T14s, T16)*; *P-Series (P1, P14s, P16v, P16)* (workstation ISV hingga 192 GB ECC); *L-Series & E-Series*.
* **ThinkBook (SMB & Prosumer)**: Jembatan konsumen-bisnis, termasuk **ThinkBook Plus Gen 6 Rollable** (layar OLED bermotor 14" ke 16,7").
* **Yoga & IdeaPad**: *Yoga Slim*, *Yoga 2-in-1*, *Yoga Pro 9i* (Mini-LED), serta *IdeaPad Slim 3/5* dan *IdeaPad Pro 5*.
* **Legion & LOQ (Gaming)**: *Legion 9i / Pro 7i / Pro 5i* (TGP penuh, *Coldfront Vapor / Liquid Metal*), *Legion 7i / Slim 5*, dan *LOQ* (gaming value).
* **Linux**: Standar emas industri melalui modul upstream `thinkpad_acpi` dan pembaruan BIOS/EC langsung via **LVFS (`fwupd`)**.

### 2. ASUS
* **Zenbook**: *Zenbook S-Series (S 13, S 14 UX5406, S 16)* berbahan **Ceraluminum** dan *Zenbook Duo (UX8406)* layar ganda 14" OLED.
* **Vivobook**: *Vivobook Go / 14 / 15*, *Vivobook S-Series*, dan *Vivobook Pro*.
* **ProArt**: *ProArt P16*, *ProArt PX13*, dan *ProArt PZ13* dengan **ASUS DialPad**.
* **ROG & TUF Gaming**: *ROG Zephyrus (G14, G16)*, *ROG Strix (SCAR 16/18, G16/G18)*, *ROG Flow (Z13 GZ302 Strix Halo)*, dan *TUF Gaming (A14, A15, A16, F15/F16)*.
* **ExpertBook**: *ExpertBook B9 OLED* (990 gram), *B5*, dan *P-Series*.
* **Linux**: Didukung kuat oleh proyek komunitas **asus-linux.org** (`asusctl` / `supergfxctl` / `asus-nb-wmi`).

### 3. Dell (Restrukturisasi Penamaan 2025–2026)

| Pilar Baru Dell (2025–2026) | Merek Warisan yang Digantikan (2023–2024) | Segmen & Karakteristik Rekayasa |
| :--- | :--- | :--- |
| **Dell** *(Base)* | *Inspiron* (standar) | Laptop konsumen harian berbiaya efisien. |
| **Dell Plus** | *Inspiron Plus* | Kelas menengah konsumen dan kreator ringan berbahan aluminium. |
| **Dell Premium** | *XPS (13, 14, 16)* | Ultraportabel *flagship* CNC aluminium + baris tombol sentuh kapasitif. |
| **Dell Pro** *(Base & Plus)* | *Latitude (3000, 5000, 7000)* | Laptop bisnis korporasi standar dengan *Dell SafeBIOS*. |
| **Dell Pro Premium** | *Latitude 9000 / Ultralight* | Ultrabook eksekutif korporasi ultra-ringan berbahan magnesium. |
| **Dell Pro Max** *(Base, Plus, Premium)* | *Precision (3000, 5000, 7000)* | *Mobile workstation* ISV; mengadopsi modul memori **CAMM2** dan opsi ECC. |
| **Dell Pro Rugged** | *Latitude Rugged* | Laptop tangguh bersertifikasi IP65. |
| **Alienware** | *Alienware m-series, x-series* | Merek gaming *flagship* (termasuk kebangkitan seri **Area-51**). |

### 4. HP (Konsolidasi Ekosistem 2025–2026)
* **OmniBook**: Menggantikan merek *Spectre, Envy,* dan *Pavilion* menjadi *OmniBook 3, 5, 7, X,* dan *OmniBook Ultra / Ultra Flip 14*.
* **EliteBook & ProBook**: Lini korporasi dengan **HP Sure Start** (*self-healing BIOS*) dan *HP Wolf Security*; seri *EliteBook 800/8 G1i* mempertahankan 2 slot RAM SO-DIMM.
* **ZBook**: *ZBook Firefly, Power, Studio, Fury,* dan *ZBook Ultra G1a 14* (berbasis AMD Strix Halo).
* **OMEN & Victus**: *OMEN 16/17* (gaming performa penuh) dan *Victus 15/16* (gaming value).

### 5. Acer, Apple, MSI, Gigabyte, & Razer
* **Acer**: *Swift (Go, X, Edge, Air, Swift Blade 14 799g)*, *Aspire / Aspire Vero*, *TravelMate*, serta *Predator Helios / Triton* (kipas logam **AeroBlade 3D**) dan *Nitro V / 16*.
* **Apple**: *MacBook Air 13/15* (**fanless** M3/M4/M5) dan *MacBook Pro 14/16* (pendingin aktif, layar **Liquid Retina XDR Mini-LED**, *Unified Memory* hingga 128 GB; nol kemampuan upgrade internal).
* **MSI**: *Titan HX, Raider GE, Vector GP, Stealth, Crosshair/Katana/Cyborg/Thin* (waspada seri *Cyborg/Thin* kipas tunggal & TGP terbatas 45W–55W), serta *Prestige/Summit/Creator*.
* **Gigabyte & Razer**: *Gigabyte AORUS / G5 / AERO OLED*; *Razer Blade 14/16/18* (sasis CNC aluminium + *vapor chamber*).

---

## 2.3 Ekosistem Spesialis Modular, Regional Asia, & Pasar Indonesia

* **Framework Computer**: *Framework Laptop 13* & *Framework Laptop 16* (skor perbaikan iFixit 10/10, port tukar-pasang *Expansion Cards*, mainboard dan modul GPU *Expansion Bay* RX 7700S / RTX 5070 yang dapat diganti pengguna, dukungan resmi Fedora/Ubuntu dan *Chromium EC*).
* **OEM Linux-First**: *System76* (*Pop!_OS*, *COSMIC*, *coreboot*), *TUXEDO Computers* (`tuxedo-drivers`), *Slimbook*, dan *Star Labs*.
* **Regional Asia**: *Samsung Galaxy Book4/5*, *LG Gram* (bobot ultra-ringan magnesium-karbon), *Microsoft Surface Pro 11 / Laptop 7*, *Huawei MateBook*, *Xiaomi RedmiBook*, dan *Honor MagicBook*.
* **Tongfang vs. Clevo**: *Tongfang* lebih tipis/ringan dengan baterai besar (80–99 Wh) dan kontrol batas daya terbuka; *Clevo* lebih tebal/kokoh dengan *heatsink* besar.
* **Pasar Indonesia**: Merek lokal berbasis kemitraan ODM meliputi **Axioo** (*Axioo Pongo* berbasis sasis Clevo, *Axioo Hype*), **Advan** (*Workplus, AI Gen*), dan **Zyrex** (fokus pendidikan/TKDN). Pembeli di Indonesia wajib memisahkan **unit bergaransi resmi prinsipal lokal** dari **unit impor paralel tanpa garansi resmi** (*Framework, Razer, GPD, System76*).
