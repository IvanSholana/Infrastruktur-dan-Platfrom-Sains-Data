**Deskripsi Kasus untuk Masalah Klastering**

**Tujuan:**

Tujuan dari analisis ini adalah melakukan segmentasi pelanggan berdasarkan data dasar pelanggan yang mencakup ID Pelanggan, usia, jenis kelamin, pendapatan tahunan, dan skor belanja (Spending Score). Metode klastering akan digunakan untuk mengelompokkan pelanggan dalam segmen yang berbeda berdasarkan kesamaan karakteristik mereka, dengan menggunakan algoritma K-Means dan DBSCAN. Segmentasi ini bertujuan untuk membantu menentukan target pelanggan yang lebih mudah dipengaruhi dan memberikan wawasan strategis kepada tim pemasaran untuk perencanaan strategi pemasaran yang lebih efektif.

**Ringkasan Dataset:**
- **Variabel Target (Dependent Variable):** Tidak ada variabel target spesifik karena ini adalah masalah klastering tanpa pengawasan.
- **Fitur Prediktor (Independent Variables):**
  - **ID Pelanggan (Customer ID):** Identifikasi unik setiap pelanggan.
  - **Usia (Age):** Usia pelanggan dalam satuan tahun.
  - **Jenis Kelamin (Gender):** Jenis kelamin pelanggan.
  - **Pendapatan Tahunan (Annual Income):** Pendapatan tahunan pelanggan dalam mata uang tertentu.
  - **Spending Score:** Skor yang menggambarkan perilaku dan data pembelian pelanggan berdasarkan parameter yang telah ditetapkan.

Dataset ini berisi informasi dasar tentang pelanggan yang ideal untuk segmentasi menggunakan algoritma klastering karena adanya fitur-fitur kontinu dan kategori yang relevan untuk pengelompokan.

**Tahapan Analisis Berdasarkan Siklus Hidup Data Science:**
Proses segmentasi pelanggan akan mengikuti tahapan Data Science Life Cycle sebagai berikut:

1. **Pemahaman Masalah (Problem Understanding)**
   - **Pertanyaan Kunci:** Bagaimana kita dapat mengelompokkan pelanggan berdasarkan karakteristik dasar mereka dan menemukan target pelanggan yang mudah dipengaruhi?
   - **Tujuan Utama:** Mengelompokkan pelanggan dengan algoritma klastering dan mengidentifikasi target pelanggan yang paling potensial untuk strategi pemasaran.
  
2. **Pengumpulan Data (Data Collection)**
   - Dataset ini telah disediakan dalam file CSV dan berisi informasi dasar pelanggan, termasuk ID pelanggan, usia, jenis kelamin, pendapatan tahunan, dan skor belanja.

3. **Eksplorasi Data (Data Exploration)**
   - Memeriksa distribusi variabel (pendapatan tahunan dan skor belanja).
   - Menghitung statistik deskriptif (mean, median, standar deviasi) untuk memahami karakteristik demografis dan perilaku pelanggan.
   - Visualisasi hubungan antar variabel menggunakan scatter plot dan histogram untuk melihat pola dan keterkaitan.

4. **Persiapan Data (Data Preparation)**
   - Memeriksa apakah ada data hilang (missing values) atau outlier.
   - Melakukan normalisasi atau standarisasi data jika diperlukan.
   - Mengelola encoding untuk variabel kategori seperti jenis kelamin agar dapat diolah oleh model klastering.

5. **Pemodelan (Modeling)**
   - Menggunakan K-Means untuk melakukan klastering awal, menyesuaikan jumlah klaster (k) untuk memperoleh hasil yang optimal.
   - Menggunakan DBSCAN untuk klastering berbasis kepadatan yang lebih adaptif terhadap pola-pola yang tidak teratur.
   - Menerapkan kedua model dan membandingkan hasil klaster untuk memahami perbedaan hasil yang dihasilkan oleh masing-masing metode.

6. **Evaluasi Model (Model Evaluation)**
   - Mengukur kualitas klastering menggunakan metrik evaluasi seperti Silhouette Score dan Davies-Bouldin Index untuk menilai kepaduan dan pemisahan antar klaster.
   - Menginterpretasikan hasil klaster untuk mengidentifikasi segmen pelanggan potensial sebagai target pemasaran.

**Output yang Diharapkan:**
- Segmentasi pelanggan dengan menggunakan K-Means dan DBSCAN beserta analisis hasilnya.
- Visualisasi klaster untuk memudahkan interpretasi hasil segmentasi.
- Identifikasi segmen pelanggan potensial yang bisa menjadi target utama untuk strategi pemasaran.
- Wawasan dan kesimpulan dari hasil analisis yang dapat digunakan untuk perencanaan strategi pemasaran di dunia nyata.
