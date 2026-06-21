# Dokumentasi Hasil Kerja - Tren Teknologi & Perencanaan Karier
**Nama File Pengumpulan:** Algoritma_P15_23343073_M_Gilang_Mulya_Putra  
**Mata Kuliah:** Praktikum Pemrograman Mobile / Tugas P15  
**Komponen Pengumpulan:** Link Dokumen (README/Notion) & Link Diagram Pohon Keputusan

---

## 1. Kerangka Analisis Tren Reusable (Reusable Framework)

Kerangka kerja ini dirancang untuk mengevaluasi teknologi baru secara sistematis dan dapat digunakan kembali untuk tren teknologi apa pun di masa mendatang.

### Langkah-Langkah Kerangka Kerja (Framework Steps)
1. **Identifikasi Tren:** Menentukan teknologi baru yang sedang berkembang, mendefinisikan fundamentalnya, serta melacak akar sejarah kemunculannya.
2. **Pencarian Bukti Adopsi:** Mengumpulkan data empiris, studi kasus perusahaan besar, atau statistik global yang membuktikan bahwa tren tersebut benar-benar diadopsi di industri nyata (bukan sekadar spekulasi).
3. **Analisis Pendorong & Hambatan (Drivers & Barriers):** Mengidentifikasi faktor makro/mikro yang mempercepat adopsi teknologi (pendorong) serta batasan teknis atau regulasi yang memperlambat implementasinya (hambatan).
4. **Identifikasi Peluang untuk Flutter Developer:** Menghubungkan kapabilitas ekosistem Flutter (package, plugin, platform channels) dengan kebutuhan teknis tren tersebut.
5. **Perumusan Rekomendasi:** Menyusun langkah strategis konkret yang harus diambil oleh developer atau organisasi untuk merespons tren tersebut.

### Contoh Penerapan Kerangka: Analisis Tren "AI on-Device"

* **Identifikasi Tren:** AI on-device (Edge AI) adalah proses menjalankan model kecerdasan buatan langsung di perangkat keras lokal (smartphone) tanpa bergantung penuh pada pemrosesan server cloud. Sejarahnya berakar dari pergeseran model Cloud AI yang berat menuju efisiensi komputasi lokal berkat kehadiran chip khusus seperti NPU (Neural Processing Unit) sejak tahun 2017 hingga berkembang pesat pada rentang 2024–2026.
* **Pencarian Bukti Adopsi:** * *Google:* Integrasi model Gemini Nano langsung di tingkat sistem operasi Android (Pixel series).
    * *Apple:* Peluncuran Apple Intelligence yang memproses data bahasa dan visual secara lokal di perangkat iPhone berspesifikasi tinggi.
    * *Aplikasi Finansial:* Penerapan modul e-KYC dan *liveness detection* luring (offline) untuk verifikasi wajah pengguna baru tanpa membebani server.
* **Analisis Pendorong dan Hambatan:**
    * *Pendorong:* Pemrosesan instan tanpa latensi internet, penghematan biaya infrastruktur server cloud berskala besar, serta jaminan privasi data yang mutlak karena data sensitif tidak pernah keluar dari perangkat pengguna.
    * *Hambatan:* Keterbatasan kapasitas RAM dan baterai pada smartphone kelas menengah ke bawah (*low-to-mid end*) serta fragmentasi spesifikasi hardware yang sangat tinggi, khususnya di pasar Indonesia.
* **Identifikasi Peluang untuk Flutter Developer:**
    Developer Flutter dapat memanfaatkan kedekatan arsitektur cross-platform dengan native menggunakan package seperti `google_ml_kit` untuk kebutuhan AI mendasar atau runtime kustom seperti `tflite_flutter` dan `onnxruntime_flutter` untuk memuat model *Small Language Models* (SLMs) buatan tim Data Science internal.
* **Perumusan Rekomendasi:**
    Bagi developer mobile, mulailah menggeser paradigma dari sekadar melakukan integrasi REST API berbasis Cloud AI menuju penguasaan teknik *asynchronous programming* tingkat lanjut (seperti Dart Isolates) guna menangani beban kerja komputasi model lokal tanpa mengorbankan kelancaran antarmuka (UI).

---

## 2. Urutan Langkah Mempersiapkan & Merekam Future Tech Talk

Untuk menghasilkan presentasi teknis yang profesional dan berdampak tinggi, berikut adalah urutan langkah terstruktur yang harus dilewati:

[Pemilihan Topik] ──> [Riset Primer] ──> [Narasi] ──> [Slide Visual] ──> [Latihan] ──> [Rekaman] ──> [Promosi]


### 1. Pemilihan Topik Tren
Pilih satu tren spesifik yang memiliki urgensi tinggi dan relevan dengan ekosistem mobile, contohnya: *"Masa Depan Pemrosesan Bahasa Alami di Smartphone Menggunakan Flutter"*. Hindari topik yang terlalu luas agar pembahasan bisa mendalam dalam durasi yang ditentukan.

### 2. Riset dari Sumber Primer
Gali landasan teori dan perkembangan terbaru langsung dari pembuat teknologi atau literatur ilmiah terpercaya:
* **Google I/O & Flutter Forward:** Untuk melihat roadmap resmi, fitur framework terbaru, dan studi kasus eksperimental dari Google.
* **arXiv:** Menyisir paper ilmiah terbaru mengenai teknik kompresi model AI (*quantization* dan *pruning*) agar penjelasan memiliki landasan akademik yang kuat.

