# Algoritma_P14_23343073_MGilangMulyaPutra

# 1. Checklist Keamanan Pra-Rilis Aplikasi Flutter

## A. Audit Dependencies

### Checklist

* [ ] Jalankan `flutter pub outdated`
* [ ] Periksa package yang sudah deprecated
* [ ] Hapus package yang tidak digunakan
* [ ] Periksa kerentanan package pihak ketiga

### Verifikasi

* Tidak ada package dengan vulnerability kritis
* Semua dependency menggunakan versi stabil terbaru

---

## B. Pemeriksaan AndroidManifest.xml

### Checklist

* [ ] android:allowBackup="false"
* [ ] android:debuggable="false"
* [ ] Tidak ada permission yang tidak diperlukan
* [ ] Network Security Config sudah benar

### Verifikasi

* APK release tidak dapat di-debug
* Backup aplikasi dinonaktifkan

---

## C. Pemeriksaan Info.plist (iOS)

### Checklist

* [ ] ATS (App Transport Security) aktif
* [ ] Permission hanya yang diperlukan
* [ ] Tidak ada konfigurasi debug

### Verifikasi

* Seluruh koneksi menggunakan HTTPS

---

## D. Verifikasi Secure Storage

### Checklist

* [ ] Token tidak disimpan di SharedPreferences
* [ ] Token disimpan di Flutter Secure Storage
* [ ] Password tidak pernah disimpan plaintext

### Verifikasi

* Access token berhasil dibaca dari Secure Storage
* Tidak ditemukan token di local cache biasa

---

## E. Pengujian Certificate Pinning

### Checklist

* [ ] Certificate pinning aktif
* [ ] Sertifikat valid
* [ ] Pengujian terhadap sertifikat palsu

### Verifikasi

* Koneksi ditolak saat menggunakan sertifikat tidak valid

---

## F. Aktivasi Code Obfuscation

### Checklist

* [ ] Build release menggunakan obfuscation
* [ ] Symbol map tersimpan

Command:

flutter build apk --release --obfuscate --split-debug-info=debug-info

### Verifikasi

* Nama class tidak mudah dibaca setelah decompile

---

# 2. Flowchart Penanganan Token yang Aman

START

↓

Login Berhasil

↓

Terima Access Token + Refresh Token

↓

Simpan ke Flutter Secure Storage

↓

Kirim Request API

↓

Apakah Response = 401?

├── Tidak

│ ↓

│ Request Berhasil

│ ↓

│ END

│

└── Ya

↓

Refresh Token Masih Valid?

├── Ya

│ ↓

│ Request Refresh Token

│ ↓

│ Simpan Token Baru

│ ↓

│ Ulangi Request Awal

│ ↓

│ END

│

└── Tidak

↓

Hapus Token dari Storage

↓

Logout User

↓

Redirect ke Login Page

↓

END

---

# 3. Prosedur Security Audit Sederhana

## Langkah 1 - Memahami Struktur Proyek

Periksa:

* pubspec.yaml
* AndroidManifest.xml
* Info.plist
* Struktur folder

Tujuan:

Memahami area yang berpotensi sensitif.

---

## Langkah 2 - Identifikasi Penyimpanan Data

Cari:

* SharedPreferences
* Secure Storage
* SQLite
* Hive

Pertanyaan:

Apakah data sensitif disimpan dengan aman?

---

## Langkah 3 - Identifikasi Anti-Pattern Keamanan

Contoh:

### Buruk

Token di SharedPreferences

API Key hardcoded

HTTP tanpa HTTPS

Logging password

Certificate pinning tidak ada

### Baik

Token di Secure Storage

HTTPS aktif

Secret tidak tersimpan di source code

---

## Langkah 4 - Review Komunikasi API

Periksa:

* HTTPS digunakan?
* JWT digunakan?
* Refresh token tersedia?
* Error 401 ditangani?

---

## Langkah 5 - Review Dependency

Periksa:

pubspec.yaml

Cari:

* Package tidak terawat
* Package rentan

---

## Langkah 6 - Memberikan Komentar GitHub

Format:

### Temuan

Access token masih disimpan di SharedPreferences.

### Risiko

Token dapat diekstrak pada perangkat yang telah di-root.

### Rekomendasi

Gunakan flutter_secure_storage untuk menyimpan token.

---

## Langkah 7 - Dokumentasi Audit

Buat tabel:

| Temuan                     | Risiko | Prioritas | Rekomendasi    |
| -------------------------- | ------ | --------- | -------------- |
| Token di SharedPreferences | Tinggi | Tinggi    | Secure Storage |
| HTTP tanpa TLS             | Tinggi | Tinggi    | HTTPS          |

---

# Kesimpulan

Keamanan aplikasi mobile harus diperiksa sebelum rilis melalui audit dependency, konfigurasi platform, penyimpanan data, komunikasi API, dan hardening aplikasi. Security audit sederhana dapat membantu menemukan kerentanan sejak awal sehingga risiko keamanan di lingkungan produksi dapat diminimalkan.
