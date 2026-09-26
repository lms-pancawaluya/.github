# LMS Pancawaluya

**Learning Management System untuk mendukung pengembangan kompetensi Guru SMA melalui nilai-nilai Pancawaluya.**

LMS Pancawaluya adalah platform pembelajaran digital yang dirancang untuk membantu Guru SMA di lingkungan **Dinas Pendidikan Provinsi Jawa Barat** dalam mempelajari, memahami, dan menerapkan lima nilai utama Pancawaluya:

> **Cageur · Bageur · Bener · Pinter · Singer**

Pembelajaran disusun dalam **Course** (kelas/pelatihan) yang berisi beberapa **Module**, masing-masing dengan **Pre-Test**, materi (video/teks/PDF/tautan) yang bisa disisipi mini-quiz, dan **Post-Test**. Course yang tuntas 100% dapat diklaim sertifikatnya secara otomatis.

---

## ✨ Features

### 👨‍🏫 Guru

- Dashboard dan progres belajar per tahap (Pre-Test → Materi → Post-Test)
- Katalog course & modul pembelajaran (online maupun offline)
- Materi video (dengan mini-quiz interaktif), materi teks, PDF, dan tautan
- Pre-Test dan Post-Test per modul
- Klaim & unduh sertifikat otomatis saat course tuntas 100%
- Diskusi & komentar per course/modul (dengan mention)
- Saran & Masukan per course
- Pusat Bantuan — buat dan pantau tiket helpdesk
- Notifikasi aktivitas (modul baru, balasan tiket, dsb.) beserta preferensinya
- Checklist nilai Pancawaluya
- Registrasi guru dengan autofill data sekolah berdasarkan NIP
- Manajemen profil, verifikasi OTP, dan reset password

### 🧑‍🏫 Pengajar

- Dashboard pemantauan guru yang menjadi cakupannya (per sekolah)
- Kelola data akun guru dalam cakupannya
- Kelola course & modul yang dibuatnya sendiri
- Monitoring progres belajar & hasil evaluasi guru
- Diskusi & komentar course/modul
- Kelola tiket bantuan dari guru

### 🛠️ Admin

- Dashboard administrasi & monitoring menyeluruh
- Manajemen course dan modul pembelajaran
- Manajemen konten (video, teks, PDF, tautan) dan mini-quiz
- Manajemen Pre-Test, Post-Test, dan bank soal
- Manajemen template dan penerbitan sertifikat
- Manajemen akun guru & pengajar
- Manajemen checklist nilai Pancawaluya
- Moderasi diskusi course/modul
- Kelola tiket bantuan (helpdesk)
- Pencarian global lintas modul, konten, dan tiket
- Monitoring progres, hasil evaluasi, dan saran & masukan guru

> **Rencana Tindak Lanjut (RTL):** fondasi fiturnya sudah ada di backend dan frontend, namun untuk saat ini **sengaja belum ditampilkan** di antarmuka pengguna karena alur bisnisnya masih difinalisasi.

---

## 🧭 Pancawaluya

| Nilai      | Makna                                    |
| ---------- | ----------------------------------------- |
| **Cageur** | Sehat secara fisik dan mental             |
| **Bageur** | Percaya diri dan mampu berkolaborasi      |
| **Bener**  | Disiplin dan menjunjung integritas        |
| **Pinter** | Tertib dan taat pada norma                |
| **Singer** | Responsif dan memiliki jiwa kepemimpinan  |

---

## 🏗️ Architecture

LMS Pancawaluya menggunakan arsitektur **frontend–backend** yang terpisah, dengan penyimpanan berkas terpisah dari database.

```
┌─────────────────────────────────┐
│         LMS Pancawaluya          │
└────────────────┬─────────────────┘
                  │
          ┌───────┴───────┐
          │               │
          ▼               ▼
     ┌─────────┐    ┌───────────┐
     │ Frontend│───▶│  Backend  │
     └─────────┘API │ (Express) │
                 JWT └─────┬─────┘
                           │
              ┌────────────┼────────────┐
              ▼            ▼            ▼
      ┌───────────────┐ ┌──────────┐ ┌────────────┐
      │  PostgreSQL /  │ │ Supabase │ │ Cloudinary │
      │    Prisma      │ │ Storage  │ │ (PDF: modul│
      │   (Supabase)   │ │ (foto)   │ │ & sertifikat)│
      └───────────────┘ └──────────┘ └────────────┘
```

Data pembelajaran mengikuti hierarki **Course → Module → Content**, dengan Pre-Test dan Post-Test terpasang di level Module. Frontend berkomunikasi dengan backend melalui REST API beramplop `{ sukses, pesan, data }`, dengan autentikasi berbasis JWT.

---

## 🧰 Tech Stack

### Frontend

- **Next.js 16** (App Router, Turbopack)
- **React 19**
- **TypeScript**
- **Tailwind CSS 4**
- **Axios** & native `fetch`
- **React Hook Form**
- **Lucide React** (ikon)

### Backend

- **Node.js** & **Express 5**
- **Prisma ORM**
- **PostgreSQL** via **Supabase**
- **JWT** (autentikasi) & **bcryptjs** (hashing password)
- **Resend** — pengiriman email OTP
- **Multer** — unggah berkas (foto profil, dokumen RTL)
- **Cloudinary** — penyimpanan PDF (template & hasil sertifikat)
- **pdf-lib** — generate PDF sertifikat (overlay ke template)
- **Helmet** & **CORS** — keamanan API

---

## 📦 Repositories

| Repository                                                 | Description                                              |
| ----------------------------------------------------------- | ---------------------------------------------------------- |
| [`frontend`](https://github.com/lms-pancawaluya/frontend)   | Web application dan user interface LMS (Next.js)           |
| [`backend`](https://github.com/lms-pancawaluya/backend)     | REST API, business logic, autentikasi, dan database        |
| [`.github`](https://github.com/lms-pancawaluya/.github)     | Konfigurasi, panduan kontribusi, dan workflow default organisasi |

---

## 🔐 User Roles

LMS Pancawaluya memiliki tiga role utama:

**Guru**
Mengikuti pembelajaran (Pre-Test, materi, Post-Test), berdiskusi di course/modul, mengklaim sertifikat, mengirim saran & masukan, dan membuat tiket bantuan.

**Pengajar**
Memantau dan mengelola data guru dalam cakupan sekolahnya, turut mengelola course/modul yang dibuatnya sendiri, serta menangani tiket bantuan.

**Admin**
Mengelola keseluruhan course/modul/konten, evaluasi, sertifikat, akun guru/pengajar, checklist, moderasi diskusi, serta monitoring progres di seluruh sekolah.

---

## 📚 Project Structure

```
lms-pancawaluya/
│
├── frontend/     # Next.js web application
├── backend/      # Express REST API + Prisma
└── .github/      # Organization-wide configuration
```

---

## 🎯 Project Goals

LMS Pancawaluya dikembangkan untuk:

- Mendigitalisasi proses pembelajaran Guru SMA melalui course terstruktur (Pre-Test → Materi → Post-Test).
- Menyediakan materi pembelajaran multi-format (video, teks, PDF, tautan) dengan mini-quiz interaktif.
- Mendorong penerapan nilai-nilai Pancawaluya melalui checklist harian.
- Mengapresiasi pencapaian guru melalui sertifikat resmi.
- Memfasilitasi diskusi dan dukungan lewat forum modul dan helpdesk.
- Mempermudah pemantauan progres belajar oleh Pengajar dan Admin.
- Menyediakan sistem administrasi dan evaluasi yang terintegrasi.

---

Built with ❤️ for **Teachers**
