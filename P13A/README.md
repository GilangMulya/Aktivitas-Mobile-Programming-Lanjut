# Dekomposisi_P13_23343073_MGilangMulyaPutra

# 1. Dekomposisi Fitur Login dan Autentikasi dalam Clean Architecture

## A. Entity

### User

Merepresentasikan data pengguna yang telah berhasil login.

Atribut:

* id
* name
* email

### AuthToken

Merepresentasikan token autentikasi.

Atribut:

* accessToken
* refreshToken
* expiredAt

---

## B. Use Case

### LoginUseCase

Tanggung Jawab:

* Memvalidasi input login
* Mengirim permintaan login
* Mengembalikan data pengguna dan token

### LogoutUseCase

Tanggung Jawab:

* Menghapus token
* Menghapus sesi pengguna

### RefreshTokenUseCase

Tanggung Jawab:

* Memperbarui access token yang kadaluarsa

### GetCurrentUserUseCase

Tanggung Jawab:

* Mengambil data pengguna yang sedang login

---

## C. Data Source

### Remote Data Source

Digunakan untuk:

* Login API
* Refresh Token API
* Logout API
* Get Profile API

Contoh:
AuthRemoteDataSource

---

### Local Data Source

Digunakan untuk:

* Menyimpan token
* Membaca token
* Menghapus token

Contoh:
AuthLocalDataSource

Media Penyimpanan:

* Flutter Secure Storage

---

## D. Alur Presentation Layer

1. User mengisi email dan password.
2. User menekan tombol Login.
3. LoginPage mengirim event ke AuthBloc.
4. AuthBloc menjalankan LoginUseCase.
5. LoginUseCase memanggil AuthRepository.
6. Repository memanggil AuthRemoteDataSource.
7. API mengembalikan token dan data user.
8. Repository menyimpan token ke LocalDataSource.
9. AuthBloc mengubah state menjadi Authenticated.
10. UI menampilkan Dashboard.

---

# 2. Dekomposisi Tim MVVM (4 Developer)

## Developer 1 – Model Layer

Tanggung Jawab:

* Entity
* Data Model
* Repository Interface
* API Response Mapping

Batasan:

* Tidak membuat UI
* Tidak mengelola state View

---

## Developer 2 – ViewModel Layer

Tanggung Jawab:

* State Management
* Business Logic
* Data Processing

Batasan:

* Tidak membuat Widget
* Tidak melakukan HTTP Request langsung

---

## Developer 3 – View Layer

Tanggung Jawab:

* UI
* Layout
* User Interaction

Batasan:

* Tidak menulis business logic
* Tidak mengakses API langsung

---

## Developer 4 – Testing

Tanggung Jawab:

* Unit Test
* Widget Test
* Integration Test

Batasan:

* Tidak mengubah implementasi fitur utama

---

## Pencegahan Konflik

* Model hanya berkomunikasi melalui interface.
* View hanya membaca state dari ViewModel.
* ViewModel tidak mengetahui detail UI.
* Testing menggunakan mock dependency.

---

# 3. Daftar File Fitur Daftar Produk (Clean Architecture + BLoC)

## Struktur Folder

lib/

├── data/

├── domain/

├── presentation/

---

## Data Layer

### product_model.dart

Lokasi:

data/models/

Tugas:

* Representasi data produk dari API

---

### product_remote_datasource.dart

Lokasi:

data/datasources/

Tugas:

* Mengambil data produk dari server

---

### product_repository_impl.dart

Lokasi:

data/repositories/

Tugas:

* Implementasi ProductRepository

---

## Domain Layer

### product.dart

Lokasi:

domain/entities/

Tugas:

* Entity produk

---

### product_repository.dart

Lokasi:

domain/repositories/

Tugas:

* Kontrak repository

---

### get_products_usecase.dart

Lokasi:

domain/usecases/

Tugas:

* Mengambil daftar produk

---

## Presentation Layer

### product_bloc.dart

Lokasi:

presentation/bloc/

Tugas:

* Mengelola event dan state

---

### product_event.dart

Lokasi:

presentation/bloc/

Tugas:

* Mendefinisikan event

Contoh:

* LoadProducts

---

### product_state.dart

Lokasi:

presentation/bloc/

Tugas:

* Mendefinisikan state

Contoh:

* Loading
* Loaded
* Error

---

### product_page.dart

Lokasi:

presentation/pages/

Tugas:

* Menampilkan daftar produk

---

### product_card.dart

Lokasi:

presentation/widgets/

Tugas:

* Widget item produk

---

## Dependency Injection

### injection_container.dart

Lokasi:

core/di/

Tugas:

* Registrasi repository
* Registrasi use case
* Registrasi bloc

---

# Kesimpulan

Clean Architecture membagi fitur menjadi beberapa layer yang memiliki tanggung jawab berbeda sehingga kode lebih mudah diuji, dipelihara, dan dikembangkan. Pada fitur Daftar Produk, setiap file memiliki peran spesifik sehingga perubahan pada satu bagian tidak memengaruhi keseluruhan aplikasi.
