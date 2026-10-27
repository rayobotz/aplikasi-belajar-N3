# Aplikasi Belajar N3 — Versi GitHub Pages (Progres Tersimpan)

Satu aplikasi belajar JLPT N3 (fondasi N4 → N3) dalam satu file `index.html`,
siap di-hosting statis (mis. GitHub Pages). Isinya sama persis dengan versi link:
16 misi, Mode Penguat 70 pola bunpō dari 『JLPT N3 この一冊で合格する』（日本語の森）,
review kosakata 107 kata (hari 1–12), kuis konteks, dan audio MP3 penutur asli.

## Bedanya dari versi link

Progres **tersimpan di browser pengguna** lewat `localStorage`:

- XP, level, misi/deck/kuis yang selesai, skor terakhir, kartu tumpukan ulang
  (SRS/Leitner versi aplikasi ini), rentetan jawaban benar, dan rangkaian hari
  belajar (streak) disimpan otomatis setiap ada perubahan.
- Menutup / memuat ulang halaman **tidak** meng-nol-kan progres, selama dibuka
  di perangkat dan browser yang sama.
- Ada tombol **"Reset progres"** di bagian "Data tersimpan & pengaturan"
  (dengan konfirmasi dua kali).
- Progres tidak dikirim ke siapa pun dan tidak ada di server. Ganti HP/browser,
  mode privat/incognito, atau hapus data browser = progres hilang.
- Fitur kabar "2 hari tidak dibuka" tetap **tidak** ada di versi ini
  (itu hanya di versi server Muse).

## Struktur folder

```
aplikasi-n3-github/
├── index.html          <- aplikasi utamanya (satu file)
├── README.md
└── assets/
    ├── hero.webp
    └── audio/          <- 9 file MP3 (contoh + listening)
```

Jangan pisahkan `index.html` dari folder `assets/` — audio dan gambar
direferensikan dengan path relatif `assets/...`.

## Cara pasang di GitHub Pages

1. Buat akun GitHub (kalau belum punya), lalu buat repository baru
   (mis. `aplikasi-belajar-n3`).
2. Upload **seluruh isi folder ini** ke repository (termasuk folder `assets`),
   pastikan `index.html` berada di root repository.
3. Di repository: **Settings → Pages → Build and deployment → Source:
   Deploy from a branch**, pilih branch `main` dan folder `/ (root)`, simpan.
4. Tunggu ±1 menit — GitHub akan menampilkan URL situsnya
   (biasanya `https://<username>.github.io/aplikasi-belajar-n3/`).
   Link itulah yang dikirim ke pengguna.
5. Untuk memperbarui materi nanti: upload ulang `index.html` (dan aset baru
   bila ada) ke repository yang sama — URL-nya tetap, dan progres pengguna
   tetap tersimpan selama kunci penyimpanannya tidak berubah.

## Kunci penyimpanan

- Key: `aplikasi-belajar-n3:progress:v1`
- Isi: `{ version: 1, state: { xp, done, scores, review, badges, correctStreak },
  meta: { streakDays, lastStudyDate, firstOpenedAt, lastOpenedAt, totalOpens, savedAt } }`

Catatan: di `file://` progres tersimpan per folder/lokasi file; setelah
di-hosting, progres tersimpan per origin (domain) GitHub Pages. Jadi progres
yang terlanjur dibuat saat membuka file lokal tidak ikut pindah ke versi online.
