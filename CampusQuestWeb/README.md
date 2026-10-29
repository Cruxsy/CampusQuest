# CampusQuest — Prototipe NFC Campus Companion

CampusQuest adalah prototipe front-end satu halaman dengan enam modul utama:
1. Dashboard & Aktivitas
2. Campus Rewards
3. Absensi Kuliah
4. Akses Perpustakaan & Loker
5. Peminjaman Buku
6. Kas Iuran

Pendaftaran mahasiswa dan fungsi tulis/baca NFC tersedia melalui menu **Daftar & Tulis NFC** (bukan tab ketujuh).

## Cara mencoba secara lokal
- Buka `index.html` di browser untuk mencoba antarmuka dan fitur dengan pemilihan mahasiswa manual.
- Data disimpan menggunakan `localStorage` pada browser/perangkat tersebut.
- NFC Web umumnya membutuhkan Chrome Android yang kompatibel, HTTPS, izin pengguna, serta tag NFC NDEF yang sesuai. Membuka file HTML langsung tidak cukup untuk pengujian NFC.

## Cara menerbitkan dengan GitHub Pages (untuk HTTPS dan pengujian NFC)
1. Buat repository GitHub baru.
2. Unggah seluruh isi folder proyek ini ke root repository (termasuk `.github`, `icons`, `index.html`, `manifest.webmanifest`, dan `sw.js`).
3. Buka tab **Actions** dan jalankan workflow **Deploy CampusQuest to GitHub Pages** jika belum berjalan otomatis.
4. Jika diminta, buka **Settings → Pages** dan pilih **GitHub Actions** sebagai build/deployment source.
5. Setelah workflow berhasil, buka URL Pages yang ditampilkan pada hasil deployment di Chrome Android.
6. Pastikan HP mendukung NFC dan tag yang dipakai mendukung penulisan NDEF. Berikan izin NFC saat diminta.
7. Di CampusQuest, buka **Daftar & Tulis NFC**, isi nama dan NIM, buat profil, pilih profil, lalu tekan **Tulis ke NFC**. Untuk membaca, tekan **Baca NFC** atau gunakan tombol pindai di modul terkait.

## Catatan penting
- Semua data masih lokal di satu browser/perangkat; tidak ada server atau sinkronisasi antar-HP.
- Pencatatan QRIS belum terintegrasi dengan penyedia pembayaran dan tidak memverifikasi bahwa pembayaran benar-benar berhasil. Kasir perlu memeriksa pembayaran secara terpisah; data reward di sini hanya catatan demo.
- Absensi memakai kunci unik mahasiswa + mata kuliah + pertemuan + tanggal agar tap berulang tidak membuat catatan duplikat pada data lokal perangkat itu.
- Gelang menyimpan teks `CAMPUSQUEST|V1|NIM=...|TOKEN=...`. NIM pada tag dapat dibaca oleh perangkat kompatibel dan isi tag statis bisa disalin. Ini bukan sistem autentikasi yang aman untuk produksi. Untuk produksi, lebih aman menyimpan token acak saja pada tag dan memetakan token ke NIM di backend dengan kontrol akses; pertimbangkan tag dengan autentikasi kriptografis untuk kebutuhan keamanan lebih tinggi.
- Loker, akses perpustakaan, poin, dan kas merupakan simulasi pencatatan. Prototipe tidak mengoperasikan kunci fisik dan tidak memindahkan uang.
- Gunakan data mahasiswa fiktif untuk demo, bukan data pribadi nyata, saat menguji pada layanan hosting publik.

## Data
Gunakan **Pengaturan → Ekspor JSON** untuk membuat cadangan lokal. Impor JSON akan mengganti data lokal yang sedang tersimpan. Reset menghapus semua data lokal pada browser ini.
