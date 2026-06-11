# Algoritma_P13_23343073_MGilangMulyaPutra

# 1. Algoritma Evaluasi Arsitektur Proyek Baru

## Flowchart Pemilihan Arsitektur

START

↓

Identifikasi ukuran tim

↓

Apakah tim ≤ 2 orang?

├─ Ya → Pertimbangkan MVC atau MVVM sederhana

└─ Tidak

↓

Apakah tim > 5 orang?

├─ Ya → Pertimbangkan Clean Architecture

└─ Tidak

↓

Evaluasi kompleksitas domain bisnis

↓

Apakah bisnis sederhana?

├─ Ya → MVC

└─ Tidak

↓

Apakah banyak aturan bisnis?

├─ Ya → MVVM atau Clean Architecture

└─ Tidak → MVVM

↓

Evaluasi kebutuhan testability

↓

Apakah unit test menjadi prioritas?

├─ Ya → Clean Architecture

└─ Tidak

↓

Evaluasi timeline proyek

↓

Apakah deadline sangat ketat?

├─ Ya → MVC atau MVVM

└─ Tidak → Clean Architecture

↓

Pilih arsitektur

↓

Dokumentasikan alasan pemilihan

↓

END

---

## Kriteria Pemilihan

### MVC

Cocok jika:

* Tim kecil
* Fitur sederhana
* Deadline singkat

### MVVM

Cocok jika:

* Kompleksitas menengah
* Membutuhkan state management yang baik
* Testability cukup penting

### Clean Architecture

Cocok jika:

* Tim besar
* Domain kompleks
* Proyek jangka panjang
* Testability tinggi

---

# 2. Pair Programming Virtual dengan VS Code Live Share

## Langkah 1 - Membuka Sesi Live Share

Host:

* Membuka project di VS Code
* Menjalankan Live Share
* Membagikan link sesi

Peserta:

* Join menggunakan link

Risiko:

* Koneksi internet tidak stabil

---

## Langkah 2 - Menentukan Driver dan Navigator

Driver:

* Mengetik kode

Navigator:

* Memberikan arahan
* Memikirkan solusi

Contoh:

Developer A = Driver

Developer B = Navigator

Rotasi setiap 20 menit.

Risiko:

* Salah satu anggota pasif

---

## Langkah 3 - Mendesain ViewModel

Diskusi:

* State yang dibutuhkan
* Event yang tersedia
* Repository yang digunakan

Output:

ProductViewModel

---

## Langkah 4 - Implementasi Bersama

Driver:

* Menulis kode

Navigator:

* Mengawasi desain
* Mengidentifikasi bug

Contoh:

class ProductViewModel {
...
}

Risiko:

* Konflik desain

---

## Langkah 5 - Code Review Singkat

Checklist:

* Naming convention
* Separation of concerns
* Error handling
* Testability

Risiko:

* Review terlalu terburu-buru

---

## Langkah 6 - Commit dan Push

Commit:

git commit -m "Add ProductViewModel"

Push ke repository.

---

## Langkah 7 - Dokumentasi GitHub

Tambahkan:

* Tujuan sesi
* Anggota yang terlibat
* Hasil implementasi
* Temuan selama diskusi

Output:

README atau Wiki GitHub

---

# 3. Prosedur Refactoring God Widget menjadi MVVM

## Kondisi Awal

God Widget:

* UI
* Business Logic
* API Call
* State Management

berada dalam satu file.

Risiko:

* Sulit diuji
* Sulit dipelihara

---

## Langkah 1 - Identifikasi Fungsionalitas

Pisahkan:

* UI
* Business Logic
* Data Access

Risiko:

* Salah memahami alur aplikasi

---

## Langkah 2 - Dokumentasikan Perilaku Saat Ini

Catat:

* Input
* Output
* Skenario penggunaan

Tujuan:

Mencegah perubahan perilaku aplikasi.

Risiko:

* Fitur penting terlewat

---

## Langkah 3 - Tambahkan Testing

Buat:

* Unit Test
* Widget Test

Tujuan:

Sebagai safety net.

Risiko:

* Refactoring tanpa pengujian

---

## Langkah 4 - Ekstrak Model

Pindahkan:

* Data class
* Entity

ke folder model.

Contoh:

product_model.dart

Risiko:

* Mapping data rusak

---

## Langkah 5 - Ekstrak Repository

Pindahkan:

* API Call
* Database Access

ke repository.

Contoh:

product_repository.dart

Risiko:

* Error dependency

---

## Langkah 6 - Buat ViewModel

Pindahkan:

* Business Logic
* State

ke ViewModel.

Contoh:

product_viewmodel.dart

Risiko:

* State tidak sinkron

---

## Langkah 7 - Hubungkan UI ke ViewModel

UI hanya:

* Menampilkan state
* Mengirim event

UI tidak lagi:

* Memanggil API langsung

Risiko:

* UI gagal menerima update state

---

## Langkah 8 - Jalankan Testing

Verifikasi:

* Semua fitur tetap berjalan
* Tidak ada regresi

Risiko:

* Bug tersembunyi

---

## Langkah 9 - Code Review

Periksa:

* Dependency
* Naming
* Arsitektur

Tujuan:

Menjaga konsistensi MVVM.

---

## Langkah 10 - Deploy Bertahap

Gunakan:

* Internal testing
* Beta testing

Sebelum production release.

Risiko:

* Bug muncul pada pengguna akhir

Mitigasi:

* Monitoring
* Rollback plan

---

# Link Diagram

Diagram flowchart dibuat menggunakan:

* Draw.io
* Lucidchart
* Mermaid
* Canva

Lampirkan link diagram pada submission bersama link dokumen.

