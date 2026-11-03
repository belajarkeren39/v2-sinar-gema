# Sinar & Gema — Kiri atau Kanan

IPAS kelas V SD · Cahaya dan Bunyi. Layar kamera dibagi dua: daerah **KIRI** dan daerah **KANAN**. Tiap soal menampilkan dua pilihan jawaban, satu di tiap daerah. Murid berpindah ke daerah jawaban yang menurut mereka benar.

## Menjalankan
- **Kamera:** buka `mulai-lokal.cmd` (atau `node server.cjs`) lalu buka `http://127.0.0.1:8765`. Kamera butuh HTTPS atau localhost.
- **Tanpa kamera:** buka `index.html`, pilih kontrol **Tombol**. Ketuk separuh layar atau tekan ← / → (A / L).
- 

## Alur satu soal
1. **Baca:** soal dan dua pilihan tampil; waktu belum berjalan. Tekan **Mulai hitung mundur** (Enter).
2. **Berpindah:** 10/15/20 detik (diatur di pengaturan). Murid berjalan ke daerah jawabannya. Tampilan menunjukkan persentase murid di tiap sisi.
3. **Terkunci:** 3 detik diam. Posisi dirata-ratakan pada 2 detik terakhir.
4. **Pembahasan:** sisi benar menyala hijau, sisi salah memerah, lalu penjelasan tampil. Enam soal per sesi.

Skor: +20 untuk sisi mayoritas yang benar. Bila tidak ada murid terbaca atau kedua sisi hampir sama, soal ditandai "posisi belum jelas" dan tidak mendapat poin.

## Kalibrasi kamera
1. **Bingkai kosong:** semua murid keluar bingkai, kamera merekam latar 3 detik dan mengukur noise.
2. **Uji dua sisi:** satu murid berdiri di kiri lalu kanan; keduanya harus terbaca.

Kamera harus diam dan tegak. Kalibrasi ulang tersedia lewat **Jeda**.

## Batas kemampuan
- Deteksi memakai selisih gambar terhadap latar kosong (bukan pengenalan orang, wajah, atau pose). Ia mengukur seberapa luas tiap sisi tertutup sesuatu yang bukan latar, sehingga barang yang dipindah, orang lewat, atau perubahan cahaya besar ikut terbaca.
- Penilaian untuk **kelompok** (sisi mayoritas), bukan per murid. Kamera tidak mengenali siapa berdiri di mana. Untuk penilaian individu, minta tiap murid mencocokkan posisinya dengan sisi hijau saat pembahasan, atau catat manual.
- Murid yang berdiri tepat di garis tengah (±3% lebar) tidak dihitung ke sisi mana pun.
- Kamera nyata belum diuji bersama murid; lihat `HASIL-UJI.md`.

## Bank soal
Bank 75 soal tidak berubah (tiga opsi per soal, ruang guru dan impor/ekspor JSON tetap sama). Saat bermain, setiap soal memakai kunci jawaban ditambah satu pengecoh acak, sehingga tampil dua pilihan. Pengecoh dapat berbeda antar sesi.

## Berkas
`index.html` (aplikasi + bank), `bank-soal.json` (cadangan), `server.cjs`, `mulai-lokal.cmd`, `manifest.json`. Semua ilustrasi (latar sampul dan maskot prisma) berupa SVG di dalam `index.html`; folder `asset/` hanya berisi audio opsional.
