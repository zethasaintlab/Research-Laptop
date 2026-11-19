# Module 01 — Global Laptop Taxonomy (Taksonomi Laptop Global)

Taksonomi laptop modern bersifat **multidimensi** (*non-mutually exclusive*). Satu perangkat fisik dapat diklasifikasikan secara simultan berdasarkan tujuan penggunaannya, bentuk fisiknya, arsitektur silikonnya, segmen harganya, dan sistem operasinya. Sebagai contoh, sebuah *Lenovo ThinkPad X1 Carbon Gen 12/13* secara bersamaan adalah **Business/Enterprise Laptop** (tujuan), **Traditional Clamshell** (faktor bentuk), **x86-64 SoC Platform** (perangkat keras), **Premium/Enterprise** (segmen), dan **Windows / Linux-Certified Platform** (sistem operasi).

---

## 1.1 Klasifikasi Berdasarkan Tujuan Penggunaan (General Purpose)

### A. Consumer / Everyday Laptop (Laptop Konsumen & Penggunaan Harian)
* **Definisi & Tujuan Utama**: Komputer portabel arus utama yang dirancang untuk komputasi harian berbiaya efisien seperti penjelajahan web, pengolahan dokumen perkantoran, konsumsi media, dan konferensi video.
* **Target Pengguna**: Pengguna rumahan, pelajar umum, dan pekerja administrasi ringan.
* **Konfigurasi Perangkat Keras Tipikal**:
  * *CPU & GPU*: Prosesor kelas efisiensi dasar hingga menengah (*Intel Core 3 / Core 5 U-series*, *AMD Ryzen 3 / Ryzen 5 7000/8000 U-series*, *Qualcomm Snapdragon X*). Mengandalkan GPU terintegrasi (iGPU) dasar.
  * *RAM & Penyimpanan*: 8 GB hingga 16 GB DDR4/DDR5 atau LPDDR5; SSD PCIe NVMe 256 GB hingga 512 GB (sering kali menggunakan slot M.2 2242 atau 2280 tunggal).
  * *Layar*: 14 hingga 15,6 inci, resolusi Full HD (1920×1080) atau WUXGA (1920×1200), panel IPS atau TN (pada segmen terbawah), cakupan warna 45% NTSC (~62% sRGB), kecerahan 250–300 nits, *refresh rate* 60 Hz.
  * *Sistem Pendingin & Baterai*: Satu kipas kecil dengan satu *heat pipe* tipis; kapasitas baterai 38–50 Wh; pengisian daya 45W–65W.
* **Keunggulan**: Harga terjangkau, bobot relatif ringan (1,4–1,7 kg), cukup senyap pada beban ringan.
* **Keterbatasan**: Sasis umumnya berbahan plastik polikarbonat dengan kelenturan tinggi, kualitas layar dan reproduksi warna terbatas, kapasitas termal tidak dirancang untuk beban berat jangka panjang, serta pada banyak model modern RAM disolder permanen tanpa slot ekspansi.
* **Miskonsepsi Umum**: Menganggap prosesor dengan label *Core i7* atau *Ryzen 7* pada sasis *consumer* tipis memiliki performa yang setara dengan *Core i7* atau *Ryzen 7* pada laptop *gaming* atau *workstation*.
* **Contoh Representatif**: *Acer Aspire Go / Aspire 5*, *ASUS Vivobook 14/15 (non-Pro)*, *Lenovo IdeaPad Slim 3 / Slim 5*, *HP 14s / Pavilion 15*.

