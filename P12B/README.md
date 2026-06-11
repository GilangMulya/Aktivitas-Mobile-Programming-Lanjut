# Algoritma_P12_23343073_MGilangMulyaPutra

# 1. Decision Tree Pemilihan Mekanisme Penyimpanan Data

## Diagram (Versi Teks)

START

│

├── Apakah data sensitif?

│   │

│   ├── YA

│   │   ├── Apakah berupa token atau kredensial?

│   │   │   ├── YA → Flutter Secure Storage

│   │   │   └── TIDAK

│   │   │

│   │   ├── Apakah membutuhkan query kompleks?

│   │   │   ├── YA → SQLite + Encryption

│   │   │   └── TIDAK → Hive + Encryption

│   │

│   └── TIDAK

│       ├── Apakah membutuhkan query kompleks?

│       │   ├── YA

│       │   │   ├── Apakah data berukuran besar?

│       │   │   │   ├── YA → SQLite

│       │   │   │   └── TIDAK → Isar

│       │

│       │   └── TIDAK

│       │       ├── Apakah hanya key-value sederhana?

│       │       │   ├── YA → SharedPreferences

│       │       │   └── TIDAK → Hive

│       │

│       ├── Apakah perlu sinkronisasi real-time?

│       │   ├── YA → Firebase / Supabase

│       │   └── TIDAK

│       │

│       ├── Apakah harus tersedia offline?

│       │   ├── YA → Local Cache

│       │   └── TIDAK → API Only

END

---

# 2. Algoritma Audit Keamanan Penyimpanan Data Flutter

## Langkah 1 - Identifikasi Semua Titik Penyimpanan

Periksa:

* SharedPreferences
* Flutter Secure Storage
* Hive
* Isar
* SQLite
* File Storage
* Cache Directory

Output:
Daftar seluruh lokasi penyimpanan data.

Risiko:
Data sensitif tersebar di banyak lokasi.

---

## Langkah 2 - Klasifikasi Sensitivitas Data

Kategori:

### Tinggi

* Password
* Access Token
* Refresh Token
* Informasi pembayaran

### Sedang

* Profil pengguna
* Riwayat transaksi

### Rendah

* Tema aplikasi
* Preferensi UI

Output:
Matriks sensitivitas data.

---

## Langkah 3 - Evaluasi Mekanisme Penyimpanan

Pertanyaan:

* Apakah token berada di Secure Storage?
* Apakah database terenkripsi?
* Apakah backup Android dinonaktifkan?
* Apakah data sensitif tersimpan dalam cache?

Output:
Daftar temuan keamanan.

---

## Langkah 4 - Analisis Risiko

Contoh:

Temuan:
Token berada di SharedPreferences

Risiko:
Account takeover

Severity:
High

---

## Langkah 5 - Rekomendasi Perbaikan

Contoh:

Masalah:
Token di SharedPreferences

Perbaikan:
Migrasi ke Flutter Secure Storage

Prioritas:
Tinggi

---

## Langkah 6 - Laporan Audit

Format:

| Temuan                     | Risiko | Prioritas | Solusi            |
| -------------------------- | ------ | --------- | ----------------- |
| Token di SharedPreferences | Tinggi | Tinggi    | Secure Storage    |
| Database tanpa enkripsi    | Sedang | Sedang    | Enkripsi Database |

---

# 3. Menambahkan Offline Support ke Aplikasi Flutter

## Langkah 1 - Identifikasi Data yang Perlu Cache

Contoh:

* Produk
* Profil pengguna
* Riwayat transaksi
* Wishlist
* Keranjang belanja

Risiko:
Cache data yang tidak perlu.

---

## Langkah 2 - Memilih Mekanisme Cache

Data sederhana:

* SharedPreferences

Data kompleks:

* Hive
* Isar
* SQLite

Data sensitif:

* Secure Storage

Risiko:
Salah memilih storage menyebabkan performa buruk.

---

## Langkah 3 - Implementasi Repository Pattern

Struktur:

UI

↓

Repository

↓

Remote Data Source

↓

API

dan

Repository

↓

Local Data Source

↓

Hive / SQLite

Logika:

Jika internet tersedia:

* Ambil dari API
* Simpan ke cache

Jika offline:

* Ambil dari cache lokal

---

## Langkah 4 - Implementasi Connectivity Checker

Gunakan:

connectivity_plus

Fungsi:

* Deteksi online/offline
* Menentukan sumber data

---

## Langkah 5 - Sinkronisasi Data

Saat koneksi kembali:

* Upload perubahan lokal
* Refresh cache

Risiko:
Conflict data.

Solusi:
Timestamp dan versioning.

---

## Langkah 6 - Testing Offline

Skenario:

1. Login saat online
2. Matikan internet
3. Buka aplikasi kembali
4. Akses data cache
5. Tambahkan data lokal
6. Aktifkan internet
7. Sinkronisasi otomatis

Expected Result:

* Aplikasi tetap dapat digunakan
* Data tidak hilang
* Sinkronisasi berhasil

---

# Link Diagram

Diagram Decision Tree dibuat menggunakan:

* Draw.io / Lucidchart / Mermaid

Lampirkan link diagram pada submission bersama link dokumen.

