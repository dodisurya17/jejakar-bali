# Panduan Mencoba Demo JEJAKAR BALI (WebAR)

File `index.html` ini adalah prototipe **WebAR sungguhan** — bukan simulasi.
Kalau dibuka lewat kamera HP, kamu akan benar-benar melihat figur 3D prajurit
(representasi tokoh Puputan Badung) muncul menimpa dunia nyata, lengkap dengan
panel judul melayang, tombol info sejarah, dan narasi suara (text-to-speech
Bahasa Indonesia).

Teknologi yang dipakai: **A-Frame + AR.js** (gratis, open source, murni jalan
di browser — HP wisatawan tidak perlu install apa pun).

## Kenapa tidak bisa langsung discan dari sini?

AR.js butuh akses kamera, dan browser modern **mewajibkan koneksi HTTPS**
untuk mengizinkan akses kamera dari sebuah situs. Karena itu file ini perlu
di-*hosting* dulu ke sebuah URL HTTPS sebelum bisa dibuka dan discan dari HP.
Untungnya ada beberapa cara gratis untuk itu:

### Cara tercepat: GitHub Pages (gratis, 5 menit)
1. Buat akun GitHub (kalau belum punya) di github.com
2. Buat repository baru, misalnya `jejakar-bali-demo`
3. Upload file `index.html` ke repository tersebut
4. Masuk ke **Settings > Pages**, pilih branch `main` sebagai source
5. Tunggu 1-2 menit, GitHub akan memberi URL seperti:
   `https://namamu.github.io/jejakar-bali-demo/`
6. Buka URL itu di HP (Chrome/Safari) — browser akan minta izin kamera, izinkan

### Alternatif: Netlify Drop (lebih cepat, tanpa akun GitHub)
1. Buka **app.netlify.com/drop**
2. Drag & drop folder ini ke halaman tersebut
3. Netlify langsung memberi URL HTTPS yang bisa dipakai

## Cara membuat QR Code menuju demo ini

Setelah dapat URL hosting (misalnya dari GitHub Pages/Netlify), buat QR code
yang mengarah ke URL tersebut. Bisa pakai:
- qr-code-generator.com (gratis, tinggal paste URL)
- Google "generate QR code" — banyak tools gratis

File `qr-code-contoh.png` di folder ini adalah **contoh format QR**, tapi
isinya masih URL placeholder — ganti dengan URL hosting asli kamu.

## Cara uji coba di lokasi (atau di meja kerja dulu)

1. Cetak / tampilkan di layar lain **marker Hiro** (marker uji standar AR.js) —
   unduh gratis di: `https://ar-js-org.github.io/AR.js/data/images/hiro.png`
   (marker inilah yang dideteksi kamera untuk memicu munculnya figur 3D)
2. Buka URL hasil hosting di HP, izinkan akses kamera
3. Arahkan kamera HP ke marker Hiro yang sudah dicetak
4. Figur 3D prajurit akan muncul berputar di atas marker, lengkap panel judul
5. Tap tombol **"📖 Info Sejarah"** untuk membaca narasi
6. Tap tombol **"🔊 Dengar Narasi"** untuk mendengarkan narasi (text-to-speech)

## Untuk implementasi nyata di Puputan Badung (bukan sekadar demo)

Prototipe ini memakai marker Hiro (pola kotak hitam-putih generik) karena
gratis dan stabil dideteksi — cocok untuk pembuktian konsep. Untuk versi
produksi sesungguhnya, ada 2 pendekatan yang bisa dipilih tim:

**A. Marker custom bermotif Bali**
Ganti pola Hiro dengan pola/gambar buatan sendiri (misalnya motif ukiran
atau logo JEJAKAR BALI) memakai AR.js Marker Training tool
(`ar-js-org.github.io/AR.js/three.js/examples/marker-training/examples/generator.html`),
lalu dicetak dan ditempel berdampingan dengan QR Code di lokasi wisata.

**B. Location-based AR (tanpa marker fisik)**
Memakai GPS + kompas HP untuk memicu munculnya objek 3D begitu wisatawan
berdiri di titik geografis tertentu (misalnya di Lapangan Puputan Badung),
tanpa perlu marker sama sekali. AR.js juga mendukung mode ini
(`arjs='sourceType: webcam; ... locationBased`). Cocok untuk destinasi
outdoor luas, tapi akurasi GPS di lapangan perlu diuji langsung.

**Untuk model 3D yang lebih realistis:**
Figur prajurit di demo ini masih berbentuk geometris sederhana (kubus,
silinder, bola) sebagai bukti konsep gratis dan ringan. Untuk hasil final,
tim bisa bekerja sama dengan modeler 3D (mahasiswa DKV/animasi) atau memesan
aset dari platform seperti Sketchfab / TurboSquid, lalu mengimpornya ke
scene AR.js dalam format `.glb`/`.gltf`.
