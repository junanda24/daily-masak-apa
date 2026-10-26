# Spec — MasakApa

## Requirements

### R1 — Katalog masakan
- SHALL memuat minimal 30 masakan Indonesia nyata, masing-masing dengan:
  nama, waktu masak (menit), estimasi biaya per porsi (rupiah), level pedas
  (Tidak pedas / Ringan / Sedang / Pedas), bahan utama, daftar bahan, dan
  langkah memasak singkat yang benar (resep standar, bukan karangan).
- WHEN katalog dimuat THEN semua kartu menampilkan nama, waktu, biaya/porsi,
  dan level pedas — tidak ada kartu kosong atau placeholder.

### R2 — Filter bahan
- SHALL menyediakan pilihan bahan multi-pilih (Ayam, Telur, Tempe, Tahu,
  Mie, Ikan, Daging Sapi, Udang, Sayur, Kentang, Sosis, Jamur, Kornet).
- WHEN satu atau lebih bahan dipilih THEN hasil diurutkan dari kecocokan
  tertinggi (semua bahan utama tersedia dulu), dan tiap kartu yang belum
  lengkap menampilkan label "Kurang: <bahan>".
- WHEN tidak ada bahan dipilih THEN semua masakan tampil (tanpa filter).

### R3 — Filter mode & pencarian
- SHALL menyediakan mode: Semua, Cepat (≤ 20 menit), Hemat (≤ Rp10.000/porsi),
  Spesial (≥ 45 menit), plus kotak pencarian nama masakan.
- WHEN mode atau kata kunci berubah THEN daftar hasil diperbarui seketika.

### R4 — Acak menu (delight)
- SHALL menyediakan tombol "Acak Menu" yang menganimasikan pergantian nama
  masakan beberapa kali lalu berhenti di satu masakan dan menampilkannya
  sebagai pilihan terpilih.
- WHEN tombol ditekan THEN animasi berjalan dan hasil akhirnya selalu
  masakan yang valid dari katalog (tidak pernah kosong).

### R5 — Rencana seminggu
- SHALL menyediakan tombol "Buat Rencana Seminggu" yang menghasilkan 7 menu
  berbeda (Senin–Minggu) dengan variasi bahan utama (tidak ada bahan utama
  yang sama lebih dari 2 kali) dan menyertakan minimal 2 menu cepat.
- SHALL menghasilkan daftar belanja gabungan dari 7 menu itu, dikelompokkan
  (Protein / Sayur & Buah / Bumbu & Dapur), tanpa duplikat, dengan tombol
  "Salin Daftar" dan "Acak Lagi".
- WHEN rencana dibuat THEN rencana tersimpan di localStorage dan tetap ada
  saat halaman dibuka ulang; tombol "Hapus Rencana" menghapusnya.

### R6 — Detail resep
- SHALL menampilkan detail tiap masakan (daftar bahan + langkah) saat
  kartunya dibuka, dan bisa ditutup kembali.
- WHEN detail dibuka THEN langkah yang ditampilkan adalah langkah memasak
  yang masuk akal dan berurutan untuk masakan itu.

### R7 — Persistensi & perangkat
- SHALL menyimpan pilihan bahan di localStorage sehingga kembali saat
  halaman dibuka ulang.
- SHALL tampil rapi di layar HP (satu kolom, tombol mudah ditekan) maupun
  desktop, dengan copy Bahasa Indonesia natural dan TANPA emoji pada label.

### R8 — Kejujuran data
- SHALL menampilkan catatan bahwa estimasi biaya per porsi adalah perkiraan
  dan harga pasar bisa berbeda.
- SHALL NOT memakai lorem ipsum, placeholder palsu, atau fungsi mati.