### B. Ultrabook vs. Thin-and-Light Laptop (Laptop Ultratipis & Portabel)
* **Definisi & Tujuan Utama**:
  * **Thin-and-Light Laptop** adalah kategori industri umum untuk laptop berprofil tipis (ketebalan umumnya di bawah 17–18 mm) dan berbobot ringan (di bawah 1,5 kg untuk ukuran 13–14 inci) yang mengutamakan mobilitas tinggi.
  * **Ultrabook** secara historis merupakan merek dagang dan standar sertifikasi yang diperkenalkan oleh Intel pada tahun 2011, yang kini evolusinya diteruskan melalui program sertifikasi **Intel Evo Edition** (mensyaratkan standar ketat pada kecepatan bangun dari mode tidur, daya tahan baterai nyata, pengisian cepat, konektivitas Thunderbolt/Wi-Fi 6E/7, dan dimensi tipis).
* **Target Pengguna**: Eksekutif bergerak, konsultan, jurnalis, mahasiswa, dan pekerja jarak jauh (*remote workers*).
* **Konfigurasi Perangkat Keras Tipikal**:
  * *CPU & GPU*: Prosesor berdaya rendah berarsitektur efisiensi tinggi (*Intel Core Ultra 5/7 seri V atau U*, *AMD Ryzen AI 7/9 seri U/HX ber-TDP 15W–28W*, *Apple M3/M4/M5*, *Qualcomm Snapdragon X Plus/Elite*). Mengandalkan iGPU modern (*Intel Arc 130V/140V*, *AMD Radeon 880M/890M*, *Apple 8–10 core GPU*).
  * *RAM & Penyimpanan*: 16 GB hingga 32 GB LPDDR5X berkecepatan tinggi (6400–8533 MT/s) yang disolder langsung ke papan utama (*on-package* atau *on-board*) demi menghemat ruang vertikal dan daya listrik; SSD PCIe 4.0 NVMe 512 GB – 2 TB.
  * *Layar*: 13,3 hingga 14,5 inci (atau hingga 15,3–16 inci pada varian ultra-ringan seperti *LG Gram* atau *MacBook Air 15*), rasio aspek 16:10, resolusi 1920×1200 hingga 2880×1800 (2.8K), panel IPS 100% sRGB atau OLED 100% DCI-P3, kecerahan 400–500 nits.
  * *Sistem Pendingin & Baterai*: Kipas profil ultra-tipis (*liquid crystal polymer blades*) dengan *vapor chamber* tipis atau tanpa kipas (*fanless*) pada *Apple MacBook Air*; baterai padat energi 55–75 Wh dengan daya tahan nyata 10–18 jam.
* **Keunggulan**: Portabilitas ekstrem (0,98–1,35 kg), material sasis premium (aluminium CNC, paduan magnesium-aluminium, atau serat karbon), daya tahan baterai sangat panjang, dan layar berkualitas tinggi.
* **Keterbatasan**: Keterbatasan ruang fisik memaksa pembatasan *thermal envelope* (15W–28W kontinu), hampir seluruh model meniadakan kemampuan peningkatan RAM (*non-upgradeable RAM*), serta jumlah port I/O fisik terbatas.
* **Miskonsepsi Umum**: Mengira semua laptop tipis adalah "Ultrabook" resmi, atau menganggap laptop tipis dengan prosesor generasi terbaru dapat mengeksekusi rendering 3D berat secepat laptop tebal dengan TDP 65W+.
* **Contoh Representatif**: *Apple MacBook Air 13/15 (M3/M4)*, *ASUS Zenbook S 13/14/16 OLED*, *Lenovo Yoga Slim 7i Aura Edition*, *Dell XPS 13 (9340/9345)*, *LG Gram 14/16*.

