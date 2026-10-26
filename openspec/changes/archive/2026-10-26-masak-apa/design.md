# Design — MasakApa

## Stack
Satu web artifact statis (HTML + CSS + JavaScript, tanpa framework, tanpa
build step, tanpa backend). Data resep tertanam sebagai array di dalam file.
Persistensi via localStorage. Tidak ada fetch eksternal saat dibuka.

## Struktur halaman (satu file, seksi berurutan)
1. Header: judul "MasakApa" + tagline "Bingung masak apa hari ini? Beres."
2. Hero acak: tombol besar "Acak Menu" + area hasil shuffle.
3. "Bahan yang ada di dapur": chip multi-pilih (13 bahan).
4. Mode + pencarian: pil Semua / Cepat / Hemat / Spesial + input cari.
5. Hasil: kartu masakan (nama, waktu, biaya/porsi, pedas, badge kecocokan,
   tombol "Lihat Resep" → panel detail bahan + langkah).
6. Rencana Seminggu: tombol buat, 7 kartu hari, daftar belanja berkelompok,
   tombol Salin Daftar / Acak Lagi / Hapus Rencana.
7. Catatan kejujuran harga + footer.

## Keranjang state (lima keranjang)
- Data statis: array katalog masakan (tetap, bukan state).
- State UI (in-memory): bahan terpilih, mode aktif, kata kunci, hasil acak,
  menu yang detailnya terbuka.
- State turunan (computed): daftar hasil tersaring + terurut, daftar belanja
  gabungan dari rencana minggu.
- State tersimpan (localStorage): bahan terpilih, rencana minggu.
- Tidak ada server state (tanpa backend) dan tidak ada form state khusus.

## Visual (mode Operate, dunia "dapur hangat")
- Latar krem hangat, aksen merah terakota, teks arang gelap, heading serif
  (Georgia) + bodi sans sistem. Mobile-first, satu kolom, lebar maks 720px.
- Tanpa emoji pada label — badge hanya teks ("Cepat", "Hemat", "Pedas",
  "Bahan lengkap", "Kurang: ...").
- Delight: animasi shuffle pada Acak Menu (nama berganti cepat ±900ms lalu
  berhenti dengan efek pop), chip yang berubah warna saat aktif, kartu
  terangkat saat disentuh.

## Aturan arsitektur yang dipatuhi
- Satu file, seksi berurutan (disiplin single-file untuk static).
- Tidak ada import antar-fitur (tidak relevan — satu file), tidak ada
  komponen >300 baris yang terpisah, tidak ada secret (tidak ada secret
  sama sekali), tidak ada fungsi mati.
- Anti-AI-slop: copy Bahasa Indonesia natural, kalimat pendek, tanpa
  kata-kata generik ala template AI.
