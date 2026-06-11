# Dekomposisi_P12_23343073_MGilangMulyaPutra

# 1. Dekomposisi Arsitektur Penyimpanan Data Lokal Aplikasi E-Commerce

| Kategori Data                | Volume       | Frekuensi Akses | Sensitivitas  | Penyimpanan yang Direkomendasikan                  |
| ---------------------------- | ------------ | --------------- | ------------- | -------------------------------------------------- |
| Access Token & Refresh Token | Kecil        | Tinggi          | Sangat Tinggi | Flutter Secure Storage                             |
| Profil Pengguna              | Kecil-Sedang | Sedang          | Tinggi        | SQLite / Hive + Secure Storage untuk data sensitif |
| Keranjang Belanja (Cart)     | Sedang       | Sangat Tinggi   | Sedang        | Hive / Isar                                        |
| Wishlist                     | Sedang       | Tinggi          | Rendah-Sedang | Hive / Isar                                        |
| Cache Produk                 | Besar        | Sangat Tinggi   | Rendah        | SQLite / Isar                                      |
| Riwayat Pesanan              | Besar        | Sedang          | Tinggi        | SQLite                                             |
| Pengaturan Aplikasi          | Sangat Kecil | Rendah          | Rendah        | SharedPreferences                                  |
| Data Pencarian Terakhir      | Kecil        | Tinggi          | Rendah        | SharedPreferences / Hive                           |

## Alasan Pemilihan

### Token

Token autentikasi harus menggunakan Flutter Secure Storage karena memanfaatkan Android Keystore dan iOS Keychain sehingga lebih aman dibanding SharedPreferences.

### Cache Produk

Jumlah data produk dapat mencapai ribuan item sehingga membutuhkan database lokal yang mampu melakukan query dan indexing secara efisien.

### Cart dan Wishlist

Data sering berubah dan sering diakses sehingga Hive atau Isar cocok karena performa baca/tulis yang tinggi.

---

# 2. Proses Migrasi Database SQLite dari Versi 1 ke Versi 2

## Kasus

Versi 1:

users

* id
* name
* email

Versi 2:

users

* id
* name
* email
* phone_number

---

## Langkah 1 - Analisis Perubahan Schema

Aktivitas:

* Menentukan perubahan tabel
* Menentukan dampak terhadap data lama

Risiko:

* Perubahan tidak kompatibel dengan data lama
* Kehilangan data penting

---

## Langkah 2 - Meningkatkan Database Version

Contoh:

databaseVersion = 2;

Risiko:

* Migrasi tidak terpicu
* Versi database tidak sinkron

---

## Langkah 3 - Menulis Script Migrasi

Contoh:

ALTER TABLE users
ADD COLUMN phone_number TEXT;

Risiko:

* Kesalahan SQL
* Aplikasi crash saat startup

---

## Langkah 4 - Implementasi Fungsi onUpgrade

Contoh:

onUpgrade(db, oldVersion, newVersion) {
if (oldVersion < 2) {
db.execute(
'ALTER TABLE users ADD COLUMN phone_number TEXT'
);
}
}

Risiko:

* Kondisi versi salah
* Migrasi dijalankan berulang

---

## Langkah 5 - Testing Migrasi

Aktivitas:

* Install aplikasi versi 1
* Isi data
* Upgrade ke versi 2

Risiko:

* Data lama hilang
* Data baru tidak terbentuk

---

## Langkah 6 - Testing Edge Cases

Aktivitas:

* Database kosong
* Database rusak
* Versi lama berbeda

Risiko:

* Crash pada sebagian pengguna

---

## Langkah 7 - Deployment

Aktivitas:

* Rilis ke Play Store/App Store

Risiko:

* Bug migrasi muncul di perangkat pengguna
* Kehilangan data massal

Mitigasi:

* Backup database
* Monitoring crash
* Rollback plan

---

# 3. Pertanyaan untuk Klien Sebelum Memilih Strategi Penyimpanan

## A. Kebutuhan Teknis

1. Berapa jumlah data yang akan disimpan?
2. Apakah aplikasi harus dapat berjalan offline?
3. Seberapa sering data diperbarui?
4. Apakah diperlukan relasi antar data?
5. Berapa target performa baca/tulis data?
6. Apakah data perlu disinkronkan dengan server?

---

## B. Kebutuhan Bisnis

1. Data apa yang paling penting bagi pengguna?
2. Berapa lama data harus disimpan?
3. Apakah pengguna dapat menggunakan banyak perangkat?
4. Apakah diperlukan sinkronisasi real-time?
5. Bagaimana pertumbuhan jumlah pengguna dalam beberapa tahun ke depan?
6. Apakah kehilangan sebagian data dapat diterima?

---

## C. Persyaratan Keamanan dan Regulasi

1. Apakah terdapat data pribadi pengguna?
2. Apakah aplikasi menyimpan data pembayaran?
3. Apakah harus mematuhi GDPR, PDP Indonesia, atau regulasi lain?
4. Apakah data perlu dienkripsi?
5. Siapa yang boleh mengakses data tersebut?
6. Berapa lama data wajib disimpan menurut regulasi?
7. Apakah diperlukan audit trail atau logging keamanan?