### C. Gaming Laptop (Laptop Gim)
* **Definisi & Tujuan Utama**: Komputer portabel berperforma tinggi yang dirancang untuk menjalankan gim video 3D modern pada *frame rate* tinggi dengan memprioritaskan daya komputasi grafis diskrit (dGPU), kapasitas pembuangan panas (*thermal dissipation*), dan responsivitas layar.
* **Target Pengguna**: Pemain gim (*gamers*), pemain esports kompetitif, serta pengguna teknis yang membutuhkan performa komputasi tinggi dengan anggaran lebih efisien dibandingkan *mobile workstation*.
* **Konfigurasi Perangkat Keras Tipikal**:
  * *CPU & GPU*: Prosesor kelas performa tinggi ber-TDP 45W–55W+ (*Intel Core i7/i9 HX-series*, *Core Ultra 7/9 H/HX-series*, *AMD Ryzen 7/9 HS atau HX-series*). Dipadukan dengan GPU diskrit (*NVIDIA GeForce RTX 4050/4060/4070/4080/4090* atau *RTX 5050–5090 Laptop*, serta *AMD Radeon RX 7600S/7700S*).
  * *RAM & Penyimpanan*: 16 GB hingga 64 GB DDR5 *dual-channel* (umumnya menggunakan 2 slot SO-DIMM yang dapat di-upgrade); 1 hingga 2 slot SSD M.2 PCIe 4.0/5.0 NVMe.
  * *Layar*: 14 hingga 18 inci, *refresh rate* tinggi 144 Hz hingga 360 Hz (atau 240 Hz OLED/Mini-LED pada kelas atas), waktu respons piksel rendah (1–3 ms), mendukung *NVIDIA G-SYNC* atau *AMD FreeSync*.
  * *Sistem Pendingin & Baterai*: Sistem pendingin masif dengan 2 hingga 3 kipas, banyak *heat pipe* tembaga atau *vapor chamber* penuh, penggunaan *liquid metal* atau *phase-change thermal interface material (PTM7950)*, serta lubang pembuangan panas di sisi belakang dan samping. Baterai besar 70–99,9 Wh (batas maksimum regulasi penerbangan FAA/IATA adalah 100 Wh), disertai adaptor daya eksternal besar (180W hingga 330W+).
* **Sub-Klasifikasi Penting**:
  1. *Budget / Entry Gaming* (TGP GPU dibatasi 45W–75W, bodi plastik, layar 144 Hz 45% NTSC — mis. *Lenovo LOQ*, *Acer Nitro V*, *ASUS TUF Gaming A15*).
  2. *Mainstream / Mid-Range Gaming* (TGP penuh 100W–140W pada RTX x060/x070, layar 100% sRGB — mis. *Lenovo Legion 5/Slim 5*, *ASUS ROG Strix G16*, *HP Omen 16*).
  3. *Thin-and-Light Gaming* (Bobot 1,5–1,9 kg, sasis aluminium CNC — mis. *ASUS ROG Zephyrus G14/G16*, *Razer Blade 14/16*, *Lenovo Legion Slim 7*).
  4. *Desktop Replacement / Enthusiast Gaming* (Layar 17–18 inci, total daya CPU+GPU hingga 230W–250W+ — mis. *MSI Titan 18 HX*, *ASUS ROG Strix SCAR 18*, *Lenovo Legion Pro 7i*).
* **Keterbatasan**: Bobot berat (2,1–3,6 kg beserta adaptor daya), kebisingan kipas tinggi saat beban penuh (45–55 dBA), dan daya tahan baterai singkat (3–6 jam penggunaan ringan) pada model dengan CPU berarsitektur *chiplet* atau manajemen daya dGPU yang kurang agresif.
* **Miskonsepsi Umum**: Memilih laptop gaming hanya berdasarkan nama seri GPU (mis. RTX 4070) tanpa memeriksa batas daya **TGP (Total Graphics Power)** dan keberadaan **MUX Switch**.

### D. Creator Laptop vs. Professional Laptop vs. Mobile Workstation

