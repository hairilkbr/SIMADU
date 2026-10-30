# SIMADU Android WebView

Proyek Android Studio untuk membungkus website layanan Disdukcapil Kabupaten Buol sebagai aplikasi bernama **SIMADU**.

URL awal: `https://disdukcapil.buolkab.go.id/jelajahi-layanan`

## Fitur yang disiapkan
- WebView dengan JavaScript dan DOM storage.
- Tombol kembali Android mengikuti riwayat halaman.
- Pemilih file untuk formulir unggah pada website.
- Unduh file melalui Android DownloadManager, dengan notifikasi unduhan.
- Splash screen dan ikon dasar SIMADU.
- Tautan HTTP/HTTPS ke luar domain dibuka di browser eksternal.
- Unduhan dibatasi ke domain `disdukcapil.buolkab.go.id` demi keamanan.

## Membuat APK
1. Instal Android Studio versi stabil dan Android SDK Platform 35.
2. Ekstrak ZIP ini.
3. Android Studio → **Open** → pilih folder `SIMADU_Android_Project`.
4. Tunggu Gradle Sync selesai.
5. Pilih **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
6. APK debug biasanya ada di `app/build/outputs/apk/debug/app-debug.apk`.

## Catatan penting
- Website harus dapat diakses melalui HTTPS dan mengizinkan tampilan dalam WebView. Saya belum dapat memverifikasi halaman target karena permintaan pemeriksaan dari lingkungan ini mengalami timeout; uji di perangkat sebelum dipakai.
- Fitur unggah bekerja melalui pemilih file Android bila halaman menggunakan input file HTML standar. Alur unggah khusus atau kamera mungkin memerlukan penyesuaian.
- Notifikasi dalam proyek ini mencakup notifikasi unduhan. **Notifikasi push** untuk berita/status layanan saat aplikasi tidak dibuka membutuhkan backend atau layanan push seperti Firebase Cloud Messaging dan konfigurasi server.
- Aplikasi memuat situs layanan kependudukan. Pastikan Anda berwenang menerbitkan aplikasi yang memakai nama/layanan instansi, memperoleh persetujuan pemilik website, dan menjaga keamanan data pribadi.
- Jangan menambahkan `addJavascriptInterface` tanpa kebutuhan dan tinjauan keamanan.

## Build APK tanpa Android Studio (melalui GitHub Actions)
1. Buat akun GitHub jika belum punya, lalu buat repository baru bernama `SIMADU`.
2. Unggah seluruh isi folder proyek ini ke repository, termasuk folder `.github/workflows`.
3. Buka tab **Actions** pada repository dan pilih workflow **Build SIMADU APK**.
4. Klik **Run workflow** jika belum berjalan otomatis.
5. Setelah status selesai, buka hasil workflow dan unduh artifact **SIMADU-debug-APK**. Ekstrak ZIP artifact untuk mendapatkan `app-debug.apk`.
6. Pindahkan APK ke ponsel Android dan instal. Android mungkin meminta Anda mengizinkan instalasi dari sumber tersebut.

APK yang dihasilkan adalah APK debug untuk uji coba, bukan rilis Play Store yang ditandatangani dengan kunci produksi.
