# Panduan kontribusi — lms-pancawaluya

File ini berlaku untuk seluruh repo di organisasi (frontend, backend).

## Aturan dasar

- `main` di setiap repo adalah branch protected — dilarang push langsung,
  wajib lewat Pull Request. Aturan ini berlaku untuk semua orang, termasuk
  yang berstatus Owner (branch protection diset dengan "Do not allow
  bypassing the above settings" aktif).
- Set default pull strategy ke rebase, sekali saja di komputer masing-masing,
  supaya histori tetap linear dan konflik lebih jarang menumpuk:
  ```
  git config --global pull.rebase true
  ```

## Penamaan branch

Buat branch baru dari `main` untuk setiap task, jangan kerja lama di satu
branch tanpa sinkron:

- `feat/nama-fitur` — fitur baru, misal `feat/dashboard-admin`
- `fix/nama-bug` — perbaikan bug, misal `fix/header-overlap`
- `chore/deskripsi` — perubahan non-fitur (dependency, config, dll)

Hapus branch setelah PR di-merge.

## Alur kerja harian

1. Sebelum mulai kerja: `git checkout main && git pull`
2. **Koordinasi singkat dulu** di grup tim kalau mau menyentuh file yang
   sering dipakai bareng (Header, layout utama, routing) — cukup satu
   pesan "aku mau ubah Header buat X" supaya tidak dua orang jalan
   bersamaan di file yang sama tanpa saling tahu
3. Buat branch, kerja, **commit kecil dan sering** — jangan menumpuk semua
   perubahan jadi satu commit besar di akhir
4. Push branch, buka PR sedini mungkin sebagai **Draft PR** kalau
   pekerjaan belum selesai — rekan tim bisa lihat progres dan tahu area
   mana yang sedang "dipegang" orang lain
5. Tandai "Ready for review" setelah selesai
6. Setelah ada approval + CI hijau, merge pakai **Squash and merge**
7. `git pull` lagi di lokal sebelum mulai task berikutnya

## Kenapa ini penting

Merge conflict besar hampir selalu terjadi karena branch hidup lama tanpa
sinkron ke `main`. Semakin sering `pull` dan semakin pendek umur branch,
semakin kecil (atau bahkan tidak ada) konflik yang muncul saat merge.

## Review

- Setiap PR butuh minimal 1 review sebelum merge.
- GitHub otomatis melarang approve PR milik sendiri, jadi review harus
  datang dari salah satu anggota tim lain.
- Untuk repo dengan 1 kontributor utama (misal backend saat ini), reviewer
  boleh dari anggota tim lain sebagai pengecekan kedua — tidak harus paham
  detail backend, cukup baca perubahan dan pastikan tidak ada yang janggal.
