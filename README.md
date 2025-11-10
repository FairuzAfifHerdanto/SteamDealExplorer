**🎮 Steam Deal Explorer**

Sebuah dashboard visualisasi data interaktif untuk menemukan penawaran (deal) game terbaik di Steam, dibuat sebagai bagian dari Proyek A4.

**🚀 Demo Interaktif**

Visualisasi ini di-hosting menggunakan GitHub Pages. Anda bisa mengakses dan berinteraksi dengan versi livenya di sini:

https://edrilmarfadli.github.io/SteamDealExplorer/steam_deal_explorer.html

**📖 Deskripsi Proyek
**
Seringkali sulit untuk menemukan game yang bagus sekaligus murah di Steam. Diskon besar (misalnya -80%) belum tentu berarti gamenya bagus (bisa jadi ulasannya 'Mixed'). Sebaliknya, game berkualitas tinggi (ulasan 'Overwhelmingly Positive') mungkin jarang diskon.

Steam Deal Explorer adalah alat bantu untuk mengatasi masalah ini. Dashboard interaktif ini memungkinkan pengguna untuk memfilter ribuan game Steam berdasarkan:

- Harga

- Persentase Diskon

- Kualitas Ulasan (Recent Reviews)

- Judul Game

Tujuannya adalah untuk membantu pengguna mendefinisikan "penawaran terbaik" versi mereka sendiri dan menemukan game berkualitas tinggi yang sesuai dengan budget mereka.

**✨ Fitur Utama**

Filter Interaktif: Cari berdasarkan judul, atur slider untuk rentang harga dan persentase diskon.

Filter Kualitas: Pilih satu atau beberapa kategori ulasan (misalnya, hanya tampilkan game 'Overwhelmingly Positive' dan 'Very Positive').

Scatter Plot (Harga Asli vs. Harga Diskon): Visualisasi yang kuat untuk melihat seberapa besar penghematan Anda. Semakin jauh titik dari garis diagonal, semakin bagus penawarannya.

Histogram Distribusi Diskon: Melihat seberapa umum diskon (misalnya -50%, -75%) pada game yang Anda filter.

Bar Chart (Diskon vs. Ulasan): Menjawab pertanyaan, "Apakah game dengan ulasan bagus mendapat diskon lebih kecil?"

Daftar 'Top Savings': Daftar game yang sudah terfilter, diurutkan berdasarkan jumlah uang (dalam dolar) yang paling banyak Anda hemat.

**🔬 Rasionalisasi Desain (Design Rationale)
**
Pilihan desain visualisasi dan interaksi didasarkan pada tujuan utama: memungkinkan pengguna untuk "menemukan penawaran bagus secara subjektif".

**Pilihan Visual Encoding**

**Scatter Plot (Harga Asli vs. Harga Saat Ini)**: Ini adalah visualisasi inti. Sebuah diskon -80% tidak ada artinya jika harga aslinya hanya $1. Sebaliknya, diskon -40% untuk game $60 (hemat $24) jauh lebih signifikan. Plot ini, ditambah dengan garis y=x (garis tanpa diskon), secara visual mengkodekan nilai penghematan moneter sebagai jarak vertikal titik dari garis. Ini jauh lebih informatif daripada hanya menunjukkan persentase diskon.

**Bar Chart (Diskon Rata-rata vs. Ulasan)**: Daripada membanjiri pengguna dengan ribuan titik data, saya memilih untuk mengagregasi data. Bar chart ini dengan cepat menjawab pertanyaan analitis tingkat tinggi: "Secara rata-rata, apakah game 'Overwhelmingly Positive' mendapatkan diskon yang lebih buruk daripada game 'Mixed'?"

**Histogram (Distribusi Diskon)**: Ini memberikan konteks penting bagi pengguna. Ini membantu mereka memahami "lanskap" diskon saat ini. Jika mereka melihat banyak game di bin -75%, mereka tahu bahwa itu adalah diskon yang umum.

Daftar "Top Savings" (Tabel Teks): Grafik bagus untuk analisis pola, tetapi untuk tindakan, pengguna memerlukan daftar yang jelas dan dapat dibaca. Daftar yang diurutkan ini adalah "jawaban" akhir. Setelah pengguna menerapkan semua filter (budget, kualitas), daftar ini memberi mereka hasil yang dapat ditindaklanjuti, diurutkan berdasarkan penghematan dolar terbesar.

**Pilihan Interaksi**

**Filter (Kontrol)**: Interaksi utama adalah filtering (penyaringan), bukan brushing & linking yang kompleks. Tujuannya adalah untuk mempersempit (drill-down) dari ribuan game menjadi segelintir game yang relevan.

**Slider (Harga & Diskon)**: Slider adalah cara paling intuitif untuk menentukan rentang numerik.

**Dropdown Multi-Select (Ulasan)**: Kualitas (ulasan) adalah data kategorikal. Dropdown multi-select memungkinkan pengguna untuk menggabungkan kategori (misalnya, "Hanya tampilkan game 'Very Positive' DAN 'Overwhelmingly Positive'").

**Hover (Detail-on-Demand)**: Plotly.js menyediakan tooltips (info saat hover) yang kaya secara default. Ini penting untuk melihat detail game (judul, harga, dll.) tanpa harus mencari di daftar.

**Alternatif yang Dipertimbangkan**

Treemap: kami mempertimbangkan menggunakan treemap untuk memvisualisasikan game berdasarkan kategori atau popularitas. Namun, ini saya batalkan karena kurang efektif untuk tujuan utama (mencari diskon) dan akan membuat dashboard terlalu padat.

Satu Scatter Plot Besar: Alternatif lain adalah bubble chart tunggal (Harga vs. Diskon, dengan ukuran = skor ulasan). Ini ditolak karena bar chart dan filter multi-select terpisah jauh lebih mudah dibaca dan lebih presisi untuk memfilter berdasarkan kualitas.

**🛠️ Proses Pengembangan (Development Process)**

- Pembagian Kerja

1. Edril Marfadli : Dataset & csv
2. Aqilah Fikry Albari: HTML
3. Gilang Yanuar Cahaya: HTML
4. Fairuz Afif : HTML
   
**Aspek yang Memakan Waktu Terbanyak:
**
1. Logika Reaktivitas & Filtering (Tugas Anggota 2, Inti): Membuat semua visualisasi (tiga chart dan satu daftar teks) diperbarui secara instan sebagai respons terhadap kombinasi dari empat jenis filter yang berbeda adalah bagian terlama, membutuhkan debugging yang signifikan, dan menyerap sebagian besar waktu tim.

2. Desain & Styling (Tugas Anggota 3): Memastikan tampilan dashboard yang profesional, responsif, dan konsisten dengan tema gelap Steam juga membutuhkan waktu tuning yang cukup lama.

3. Transformasi Data & Analisis Awal: Tugas ini, yang meliputi konversi format data dan EDA, adalah tugas yang paling cepat diselesaikan, diperkirakan total 2-3 jam gabungan antara Anggota 1 dan Anggota 5.


**📊 Sumber Data**

Dataset utama: steam_store_data_2024.csv

Data di-pre-processing dan di-embed langsung ke dalam file .html untuk mempermudah hosting dan performa.

**🏃 Menjalankan Secara Lokal**

Karena semua library (Plotly.js) dan data sudah tertanam di dalam file steam_deal_explorer.html, Anda tidak perlu menjalankan web server lokal.

Clone atau unduh repositori ini.

Buka file steam_deal_explorer.html di browser favorit Anda.
