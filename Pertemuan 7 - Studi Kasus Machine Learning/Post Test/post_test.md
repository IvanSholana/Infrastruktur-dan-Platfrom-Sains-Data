# Post-Test: Implementasi Studi Kasus Machine Learning

**Dataset yang digunakan:** [American House Prices](https://www.kaggle.com/datasets/jeremylarcher/american-house-prices-and-demographics-of-top-cities) dari Kaggle.

## Tujuan
Dalam post-test ini, kita akan menggunakan dataset untuk membuat tiga jenis model machine learning: regresi, klasifikasi, dan klustering. Tujuan dari tugas ini adalah untuk menguji pemahaman  dalam menerapkan berbagai teknik machine learning pada studi kasus yang diberikan.

## Ringkasan Dataset

Dataset ini mencakup berbagai variabel terkait perumahan dan demografi di 50 kota besar di Amerika Serikat berdasarkan populasi.

| **Variabel**                  | **Deskripsi**                                                                                         |
|-------------------------------|-------------------------------------------------------------------------------------------------------|
| **Zip Code**                  | Kode pos di mana properti berada                                                             |
| **Price**                     | Harga yang terdaftar untuk properti                                                         |
| **Beds**                      | Jumlah kamar tidur                                                     |
| **Baths**                     | Jumlah kamar mandi                                                     |
| **Living Space**              | Total luas ruang tamu dalam satuan *square feet*                        |
| **Address**                   | Alamat dari properti tersebut                                                          |
| **City**                      | Nama kota dimana properti berada                                                            |
| **State**                     | Nama negara bagian di mana properti berada                                                   |
| **Zip Code Population**       | Perkiraan jumlah penduduk dalam kode pos                         |
| **Zip Code Density**          | Perkiraan jumlah penduduk per mil persegi dalam kode pos                   |
| **County**                    | Nama daerah di mana properti berada                                                          |
| **Median Household Income**   | Perkiraan pendapatan rumah tangga secara median                              |
| **Latitude**                  | Garis lintang kode pos dari properti                                       |
| **Longitude**                 | Garis bujur kode pos dari properti                                         |

## Instruksi Langkah demi Langkah

### 1. Persiapan dan Pre-Processing Data
   - **Unduh dataset** dari Kaggle melalui link di atas.
   - **Eksplorasi data**:
     - Tinjau setiap kolom untuk memahami fitur yang tersedia dan menentukan variabel target.
     - Identifikasi potensi masalah dalam data, seperti nilai yang hilang atau variabel kategorikal.
   - **Pre-processing**:
     - Pembersihan data: Hapus atau tangani data yang hilang, misalnya dengan imputasi.
     - Encoding variabel kategorikal: Ubah fitur teks menjadi variabel numerik apabila diperlukan.
     - Normalisasi atau standarisasi: Terapkan pada variabel numerik yang akan dimasukkan ke model untuk memastikan skala yang seragam.

### 2. Model Regresi: Prediksi Harga Rumah
   - **Tugas**: Gunakan model regresi untuk memprediksi harga rumah (`Price`) berdasarkan fitur, seperti `Living Space`, `Beds`, `Baths`, `Median Household Income` (bisa menggunakan fitur lain apabila mendukung pembuatan model).
   - **Model yang Digunakan**: Linear Regression
   - **Output yang Diharapkan**:
     - Hasil Prediksi: Prediksi harga rumah untuk data uji yang belum terlihat oleh model.
     - Evaluasi Model: Nilai Mean Absolute Error (MAE) atau Root Mean Squared Error (RMSE) yang menunjukkan akurasi prediksi model terhadap harga rumah.
   - **Interpretasi**:
     - Ringkas kesesuaian model, misalnya, apakah MAE atau RMSE menunjukkan prediksi yang akurat untuk data ini.

### 3. Model Klasifikasi: Kategorisasi Harga Rumah
   - **Tugas**: Tentukan kategori harga rumah berdasarkan `price` untuk klasifikasi ke dalam kelas harga, misalnya "Rendah," "Sedang," dan "Tinggi."
   - **Langkah-Langkah**:
     - Buat label kategori harga berdasarkan persentil atau rentang harga tertentu.
     - Tambahkan kolom baru `price_category` ke dataset dengan nilai kategori tersebut.
   - **Model yang Digunakan** (pilih salah satu model): Logistic Regression, K-Nearest Neighbors (KNN), Naive Bayes, atau Support Vector Machine (SVM).
   - **Output yang Diharapkan**:
     - Hasil Klasifikasi: Kategori harga untuk setiap rumah dalam data uji.
     - Evaluasi Model: Metrik akurasi, precision, recall, dan F1-score untuk mengevaluasi kualitas klasifikasi.
   - **Interpretasi**:
     - Jelaskan performa model klasifikasi, apakah akurasi tinggi atau apakah terdapat ketidakseimbangan dalam prediksi kategori tertentu.

### 4. Model Klustering: Pengelompokan Rumah Berdasarkan Fitur
   - **Tugas**: Kelompokkan rumah berdasarkan fitur demografi dan properti, seperti `Living Space`, `Beds`, `Baths`, dan `Median Household Income`. Tujuan klustering adalah menemukan pola dalam data yang dapat mengelompokkan rumah dengan karakteristik serupa.
   - **Model yang Digunakan** (pilih salah satu model): K-Means atau DBScan
   - **Output yang Diharapkan**:
     - Hasil Klaster: Label klaster untuk setiap rumah yang menunjukkan segmen masing-masing.
     - Visualisasi Klaster: Plot yang menunjukkan hasil klastering, dengan warna berbeda untuk setiap klaster.
     - Evaluasi Klaster: Metrik seperti Silhouette Score untuk menunjukkan kualitas segmentasi.
   - **Interpretasi**:
     - Berikan gambaran singkat tentang karakteristik setiap klaster, seperti klaster dengan rumah-rumah berukuran besar atau klaster dengan pendapatan median tinggi.
     - Identifikasi segmen atau klaster yang mungkin menjadi target potensial untuk strategi pemasaran.

## 5. Kesimpulan
   - **Output yang Diharapkan**:
     - Rangkuman dari setiap model, mencakup akurasi model regresi, klasifikasi harga, dan segmentasi klaster.
     - Rekomendasi singkat: Berdasarkan hasil klastering, tentukan segmen yang memiliki potensi tinggi sebagai target utama untuk pemasaran, atau kategori harga yang menarik untuk strategi promosi.
