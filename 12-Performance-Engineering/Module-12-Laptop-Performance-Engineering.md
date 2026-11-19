# Module 12 — Laptop Performance Engineering (Rekayasa Performa Laptop)

## 12.1 Dinamika Sistemik & Analisis Hambatan (*Bottleneck Analysis*)

```
====================================================================================
           MODEL SISTEMIK KENDALA FISIKA & DATA DALAM SEBUAH LAPTOP
====================================================================================
  [Sumber Daya: Adaptor AC (65W–330W) ATAU Baterai Li-Po (Batas Arus C-Rate)]
                                       │
                                       ▼
  ┌──────────────────────────────────────────────────────────────────────────────┐
  │       REGULASI DAYA & FIRMWARE (VRM, Embedded Controller, BIOS PL1/PL2)      │
  └────────────────────────┬───────────────────────────┬─────────────────────────┘
                           │ (Anggaran Daya Bersama)   │
                           ▼                           ▼
                 ┌───────────────────┐       ┌───────────────────┐
                 │  CPU + iGPU + NPU │◄─────►│   Discrete GPU    │
                 │   (15W – 120W+)   │ PCIe  │   (35W – 175W)    │
                 └─────────┬─────────┘       └─────────┬─────────┘
                           │                           │
            ┌──────────────┼──────────────┐            │
            ▼              ▼              ▼            ▼
     [RAM Bandwidth] [SSD NVMe I/O] [Layar/Panel] [Dedicated VRAM]
      (Bottleneck 1) (Bottleneck 2) (Konsumsi 2-9W) (Bottleneck 3)
            │              │                           │
            └──────────────┼───────────────────────────┘
                           ▼
  ┌──────────────────────────────────────────────────────────────────────────────┐
  │       ANGGARAN TERMAL SASIS (Heat Pipes / Vapor Chamber / Kipas LCP)         │
  │    Batas Akhir: Suhu Silikon Tj_max (95°C–105°C) & Suhu Kulit Sasis (STAPM)  │
  └──────────────────────────────────────────────────────────────────────────────┘
```

* **CPU-Bound vs. GPU-Bound**: Gim esports 1080p rendah bersifat *CPU-bound* (sensitif *IPC single-core*, cache L3/3D V-Cache, dan MUX Switch), sedangkan gim AAA 1440p/4K Ray Tracing bersifat *GPU-bound* (sensitif shader, TGP, dan kapasitas VRAM).
* **Pembagian Daya & Termal (*Power Sharing*)**: *Intel DTT* dan *AMD SmartShift* membagi anggaran watt total sasis antara CPU dan GPU saat keduanya dibebani 100% bersamaan.
* **VRM Throttling (`BD PROCHOT` / `EDP`)**: Panas berlebih pada sirkuit pengatur tegangan VRM memaksa CPU turun ke frekuensi dasar meskipun suhu die CPU masih dingin.

---

## 12.2 Tujuh Rezim Performa Laptop (*The Seven Performance Regimes*)

