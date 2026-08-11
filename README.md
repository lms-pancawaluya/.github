# .github

Repo ini bukan project biasa — isinya konfigurasi default yang otomatis
berlaku ke **semua repo** di organisasi `lms-pancawaluya` (termasuk
`frontend` dan `backend`), selama repo tersebut belum punya file sejenis
di dalamnya sendiri.

## Isi repo ini

- **`CONTRIBUTING.md`** — panduan alur kerja: penamaan branch, cara commit,
  alur Pull Request. Muncul otomatis sebagai link di halaman "Contributing"
  tiap repo yang belum punya `CONTRIBUTING.md` sendiri.
- **`PULL_REQUEST_TEMPLATE.md`** — isi form yang otomatis muncul setiap kali
  ada yang membuka Pull Request baru di repo mana pun di organisasi ini
  (yang belum punya template sendiri).

## Kalau mau ubah aturan

Cukup edit file di repo ini, tidak perlu ubah satu-satu ke tiap repo
(`frontend`, `backend`, dst) — perubahan otomatis berlaku ke semua.

Kalau suatu repo butuh aturan yang beda dari default (misal `backend` mau
template PR yang berbeda dari `frontend`), tinggal taruh file dengan nama
sama di repo tersebut — file lokal itu akan menimpa default dari sini.
