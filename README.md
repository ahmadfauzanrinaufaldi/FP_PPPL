# FullstackExpense Project

## Nama Anggota Kelompok 3

- Edward Yosafat Sirait (5026221091) 
- Ahmad Fauzan Rinaufaldi (5026221143)
- Christopher C. Pangaribuan (5026221150)
- Andika Insan Patria (5026221211)

## Deskripsi

FullstackExpense adalah aplikasi web yang dirancang untuk membantu pengguna mengelola keuangan pribadi mereka dengan melacak pendapatan dan pengeluaran secara efektif. Proyek ini mengadopsi pendekatan full-stack, mengombinasikan backend yang kuat yang dibangun dengan Node.js dan Express.js untuk melayani frontend yang interaktif yang dikembangkan menggunakan HTML, CSS, dan JavaScript murni.

Pusat dari aplikasi ini adalah integrasinya dengan Google Firebase, yang menyediakan layanan autentikasi pengguna yang aman dan kemampuan basis data NoSQL (Firestore) untuk menyimpan data transaksi secara real-time. Ini memastikan bahwa data keuangan pengguna selalu terbaru dan aman.

Selain fungsionalitas inti pelacakan keuangan, FullstackExpense juga menonjolkan pipeline DevOps yang komprehensif. Ini mencakup konfigurasi Continuous Integration (CI) menggunakan GitHub Actions untuk otomatisasi linting kode (ESLint), pengujian unit (Jest), dan analisis kualitas kode (SonarCloud). Untuk Continuous Deployment (CD), aplikasi secara otomatis membangun citra Docker dan menyebarkannya ke Google Cloud Run, memastikan deployment yang efisien dan andal.

Secara keseluruhan, FullstackExpense bertujuan untuk menyediakan alat yang user-friendly dan andal bagi individu untuk memvisualisasikan dan mengelola kesehatan finansial mereka, didukung oleh infrastruktur yang modern dan otomatis.

