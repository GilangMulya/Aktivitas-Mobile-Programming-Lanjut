# Dekomposisi_P14_23343073_MGilangMulyaPutra

# 1. Dekomposisi Domain Keamanan Aplikasi Mobile

| Domain                         | Ancaman Utama                             | Mekanisme Mitigasi                                 | Tools/Package Flutter                   |
| ------------------------------ | ----------------------------------------- | -------------------------------------------------- | --------------------------------------- |
| Authentication & Authorization | Account takeover, credential theft        | OAuth2, JWT, MFA, biometrik                        | flutter_appauth, local_auth             |
| Secure Data Storage            | Insecure Data Storage, token leakage      | Android Keystore, iOS Keychain, enkripsi lokal     | flutter_secure_storage                  |
| Network Security               | Man-in-the-Middle (MITM), packet sniffing | HTTPS/TLS, Certificate Pinning                     | dio, http_certificate_pinning           |
| Application Hardening          | Reverse engineering, code tampering       | Obfuscation, anti-debugging, integrity check       | flutter build apk --obfuscate           |
| Session & Token Management     | Session hijacking, token replay           | Refresh token, token expiration, logout management | dio interceptor, flutter_secure_storage |
| Input & API Security           | Injection, insecure API access            | Input validation, API authorization, rate limiting | dio, retrofit                           |
| Device Security                | Rooted/jailbroken device abuse            | Root/jailbreak detection                           | jailbreak_detection, root_check         |

---

# 2. Skenario Login Aplikasi Perbankan Mobile (Dari Sisi Keamanan)

### Langkah 1

Pengguna membuka aplikasi mobile banking.

### Langkah 2

Aplikasi memeriksa apakah perangkat terdeteksi root/jailbreak.

### Langkah 3

Pengguna memasukkan PIN atau menggunakan biometrik.

### Langkah 4

Input divalidasi secara lokal sebelum dikirim ke server.

### Langkah 5

Aplikasi membuat request login melalui HTTPS/TLS.

### Langkah 6

Certificate server divalidasi menggunakan certificate pinning.

### Langkah 7

Server memverifikasi kredensial pengguna.

### Langkah 8

Server menghasilkan access token dan refresh token.

### Langkah 9

Token dikirim kembali melalui koneksi terenkripsi.

### Langkah 10

Aplikasi menyimpan token pada Flutter Secure Storage.

### Langkah 11

Aplikasi membuat session pengguna yang aktif.

### Langkah 12

Request API pertama (misalnya profil rekening) dikirim dengan access token pada Authorization Header.

### Langkah 13

Server memvalidasi token dan hak akses pengguna.

### Langkah 14

Server mengirim data rekening.

### Langkah 15

Data ditampilkan ke pengguna dan sesi login berhasil dibuat.

---

# 3. Roadmap Pembelajaran Keamanan Mobile

## A. Wajib Dikuasai Segera

1. HTTPS dan TLS
2. JWT Authentication
3. OAuth2
4. Flutter Secure Storage
5. OWASP Mobile Top 10
6. Secure API Communication
7. Session Management
8. Input Validation
9. Password Hashing Concept
10. Dasar Cryptography

---

## B. Penting untuk Produksi

1. Certificate Pinning
2. Biometric Authentication
3. Secure Logging
4. Secure Coding Practices
5. Root/Jailbreak Detection
6. API Rate Limiting
7. Secrets Management
8. Dependency Security Audit
9. Security Testing
10. Penetration Testing Dasar

---

## C. Lanjutan untuk Spesialis Keamanan

1. Reverse Engineering Android/iOS
2. Mobile Malware Analysis
3. Dynamic Application Security Testing (DAST)
4. Static Application Security Testing (SAST)
5. Advanced Cryptography
6. Threat Modeling
7. Secure SDLC
8. Runtime Application Self-Protection (RASP)
9. Mobile Forensics
10. Vulnerability Research dan Exploit Analysis

---

# Kesimpulan

Keamanan aplikasi mobile tidak hanya berfokus pada login dan penyimpanan token, tetapi mencakup berbagai domain mulai dari autentikasi, penyimpanan data, keamanan jaringan, hingga perlindungan aplikasi dari reverse engineering. Pendekatan berlapis (defense in depth) menjadi kunci untuk membangun aplikasi yang aman dan tahan terhadap berbagai ancaman modern.
