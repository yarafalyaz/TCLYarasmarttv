# Fork notes — perubahan dari upstream CleanYourTV

## Header
- Greeting + nama `Yara Falya Zimirleen` semibold (font `outfit_semibold`).
- Cuaca Open-Meteo (Mampang Prapatan, -6.2423, 106.8308), refresh 30 menit. Butuh izin `INTERNET` — ditambah di `AndroidManifest.xml` (launcher upstream sengaja tanpa internet).
- Prayer Times Aladhan method 20 (Kemenag): Subuh, Dzuhur, Ashar, Maghrib, Isya. Sesudah Isya target Subuh besok.
- Glass night: `header_glass.xml` gradasi gelap, dipakai header greeting/cuaca, judul app kanan, indikator titik.

## Layout
- Judul app besar dipindah kanan (`hero`, `layout_gravity=top|right`), supaya foto di kiri tidak tertutup.
- Indikator titik: glass chip sendiri, terpisah dari judul.
- Grid 6 kolom, pill Pustaka aplikasi bawah disembunyikan (`library_button: true` + `show_library_pill: false`), tombol grid di top bar tetap.
- Footer: `© <tahun otomatis> YaraSoft. All rights reserved. · TCL Smart TV · Android TV 11` — merk/model/OS dibaca dari `Build`, bukan hardcode.

## Remote
- `app_keys`: `KEYCODE_BUTTON_3` + `KEYCODE_TCL_YOUTUBE` → `org.smarttube.beta` (scancode YouTube remote TCL `0xf1d` = 3869).
- YouTube asli (`com.google.android.youtube.tv`) di-disable via ADB supaya tombol remote tidak diambil firmware.
- SmartTube tampil sebagai tile "YouTube": `app_labels` + `app_banners` (`banner_youtube.png`).

## Screensaver
- `ClockDream`: slideshow dari folder `slideshow/` di external files launcher, 5 menit/foto, urutan sequential, dissolve 1,2 detik (`TransitionDrawable`).
- Folder `slideshow/` terpisah dari wallpaper Home, supaya Home tidak ikut berotasi.
- `ThemeFiles`/`ThemeProvider`: whitelist path `slideshow/*.jpg|png|webp` + delete folder slideshow.

## Tema
- `custom/themes/appletv/config.json` — tema aktif.
- `custom/themes/six-custom/config.json` — tema cadangan.
- Wallpaper pribadi dan foto screensaver pribadi **tidak** disertakan (privasi). Taruh manual:
  - Wallpaper: `wallpaper.jpg` di folder tema, lalu `tools/theme.sh`.
  - Screensaver: upload ke `Android/data/com.gathin.tvhome/files/slideshow/` via `content://com.gathin.tvhome.theme/slideshow/ss1.jpg` dst.

## Debloat
- `custom/debloat/debloat.txt` — daftar paket dinonaktifkan (konservatif). Netflix, Vision+, SmartTube, Downloader, File Manager+, Voice Assistant, Chromecast, Miracast, update firmware dipertahankan.