🔗 [Link Repository GitHub](https://github.com/chrsthper/FullstackExpense)

## Features

- **Autentikasi Pengguna**
  - Pendaftaran dan login yang aman menggunakan Firebase Authentication.

- **Pelacakan Pengeluaran**
  - Menambahkan, mengedit, dan melihat transaksi pendapatan dan pengeluaran.

- **Perhitungan Saldo Otomatis**
  - Menghitung dan menampilkan current balance, total income, dan total expense secara real-time.

- **Kategorisasi Transaksi**
  - Mengelola transaksi berdasarkan kategori tetap seperti: Makanan, Transportasi, Gaji, dll.

- **Penyaringan Transaksi Tingkat Lanjut**
  - Filter transaksi berdasarkan jenis (income/expense) serta kategori tertentu.

- **Visualisasi Data**
  - Menggunakan Chart.js untuk menampilkan:
    - Perbandingan income vs expense.
    - Distribusi transaksi berdasarkan kategori (Pie Chart).

- **Desain Responsif**
  - Antarmuka pengguna yang kompatibel untuk desktop maupun mobile.

- **Logout**
  - Pengguna dapat keluar dari sesi secara aman menggunakan Firebase signOut.
 
## Memulai Proyek FullstackExpense: Forking dan Konsep Awal

Proyek FullstackExpense dimulai dengan proses forking dari repositori GitHub yang sudah ada. Langkah forking ini krusial karena menciptakan salinan independen dari proyek asli di akun GitHub kami, yang kemudian dapat dikembangkan dan dimodifikasi tanpa memengaruhi repository hulu (upstream). Setelah proses forking, repository di-clone ke lingkungan pengembangan lokal. Pada tahap awal ini, arsitektur aplikasi masih mengadopsi konsep Model-View-Controller (MVC) dengan MySQL sebagai sistem manajemen basis datanya.


**Gambaran Awal Aplikasi**
Berikut adalah detail kondisi aplikasi saat pertama kali di-fork dan diimplementasikan sebelum proses refactoring signifikan dimulai:

- **Konsep Arsitektur & Teknologi Awal**
  - Arsitektur MVC: Aplikasi dibangun berdasarkan pola Model-View-Controller, yang memisahkan logika aplikasi ke dalam komponen-komponen terstruktur (Model untuk data/logika bisnis, View untuk antarmuka pengguna, dan Controller untuk penanganan input).
  - Database MySQL: MySQL digunakan sebagai basis data relasional untuk menyimpan semua data, termasuk informasi pengguna dan catatan transaksi. Interaksi backend aplikasi saat itu bergantung sepenuhnya pada koneksi ke database MySQL.
  - Lingkungan Lokal: Server backend dibangun dengan Node.js dan Express.js, berinteraksi langsung dengan database MySQL yang diatur secara lokal.

- **Proses Setup dan Konektivitas Database**
  Untuk menjalankan aplikasi pada tahap awal ini, langkah-langkah spesifik diperlukan untuk menyiapkan lingkungan database:
  - Pengembang perlu membuat database MySQL kosong secara manual dengan penamaan yang sesuai dengan source code asli untuk memastikan aplikasi dapat terhubung dengan benar.
  - Setelah menginstal dependensi proyek (npm install), aplikasi akan secara otomatis terhubung ke database MySQL yang telah disiapkan. Proses ini juga akan membuat tabel-tabel yang diperlukan dalam database sesuai dengan skema yang didefinisikan dalam kode sumber.
  - Aplikasi kemudian dapat dimulai dengan perintah npm start, yang akan mengaktifkan server Node.js dan memungkinkan interaksi dengan frontend melalui database MySQL.

- **Tampilan Antarmuka Pengguna Awal**
  - Halaman Login (localhost:4000/login.html)
    Terdiri dari input untuk Enter Email dan Enter Password. Tombol Login, serta tautan untuk New User register dan Forget Password. Desain minimalis dengan latar belakang hijau toska dan elemen formulir berwarna putih.
  - Halaman Expense Tracker (localhost:4000/expense.html)
    Memiliki formulir untuk memasukkan data transaksi (Select Income Or Expense, Amount, Description, Category, Date dengan format dd/mm/yyyy, dan Time).
  - Tombol Add Expense untuk menyimpan transaksi
    Bagian Balance serta daftar All Expenses dan All Incomes untuk melihat ringkasan transaksi. Tampilan ini juga menggunakan skema warna hijau toska dan putih.

## Evolusi Proyek: Refactoring ke Firebase dan Keuntungan DevOps

Setelah mengevaluasi arsitektur awal, tim memutuskan untuk melakukan **refactoring besar-besaran** dengan mengganti backend dari MySQL dan Express.js ke **Firebase**, demi menyederhanakan pengelolaan backend dan meningkatkan efisiensi DevOps.

### Alasan Migrasi ke Firebase

#### 1. Penyederhanaan Arsitektur (Backend-as-a-Service)
- Firebase menggantikan kebutuhan backend custom yang kompleks.
- Tidak perlu lagi mengelola server sendiri, koneksi database, session, dan autentikasi manual.
- Logika CRUD data transaksi sekarang dilakukan langsung di frontend via Firebase SDK.

#### 2. Efisiensi Testing dan DevOps
- Pengujian backend menjadi lebih ringan karena banyak fungsi (seperti auth & database) sudah ditangani oleh Firebase.
- Tim bisa fokus pada **CI/CD pipeline**, kualitas kode, dan automasi alur kerja.

#### 3. Hosting & Deployment Lebih Mudah
- Firebase menyediakan layanan managed seperti **Firestore** dan **Authentication**.
- Tidak perlu provisioning server untuk hosting atau pengelolaan database manual.
- Mendukung integrasi CI/CD dan deployment otomatis ke Google Cloud Run.

---

### Peningkatan Frontend Setelah Refactor

#### 1. Desain UI Lebih Modern
- UI diperbarui menjadi lebih profesional dengan skema warna dark mode yang konsisten.
- Tata letak lebih bersih dan rapi untuk meningkatkan UX.

#### 2. Penyaringan Transaksi Lanjutan
- Pengguna dapat memfilter transaksi berdasarkan:
  - Tipe: Income / Expense / All
  - Kategori: Makanan, Gaji, Transportasi, dll

#### 3. Visualisasi Data Interaktif
- Menggunakan **Chart.js** untuk menampilkan grafik:
  - Perbandingan total pendapatan vs pengeluaran
  - Distribusi transaksi berdasarkan kategori

#### 4. Responsivitas
- Desain frontend dioptimalkan untuk semua ukuran layar (mobile-friendly)

---

### Dampak ke Struktur Kode

| Sebelum Refactor                | Setelah Refactor (Firebase)           |
|-------------------------------|----------------------------------------|
| Express.js sebagai REST API    | Firebase SDK langsung digunakan di frontend |
| Sequelize + MySQL              | Firestore (NoSQL, realtime database)   |
| Session manual                 | Firebase Authentication                |
| Login/logout pakai JWT manual  | signInWithEmailAndPassword & signOut  |
| Test koneksi DB & auth         | Fokus test logika UI dan validasi form |
| CRUD pakai router API          | CRUD langsung via SDK Firestore       |

---

### Outcome
Dengan migrasi ke Firebase dan penyusunan ulang pipeline DevOps:

- Pengembangan frontend jadi lebih cepat
- Backend lebih ringan dan aman (mengandalkan platform Google)
- CI/CD lebih stabil dan modular
- Fitur utama aplikasi tetap terjaga, bahkan lebih optimal

## Tools dan Software yang Digunakan

Proyek FullstackExpense memanfaatkan kombinasi tools dan software modern untuk memfasilitasi pengembangan, pengujian, dan deployment aplikasi. Berikut adalah rinciannya:

---

### Google Spreadsheet

Google Spreadsheet digunakan sebagai alat bantu kolaboratif yang fundamental dalam mengelola proyek DevOps secara efisien. Dengan fleksibilitas dan kemampuan kolaborasi real-time, Google Spreadsheet memfasilitasi pencatatan dan pemantauan tugas (task), linimasa (timeline), serta status pekerjaan secara transparan. Spreadsheet ini dirancang secara khusus untuk mendukung prinsip DevOps yang menekankan integrasi yang erat antara tim pengembangan (development) dan tim operasional (operations).
Dalam penggunaannya, kami mengadopsi format tabular untuk menyusun tugas berdasarkan kategori status, seperti backlog, in progress, testing, dan done, yang sangat serupa dengan pendekatan Kanban. Setiap entri tugas di dalam spreadsheet ini mencakup informasi penting, termasuk deskripsi tugas, penanggung jawab, prioritas, tenggat waktu, dan status terkini. Melalui fitur-fitur bawaan Google Spreadsheet seperti filter, conditional formatting, dan kemampuan kolaborasi simultan, seluruh tim dapat menjaga visibilitas proyek yang tinggi dan meningkatkan akuntabilitas antar anggota tim. Ini memungkinkan pemangku kepentingan untuk melihat kemajuan proyek secara sekilas, mengidentifikasi hambatan, dan membuat keputusan yang tepat waktu.

---

### 🧠 GitHub

GitHub adalah platform hosting repositori Git berbasis cloud yang memainkan peran sentral dalam proyek FullstackExpense untuk manajemen kontrol versi, kolaborasi tim, dan integrasi dengan alur kerja DevOps. Penggunaan GitHub memastikan bahwa semua perubahan kode terlacak, terdokumentasi, dan dapat dikelola dengan efisien sepanjang siklus pengembangan.
Berikut adalah aspek-aspek utama dari penggunaan GitHub dalam proyek ini:
Kontrol Versi Terdistribusi: GitHub menyimpan repositori Git proyek, yang memungkinkan tim untuk melacak setiap perubahan pada codebase, kembali ke versi sebelumnya jika diperlukan, dan mengelola berbagai fitur secara paralel menggunakan branching.
Kolaborasi Tim: Platform ini memfasilitasi kolaborasi yang lancar antar pengembang. Anggota tim dapat bekerja pada fitur yang berbeda secara bersamaan, menggabungkan perubahan mereka melalui pull request (merge request), dan melakukan code review untuk memastikan kualitas kode.
Manajemen Repositori: GitHub menyediakan antarmuka yang intuitif untuk mengelola repositori, termasuk fitur untuk isu (issues), pull request, dan wiki, meskipun fokus utama di sini adalah kontrol versi dan CI/CD.
Integrasi CI/CD dengan GitHub Actions: Salah satu penggunaan paling krusial dari GitHub dalam proyek ini adalah integrasinya dengan GitHub Actions. Ini adalah fitur CI/CD bawaan GitHub yang memungkinkan otomatisasi alur kerja pembangunan, pengujian, dan deployment langsung dari repositori. Setiap push atau pull request memicu workflow otomatis untuk memastikan kode memenuhi standar kualitas dan siap untuk deployment.

---

### 🌐 HTML (HyperText Markup Language)

Digunakan untuk menyusun struktur halaman web:

- **File utama**: `login.html`, `signUp.html`, `expense.html`, dll.
- Elemen penting: `<form>`, `<input>`, `<select>`, `<button>`, `<div>`

---

### 🎨 CSS (Cascading Style Sheets)

Berfungsi untuk mempercantik tampilan halaman web.

- **File utama**: `public/css/index.css`
- Style untuk elemen seperti `auth-container`, `buttons`, dan layout UI
- Framework tambahan: **Bootstrap 5** via CDN

---

### 🧩 JavaScript (Browser-side)

JavaScript bertanggung jawab atas seluruh logika interaktif frontend:

| File JS           | Fungsi Utama |
|------------------|--------------|
| `signup.js`      | Proses registrasi user ke Firebase Auth |
| `login.js`       | Login ke Firebase dan redirect ke dashboard |
| `expense.js`     | CRUD transaksi, hitung saldo, logika filter & chart |
| `utils.js`       | Fungsi `formatRupiah()` dan helper umum |
| `firebase-config.js` | Menyimpan konfigurasi project Firebase |

---

### ⚙️ Node.js

Node.js adalah platform JavaScript di sisi server. Digunakan untuk:

- Menjalankan server lokal (`server.js`)
- Menyajikan frontend via folder `public/`
- Berbasis event-driven dan non-blocking I/O

---

### 🧭 Express.js

Express digunakan untuk:

- **Routing**: Menangani permintaan ke endpoint seperti `/`, `/login.html`, dsb
- **Static Serving**: Menyajikan file statis dari folder `public/`
- **Server Init**: File `server.js` sebagai entry point aplikasi

---

### 🔥 Firebase

Firebase menyediakan dua layanan utama:

#### 1. Firebase Authentication
- Pendaftaran user via `createUserWithEmailAndPassword`
- Login user via `signInWithEmailAndPassword`
- Logout via `signOut`
- Menyimpan user info ke Firestore setelah sign-up

#### 2. Cloud Firestore
- Menyimpan seluruh transaksi user (`entries`)
- Struktur dokumen NoSQL
- Operasi: `addDoc`, `updateDoc`, `deleteDoc`, `query` berdasarkan `userId`
- Realtime sync data frontend dan Firestore

---

### 🧪 Jest

Jest digunakan untuk unit dan integration test:

| File Test           | Fungsi Pengujian |
|---------------------|------------------|
| `signup.test.js`    | Validasi proses register |
| `login.test.js`     | Login menggunakan kredensial |
| `logout.test.js`    | Validasi `signOut` dan hapus localStorage |
| `expense.test.js`   | Pengujian `addDoc` transaksi ke Firestore |
| `formatRupiah.test.js` | Format angka ke mata uang |
| `server.test.js`    | HTTP response server.js |

- **Mocking**: Modul Firebase dan `localStorage` dimock agar testing terisolasi
- **Coverage**: Jest menghasilkan `lcov.info` sebagai laporan cakupan untuk SonarCloud

---

### 🧼 ESLint

ESLint adalah tool untuk:

- Menjaga kualitas sintaks JavaScript
- Menghindari bug atau code smell sejak awal

#### Konfigurasi:

- File: `eslint.config.mjs`
- Plugins: `@eslint/js`, `@eslint/json`, `@eslint/css`
- Pengecualian direktori: `__tests__/`, `coverage/`

---

### 🧠 SonarCloud

SonarCloud memindai kualitas kode dan keamanan secara otomatis dalam pipeline CI.

#### Fungsi:
- Mendeteksi bug, code smells, vulnerability
- Melacak coverage dari Jest

#### File Konfigurasi:
- `sonar-project.properties`:
  - `sonar.projectKey`, `sonar.organization`
  - `sonar.sources`, `sonar.exclusions`
  - `sonar.javascript.lcov.reportPaths`

---

### 📦 Docker

Docker digunakan untuk mengemas aplikasi ke dalam container:

- Base image: `node:18-alpine`
- Copy semua source code ke image
- ENV config untuk Firebase disediakan via GitHub Secrets

Manfaat:
- Konsistensi environment
- Portabilitas ke semua platform
- Integrasi dengan Google Cloud Run via Artifact Registry

---

### ⚙️ GitHub Actions

CI/CD pipeline otomatis terdiri dari dua file:

- **ci.yml**: Lint → Test → SonarCloud → Docker build + push ke GCR
- **cd.yml**: Deploy image ke Cloud Run setelah CI sukses di `main`

---

### ☁️ Google Cloud Platform (GCP)

Platform hosting dan deployment aplikasi.

#### Layanan yang digunakan:

- **Google Cloud Build**: Build Docker image
- **Artifact Registry**: Menyimpan image hasil build
- **Cloud Run**: Menjalankan container secara autoscale
- **Logging & Monitoring**: Otomatis aktif untuk aplikasi Cloud Run

---

