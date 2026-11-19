# Module 07 — GPU Encyclopedia (Ensiklopedia Arsitektur GPU & Ekosistem Grafis Laptop)

## 7.1 Fundamental Arsitektur & Terminologi Lintas-Vendor

| Komponen Fungsional | Terminologi NVIDIA | Terminologi AMD | Terminologi Intel | Fungsi Nyata dalam Komputasi |
| :--- | :--- | :--- | :--- | :--- |
| **Blok Komputasi Utama** | **Streaming Multiprocessor (SM)** | **Compute Unit (CU)** | **Xe-Core** | Kelompok pemrosesan dasar yang menampung unit shader, cache L1, dan penjadwal warp/wavefront. |
| **Unit Shader Dasar** | **CUDA Core** *(128/SM)* | **Stream Processor (SP)** *(64/CU)* | **Vector Engine** *(128/Xe-Core)* | Menghitung operasi matematika FP32/INT32 untuk geometri, *shading*, dan fisika. |
| **Unit Akselerasi Matriks / AI** | **Tensor Core** *(4/SM)* | **AI Accelerator** *(2/CU)* | **XMX Engine** | Mempercepat perkalian matriks untuk upscaling AI (*DLSS, FSR 4, XeSS*) dan inferensi neural. |
| **Unit Ray Tracing** | **RT Core** *(1/SM)* | **Ray Accelerator (RA)** *(1/CU)* | **Ray Tracing Unit (RTU)** | Menghitung persilangan sinar cahaya terhadap struktur pembatas (*BVH Traversal*) secara perangkat keras. |
| **Unit Tekstur & Piksel Akhir** | **TMU** & **ROP** | **TMU** & **ROP** | **Sampler** & **Pixel Backend** | *TMU* memetakan gambar tekstur 2D ke permukaan 3D; *ROP* menulis piksel akhir dan anti-aliasing ke frame buffer. |

---

## 7.2 Ekosistem GPU Laptop NVIDIA, AMD, & Intel

### A. NVIDIA GeForce RTX 50 Series (*Blackwell*, 2025–2026) & RTX 40 Series (*Ada Lovelace*)
* **Inovasi Blackwell Laptop**: Mengadopsi memori **GDDR7** di seluruh jajaran, *5th-Gen Tensor Cores* dengan presisi **FP4**, *4th-Gen RT Cores*, *DLSS 4 Multi Frame Generation (MFG)*, serta **9th-Gen NVENC** yang menambahkan dukungan perangkat keras native untuk **encode/decode video 4:2:2 10-bit**.

| Model GPU Laptop (RTX 50 Series) | Kode Silikon Die | CUDA Cores | Kapasitas & Tipe VRAM | Lebar Bus & Bandwidth Memori | Rentang TGP Khas OEM (termasuk Dynamic Boost) | Posisi Kelas & Catatan Teknis |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **GeForce RTX 5090 Laptop GPU** | `GB203-400` | 10.496 | **24 GB GDDR7** | 256-bit / **896 GB/s** | 95W – **175W** | Flagship desktop replacement & LLM lokal (setara silikon RTX 5080 Desktop). |
| **GeForce RTX 5080 Laptop GPU** | `GB203-250` | 7.680 | **16 GB GDDR7** | 256-bit / **896 GB/s** | 80W – **175W** | Kelas antusias tinggi; peningkatan VRAM menjadi 16 GB. |
| **GeForce RTX 5070 Ti Laptop GPU** | `GB205-200` | 5.888 | **12 GB GDDR7** | 192-bit / **672 GB/s** | 60W – **140W** | *Sweet-spot* baru kelas menengah-atas; mengatasi batas 8 GB VRAM. |
| **GeForce RTX 5070 Laptop GPU** | `GB206-300` | 4.608 | **8 GB** *(atau 12 GB SKU tertentu)* **GDDR7** | 128-bit / **384 GB/s** | 50W – **115W** | Menengah; kapasitas standar 8 GB membatasi tekstur Ultra 1440p di gim berat. |
| **GeForce RTX 5060 Laptop GPU** | `GB206-200` | 3.328 | **8 GB GDDR7** | 128-bit / **384 GB/s** | 45W – **115W** | Arus utama (*mainstream*) dengan bandwidth tinggi 384 GB/s. |
| **GeForce RTX 5050 Laptop GPU** | `GB207-300` | 2.560 | **8 GB GDDR7** | 128-bit / **384 GB/s** | 35W – **100W+** | Entry-level gaming & kreator; naik dari 6 GB (RTX 4050) menjadi 8 GB GDDR7. |