| Dimensi Teknis | Creator Laptop | Mobile Workstation |
| :--- | :--- | :--- |
| **Tujuan Utama** | Pengeditan video, fotografi, desain grafis, produksi audio, dan pembuatan konten 3D ringan-menengah. | Rekayasa CAD/CAM, simulasi elemen hingga (FEA), arsitektur BIM, riset ilmiah, dan pelatihan model AI/ML berat. |
| **Kelas GPU & Driver** | GPU konsumen kelas atas (*NVIDIA GeForce RTX 40/50 Series* dengan **NVIDIA Studio Drivers** yang dioptimalkan untuk aplikasi kreatif seperti Adobe Premiere, DaVinci Resolve, Blender). | GPU profesional tersertifikasi (*NVIDIA RTX Ada Generation / Blackwell Pro Laptop*, *AMD Radeon Pro*) atau UMA kelas workstation (*Apple M-Pro/Max*) dengan **ISV Certifications** (SolidWorks, AutoCAD, Revit, CATIA). |
| **Keandalan Memori** | RAM DDR5 atau LPDDR5X non-ECC (16 GB – 64 GB). | Mendukung memori **ECC (Error-Correcting Code)** pada konfigurasi prosesor *Intel Core HX / Xeon* atau *AMD Ryzen PRO* tertentu untuk mencegah korupsi data komputasi kritis, kapasitas hingga 128 GB – 192 GB (4 slot SO-DIMM pada workstation 16–17 inci). |
| **Kalibrasi Layar** | Prioritas utama pada akurasi warna terkalibrasi pabrik ($\Delta E < 1$ atau $< 2$), cakupan luas (100% sRGB, 100% DCI-P3, atau AdobeRGB), sering kali *Pantone Validated*. | Resolusi tinggi dengan akurasi warna baik, rasio 16:10, dan opsi layar anti-silau (*matte*) berdaya tahan tinggi untuk pembacaan garis teknik presisi. |
| **Sasis & Ketahanan** | Estetika modern, tipis, dan ringan (1,5–2,2 kg), berbahan aluminium anodisasi. | Sasis sangat kokoh memenuhi standar ketahanan militer **MIL-STD-810H**, desain termal yang dirancang untuk beban komputasi 100% selama berhari-hari tanpa *throttling*, bobot 1,8–3,5 kg. |
| **Contoh Produk** | *ASUS ProArt P16 / PX13*, *Apple MacBook Pro 14/16*, *Lenovo Yoga Pro 9i*, *MSI Creator Z16/Z17*. | *Lenovo ThinkPad P1 / P16*, *Dell Precision 5690 / 7680*, *HP ZBook Studio / Fury 16 G11*. |

### E. Business & Enterprise Laptop (Laptop Bisnis & Korporasi)
* **Definisi & Tujuan Utama**: Perangkat komputasi yang dirancang khusus untuk lingkungan perusahaan, instansi pemerintah, dan organisasi skala besar yang memprioritaskan keamanan tingkat perangkat keras, kemudahan pengelolaan jarak jauh oleh tim TI (*manageability*), keandalan jangka panjang, dan ergonomi pengetikan.
* **Target Pengguna**: Karyawan korporasi, eksekutif, analis bisnis, staf pemerintahan, dan pekerja lapangan profesional.
* **Konfigurasi Perangkat Keras & Fitur Khusus**:
  * *Platform Keamanan & Manajemen*: Mendukung **Intel vPro Enterprise/Essentials** atau **AMD Ryzen PRO** (mengaktifkan manajemen *out-of-band* seperti Intel AMT untuk perbaikan sistem jarak jauh bahkan saat OS tidak merespons), chip keamanan diskrit **TPM 2.0**, pembaca sidik jari terintegrasi tombol daya, kamera inframerah (IR) untuk *Windows Hello* dengan penutup fisik (*privacy shutter*), serta fitur *tamper detection* pada sasis.
  * *Ketahanan & Ergonomi*: Sasis magnesium, serat karbon, atau aluminium yang lolos uji ketahanan jatuh, getaran, kelembapan, dan suhu ekstrem (**MIL-STD-810H**), keyboard tahan tumpahan cairan (*spill-resistant*) dengan jarak tekan tombol (*key travel*) dalam (1,5–1,8 mm), serta perangkat penunjuk ganda (*touchpad* kaca + *TrackPoint* pada ThinkPad).
  * *Garansi & Siklus Hidup*: Jaminan ketersediaan suku cadang selama 3–5 tahun, garansi *on-site next-business-day*, dan stabilitas gambar sistem operasi (*image stability*).
