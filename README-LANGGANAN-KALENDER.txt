# Jadwal STI — versi fokus langganan kalender

## Perubahan frontend
- Menghapus fitur unduh `.ics` untuk 1 minggu/1 bulan.
- Mengganti area tersebut dengan fitur salin URL langganan kalender untuk kelas aktif (A/B).
- Menambahkan panduan singkat iPhone dan Android.
- Tidak membuat klaim bahwa sinkronisasi atau alarm selalu instan/terjamin.

## Penting: endpoint kalender belum dipasang
Frontend ini belum dapat berlangganan secara nyata sampai tersedia feed kalender publik berformat iCalendar (`text/calendar`) melalui HTTPS. Setelah endpoint PHP dipasang, ubah konstanta berikut di `script.js`:

```js
const CALENDAR_FEED_BASE_URL = 'https://YOUR-INFINITYFREE-DOMAIN/calendar.php?class=';
```

Ganti `https://YOUR-INFINITYFREE-DOMAIN/calendar.php?class=` dengan alamat endpoint sebenarnya dan pertahankan tanda `=` di akhir, agar script menambahkan `A` atau `B`.

Contoh format URL (hanya contoh, belum aktif):
`https://domain-anda.example/calendar.php?class=A`

## Sinkronisasi dan pengingat
- Kalender berlangganan mengambil data dari URL feed; aplikasi kalender menentukan kapan feed disegarkan. Pembaruan tidak dijamin langsung muncul.
- Google Calendar di Android umumnya memerlukan penambahan kalender lewat Google Calendar versi web menggunakan URL kalender; kalender kemudian dapat tampil di perangkat yang tersinkron ke akun.
- iPhone dapat menggunakan langganan kalender berbasis URL melalui aplikasi/pengaturan kalender.
- Pengingat 30 menit sebelum kelas tidak dapat dijamin lintas aplikasi. Perlu pengujian pada aplikasi kalender yang digunakan, karena dukungan alarm untuk kalender berlangganan berbeda-beda.
