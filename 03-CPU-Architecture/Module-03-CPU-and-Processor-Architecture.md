# Module 03 — CPU & Processor Architecture (Arsitektur CPU & Prosesor)

## 3.1 Anatomi Chip Laptop Modern: Membedah Silikon di Balik Kemasan

```
====================================================================================
                     PAKET PROSESOR LAPTOP MODERN (SoC / MULTI-TILE)
====================================================================================
  ┌──────────────────────────────────────┐   ┌──────────────────────────────────┐
  │       COMPUTE ENGINE (CPU)           │   │     GRAPHICS ENGINE (iGPU)       │
  │  • P-Cores (Performance)             │   │  • Shader / Execution / Xe Cores │
  │  • E-Cores & LP-E Cores (Efficiency) │   │  • Ray Tracing & Tensor/XMX      │
  │  • Cache Hierarki (L1, L2, L3/LLC)   │   │  • Media Engine (Encode/Decode)  │
  └──────────────────┬───────────────────┘   └────────────────┬─────────────────┘
                     │                                        │
  ┌──────────────────┴────────────────────────────────────────┴─────────────────┐
  │              INTERCONNECT FABRIC & SYSTEM LEVEL CACHE (SLC)                 │
  │         (Ring Bus / AMD Infinity Fabric / Intel NoC / Apple Fabric)         │
  └───┬───────────────┬───────────────┬───────────────┬─────────────────────┬───┘
      │               │               │               │                     │
┌─────▼─────┐   ┌─────▼─────┐   ┌─────▼─────┐   ┌─────▼─────┐   ┌───────────▼───┐
│    NPU    │   │  ISP/DSP  │   │  MEMORY   │   │ SECURITY  │   │ I/O CONTROLLER│
│ (AI Boost │   │ (Kamera & │   │CONTROLLER │   │ PROCESSOR │   │ • Jalur PCIe  │
│ / XDNA /  │   │  Audio    │   │ (DDR5 /   │   │ (PSP/ME/  │   │ • USB4 / TB   │
│  Hexagon) │   │  Offload) │   │ LPDDR5X)  │   │  Pluton)  │   │ • Display Out │
└───────────┘   └───────────┘   └─────┬─────┘   └───────────┘   └───────┬───────┘
======================================╪=================================╪===========
                                      ▼                                 ▼
                             [DRAM Sistem (RAM)]             [Perangkat Eksternal]
                                                             (SSD NVMe, dGPU, Wi-Fi)
                                                                        │
                                                             ┌──────────▼──────────┐
                                                             │ EMBEDDED CONTROLLER │
                                                             │ (EC - Chip Terpisah │
                                                             │  di Motherboard:    │
                                                             │  Kipas, Baterai, KB)│
                                                             └─────────────────────┘
```

### Komponen Silikon & Pemaketan Utama
* **Unit Pemrosesan**: **CPU** (eksekusi instruksi serbaguna), **GPU / iGPU** (komputasi paralel vektor/piksel), **NPU** (akselerator matriks AI berdaya rendah 1W–5W), **ISP** (pemroses sinyal sensor kamera), dan **DSP** (pemroses sinyal audio & sensor siaga).
* **Pengendali & Keamanan**: **Integrated Memory Controller (IMC)**, **I/O Controller** (PCIe, USB4/Thunderbolt, DisplayPort/eDP), **PCH** (kini mayoritas dilebur ke dalam paket SoC), **Security Processor / Hardware Root-of-Trust** (*Intel CSME, AMD PSP, Microsoft Pluton, Apple Secure Enclave*), dan **Embedded Controller (EC)** (chip mikrokontroler terpisah di motherboard yang mengatur keyboard, kurva kipas, pengisian baterai, dan sensor suhu).
* **Anatomi Fisik**: **Die** (keping silikon tunggal), **Monolithic Die vs. Chiplet / Multi-Tile** (pemisahan fungsi ke beberapa keping silikon dalam satu paket menggunakan *Intel Foveros / EMIB* atau *TSMC CoWoS / fan-out*), **Process Node** (generasi kepadatan transistor seperti *TSMC N3E, N4P, Intel 18A*), serta **ISA** (*x86-64, ARM64*) vs. **Microarchitecture** (*Zen 5, Lion Cove, Cougar Cove, Oryon*).

