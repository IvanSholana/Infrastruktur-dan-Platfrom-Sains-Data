dataset:
[Salary_dataset.csv](https://github.com/user-attachments/files/17378982/Salary_dataset.csv)[Uploading Salary_dataset.csv…,YearsExperience,Salary
0,1.2000000000000002,39344.0
1,1.4000000000000001,46206.0
2,1.6,37732.0
3,2.1,43526.0
4,2.3000000000000003,39892.0
5,3.0,56643.0
6,3.1,60151.0
7,3.3000000000000003,54446.0
8,3.3000000000000003,64446.0
9,3.8000000000000003,57190.0
10,4.0,63219.0
11,4.1,55795.0
12,4.1,56958.0
13,4.199999999999999,57082.0
14,4.6,61112.0
15,5.0,67939.0
16,5.199999999999999,66030.0
17,5.3999999999999995,83089.0
18,6.0,81364.0
19,6.1,93941.0
20,6.8999999999999995,91739.0
21,7.199999999999999,98274.0
22,8.0,101303.0
23,8.299999999999999,113813.0
24,8.799999999999999,109432.0
25,9.1,105583.0
26,9.6,116970.0
27,9.7,112636.0
28,10.4,122392.0
29,10.6,121873.0
]()
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

