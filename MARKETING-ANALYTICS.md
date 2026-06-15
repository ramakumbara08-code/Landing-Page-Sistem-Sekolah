# Marketing Analytics

Dashboard marketing di folder ini mengelola data dari dua landing:

- Landing absensi perusahaan: `customer-product.html`
- Landing sistem sekolah: `school-product.html`
- Demo sistem sekolah: `demo-school.html`

Data disimpan di Firebase marketing sendiri melalui Apps Script marketing sendiri.

## Data Yang Disimpan

- Page view landing page
- Unique visitor berbasis visitor ID di browser
- Referrer
- UTM source, medium, campaign, term, content
- Source link lengkap
- Jenis produk landing
- Bahasa, timezone, ukuran layar, user agent
- Device ringkas: tipe perangkat dan platform
- Estimasi lokasi IP: kota, provinsi/region, negara, IP, dan provider jika layanan geolocation berhasil membaca data
- Klik tombol CTA
- Lead demo: nama, WhatsApp, kab/kota, instansi/sekolah, link WhatsApp, consent broadcast
- Status funnel lead: lead baru, sudah dihubungi, prospek cocok, demo dijadwalkan, demo selesai, negosiasi, closing, tidak lanjut, arsip
- Template WhatsApp global di dashboard dengan placeholder `{{nama}}`, `{{nama_sekolah}}`, `{{kab_kota}}`, dan `{{produk}}`
- History kunjungan dan event CTA per lead berdasarkan visitor ID/session ID
- History follow-up WhatsApp per tanggal
- Aktivitas demo berdasarkan `leadId`: login demo, buka menu, simulasi scan, input dummy, dan klik fitur
- Skor minat lead berdasarkan kunjungan, CTA, submit form, dan aktivitas demo

## Link Broadcast Dengan UTM

Landing sistem sekolah:

```text
school-product.html?utm_source=whatsapp&utm_medium=broadcast&utm_campaign=sekolah_juni
```

Landing absensi perusahaan:

```text
customer-product.html?utm_source=whatsapp&utm_medium=broadcast&utm_campaign=absensi_juni
```

Link demo tertaut lead:

```text
demo-school.html?leadId=lead_xxx&utm_source=marketing_dashboard&utm_medium=demo_link&utm_campaign=sistem_sekolah
```

Untuk preview tanpa menyimpan kunjungan analytics:

```text
?no_track=1
```

Untuk preview tetap tracking tetapi tanpa mengambil estimasi lokasi IP:

```text
?no_ip_location=1
```

## Panel Analytics

Dashboard dapat memfilter:

- sumber traffic
- status funnel
- source link
- tanggal masuk lead
- nama/WA/kab-kota/instansi

Klik `Detail` pada lead untuk melihat device dan history kunjungan halaman.

Klik `Copy Demo` pada tabel lead untuk menyalin link demo yang sudah membawa `leadId`. Ketika calon customer membuka link tersebut, aktivitasnya di halaman demo akan masuk ke history lead.

Kolom `Lokasi IP` adalah estimasi dari alamat IP, bukan GPS. Data ini tidak membutuhkan izin lokasi browser, tetapi akurasinya bisa berbeda jika pengunjung memakai VPN, proxy, jaringan kantor, atau operator seluler.

## CRUD dan Deduplikasi Lead

Dashboard menyediakan tambah, edit, hapus, detail, dan follow-up WA untuk data lead.

Jika calon customer mengisi form berkali-kali dengan nomor WA yang sama, sistem tidak membuat kontak ganda. Data baru akan digabung ke lead lama, lalu history submission, visitor/session, klik CTA, dan kunjungan tetap terkumpul di detail lead.

## WhatsApp

Website tidak mengirim pesan WhatsApp otomatis tanpa WhatsApp Business API atau gateway resmi. Sistem marketing ini menyimpan lead, membuka WhatsApp admin dengan teks otomatis dari template global, menyediakan tombol follow-up WA, menampilkan history kunjungan, dan export CSV untuk broadcast.