---

## 3.2 Sepuluh Pilar Arsitektur CPU Modern

1. **ISA (`x86-64` vs. `ARM64`) & CISC vs. RISC**: CPU x86-64 modern menerjemahkan instruksi CISC panjang variabel (1–15 byte) menjadi operasi mikro internal mirip RISC (*micro-ops*), sedangkan ARM64 menggunakan instruksi panjang tetap 4 byte yang menyederhanakan dekoder lebar (8–10 wide) dan menyediakan 31 register tujuan umum.
2. **Topologi Core & Arsitektur Hibrida (`P-Core`, `E-Core`, `LP-E Core`)**: *P-Core* berfokus pada latensi rendah dan *IPC single-thread*; *E-Core* memaksimalkan kepadatan *multi-thread* per watt; *LP-E Core* berada di pulau daya rendah terisolasi untuk beban latar belakang tanpa menyalakan cache L3 utama.
3. **Simultaneous Multithreading (SMT) / Hyper-Threading**: Mengekspos dua *logical thread* per core fisik untuk mengisi unit eksekusi yang menganggur saat menunggu data memori (+20%–35% throughput multi-thread). Dihapus pada desain efisiensi ekstrem seperti *Intel Lion Cove / Cougar Cove* dan *Apple Silicon*.
4. **Clock Speed (`Base` vs. `Boost`) & IPC**: $\text{Kinerja Single-Core} \propto \text{IPC} \times \text{Frekuensi Clock}$. Perbandingan GHz hanya valid di dalam mikroarsitektur yang sama.
5. **Pipeline Architecture, Branch Prediction, & Out-of-Order Execution (OoOE)**: Prediktor cabang (seperti *two-ahead branch predictor* pada Zen 5) dan eksekusi spekulatif di luar urutan menjaga unit ALU tetap terisi penuh di tengah latensi memori.
6. **Hierarki Cache (`L1` $\rightarrow$ `L2` $\rightarrow$ `L3` $\rightarrow$ `SLC`) & Memory Controller**: Menjembatani *Memory Wall* antara inti CPU berkecepatan nanodetik dengan DRAM eksternal. *System Level Cache (SLC)* memungkinkan CPU, iGPU, dan NPU berbagi data tanpa menyentuh RAM luar.
7. **Interkoneksi CPU & Topologi NUMA**: *Ring Bus* atau *AMD Infinity Fabric* menghubungkan core dan cache. Desain *dual-CCD chiplet* (*Ryzen 7045HX / 9955HX*) memiliki perbedaan latensi akses antara intra-CCD dan lintas-CCD.
8. **Manajemen Daya (`DVFS`, `P-States`, `C-States`, `PL1/PL2/Tau`) & Thermal Throttling**: *PL2 / FPPT* mengatur lonjakan daya sesaat (*burst*), sedangkan *PL1 / SPL* mengatur batas daya berkelanjutan (*sustained*) sebelum suhu menyentuh $T_{j\text{max}}$ ($95^\circ\text{C}–105^\circ\text{C}$).
9. **Penjadwalan CPU (`Intel Thread Director` & `AMD CPPC`)**: Telemetri perangkat keras yang memberi tahu penjadwal OS (Windows 11 / Linux `EEVDF`) core mana yang paling efisien dan cepat untuk tiap utas.
10. **Virtualisasi Perangkat Keras & Keamanan Silikon**: Akselerasi `Intel VT-x / VT-d` dan `AMD-V / AMD-Vi` (*SLAT/EPT/RVI* dan *IOMMU*), serta fitur keamanan `NX/XD`, `SMEP/SMAP`, `CET Shadow Stack`, `AMD SME/SEV`, dan `ARM MTE`.
