# LMS Pancawaluya

**Learning Management System untuk mendukung pengembangan kompetensi Guru SMA melalui nilai-nilai Pancawaluya.**

LMS Pancawaluya adalah platform pembelajaran digital yang dirancang untuk membantu Guru SMA di lingkungan **Dinas Pendidikan Provinsi Jawa Barat** dalam mempelajari, memahami, dan menerapkan lima nilai utama Pancawaluya:

> **Cageur · Bageur · Bener · Pinter · Singer**

Platform ini menyediakan pembelajaran berbasis modul yang dilengkapi video, materi teks, mini-quiz, evaluasi, serta pemantauan progres pembelajaran.

---

## ✨ Features

### 👨‍🏫 Guru

* Dashboard dan progres pembelajaran
* Katalog modul pembelajaran
* Video pembelajaran dengan mini-quiz
* Materi pembelajaran berbasis teks
* Evaluasi pembelajaran
* Checklist nilai Pancawaluya
* Riwayat dan progres modul
* Manajemen profil
* Verifikasi OTP dan reset password

### 🛠️ Admin

* Dashboard administrasi
* Manajemen modul pembelajaran
* Manajemen konten video dan materi
* Manajemen evaluasi dan soal
* Manajemen mini-quiz
* Manajemen akun guru
* Manajemen checklist Pancawaluya
* Monitoring progres dan hasil evaluasi guru

---

## 🧭 Pancawaluya

| Nilai      | Makna                                    |
| ---------- | ---------------------------------------- |
| **Cageur** | Sehat secara fisik dan mental            |
| **Bageur** | Percaya diri dan mampu berkolaborasi     |
| **Bener**  | Disiplin dan menjunjung integritas       |
| **Pinter** | Tertib dan taat pada norma               |
| **Singer** | Responsif dan memiliki jiwa kepemimpinan |

---

## 🏗️ Architecture

LMS Pancawaluya menggunakan arsitektur **frontend–backend** yang terpisah.

```text
┌───────────────────────────────┐
│        LMS Pancawaluya        │
└───────────────┬───────────────┘
                │
        ┌───────┴───────┐
        │               │
        ▼               ▼
   ┌─────────┐     ┌─────────┐
   │ Frontend│────▶│ Backend │
   └─────────┘ API └────┬────┘
                        │
                        ▼
                 ┌─────────────┐
                 │ PostgreSQL  │
                 │  / Supabase │
                 └─────────────┘
```

Frontend berkomunikasi dengan backend melalui REST API dengan autentikasi berbasis JWT. Backend menangani business logic, database, authentication, authorization, dan penyimpanan data.

---

## 🧰 Tech Stack

### Frontend

* **Next.js 16**
* **React 19**
* **TypeScript**
* **Tailwind CSS 4**
* Native `fetch`
* App Router

### Backend

* **Node.js**
* **Express 5**
* **Prisma ORM**
* **PostgreSQL**
* **Supabase**
* **JWT**
* **bcrypt**
* **Resend**

---

## 📦 Repositories

| Repository                                                | Description                                            |
| --------------------------------------------------------- | ------------------------------------------------------ |
| [`frontend`](https://github.com/lms-pancawaluya/frontend) | Web application dan user interface LMS                 |
| [`backend`](https://github.com/lms-pancawaluya/backend)   | REST API, business logic, authentication, dan database |
| [`.github`](https://github.com/lms-pancawaluya/.github)   | Konfigurasi dan workflow default organisasi            |

---

## 🔐 User Roles

LMS Pancawaluya memiliki dua role utama:

**Guru**

Mengikuti pembelajaran, mengerjakan mini-quiz dan evaluasi, serta memantau progres pembelajaran.

**Admin**

Mengelola keseluruhan konten pembelajaran, akun guru, evaluasi, checklist, dan monitoring progres.

---

## 📚 Project Structure

```text
lms-pancawaluya/
│
├── frontend/     # Next.js web application
├── backend/      # Express REST API
└── .github/      # Organization-wide configuration
```

---

## 🎯 Project Goals

LMS Pancawaluya dikembangkan untuk:

* Mendigitalisasi proses pembelajaran Guru SMA.
* Menyediakan materi pembelajaran yang terstruktur.
* Mendorong penerapan nilai-nilai Pancawaluya.
* Mempermudah pemantauan progres pembelajaran.
* Menyediakan sistem administrasi dan evaluasi yang terintegrasi.

---

<p align="center">
  Built with ❤️ for <strong>Teachers</strong>
</p>
