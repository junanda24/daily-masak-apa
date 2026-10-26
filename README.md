# MasakApa — Bingung Masak Apa? Beres.

Web app statis (tanpa backend, tanpa login) yang menjawab pertanyaan paling
sering di dapur Indonesia: **"hari ini masak apa?"** — dari bahan yang sudah
ada di dapur, bukan dari nama masakan yang harus diingat dulu.

Buka aplikasinya, pilih bahan yang ada (ayam, telur, tempe, tahu, dan
seterusnya), dan MasakApa langsung mengurutkan menu yang bisa dimasak
sekarang: yang bahannya lengkap di atas, yang masih kurang bahan diberi
label jelas ("Kurang: ...").

## Kenapa ide ini dipilih

Tiga hal yang bikin ide ini beda dari sekadar daftar resep:

1. **Cocokkan bahan, bukan cari nama masakan.** Orang jarang bingung karena
   tidak tahu nama masakan — mereka bingung karena tidak tahu bahan yang
   ada di kulkas bisa jadi apa. MasakApa membalik alurnya.
2. **Mode Tanggal Tua.** Filter "Hemat" (≤ Rp10.000/porsi) dan "Cepat"
   (≤ 20 menit) untuk hari-hari mepet uang maupun waktu.
3. **Rencana Seminggu + Daftar Belanja otomatis.** Satu ketukan menghasilkan
   7 menu Senin–Minggu plus daftar belanja gabungan yang sudah dikelompokkan
   (Protein / Sayur & Buah / Bumbu & Dapur) dan bisa disalin ke catatan HP.
   Ini fitur yang biasanya cuma ada di aplikasi meal-plan berbayar.

## Fitur

- **35 masakan Indonesia nyata** dengan waktu masak, estimasi biaya per
  porsi, level pedas, daftar bahan bertakaran, dan langkah memasak.
- **Filter bahan multi-pilih** (13 bahan: Ayam, Telur, Tempe, Tahu, Mie,
  Ikan, Daging Sapi, Udang, Sayur, Kentang, Sosis, Jamur, Kornet) dengan
  pengurutan berdasarkan kecocokan dan label bahan yang kurang.
- **Mode Semua / Cepat / Hemat / Spesial** + pencarian nama masakan.
- **Acak Menu** dengan animasi shuffle: nama masakan berganti cepat lalu
  berhenti di satu pilihan dengan efek pop.
- **Rencana Seminggu**: 7 menu berbeda, bahan utama tidak muncul lebih dari
  2 kali, minimal 2 menu cepat; daftar belanja gabungan tanpa duplikat;
  tombol Salin Daftar, Acak Lagi, dan Hapus Rencana.
- **Persistensi localStorage**: pilihan bahan dan rencana minggu tetap ada
  saat halaman dibuka ulang.
- **Mobile-first**: satu kolom, tombol besar, nyaman dipakai sambil
  berdiri di dapur.
- **Tanpa emoji pada label** — semua badge hanya teks.

## Cara pakai

1. Buka aplikasi (lihat "Link hasil" di bawah).
2. Pilih bahan yang ada di dapur — daftar menu langsung terurut.
3. Atau tekan **Acak Menu** kalau malas memilih.
4. Tekan **Lihat Resep** di kartu mana pun untuk bahan dan langkahnya.
5. Tekan **Buat Rencana Seminggu** untuk menu 7 hari + daftar belanja,
   lalu **Salin Daftar** untuk membawanya ke pasar.

## Cara menjalankan dari source

Tidak perlu build, tidak perlu server, tidak perlu install apa pun. File
`src/masak-apa.html` adalah aplikasi lengkap yang berdiri sendiri:

```bash
# Cara 1: buka langsung di browser
xdg-open src/masak-apa.html

# Cara 2: lewat server lokal (opsional)
cd src && python3 -m http.server 8000
# lalu buka http://localhost:8000/masak-apa.html
```

## Tech stack

- HTML + CSS + JavaScript murni (tanpa framework, tanpa build step)
- Data resep tertanam di dalam file (array JavaScript)
- localStorage untuk menyimpan pilihan bahan dan rencana minggu
- Tanpa backend, tanpa database, tanpa API eksternal, tanpa login

## Struktur folder

```
2026-10-26-masak-apa/
├── README.md
├── src/
│   └── masak-apa.html        # aplikasi lengkap (hasil export artifact)
└── openspec/
    └── changes/
        └── archive/
            └── 2026-10-26-masak-apa/
                ├── proposal.md
                ├── design.md
                ├── tasks.md
                └── specs/
                    └── masak-apa/
                        └── spec.md
```

## Link hasil

- Aplikasi: artifact `masakapa` di aplikasi Muse (dibuka lewat kartu artifact;
  belum di-share sebagai link publik)
- Repo: https://github.com/junanda24/daily-masak-apa
- Tanggal rilis: 2026-10-26

## Catatan / temuan saat build

- **Tanpa backend itu keputusan sadar.** Data resep statis, tidak ada data
  pengguna yang perlu disimpan di server, dan localStorage sudah cukup.
  Backend hanya akan menambah kompleksitas tanpa manfaat.
- **Estimasi biaya per porsi adalah perkiraan.** Harga bahan berbeda antar
  daerah dan waktu; aplikasi menampilkan catatan kejujuran ini secara
  eksplisit, bukan angka yang diklaim pasti.
- **Resep ditulis dari cara masak standar** masing-masing masakan (bumbu
  dan urutan langkah yang umum dipakai), bukan karangan.
- **Satu bug sempat muncul saat verifikasi**: tombol Acak Menu tidak pernah
  berhenti pada pengujian otomatis karena jam virtual tidak maju. Sudah
  diperbaiki dengan menghitung durasi dari akumulasi jeda timer, dan
  diverifikasi berhenti dengan benar.
- Yang sengaja tidak dibuat: akun/login, simpan resep favorit ke server,
  dan harga bahan real-time (butuh API dan datanya berubah-ubah) — ketiganya
  tidak dibutuhkan untuk menyelesaikan masalah inti.
