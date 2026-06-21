# Dekomposisi Tren Teknologi & Roadmap Mobile AI Developer
**Nama File Pengumpulan:** Dekomposisi_P15_23343073_M_Gilang_Mulya_Putra  
**Mata Kuliah:** Praktikum Pemrograman Mobile / Tugas P15  

---

## 1. Dekomposisi Mendalam: AI on-Device

### • Definisi dan Sejarah Singkat
AI on-device (Edge AI) adalah proses menjalankan model kecerdasan buatan (inferensi) secara lokal langsung di perangkat keras pengguna (seperti smartphone), tanpa bergantung pada pemrosesan cloud atau koneksi internet konstan. 
* **Sejarah Singkat:** Dimulai dari ketergantungan penuh pada Cloud AI (2012–2017) yang membutuhkan *bandwidth* besar dan latensi tinggi. Terobosan terjadi sekitar tahun 2017–2020 dengan hadirnya chip khusus seperti Apple Neural Engine (ANE) dan Google TPU, serta framework ringan seperti TensorFlow Lite. Memasuki tahun 2024–2026, fokus bergeser ke arah menjalankan *Small Language Models* (SLMs) secara lokal di *smartphone mid-to-high end*.

### • Teknologi Pemungkin (Enabling Technologies)
Agar model AI yang berukuran gigabyte bisa berjalan di smartphone dengan RAM terbatas, digunakan beberapa teknologi berikut:
* **Hardware Acceleration:** NPU (Neural Processing Unit) pada chipset modern (Snapdragon, MediaTek Dimensity, Apple A-Series).
* **Model Optimization:** 
  * *Quantization:* Mengubah presisi bobot model (misal dari Float32 ke Int8) untuk memangkas ukuran model hingga 75% tanpa degradasi akurasi yang signifikan.
  * *Pruning:* Menghapus parameter atau koneksi saraf yang tidak terlalu berpengaruh pada hasil akhir.
* **Framework Inferensi Mobile:** TensorFlow Lite (TFLite), ONNX Runtime Mobile, Google ML Kit, Apple CoreML, dan ExecuTorch.

### • Contoh Implementasi Nyata
* **Google Pixel & Android:** Fitur *Magic Eraser*, transkripsi audio langsung (*Live Transcribe*), dan integrasi Gemini Nano secara offline.
* **Apple Intelligence:** Pemrosesan bahasa alami (NLP) dan koreksi teks lokal pada iOS perangkat terbaru.
* **Aplikasi Finansial/E-commerce:** Pemindaian kartu kredit otomatis (OCR), verifikasi wajah (Liveness Detection) saat *e-KYC*, dan rekomendasi produk lokal berdasarkan riwayat enkripsi di perangkat.

### • Peluang untuk Developer Flutter
Flutter memiliki ekosistem yang siap mendukung integrasi ini melalui mekanisme *interoperability* yang matang:
* **Penggunaan Package Siap Pakai:** Memanfaatkan `google_ml_kit` untuk kebutuhan umum (Face Detection, Text Recognition, Object Tracking).
* **Eksekusi Model Kustom:** Menggunakan `tflite_flutter` atau `onnxruntime_flutter` untuk menjalankan model `.tflite` atau `.onnx` yang sudah dilatih sendiri.
* **Platform Channels & FFI:** Membuka peluang bagi developer Flutter untuk menulis kode performa tinggi di sisi *native* (C++, Kotlin, Swift) guna mengakses akselerasi NPU secara langsung jika belum didukung oleh *package* pub.dev.

### • Tantangan Adopsi di Indonesia
* **Fragmentasi Perangkat:** Pasar Indonesia didominasi oleh perangkat *low-to-mid end* dengan kapasitas RAM 4GB–6GB dan chipset tanpa NPU dedikasi. Developer harus membatasi ukuran model agar tidak memicu *Out-of-Memory* (OOM).
* **Konsumsi Baterai & Suhu:** Inferensi AI lokal yang terus-menerus menguras daya baterai lebih cepat dan meningkatkan suhu perangkat.
* **Kurangnya Dokumentasi & Talent:** Mayoritas developer mobile lokal masih berfokus pada integrasi REST API konvensional; pemahaman tentang arsitektur model AI, ukuran *tensor*, dan *pipeline* pra-pemrosesan data masih jarang dikuasai.

### • Proyeksi 3–5 Tahun ke Depan
* **Era Everywhere SLM:** Aplikasi mobile standar di masa depan akan dibekali *Small Language Model* internal (~1B–3B parameter) untuk fitur asisten pintar offline yang memahami konteks lokal pengguna.
* **Privasi Mutlak secara Default:** Regulasi data privasi yang semakin ketat akan memaksa industri finansial dan kesehatan di Indonesia memproses data sensitif di sisi klien menggunakan AI on-device.
* **Standardisasi Framework Cross-Platform:** Framework seperti Flutter akan memiliki dukungan *first-party* yang lebih mulus untuk *hardware-accelerated inference*, menyamakan performa *cross-platform* dengan *native*.

---

## 2. Roadmap Menjadi Mobile AI Developer (Berbasis Flutter)