* **Workstation & Linux**: Lini profesional **NVIDIA RTX PRO 500–5000 Blackwell** menyediakan driver tersertifikasi **ISV** dan opsi ECC. Di Linux, NVIDIA mengandalkan **NVIDIA Open GPU Kernel Modules (`nvidia-open`)** + ruang pengguna proprietari (mendukung penuh CUDA, OptiX, TensorRT, NVENC, dan Wayland Explicit Sync).

### B. AMD Radeon & Intel Arc Laptop
* **AMD iGPU & dGPU**: *Radeon 700M (RDNA 3)*, *Radeon 800M (RDNA 3.5 — hingga 16 CU pada Radeon 890M)*, **Radeon 8060S (40 CU RDNA 3.5 pada Strix Halo, setara dGPU RTX 4060/4070)**, serta dGPU *Radeon RX 7600S/7700S/7900M*. Di Linux didukung 100% secara terbuka oleh kernel **`amdgpu` + Mesa (`RADV` / `RadeonSI`)**.
* **Intel Arc**: *Xe-LPG (Arc 140T)*, *Xe2-LPG (Arc 140V Battlemage dengan 64 XMX engines)*, *Xe3-LPG (Arc B390 Celestial hingga 12 Xe3-cores)*, serta lini workstation **Intel Arc Pro B-Series**. Didukung driver kernel terbuka **`xe` / `i915` + Mesa `ANV`**.

---

## 7.3 Mengapa Dua Laptop dengan Model GPU Sama Memiliki Performa Berbeda Jauh?

```
====================================================================================
           PERUTEAN SINYAL TAMPILAN: OPTIMUS vs. MUX SWITCH / ADVANCED OPTIMUS
====================================================================================
  [Mode 1: MSHybrid / Optimus Standar — Penalti Performa 5%–15%]
  ┌──────────┐    PCIe Bus     ┌──────────┐   Display Engine   ┌───────────────┐
  │   dGPU   │ ──────────────► │   iGPU   │ ─────────────────► │ Layar Internal│
  │ (Render) │  (Salin Frame)  │(Pass-thru│                    │    Laptop     │
  └──────────┘                 │  Buffer) │                    └───────────────┘
                               └──────────┘

  [Mode 2: MUX Switch / Advanced Optimus — Jalur Langsung 100% Performa]
  ┌──────────┐                 ┌──────────┐   ┌────────────┐   ┌───────────────┐
  │   dGPU   │ ────────────────┼─────────────► │ MUX Switch │ ─► │ Layar Internal│
  └──────────┘                 │   iGPU   │ ─► │ (Hardware) │   │    Laptop     │
                               └──────────┘   └────────────┘   └───────────────┘
```

1. **Alokasi Daya TGP (Watt)**: Selisih antara TGP rendah (45W–55W) dan TGP penuh (115W–175W) pada GPU bernama sama menghasilkan perbedaan performa **25%–35%**.
2. **Kapasitas Pendingin Sasis & Shared Heat Pipes**.
3. **MUX Switch & Advanced Optimus**: Menghilangkan salin-frame melintasi bus PCIe ke iGPU (+5%–15% FPS dan mengaktifkan G-SYNC/FreeSync internal).
4. **Perutean Port Output Eksternal** (*direct-to-dGPU* vs *routed-to-iGPU*).
5. **Konfigurasi Memori Sistem** (*dual-channel* sangat krusial bagi iGPU).
6. **Profil Daya Firmware/BIOS** (*Quiet / Balanced / Performance / Turbo*).
7. **Kapasitas VRAM vs. Resolusi Target** (mencegah *PCIe VRAM thrashing* ketika tekstur melampaui 8 GB).
