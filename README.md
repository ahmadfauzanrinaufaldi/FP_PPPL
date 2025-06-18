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