| Rezim Performa | Jendela Waktu & Kondisi Pemicu | Mekanisme Perangkat Keras yang Terjadi | Implikasi Nyata bagi Pengguna |
| :--- | :--- | :--- | :--- |
| **1. Burst Performance** | **0 – 5 detik pertama** dari kondisi dingin/idle. | CPU melonjak ke daya **PL2 / FPPT** maksimum pada 1–2 core sebelum massa heatsink memanas. | Membuat pembukaan aplikasi dan perintah terminal pendek terasa sangat responsif. |
| **2. Peak Performance** | **5 – 30 detik awal** beban penuh (*Tau window*). | Seluruh core bekerja pada batas daya tinggi memanfaatkan *thermal mass* tembaga/uap pendingin. | Menghasilkan skor tinggi pada benchmark singkat, namun **bukan** kecepatan kerja berjam-jam. |
| **3. Sustained Performance** | **10 menit hingga berjam-jam** beban kontinu. | Titik keseimbangan termodinamika antara panas silikon dan pembuangan kipas (**PL1 / SPL**). | **Metrik paling jujur** untuk rendering video panjang, kompilasi proyek besar, dan pelatihan ML. |
| **4. Power-Limited Performance** | Suhu di bawah $T_{j\text{max}}$, tetapi frekuensi tertahan. | Firmware EC, batas arus **ICCMax/EDP**, atau kapasitas adaptor listrik membatasi pasokan Watt. | Umum pada ultrabook premium tipis yang ditala konservatif demi kesenyapan kipas. |
| **5. Thermal-Limited Performance** | Suhu menyentuh **$T_{j\text{max}}$ ($95^\circ\text{C}–105^\circ\text{C}$)** atau **STAPM**. | Pengendali termal menurunkan tegangan dan frekuensi secara bertahap (*thermal throttling*). | Terjadi pada sasis berpendingin kurang memadai atau ventilasi tersumbat debu. |
| **6. AC-Powered Performance** | Terhubung ke adaptor listrik dinding berdaya penuh. | Sirkuit **Battery Bypass** menyuplai daya penuh ke VRM; profil *Performance/Turbo* aktif. | Memberikan 100% potensi komputasi perangkat keras laptop. |
| **7. Battery-Mode Performance** | Beroperasi menggunakan daya baterai internal. | Batas laju pengosongan sel Li-Po (**C-rate**) memangkas daya laptop Windows dGPU sebesar **40%–70%**; sebaliknya **Apple Silicon** dan ultrabook efisien mempertahankan performa **100% identik**. | Wajib dipertimbangkan bagi pekerja yang sering melakukan komputasi berat jauh dari stopkontak. |

---

## 12.3 Profil Rekayasa 12 Beban Kerja Dunia Nyata & Paradoks Komponen Tertinggi

1. **Gaming**: AAA 1440p butuh VRAM ≥ 12 GB + TGP penuh + MUX Switch; Esports butuh IPC tinggi + 3D V-Cache.
2. **Software Development**: IDE indexing butuh *single-core IPC* + IOPS acak SSD TLC; kompilasi paralel butuh *sustained multi-core* + RAM ≥ 32 GB.
3. **Virtualization & Containerization**: Kapasitas RAM fisik (32–96 GB) + jumlah core/thread CPU + bandwidth SSD.
4. **Linux Desktop Usage**: Akselerasi Wayland Vulkan/OpenGL dan dekode video perangkat keras VA-API/NVDEC (`amdgpu` / Intel `xe`).
5. **AI Development (LLM Lokal)**: Kapasitas memori terpadu/VRAM (24–128 GB) + *Memory Bandwidth* (≥ 256–896 GB/s).
6. **Machine Learning (Training / Fine-Tuning)**: Ekosistem **NVIDIA CUDA / TensorRT**, presisi BF16/FP8/FP4, VRAM ≥ 16–24 GB, dan pendingin penuh.
7. **Content Creation (Foto/Desain)**: *Single-core IPC*, RAM 32 GB+, SSD TLC cepat, dan layar $\Delta E < 2$ (100% sRGB/DCI-P3/AdobeRGB).
8. **Video Editing (4K/8K)**: **Hardware Media Engine** dengan dekode/enkode native **10-bit 4:2:2** (*Apple Silicon, Intel Quick Sync, NVIDIA RTX 50 9th-Gen NVENC*).
9. **3D Rendering**: *Viewport* bersifat *single-core CPU-bound*; rendering akhir *ray/path tracing* bersifat *GPU-bound* (**NVIDIA OptiX / RT Cores**).
10. **CAD & Engineering Simulation**: Pemodelan parametrik bersifat *single-core CPU-bound*; simulasi FEA/CFD butuh *multi-core* + bandwidth memori + **GPU bersertifikasi ISV & memori ECC**.
11. **Scientific Workloads**: Instruksi vektor lebar (**AVX-512 512-bit penuh** pada Zen 5 / Panther Lake), bandwidth memori multi-kanal, dan kinerja **FP64**.
12. **General Productivity**: Efisiensi *burst*, RAM 16–32 GB, NPU 1W–5W untuk kamera/audio, dan layar 16:10 anti-silau.

* **Paradoks Komponen Tertinggi**: Menaikkan kinerja silikon 10%–15% terakhir di ujung kurva $V/f$ menuntut lonjakan daya 35%–60%. Memasang CPU/GPU kelas tertinggi di dalam sasis tipis berpendingin terbatas memicu *throttling*, kebisingan ekstrem, baterai boros, dan pemborosan anggaran (*diminishing returns*).
