# Algoritma_P11_NIM_NamaLengkap

# 1. Flowchart Checkout Aplikasi E-Commerce

Flowchart (versi teks):

Start
↓
User klik Checkout
↓
[Apakah user sudah login?]

Tidak
→ Tampilkan Login
→ Login berhasil?
→ Tidak → End
→ Ya → Lanjut

Ya
↓
[Cek koneksi internet]

Tidak ada koneksi
→ Tampilkan pesan "Periksa koneksi internet"
→ End

Ada koneksi
↓
[Cek token masih valid?]

Tidak valid
→ Refresh Token

Refresh berhasil?
→ Tidak
→ Logout dan arahkan ke Login
→ End

→ Ya
→ Lanjut

Token valid
↓
[Cek stok produk]

Stok habis
→ Tampilkan "Produk tidak tersedia"
→ End

Stok tersedia
↓
Kirim request checkout
↓
Pilih metode pembayaran
↓
Proses pembayaran
↓
[Pembayaran berhasil?]

Tidak
→ Tampilkan gagal bayar
→ Coba lagi

Ya
↓
Buat order
↓
Tampilkan halaman sukses
↓
End

---

# 2. Algoritma Penanganan Error

## a. Tidak Ada Koneksi Internet

Kondisi:

* ConnectivityResult.none

Tindakan:

* Batalkan request API
* Gunakan cache lokal jika tersedia

UI:

* Banner atau dialog
  "Tidak ada koneksi internet"

---

## b. Server Error (HTTP 500)

Kondisi:

* Response status code 500-599

Tindakan:

* Simpan log error
* Retry beberapa kali menggunakan exponential backoff

UI:

* Snackbar atau dialog
  "Server sedang mengalami gangguan"

---

## c. Request Timeout

Kondisi:

* ConnectTimeoutException
* ReceiveTimeoutException

Tindakan:

* Hentikan request
* Retry otomatis maksimal 3 kali

UI:

* "Permintaan melebihi batas waktu"

---

## d. Token Kadaluarsa (HTTP 401)

Kondisi:

* Status code 401

Tindakan:

* Jalankan refresh token
* Simpan token baru
* Ulangi request sebelumnya

Jika refresh gagal:

* Hapus token
* Logout

UI:

* Biasanya transparan
* Jika gagal refresh:
  "Sesi telah berakhir, silakan login kembali"

---

## e. Format Data Tidak Sesuai

Kondisi:

* Parsing JSON gagal
* Missing field
* Invalid data type

Tindakan:

* Tangkap exception parsing
* Gunakan fallback value

UI:

* "Terjadi kesalahan saat memproses data"

---

# 3. Implementasi Repository Pattern

## Langkah 1 - Membuat Abstract Repository

Contoh:

abstract class ProductRepository {
Future<List<Product>> getProducts();
}

Tujuan:

* Mendefinisikan kontrak akses data.

---

## Langkah 2 - Membuat Remote Data Source

Contoh:

class ProductRemoteDataSource {
final Dio dio;

Future<List<ProductModel>> getProducts() async {
final response = await dio.get('/products');
return ...
}
}

Tujuan:

* Mengambil data dari REST API.

---

## Langkah 3 - Membuat Local Data Source

Contoh:

class ProductLocalDataSource {
Future<void> saveProducts(...) {}
Future<List<Product>> getCachedProducts() {}
}

Tujuan:

* Menyimpan dan membaca cache lokal.

---

## Langkah 4 - Membuat Repository Implementation

Contoh:

class ProductRepositoryImpl
implements ProductRepository {

final ProductRemoteDataSource remote;
final ProductLocalDataSource local;

@override
Future<List<Product>> getProducts() async {
try {
final data = await remote.getProducts();
await local.saveProducts(data);
return data;
} catch (_) {
return await local.getCachedProducts();
}
}
}

Tujuan:

* Mengatur sumber data yang digunakan.

---

## Langkah 5 - Dependency Injection

Contoh:

GetIt.I.registerLazySingleton<ProductRepository>(
() => ProductRepositoryImpl(...)
);

Tujuan:

* Mengelola dependency secara terpusat.

---

## Langkah 6 - Integrasi ke UI Layer

Contoh:

class ProductPage extends StatelessWidget {
final ProductRepository repository;

...
}

Tujuan:

* Menampilkan data ke pengguna tanpa mengetahui detail API atau cache.
