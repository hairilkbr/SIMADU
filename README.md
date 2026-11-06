# SIMADU — Android WebView Project

Aplikasi Android bernama **SIMADU** yang membuka layanan resmi Disdukcapil Kabupaten Buol melalui WebView.

- URL awal: https://disdukcapil.buolkab.go.id/jelajahi-layanan
- Application ID: `id.go.buolkab.disdukcapil.simadu`
- Bahasa: Kotlin
- Android SDK: compile/target 35, minimum Android 6.0 (API 23)
- Java/Kotlin target: 17

## Fitur aplikasi yang disiapkan

1. WebView dengan JavaScript, DOM Storage, cookies, dan tampilan responsif.
2. Memulai aplikasi langsung pada halaman Jelajahi Layanan.
3. Navigasi tombol kembali Android mengikuti riwayat halaman website.
4. Pemilih dokumen Android untuk formulir upload website (termasuk pemilihan beberapa file jika diminta oleh halaman).
5. Unduhan dokumen memakai Android DownloadManager, meneruskan cookie sesi website, dan menampilkan notifikasi unduhan.
6. Splash screen, ikon dasar, serta warna identitas biru SIMADU.
7. Tautan eksternal seperti telepon, email, dan situs di luar domain dibuka melalui aplikasi/browser yang sesuai.
8. Hanya HTTPS dari domain layanan yang dimuat di dalam aplikasi; unduhan dibatasi ke domain resmi.

## Membuka dan membangun APK

1. Ekstrak ZIP proyek ini.
2. Buka Android Studio → **Open** → pilih folder `SIMADU_Android_Project`.
3. Pastikan Android SDK Platform 35 dan JDK 17 tersedia.
4. Tunggu proses Gradle Sync.
5. Pilih **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
6. APK debug akan berada di `app/build/outputs/apk/debug/app-debug.apk`.

### Alternatif build melalui GitHub Actions

Workflow tersedia di `.github/workflows/build-apk.yml`.

1. Buat repository GitHub bernama `SIMADU`.
2. Upload isi folder proyek (termasuk folder `.github`).
3. Buka tab **Actions** dan jalankan workflow **Build SIMADU APK**.
4. Setelah berhasil, unduh artifact `SIMADU-debug-APK` dan ekstrak file `app-debug.apk`.

## Catatan verifikasi penting

- Proyek ini adalah **kerangka aplikasi WebView**, bukan APK final yang sudah dikompilasi dan diuji pada perangkat.
- Pemeriksaan otomatis terhadap URL target belum berhasil dilakukan dari lingkungan pembuatan proyek. Karena itu, fungsi setiap alur website (login, pendaftaran, seluruh formulir, validasi, unggah, status permohonan, dan unduh) harus diuji langsung pada perangkat Android.
- Upload standar HTML didukung melalui pemilih file Android. Jika website memakai upload kamera khusus, popup/new-tab, autentikasi pihak ketiga, atau integrasi browser tertentu, perlu penyesuaian setelah alur tersebut diuji.
- Notifikasi saat unduhan selesai sudah disiapkan. **Notifikasi push** status permohonan/berita ketika aplikasi tertutup memerlukan dukungan backend atau Firebase Cloud Messaging; WebView saja tidak dapat membuat push notification dari website tanpa integrasi server.
- Aplikasi menggunakan HTTPS dan tidak mengaktifkan akses file lokal atau JavaScript bridge. Jangan menambahkan `addJavascriptInterface` tanpa kebutuhan dan tinjauan keamanan.
- Pastikan ada izin/otorisasi dari pengelola website dan instansi sebelum mendistribusikan APK dengan nama serta layanan resmi. Jangan gunakan data penduduk sungguhan untuk pengujian.
- APK debug bukan rilis Play Store. Untuk distribusi resmi, siapkan signing key produksi, kebijakan privasi, dan pengujian keamanan.

## Identitas aplikasi

- Nama: SIMADU
- Warna utama: `#0756A4`
- Warna aksen: `#F3C969`
