# Form Tamu Mandiri

Halaman statis untuk mencatat kehadiran tamu dari ponsel. Formulir dapat
digunakan tanpa backend; data akan tersimpan di `localStorage` pada browser
yang digunakan.

## Menjalankan secara lokal

Buka `guest-mobile.html` di browser, atau jalankan server statis dari folder
ini:

```bash
python -m http.server 8000
```

Lalu buka <http://localhost:8000>. `index.html` meneruskan ke halaman formulir.

## Hosting dengan GitHub Pages

Folder ini berisi seluruh berkas yang diperlukan untuk hosting statis. Jika
membuat repository khusus untuk halaman ini, unggah isi folder ini ke root
repository, lalu:

1. Buka **Settings > Pages** di repository GitHub.
2. Pada **Build and deployment**, pilih **Deploy from a branch**.
3. Pilih branch publikasi (biasanya `main`) dan folder `/(root)`, lalu klik
   **Save**.
4. Setelah publikasi selesai, buka alamat GitHub Pages yang ditampilkan pada
   halaman Settings. `index.html` akan meneruskan ke formulir.

GitHub Pages hanya meng-host berkas statis. Untuk menyimpan data bersama
secara online, deploy backend Google Apps Script sebagai Web App dan atur URL
di `config.js` sebelum publikasi:

```js
window.BUKU_TAMU_GAS_URL = 'https://script.google.com/macros/s/ID_DEPLOYMENT/exec';
```

Berikan akses Web App sesuai kebutuhan aplikasi. Tanpa URL Apps Script yang
valid, formulir menggunakan `localStorage`; data tersebut hanya tersedia di
browser/perangkat yang menyimpannya dan tidak tersinkron ke Google Sheets.

## Mengunduh data ke komputer

Setelah formulir berhasil disimpan, klik **Unduh data JSON**. Browser akan
mengunduh satu file JSON untuk data tamu tersebut. Jika browser menyimpannya
di folder Downloads, pindahkan file itu ke
`C:\Users\USER\buku-tamu-app\guest-mobile`. GitHub Pages tidak dapat menulis
file secara langsung ke folder di komputer.

## Berkas

- `index.html` — halaman masuk yang meneruskan ke formulir
- `guest-mobile.html` — formulir tamu
- `guest-mobile.js` — logika formulir, kamera, dan penyimpanan
- `style.css` — tampilan responsif
- `config.js` — URL backend Apps Script