### 3. Penyusunan Narasi yang Meykinkan
Gunakan struktur penceritaan (storytelling) yang logis untuk mempertahankan perhatian audiens:
* *The Hook (Menit 1):* Paparkan masalah nyata di industri saat ini (misal: biaya server cloud AI yang membengkak).
* *The Solution (Menit 2-5):* Perkenalkan tren teknologi terpilih sebagai jawaban mutakhir atas masalah tersebut.
* *The Technical Deep Dive (Menit 6-12):* Bedah arsitektur teknis dan bagaimana implementasinya di Flutter.
* *The Conclusion (Menit Akhir):* Berikan rangkuman dan ajakan bertindak (*call to action*) bagi para developer.

### 4. Pembuatan Slide Visual
Desain slide dengan prinsip minimalis dan fungsional:
* Gunakan grafik, diagram arsitektur, atau potongan kode (*code snippets*) yang bersih daripada deretan teks paragraf yang padat.
* Gunakan kontras warna yang tinggi (misalnya tema gelap dengan aksen warna neon terang untuk teks penting).

### 5. Latihan Presentasi
* Lakukan simulasi berbicara di depan cermin atau rekam suara sendiri untuk mengukur ketepatan waktu durasi presentasi.
* Latih intonasi suara agar tidak monoton dan pastikan artikulasi istilah teknis (seperti *tensor, inference, asynchronous*) diucapkan dengan jelas.

### 6. Rekaman dengan Loom atau OBS
* **OBS Studio:** Gunakan jika ingin resolusi tinggi dengan pengaturan tata letak layar (*layout*) yang kompleks (misal: wajah presenter di pojok bawah dalam bentuk lingkaran, disandingkan dengan jendela slide presentasi).
* **Loom:** Gunakan untuk efisiensi tinggi karena video langsung terunggah ke cloud begitu rekaman selesai dan siap dibagikan melalui tautan.

### 7. Pengunggahan dan Promosi di Forum Digital
Unggah hasil video ke platform publik seperti YouTube (atur sebagai *Unlisted* jika untuk keperluan internal kuliah) atau LinkedIn. Tulis deskripsi singkat (*caption*) yang menarik perhatian, sertakan repositori GitHub dari kode contoh, dan bagikan ke komunitas developer (seperti Flutter Indonesia) untuk mendapatkan umpan balik.

---

## 3. Pohon Keputusan (Decision Tree) Spesialisasi Karier

Berikut adalah visualisasi struktur logika bercabang dalam menentukan spesialisasi karier mobile developer berdasarkan kekuatan teknis, kebutuhan ekosistem Flutter, dan realitas pasar lokal di Indonesia.

### Visualisasi Diagram Struktur Makro Pohon Keputusan
Tautan ini dapat Anda gunakan sebagai referensi atau lampiran diagram resmi pada dokumen submisi Anda:

http://googleusercontent.com/image_generation_content/0

### Representasi Logika Pohon Keputusan (Text-Based)

[START: Memilih Spesialisasi Karier Mobile]
│
├───> [1. Apa Kekuatan Teknis Saya Saat Ini?]
│       ├── Keahlian Matematika & Algoritma Kuat ───> Lanjut ke Evaluasi AI
│       ├── Pemahaman Hardware & Low-Level C++ ────> Lanjut ke Evaluasi IoT
│       └── Manajemen State & UI/UX Flutter Kuat ──> Lanjut ke Evaluasi Super Apps / PWA
│
├───> [2. Tren Mana yang Paling Banyak Membutuhkan Keahlian Flutter?]
│       ├── Tinggi (Dukungan plugin native siap pakai matang) ──> AI on-Device / Super Apps
│       └── Sedang (Membutuhkan konfigurasi jembatan hardware) ──> IoT / PWA
│
└───> [3. Di mana Peluang Pasar Terbesar di Kota/Provinsi Saya?]
├── Kota Besar/Pusat Finansial (Jakarta/Surabaya/Nasional Remote)
│     ├── Korporasi besar & Unicorn butuh optimasi internal ──> PILIHAN: Super Apps / AI Developer
│     └── Sektor Perbankan Digital/Fintech membutuhkan e-KYC ──> PILIHAN: Mobile AI Specialist
│
└── Wilayah Berkembang/Industri (Sumatera Barat/Daerah Sentra UMKM)
├── Kebutuhan efisiensi operasional biaya rendah ────────> PILIHAN: PWA / IoT Integration
└── Digitalisasi layanan publik instansi lokal ──────────> PILIHAN: Flutter Core / Super Apps Lokal


### Penjelasan Logika Pengambilan Keputusan:
* Jika Anda memiliki dasar yang kuat pada logika data dan manipulasi thread di Flutter, serta target pasar Anda adalah perusahaan teknologi skala besar (*Unicorn/Fintech*) di Indonesia, maka jalur **Mobile AI Developer (on-Device)** adalah keputusan yang paling tepat.
* Jika kekuatan Anda berada pada interaksi perangkat keras dan pasar lokal Anda didomina
