# Proposal — MasakApa: Bingung Masak Apa? Beres.

## Apa ini
Web app (frontend-only, tanpa backend, tanpa login) yang menjawab pertanyaan
paling sering di dapur Indonesia: "hari ini masak apa?". Pengguna memilih
bahan yang sudah ada di dapur, lalu aplikasi merekomendasikan masakan yang
cocok, diurutkan dari yang bahannya paling lengkap.

## Kenapa ini mengejutkan
Bukan sekadar daftar resep. Tiga hal yang bikin orang bilang "kok kepikiran":
1. **Cocokkan bahan, bukan cari nama masakan** — pilih "telur + tempe",
   langsung keluar menu yang bisa dimasak sekarang, lengkap dengan label
   bahan apa yang masih kurang.
2. **Mode Tanggal Tua** — filter "Hemat" (≤ Rp10.000/porsi) dan "Cepat"
   (≤ 20 menit) untuk hari-hari mepet.
3. **Rencana Seminggu + Daftar Belanja otomatis** — satu ketukan menghasilkan
   7 menu Senin–Minggu plus daftar belanja gabungan yang sudah dikelompokkan
   (Protein / Sayur & Buah / Bumbu & Dapur) dan bisa disalin ke catatan HP.

## Kenapa bentuk output ini
Web app statis: data resep bersifat statis, tidak ada data pengguna yang
perlu disimpan di server, dan localStorage cukup untuk menyimpan pilihan
bahan + rencana minggu. Backend tidak dibutuhkan — memakainya hanya akan
menambah kompleksitas tanpa manfaat. Bisa dibuka siapa saja dari satu link.

## Kenapa tanpa backend
Tidak ada login, tidak ada database, tidak ada API berbayar. Semua logika
(pencocokan bahan, rencana minggu, daftar belanja) berjalan di browser.
