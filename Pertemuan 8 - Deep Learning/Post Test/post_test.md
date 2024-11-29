# Post-Test: Implementasi Image Processing Menggunakan PyTorch

**Dataset yang digunakan:** [Intel Image Classification](https://www.kaggle.com/datasets/puneet6060/intel-image-classification)

## Tujuan
Praktikum ini diharapkan mampu mengimplementasikan model *image processing* menggunakan PyTorch untuk klasifikasi gambar. Post-test ini bertujuan menguji pemahaman dalam membangun, melatih, dan mengevaluasi model deep learning menggunakan dataset gambar dunia nyata.

## Tahapan Proses Implementasi

### 1. Persiapan Lingkungan dan Dataset
- Pastikan library yang dibutuhkan sudah terinstal.
- Unduh dataset dari Kaggle melalui link di atas.
- Dataset akan dibagi menjadi data train dan data test. Terapkan transformasi pada gambar, seperti mengubah ukuran gambar menjadi dimensi yang seragam dan melakukan normalisasi untuk meningkatkan stabilitas pelatihan.

### 2. Eksplorasi Dataset
- Identifikasi kelas dalam dataset (contoh: bangunan, laut, jalan, dll.).
- Lakukan visualisasi beberapa contoh gambar dari dataset untuk memahami variasi data pada tiap kelas.

### 3. Definisi Model CNN
- Bangun arsitektur CNN sederhana dengan minimal dua lapisan konvolusi.
- Gunakan fungsi aktivasi (contoh: ReLU) untuk memperkenalkan non-linearitas.
- Tambahkan lapisan pooling untuk mengurangi dimensi data.
- Tambahkan satu atau lebih lapisan *fully connected* untuk klasifikasi.

### 4. Pelatihan Model
- Tentukan fungsi loss (contoh: CrossEntropyLoss) untuk mengukur kesalahan prediksi model.
- Pilih optimizer (contoh: SGD atau Adam) untuk memperbarui bobot model selama pelatihan.
- Latih model menggunakan dataset pelatihan selama beberapa epoch, dan catat nilai loss untuk memantau kinerja model.

### 5. Evaluasi Model
- Uji model pada data test untuk menghitung akurasi prediksi secara keseluruhan.
- Hitung akurasi untuk masing-masing kelas untuk mengidentifikasi kelas yang sulit diklasifikasikan oleh model.

### 6. Analisis dan Penyempurnaan
- Jika akurasi model masih rendah, pertimbangkan untuk:
  - Menambahkan lebih banyak lapisan pada model.
  - Menggunakan augmentasi data untuk memperbesar variasi dalam dataset.
  - Meningkatkan jumlah epoch pelatihan.
  - Menggunakan parameter optimizer yang berbeda.

---

## Output yang Diharapkan
1. Visualisasi beberapa contoh gambar dari dataset dan identifikasi semua kelas yang ada.  
2. Jelaskan arsitektur model CNN yang telah dibuat dengan rincian jumlah lapisan konvolusi, pooling, dan fully connected.  
3. Nilai loss selama proses pelatihan untuk setiap epoch dan grafik loss jika memungkinkan.  
4. Akurasi keseluruhan model pada data train serta akurasi untuk masing-masing kelas dalam dataset.
5. Analisis performa model pada kelas dengan akurasi rendah beserta rekomendasi perbaikan untuk meningkatkan performa model.
---
