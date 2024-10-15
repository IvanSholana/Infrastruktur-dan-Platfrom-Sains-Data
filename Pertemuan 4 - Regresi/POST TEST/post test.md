
---

# Deskripsi Kasus untuk Masalah Regresi

**Tujuan**:  
Tujuan dari analisis ini adalah memprediksi gaji karyawan berdasarkan jumlah tahun pengalaman kerja (`Years of Experience`) menggunakan metode regresi. Model regresi ini akan dibangun untuk memprediksi nilai gaji (`Salary`) sebagai variabel target (`target variable`), dengan fitur berupa jumlah tahun pengalaman kerja. Metrik evaluasi utama yang akan digunakan adalah $R^2$ (R-squared), yang mengukur seberapa baik model regresi dapat menjelaskan variasi pada data target.

---

## Ringkasan Dataset

- **Variabel Target (Dependent Variable)**: Gaji (`Salary`)
- **Fitur Prediktor (Independent Variable)**: Jumlah Tahun Pengalaman Kerja (`Years of Experience`)

Dataset ini memiliki total 30 observasi dan dua variabel numerik yang relevan: 
- `Years of Experience`: Merupakan jumlah pengalaman kerja karyawan dalam tahun.
- `Salary`: Gaji tahunan yang diperoleh karyawan, dalam satuan mata uang yang ditentukan.

Dataset ini bersifat sederhana namun ideal untuk membangun model regresi linier karena adanya hubungan kontinu antara fitur prediktor dan variabel target.

---

## Tahapan Analisis Berdasarkan Siklus Hidup Data Science

Proses analisis data ini akan mengikuti tahapan dalam **Data Science Life Cycle**, yang meliputi beberapa langkah berikut:

### 1. Pemahaman Masalah (Problem Understanding)
   - **Pertanyaan Kunci**: Bagaimana kita dapat memprediksi gaji karyawan berdasarkan jumlah tahun pengalaman kerja mereka?
   - **Metrik Utama**: Metrik yang digunakan untuk mengevaluasi model adalah $R^2$, Mean Squared Error (MSE), dan Root Mean Squared Error (RMSE).

### 2. Pengumpulan Data (Data Collection)
   - Dataset ini telah disediakan dalam file CSV, dengan informasi tentang pengalaman kerja dan gaji karyawan. 

### 3. Eksplorasi Data (Data Exploration)
   - Memeriksa distribusi variabel (`Years of Experience` dan `Salary`).
   - Menghitung statistik deskriptif (mean, median, standar deviasi) untuk memahami karakteristik data.
   - Visualisasi hubungan antara pengalaman kerja dan gaji menggunakan scatter plot.

### 4. Persiapan Data (Data Preparation)
   - Memeriksa apakah ada data hilang (`missing values`) atau outlier.
   - Normalisasi atau standarisasi jika diperlukan.
   - Pembagian data menjadi `training set` dan `test set` untuk membangun model dan mengukur performanya pada data yang tidak terlihat.

### 5. Pemodelan (Modeling)
   - Membangun model regresi linier sederhana (`Simple Linear Regression`).
   - Melatih model pada `training set`.
   - Memprediksi nilai gaji pada `test set`.

### 6. Evaluasi Model (Model Evaluation)
   - Mengukur kinerja model menggunakan $R^2$ untuk melihat seberapa baik model dapat menjelaskan variabilitas target.
   - Menghitung MSE dan RMSE untuk menilai kesalahan prediksi.


---

## Output yang Diharapkan
- Model regresi dengan evaluasi metrik $R^2$, MSE, dan RMSE.
- Visualisasi hubungan antara prediksi gaji dan pengalaman kerja.
- Interpretasi hasil dan kesimpulan dari model.

