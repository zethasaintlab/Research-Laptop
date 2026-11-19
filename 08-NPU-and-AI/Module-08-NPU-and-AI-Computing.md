# Module 08 — NPU & AI Computing (Akselerasi Kecerdasan Buatan & Ekosistem AI PC)

## 8.1 Arsitektur Komputasi AI Heterogen & Hukum Roofline

```
====================================================================================
               ARSITEKTUR KOMPUTASI AI HETEROGEN PADA LAPTOP MODERN
====================================================================================
                          [Beban Kerja AI & Aplikasi]
                                       │
         ┌─────────────────────────────┼─────────────────────────────┐
         ▼                             ▼                             ▼
┌─────────────────────┐     ┌─────────────────────┐     ┌─────────────────────┐
│   CPU (Generalist)  │     │ NPU (AI Specialist) │     │ GPU (Parallel Beast)│
│ • Kontrol alur &    │     │ • Sirkuit MAC padat │     │ • Ribuan Tensor /   │
│   pra-pemrosesan    │     │   (Systolic / Tile) │     │   XMX Matrix Cores  │
│ • Daya: 10W–45W     │     │ • Daya: 1W–5W       │     │ • Daya: 25W–175W    │
└──────────┬──────────┘     └──────────┬──────────┘     └──────────┬──────────┘
           └───────────────────────────┼───────────────────────────┘
                                       ▼
         ┌───────────────────────────────────────────────────────────┐
         │              SUBSISTEM MEMORI & LEBAR PITA                │
         │  • Shared System RAM (DDR5 / LPDDR5X: 90–153 GB/s)        │
         │  • High-Bandwidth UMA (Apple Max / Strix Halo: 256–546GB/s)│
         │  • Dedicated VRAM (GDDR6 / GDDR7: 384–896 GB/s)           │
         └───────────────────────────────────────────────────────────┘
```

* **Format Presisi & Kuantisasi**: Kompresi bobot model dari **FP16 / BF16** (16-bit) ke **INT8 / FP8** (8-bit) atau **INT4 / FP4** (4-bit, seperti `GGUF Q4_K_M`, `AWQ`, `GPTQ`) memangkas ukuran memori hingga 75%.
* **Hukum Roofline (`Compute-Bound` vs. `Memory-Bandwidth-Bound`)**:
  * Tahap *Prompt Prefill* dan difusi gambar bersifat *compute-bound* (ditentukan oleh **TOPS / TFLOPS**).
  * Tahap *Token Generation* LLM bersifat *memory-bandwidth-bound*:
    $$\text{Batas Maksimum Token/Detik} \approx \frac{\text{Memory Bandwidth (GB/s)}}{\text{Ukuran Bobot Model di Memori (GB)}}$$
    Oleh karena itu, NPU 50 TOPS pada RAM 120 GB/s tidak dapat menandingi GPU RTX 5080 (896 GB/s) dalam kecepatan pengetikan jawaban LLM.

---

## 8.2 Implementasi Silikon Akselerator AI Lintas Vendor & Standar Copilot+ PC

| Vendor & Nama Akselerator | Generasi & Arsitektur Silikon | Kinerja Puncak (Klaim Vendor) | Dukungan Presisi Perangkat Keras | Runtime & Ekosistem Software Utama |
| :--- | :--- | :--- | :--- | :--- |
| **Intel AI Boost** | NPU 3 (*Meteor/Arrow Lake*), NPU 4 (*Lunar Lake*), NPU 5 (*Panther Lake*). | 11,5 – **50 TOPS** *(hingga ~180 TOPS total platform)* | INT8, FP16 *(NPU 3/4)*; ditambah **FP8 & INT4** *(NPU 5)*. | **Intel OpenVINO**, DirectML, ONNX Runtime, driver upstream Linux **`intel_vpu` (`ivpu`)**. |
| **AMD Ryzen AI (XDNA)** | XDNA 1 (*Ryzen 7040/8040*), XDNA 2 (*Ryzen AI 300 & AI Max*). | 10 – **55 TOPS** *(INT8)* | INT8, INT4, FP16, serta **Block FP16** native *(XDNA 2)*. | **AMD Ryzen AI Software**, ONNX Runtime, DirectML, driver upstream Linux **`amdxdna`**. |
| **Qualcomm Hexagon NPU** | Snapdragon X (`X1` Gen-1 & `X2` Gen-2). | **45 TOPS** (Gen-1) / **~80 TOPS** (Gen-2) | INT8, INT4, FP16. | **Qualcomm AI Engine Direct (QNN)**, Windows Copilot Runtime, ONNX Runtime QNN EP. |
| **Apple Neural Engine (ANE)** | M3, M4, & M5 16-core ANE (+ GPU Neural Accelerators pada M5). | 18 – **38+ TOPS** (+ akselerasi ARM SME di CPU). | FP16, INT8. | **Apple CoreML**, Metal Performance Shaders, dan **Apple MLX**. |
| **NVIDIA Tensor Cores** *(dGPU)* | 4th-Gen (*RTX 40*) & 5th-Gen (*RTX 50 Blackwell*). | **194 – 1.824 AI TOPS** *(dengan Sparsity)* | FP16, BF16, TF32, INT8, INT4, **FP8**, & **FP4** *(Blackwell)*. | **CUDA**, **TensorRT-LLM**, PyTorch, llama.cpp / Ollama (Windows & Linux). |

* **Standar Microsoft Copilot+ PC**: Mewajibkan NPU minimal **40+ TOPS (INT8)**, RAM minimal **16 GB**, dan SSD minimal **256 GB**.

---

## 8.3 Pemetaan Beban Kerja AI Lokal Nyata

| Beban Kerja AI Nyata | Unit Pemroses Utama | Bottleneck Teknis Utama | Konfigurasi Perangkat Keras Ideal |
| :--- | :--- | :--- | :--- |
| **Efek Kamera & Audio Rapat** | **NPU** (1W–3W) | Tidak ada. | Semua prosesor modern dengan NPU terintegrasi (10+ TOPS). |
| **Transkripsi Suara Lokal (Whisper)** | **NPU** atau **iGPU** | Latensi transfer memori kecil. | NPU 40+ TOPS atau iGPU modern (*Arc 140V / Radeon 890M*). |
| **LLM Lokal Ringan (7B–9B, 4-bit)** | **GPU / iGPU kuat** atau **NPU** | **Memory Bandwidth (GB/s)**. | Minimal RAM **16–32 GB** cepat (LPDDR5X-7500+) atau dGPU **VRAM ≥ 8 GB**. |
| **LLM Lokal Menengah–Besar (14B–32B)** | **dGPU Kelas Atas** atau **UMA Lebar Pita Tinggi** | **Kapasitas VRAM / UMA (12–24 GB)** + Bandwidth. | **RTX 5070 Ti / 5080 / 5090 Laptop**, atau **Apple M-Pro/Max (36–64GB)** / **AMD Strix Halo**. |
| **LLM Lokal Skala Workstation (70B+)** | **High-Capacity UMA** | **Kapasitas Memori Terpadu (≥ 64–128 GB)**. | **MacBook Pro M3/M4/M5 Max (64–128 GB)** atau **Workstation AMD Ryzen AI Max+ 395 (128 GB)**. |
| **Generasi Gambar & Video Difusi** | **dGPU NVIDIA (Tensor Cores)** | **Komputasi Matriks FP8/FP4** + **Kapasitas VRAM**. | **NVIDIA GeForce RTX 4070/4080/5070 Ti/5080/5090 Laptop** (ekosistem CUDA/PyTorch). |
