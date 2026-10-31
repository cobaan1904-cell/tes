# RUANGDIGITAL190 — Digital Store v4

Website katalog produk digital statis menggunakan HTML, CSS, dan JavaScript vanilla. Siap dipublikasikan melalui GitHub Pages.

## Isi katalog
- 10 aplikasi: Netflix, Spotify, YouTube Premium, CapCut, Alight Motion, Canva, ChatGPT, Gemini, Grammarly, dan QuillBot.
- Mobile Legends: 25 pilihan nominal Diamond.
- Free Fire: 20 pilihan nominal Diamond + Membership Mingguan, BP Card, dan Membership Bulanan.
- Harga MLBB dan Free Fire mengikuti dua gambar price list toko yang tersedia; harga aplikasi yang belum diberikan tetap ditampilkan sebagai “Harga belum tersedia”.

## Fitur
- Katalog aplikasi premium dan game top-up.
- Logo produk dengan sumber utama dan fallback lokal.
- Filter kategori dan pencarian langsung.
- Marquee logo yang berjalan dan dapat diklik.
- Modal detail hanya untuk produk yang dipilih.
- Daftar harga MLBB dan Free Fire dari price list toko yang tersedia.
- Harga, diskon, deskripsi, dan stok dapat diedit melalui konfigurasi JavaScript.
- Status stok awal adalah **Konfirmasi stok** karena stok aktual perlu dikonfirmasi melalui WhatsApp.
- Pesan WhatsApp otomatis menyebut nama produk/paket, harga, dan menanyakan ketersediaan stok.
- Floating WhatsApp draggable dengan Pointer Events.
- Tidak ada keranjang atau checkout.
- Responsif untuk ponsel, tablet, dan desktop.

## File
- `index.html` — website lengkap.
- `assets/brand/ruangdigital-logo.jpg` — logo toko.
- `assets/brand/favicon.svg` — favicon.
- `assets/logos/` — fallback logo lokal.

## Pengaturan toko
Buka `index.html`, cari blok `STORE_CONFIG` di bagian awal JavaScript.

```js
const STORE_CONFIG = {
  storeName: "RUANGDIGITAL190",
  whatsappNumber: "6285725423328",
  // ...
};
```

Nomor WhatsApp harus menggunakan format internasional tanpa `+`, spasi, atau tanda hubung.

## Mengubah produk dan harga
Cari blok `PRODUCTS`.
- Ubah `title`, `description`, `short`, dan `info` untuk informasi produk.
- Ubah `logo` untuk sumber logo utama dan `fallback` untuk logo lokal.
- Setiap `variants` mempunyai `name`, `price`, `originalPrice`, `discountEnabled`, `stock`, dan `note`.
- Gunakan angka rupiah tanpa tanda titik, misalnya `45000`.
- Gunakan `null` jika harga belum tersedia; website akan menampilkan “Harga belum tersedia”, bukan Rp0.
- `stock` dapat berisi `available`, `limited`, `out_of_stock`, atau `confirm`.
- Diskon hanya tampil jika `discountEnabled: true`, `originalPrice` terisi, dan `price` lebih rendah daripada `originalPrice`.

Contoh:
```js
{
  name: "Paket Premium — 1 Bulan",
  price: 25000,
  originalPrice: 30000,
  discountEnabled: true,
  stock: "available",
  note: "Aktivasi sesuai ketentuan admin"
}
```

## Catatan stok dan penyimpanan
Website ini statis. Tidak ada backend atau database. Mengubah konfigurasi dan mengunggah ulang file ke GitHub akan memperbarui katalog untuk semua pengunjung. Posisi tombol WhatsApp yang digeser hanya disimpan di `localStorage` browser masing-masing pengunjung; itu tidak mengubah data toko.

## Logo merek
Sumber utama logo khusus:
- Free Fire: halaman brand resmi Garena — https://ff.garena.com/en-pk/brand/
- Alight Motion: listing resmi Google Play — https://play.google.com/store/apps/details?id=com.alightcreative.motion
- Mobile Legends: Bang Bang: listing resmi Google Play — https://play.google.com/store/apps/details?id=com.mobile.legends
- Logo aplikasi lainnya menggunakan Simple Icons CDN; setiap gambar memiliki fallback SVG lokal.

Logo dan merek dagang tetap milik masing-masing pemegang hak. Penayangan logo hanya untuk mengidentifikasi produk dan bukan klaim afiliasi atau dukungan resmi. Tiga tautan thumbnail Google yang disertakan dalam brief tidak dapat dibuka saat pemeriksaan, sehingga aset Free Fire, Alight Motion, dan MLBB diambil dari sumber resmi alternatif di atas.

## Deploy ke GitHub Pages
1. Buat repository baru di GitHub, misalnya `ruangdigital190`.
2. Unggah `index.html` dan seluruh folder `assets` (jangan hanya file HTML).
3. Buka **Settings → Pages**.
4. Pilih **Deploy from a branch**.
5. Pilih branch `main` dan folder `/ (root)`, lalu klik **Save**.
6. Tunggu deployment selesai, kemudian buka URL yang ditampilkan GitHub Pages.
7. Untuk memperbarui katalog, edit `STORE_CONFIG` atau `PRODUCTS` di `index.html`, lalu commit perubahan.

## Pemeriksaan
Kode JavaScript dan struktur HTML diperiksa secara statis. Tautan logo eksternal membutuhkan koneksi internet; jika sumber eksternal gagal dimuat, fallback lokal akan digunakan. Pengujian browser langsung tidak diklaim dalam paket ini.
