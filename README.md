# TCL Yara Smart TV

Fork pribadi dari [CleanYourTV](https://github.com/Gathin23/cleanyourtv) — launcher Android TV custom untuk TCL Smart TV pribadi. Upstream: https://github.com/Gathin23/cleanyourtv (periksa lisensinya di LICENSE sebelum distribusi ulang).

## Yang diubah dari upstream
- Header: nama greeting semibold, cuaca Open-Meteo + Prayer Times (Aladhan/Kemenag) — butuh izin INTERNET (ditambah di AndroidManifest).
- Glass night header, judul app kanan + indikator titik glass terpisah.
- Footer: © tahun otomatis YaraSoft · merk TV + Android TV dari Build.TCL/Build.VERSION.
- SmartTube tampil sebagai tile YouTube (label + banner banner_youtube.png), YouTube asli disembunyikan + didisable.
- Screensaver ClockDream: slideshow folder slideshow/ (5 menit/foto, dissolve 1,2 dtk) terpisah dari wallpaper Home.
- Tema: custom/themes/appletv (6 kolom, pill Pustaka aplikasi bawah sembunyi, tombol grid atas tetap), six-custom.
- Debloat konservatif: custom/debloat/debloat.txt.

## Yang SENGAJA tidak ikut
- Wallpaper/foto pribadi, snapshot layar/shots, backup paket/TV serial (IP, android_id, nama Wi-Fi), tools/venv, build cache, APK.
- Foto screensaver pribadi (ss1-ss4) tidak dipublish. Letakkan sendiri di: Android/data/com.gathin.tvhome/files/slideshow/

## Cara pakai ringkas
1. Build+install launcher: lihat launcher/README atau tools/build-and-install.sh di upstream.
2. Push tema: TV_HOST=<IP-TV> tools/theme.sh custom/themes/appletv
3. Upload foto screensaver via ThemeProvider: content://com.gathin.tvhome.theme/slideshow/ss1.jpg dst.
