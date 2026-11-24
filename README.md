# Diel Apl — Demo UMKM

## Uji coba
- Buka `index.html` langsung di browser modern. Untuk hasil paling konsisten, jalankan server lokal dari folder ini: `python -m http.server 8080` lalu buka `http://localhost:8080`.
- Data tersimpan di localStorage browser. Gunakan menu Laporan > Cadangkan data untuk mengunduh backup JSON.
- Ekspor CSV bisa dibuka dengan Microsoft Excel. Cetak nota/laporan menggunakan dialog print browser lalu pilih Save as PDF.

## Fitur demo
- Dashboard omzet, penjualan hari ini, estimasi laba kotor, stok menipis.
- CRUD sederhana bahan, produk/HPP, pelanggan.
- Pencatatan transaksi satu produk per transaksi, diskon, nota yang bisa dicetak.
- Laporan omzet/HPP/laba kotor, CSV, backup dan restore JSON.

## Batasan penting
Ini adalah prototipe lokal untuk pengujian, bukan sistem akuntansi final. Belum ada login, sinkronisasi antarperangkat, database server, multi-item dalam satu transaksi, pemotongan bahan baku otomatis berdasarkan resep, retur/utang, atau biaya operasional. Laba yang ditampilkan adalah laba kotor (omzet dikurangi HPP), bukan laba bersih.

## Menyiapkan APK Android dengan Capacitor
Perlu komputer dengan Node.js LTS, Android Studio, dan Android SDK.
1. Buat project baru: `mkdir diel-apl-android && cd diel-apl-android && npm init -y`
2. Pasang Capacitor: `npm install @capacitor/core @capacitor/cli @capacitor/android`
3. Buat konfigurasi: `npx cap init "Diel Apl" "id.dielapl.umkm" --web-dir=www`
4. Buat folder `www` lalu salin `index.html` dan `manifest.webmanifest` ke dalam `www`.
5. Tambahkan Android: `npx cap add android`
6. Sinkronkan aset: `npx cap sync android`
7. Buka Android Studio: `npx cap open android`
8. Di Android Studio, tunggu Gradle sync selesai. Untuk uji di HP, aktifkan Developer options dan USB debugging lalu tekan Run.
9. Untuk APK debug, gunakan menu Build > Build Bundle(s) / APK(s) > Build APK(s). Android Studio akan menunjukkan lokasi file APK.
10. Untuk rilis, gunakan Build > Generate Signed Bundle / APK dan buat signing key yang aman.

## Cara web
Untuk penggunaan web publik, unggah folder web ke hosting statis. Namun, versi localStorage ini menyimpan data per browser dan tidak menyinkronkan data antarperangkat. Untuk produksi, buat backend/API dan database (misalnya PostgreSQL/Supabase/Firebase), autentikasi, validasi server, dan backup terjadwal.