* **Contoh Representatif**: *Lenovo ThinkPad T-Series / X-Series / L-Series*, *Dell Latitude 5000/7000/9000 (atau Dell Pro / Pro Max)*, *HP EliteBook 800/1000 & ProBook 400*, *ASUS ExpertBook B5/B9*.

### F. Educational Laptop & Chromebook
* **Definisi & Tujuan Utama**: Perangkat berbiaya rendah dengan daya tahan fisik tinggi yang dioptimalkan untuk lingkungan sekolah (K-12) dan pembelajaran berbasis awan (*cloud-first*).
* **Karakteristik Teknis**:
  * **Chromebook**: Menjalankan sistem operasi **ChromeOS** berbasis kernel Linux. Mengandalkan prosesor hemat daya (*Intel Processor N100/N200*, *Core i3-N305*, *MediaTek Kompanio 520/838*), RAM 4–8 GB, dan penyimpanan eMMC atau UFS 64–128 GB. Kategori **Chromebook Plus** menetapkan standar minimum lebih tinggi (CPU minimal Core i3 Gen 12 / Ryzen 3 7000 ke atas, RAM ≥ 8 GB, penyimpanan ≥ 128 GB, layar FHD IPS, kamera 1080p).
  * **Windows Education Laptop**: Konstruksi serupa dengan pelindung karet di sekeliling tepi sasis (*rubberized bumpers*), engsel hingga 180 derajat, dan tombol keyboard *anchored keys*.

### G. Rugged & Industrial Laptop (Laptop Tangguh & Industri)
* **Definisi & Tujuan Utama**: Komputer portabel khusus untuk lingkungan ekstrem (pertambangan, migas, militer, manufaktur berat).
* **Karakteristik Rekayasa**: Sertifikasi ketahanan debu dan air **IP65 / IP66**, tahan jatuh MIL-STD-810H hingga 1,8 meter, layar **1.000–1.400 nits** terbaca di bawah sinar matahari langsung, baterai ganda *hot-swappable*, serta port serial **RS-232 (DB9)** dan modul 4G/5G berantena penguat tinggi (*Panasonic Toughbook 40/55*, *Getac B360*, *Dell Pro Rugged*).

### H. AI PC (Komputer Portabel Akselerasi AI Lokal)
* **Definisi & Tujuan Utama**: Kategori laptop modern yang mengintegrasikan **Neural Processing Unit (NPU)** berkinerja tinggi di samping CPU dan GPU untuk mengeksekusi beban kerja kecerdasan buatan secara lokal (*on-device*) dengan efisiensi daya tinggi.
* **Batas Teknis & Standar Industri**:
  * **Standar Microsoft Copilot+ PC**: NPU minimal **40+ TOPS** pada presisi INT8, kapasitas RAM minimal **16 GB DDR5/LPDDR5X**, dan penyimpanan SSD minimal **256 GB**.

---

## 1.2 Klasifikasi Berdasarkan Faktor Bentuk Fisik (Physical Form Factor)

