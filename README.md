# Dekomposisi_P11_NIM_NamaLengkap

## 1. Dekomposisi Sistem Integrasi API

### Layer 1 - Presentation Layer

**Tanggung Jawab:**

* Menampilkan UI kepada pengguna.
* Mengirim event dari user ke business logic.
* Menampilkan state loading, success, dan error.

**Package Flutter:**

* flutter
* go_router
* flutter_bloc / provider

---

### Layer 2 - State Management Layer

**Tanggung Jawab:**

* Mengelola state aplikasi.
* Menjembatani UI dengan business logic.

**Package Flutter:**

* flutter_bloc
* provider
* riverpod

---

### Layer 3 - Repository Layer

**Tanggung Jawab:**

* Menentukan sumber data.
* Mengatur pengambilan data dari API atau cache lokal.
* Menyembunyikan detail implementasi data source.

**Package Flutter:**

* dio
* repository pattern (custom)

---

### Layer 4 - API Service Layer

**Tanggung Jawab:**

* Melakukan HTTP request ke server.
* Menambahkan interceptor.
* Mengelola authentication token.

**Package Flutter:**

* dio
* pretty_dio_logger

---

### Layer 5 - Local Storage Layer

**Tanggung Jawab:**

* Menyimpan token.
* Menyimpan cache data.
* Mendukung offline access.

**Package Flutter:**

* flutter_secure_storage
* hive
* isar
* shared_preferences

---

### Layer 6 - Network Layer

**Tanggung Jawab:**

* Mengatur komunikasi dengan server.
* Menangani timeout, retry, dan koneksi internet.

**Package Flutter:**

* dio
* connectivity_plus

---

## 2. Skenario Login Aplikasi Banking

1. Pengguna mengisi username dan password pada LoginScreen.
2. User menekan tombol Login.
3. Button mengirim event ke AuthBloc/AuthProvider.
4. State berubah menjadi Loading.
5. AuthRepository menerima permintaan login.
6. Repository memanggil AuthApiService.
7. Dio mengirim POST request ke endpoint /login.
8. Server memvalidasi username dan password.
9. Server mengembalikan access token dan refresh token.
10. Dio menerima response dan mem-parsing JSON.
11. Token disimpan ke Flutter Secure Storage.
12. Repository mengembalikan hasil login ke Bloc.
13. Bloc mengubah state menjadi Authenticated.
14. Aplikasi melakukan request profil pengguna menggunakan token.
15. Data profil diterima dan disimpan ke cache lokal (Hive/Isar).
16. Navigator mengarahkan pengguna ke DashboardScreen.
17. Dashboard menampilkan data akun pengguna.

Komponen yang terlibat:

* LoginScreen
* TextField
* ElevatedButton
* AuthBloc/Provider
* AuthRepository
* Dio
* AuthApiService
* Flutter Secure Storage
* Hive/Isar
* DashboardScreen

---

## 3. Roadmap Pembelajaran Integrasi API

### Tingkat Dasar

* HTTP Method (GET, POST, PUT, DELETE)
* REST API Concept
* JSON Parsing
* Future dan Async Await
* Dio Basic Usage
* Error Handling Dasar
* API Testing dengan Postman

### Tingkat Menengah

* Repository Pattern
* State Management (Bloc/Provider/Riverpod)
* Authentication JWT
* Refresh Token
* Interceptor Dio
* Caching Strategy
* Pagination
* File Upload

### Tingkat Lanjutan

* Clean Architecture
* Circuit Breaker Pattern
* Retry Mechanism
* Exponential Backoff
* Offline First Architecture
* Stale While Revalidate (SWR)
* API Monitoring & Logging
* Performance Optimization
* Distributed Caching
* Security Hardening dan Certificate Pinning
