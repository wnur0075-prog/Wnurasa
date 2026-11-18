# ScalpX (UI demo bot scalping kripto)

Aplikasi Android berbasis Capacitor. Isi aplikasi ada di `www/index.html`.

Yang sudah berfungsi (mode hanya pantau):
- Harga live Indodax (BTC, ETH, SOL, DOGE, USDT dalam IDR), candlestick
  dari data harga, dan order book. API publik, tanpa kunci.
- Tab Akun: simpan API Key + Secret Indodax di HP, uji koneksi, dan baca saldo
  (getInfo, ditandatangani HMAC-SHA512).

Belum ada: pengiriman order dan bot otomatis. Tab Strategi dan Riwayat
masih contoh tampilan. Kode koneksi belum diuji langsung ke Indodax,
jadi coba dulu dengan kunci berizin Info saja.

## Cara 1: bangun APK lewat GitHub (tanpa install apa pun)

1. Buat repo baru di GitHub, lalu upload seluruh isi folder ini
   (termasuk folder `.github`).
2. Buka tab **Actions**, pilih **Build APK**, klik **Run workflow**.
3. Setelah selesai (sekitar 5 menit), unduh artifact `scalpx-debug-apk`.
   Di dalamnya ada `app-debug.apk`.
4. Kirim ke HP, buka, izinkan "install dari sumber tidak dikenal".

## Cara 2: bangun di komputer

Syarat: Node.js 20+, JDK 21, Android Studio (atau Android SDK).

```
npm install
npx cap add android
npx cap sync android
cd android
./gradlew assembleDebug
```

APK ada di `android/app/build/outputs/apk/debug/app-debug.apk`.
Atau jalankan `npx cap open android` lalu Build > Build APK di Android Studio.

## Catatan

- Ini APK debug untuk uji coba. Untuk Play Store perlu APK/AAB yang
  ditandatangani (release signing).
- Setiap kali mengubah `www/index.html`, jalankan `npx cap sync android`
  lalu bangun ulang.