| Faktor Bentuk | Konstruksi Mekanis & Desain Engsel | Konsekuensi Termal & Port | Kemampuan Upgrade & Perbaikan | Contoh Produk Representatif |
| :--- | :--- | :--- | :--- | :--- |
| **Traditional Clamshell** | Dua bidang terpisah dihubungkan engsel 135°–180°. Distribusi beban mekanis paling stabil. | Ruang paling optimal untuk kipas ganda, *heat pipe* lurus, baterai besar, dan port lengkap. | Tertinggi di kelasnya (tergantung segmen: slot SO-DIMM & M.2 mudah diakses pada seri gaming/bisnis). | *ThinkPad T14*, *MacBook Pro 14*, *ROG Zephyrus G16*. |
| **Convertible 2-in-1 (360° Hinge)** | Engsel roda gigi ganda (*dual-torque 360° hinge*) memungkinkan layar diputar penuh menjadi tablet, *tent*, atau *stand*. | Sasis harus tipis dan seimbang; saluran pembuangan panas tidak boleh terhalang saat layar dilipat 360°. | Umumnya rendah; RAM hampir selalu disolder untuk menjaga ketipisan. | *Lenovo Yoga 9i 2-in-1*, *HP Spectre x360 14*, *ASUS ProArt PX13*. |
| **Detachable 2-in-1** | Seluruh komponen komputasi berada di balik layar tablet; keyboard terhubung magnetis via pin *pogo*. | Keterbatasan termal ekstrem karena ruang balik layar sangat tipis; bagian atas berat (*top-heavy*). | Sangat rendah (kecuali pintu SSD M.2 2230 pada Surface Pro terbaru). | *Microsoft Surface Pro 11*, *ASUS ROG Flow Z13 (GZ302)*. |
| **Dual-Screen Laptop** | Dua layar penuh terhubung engsel; keyboard fisik magnetis dapat dilepas atau diletakkan di atas layar bawah. | Tantangan manajemen daya dua panel OLED/IPS sekaligus dan penempatan baterai terbagi. | Terbatas (umumnya hanya SSD M.2); kompleksitas kabel fleksibel layar tinggi. | *ASUS Zenbook Duo (UX8406)*, *Lenovo Yoga Book 9i*. |
| **Foldable Display Laptop** | Satu panel OLED fleksibel besar (16,3–17,3 inci) dilipat di tengah menggunakan engsel tetesan air (*waterdrop hinge*). | Pendinginan pasif/sangat tipis; lapisan polimer layar rentan goresan benda tajam. | Sangat sulit diperbaiki mandiri; biaya penggantian panel lipat sangat tinggi. | *Lenovo ThinkPad X1 Fold 16*, *ASUS Zenbook 17 Fold OLED*. |
| **Rollable Display Laptop** | Panel OLED fleksibel yang menggulung ke dalam sasis dan memanjang vertikal via motor mikro (14" 5:4 $\rightarrow$ 16,7" 8:9). | Mekanisme motor penggulung memakan ruang internal sehingga mengurangi kapasitas baterai. | Kompleksitas mekanis sangat tinggi; komponen layar bermotor bersifat proprietari. | *Lenovo ThinkBook Plus Gen 6 Rollable*. |
| **Modular & Repairable Laptop** | Sasis dengan sekrup standar terukur (Torx T5), modul port I/O tukar-pasang (*Expansion Cards*), serta mainboard & GPU modular. | Sedikit lebih tebal dibanding ultrabook *unibody* ekstrem demi soket modular. | **Terbaik di industri**; seluruh komponen utama memiliki panduan perbaikan terbuka. | *Framework Laptop 13*, *Framework Laptop 16*. |
| **Desktop Replacement (DTR)** | Sasis besar 17–18 inci (tebal 25–35 mm) yang memprioritaskan daya komputasi dan pendinginan di atas mobilitas. | Mampu membuang panas 230W–250W+ secara kontinu; port lengkap termasuk RJ45 2.5GbE. | Sangat tinggi: 2–4 slot RAM, 2–4 slot SSD M.2, kartu Wi-Fi modular. | *MSI Titan 18 HX*, *Dell Precision 7780*, *Alienware m18*. |

---

## 1.3 Klasifikasi Berdasarkan Platform Perangkat Keras, Segmen Harga (IDR), & Sistem Operasi

