# Kuduko Ses Kayıt Stüdyosu — Windows Masaüstü Sürümü

Electron + taşınabilir PHP ile paketlenmiş `studio.php`. Kurulum sonrası internet gerekmez.

## Gereksinimler (yalnızca derleme yapan bilgisayarda)
- Windows 10/11
- Node.js 18+ (https://nodejs.org)

## Adımlar
```bat
npm install
npm run setup     :: PHP'yi indirir + CDN dosyalarını yerele çevirir (internet gerekir)
npm start         :: denemek için uygulamayı açar
npm run build     :: dist\ klasörüne Setup .exe ve Portable .exe üretir
```

Çıktılar `dist\` içinde:
- `Kuduko Ses Studyosu Setup 1.0.0.exe`  → kurulumlu sürüm
- `Kuduko Ses Studyosu 1.0.0.exe`        → kurulum gerektirmeyen taşınabilir sürüm

## Veriler nerede?
Projeler, veritabanı ve ses dosyaları: `%APPDATA%\kuduko-ses-studyosu\data\`
(`music.db`, `studio_uploads\`, `uploads\` [mixdown'lar], `php_errors.log`)

## Yapılan değişiklikler (orijinal studio.php'ye göre)
- Giriş sistemi kaldırıldı: tek yerel kullanıcı (id=1, "Yerel Kullanıcı").
- `users` ve `music` tabloları yerel veritabanında otomatik oluşturulur.
- Veritabanı/yükleme yolları `STUDIO_DATA_DIR` ortam değişkeninden gelir.
- `index.php` yalnızca profil resmi için basit bir yer tutucu sunar.
- Mikrofon izni Electron tarafında otomatik verilir.

## Sorun giderme
- "php.exe bulunamadı": `npm run setup` çalıştırılmamış.
- `npm run setup` PHP'yi indiremezse: https://windows.php.net/download adresinden
  **VS16/VS17 x64 Non Thread Safe** zip'ini indirip `php\` klasörüne açın (`php.exe` doğrudan `php\` içinde olmalı).
- Mikrofon görünmüyorsa: Windows Ayarlar → Gizlilik → Mikrofon → "Masaüstü uygulamalarının erişimi" açık olmalı.
- Simge eklemek için `build\icon.ico` (256x256) koyun.
