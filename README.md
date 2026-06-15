# Marketing Analytics Terpisah

Folder ini adalah aplikasi marketing mandiri yang setara dengan `absen-lama` dan `absen-sekolah`.

Tujuannya:

- Landing produk absensi dan sistem sekolah dikelola dari satu folder marketing.
- Dashboard analytics marketing tidak bergantung ke aplikasi absensi lama atau aplikasi sekolah.
- Apps Script dan Firebase marketing bisa memakai project sendiri agar data lead/kunjungan tidak bercampur dengan data operasional aplikasi.

## Struktur

```text
marketing/
  index.html
  marketing-analytics.html
  customer-product.html
  school-product.html
  demo-school.html
  assets/
  gas/
    Code.gs
    Database.gs
    MarketingAuth.gs
    MarketingTracking.gs
  firebase.json
  vercel.json
  README.md
  MARKETING-ANALYTICS.md
  DEMO-AKUN-SEKOLAH.md
  DEPLOY-MARKETING.md
```

## Halaman

- `index.html` - dashboard marketing analytics.
- `marketing-analytics.html` - alias dashboard analytics.
- `customer-product.html` - landing produk absensi perusahaan.
- `school-product.html` - landing produk sistem sekolah.
- `demo-school.html` - demo sistem sekolah dengan akun dummy dan tracking aktivitas ke lead marketing.

## Route Vercel

Jika folder `marketing` dijadikan root project Vercel:

```text
/analytics
/produk
/produk-sekolah
/produk-absensi
/demo-sekolah
/demo
```

## Konfigurasi Yang Harus Diisi

Di frontend:

- `API_BASE_URL` di `index.html`
- `API_BASE_URL` di `marketing-analytics.html`
- `MARKETING_API_URL` di `customer-product.html`
- `MARKETING_API_URL` di `school-product.html`

Semua harus mengarah ke Web App Apps Script marketing khusus.

Di backend GAS:

- `FIREBASE_URL` di `gas/Database.gs`
- `FIREBASE_SECRET` di `gas/Database.gs`

Gunakan Firebase Realtime Database khusus marketing.

## Akun Dashboard Marketing

Atur Script Properties di Apps Script marketing:

```text
MARKETING_OWNER_ID
MARKETING_OWNER_PASSWORD
MARKETING_ADMIN_ID
MARKETING_ADMIN_PASSWORD
```

Dashboard memakai action `login`, tetapi validasinya khusus marketing dan tidak membaca admin aplikasi absensi/sekolah.

## Catatan

File marketing lama di `absen-lama` dan landing sekolah di `absen-sekolah` belum dihapus agar link yang sudah ada tidak rusak. Untuk pengelolaan baru, gunakan folder `marketing`.