### Platform Perangkat Keras
1. **ISA**: **x86-64** (kompatibilitas penuh aplikasi & gim PC), **ARM64 / AArch64** (efisiensi daya tinggi per instruksi pada Apple Silicon, Qualcomm Snapdragon X, MediaTek), serta **LoongArch64 & RISC-V**.
2. **Topologi Chip**: Transisi dari arsitektur *CPU + Northbridge + PCH terpisah* menuju **SoC terintegrasi penuh** (*monolithic* maupun *multi-tile Foveros/Chiplet*).
3. **Arsitektur Memori**: **Unified Memory Architecture (UMA)** (*Apple Silicon, AMD Strix Halo*) vs. **Discrete Memory** (RAM sistem + VRAM GDDR6/GDDR7 terdedikasi).

### Segmentasi Pasar & Referensi Harga Indonesia (IDR)

| Segmen Pasar | Kisaran Referensi Pasar Indonesia (IDR) | Material Sasis & Engsel | Kualitas Layar Standar | Sistem Pendingin & Daya | Dukungan & Garansi Tipikal |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Entry-Level** | Rp 4,5 juta – Rp 7,5 juta | Plastik ABS/polikarbonat standar. | 14–15,6" TN atau IPS dasar, 45% NTSC, 220–250 nits, 60 Hz. | Pendinginan pasif atau 1 kipas kecil; charger 45W. | Garansi resmi standar 1–2 tahun *carry-in*. |
| **Budget / Value** | Rp 7,5 juta – Rp 12 juta | Plastik diperkuat atau tutup layar aluminium tipis. | 14–16" IPS FHD/WUXGA, 45% NTSC (atau 100% sRGB pada model unggulan). | 1–2 kipas standar; baterai 42–56 Wh. | Garansi 2 tahun; sering menyertakan proteksi ADP tahun pertama. |
| **Mainstream** | Rp 12 juta – Rp 20 juta | Paduan aluminium atau sasis gaming polikarbonat kokoh. | 14–16" IPS 100% sRGB atau OLED 2.8K, 300–400 nits, 60–165 Hz. | 2 kipas dengan 2–3 *heat pipe*; opsi dGPU kelas pemula-menengah. | Garansi 2–3 tahun resmi + ADP; ketersediaan suku cadang baik. |
| **Premium** | Rp 20 juta – Rp 35 juta | Aluminium *unibody* CNC, paduan magnesium-lithium, atau serat karbon. | OLED 2.8K/3.2K 120 Hz atau IPS 165–240 Hz 100% DCI-P3, $\Delta E < 2$. | *Vapor chamber* atau kipas ganda berbilah rapat dengan *liquid metal* / PTM7950. | Garansi 2–3 tahun layanan prioritas / *on-site*. |
| **High-End & Enthusiast** | Rp 35 juta – Rp 65 juta | Logam penuh presisi tinggi dengan desain estetika minimalis atau gaming penuh. | Mini-LED 1000+ nits HDR atau Tandem OLED 240 Hz. | Sistem pendingin kompleks 3 kipas / *vapor chamber* besar; TGP hingga 175W. | Layanan VIP / *on-site*; beberapa SKU tertinggi masuk via importir non-resmi. |
| **Workstation & Experimental** | Rp 65 juta – Rp 120 juta+ | Sasis kelas militer teruji penuh, serat karbon tenun, atau engsel *foldable/rollable*. | Layar terkalibrasi perangkat keras, dukungan ECC, atau panel fleksibel. | Dirancang untuk beban kerja 100% 24/7; keamanan vPro/PRO. | Kontrak layanan korporasi 3–5 tahun *next-business-day on-site*. |

### Sistem Operasi
Mencakup **Windows 11 (x86-64)**, **Windows on ARM (WoA dengan emulasi Prism)**, **Linux** (dukungan terbaik di x86-64; *Asahi Linux* matang pada Apple M1/M2; Snapdragon X aktif dikembangkan via *Device Tree*), **macOS**, **ChromeOS (Crostini/ARCVM)**, dan **Dual-Boot** (memerlukan mode NVMe AHCI non-VMD dan pengelolaan kunci *Secure Boot MOK*).
