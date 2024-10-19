# Deskripsi Kasus untuk Masalah Klasifikasi

**Tujuan** :  
Tujuan dari analisis ini adalah memprediksi status persetujuan pinjaman (disetujui atau ditolak) berdasarkan faktor-faktor tertentu seperti pendapatan pemohon, jumlah pinjaman, sejarah kredit, dan lainnya. Model klasifikasi ini akan dibangun untuk memprediksi apakah pinjaman akan disetujui atau ditolak sebagai variabel target (dependent variable), dengan beberapa fitur sebagai variabel prediktor (independent variables). Metrik evaluasi utama yang akan digunakan adalah **akurasi**, **precision**, **recall**, dan **F1-score**. Lalu **Bandingkan Hasil Evaluasi dari 3 model yang sudah dipelajari (KNN, Naive Bayes, & SVM)**.

---

## Ringkasan Dataset

- **Variabel Target (Dependent Variable)**: Status Pinjaman (`Loan_Status`)
- **Fitur Prediktor (Independent Variables)**: 
  - `Gender`: Jenis kelamin pemohon (Laki-laki/Perempuan).
  - `Married`: Status pernikahan pemohon (Ya/Tidak).
  - `Dependents`: Jumlah tanggungan.
  - `Education`: Pendidikan pemohon (Lulusan/Sarjana).
  - `Self_Employed`: Apakah pemohon wiraswasta (Ya/Tidak).
  - `ApplicantIncome`: Pendapatan pemohon.
  - `CoapplicantIncome`: Pendapatan co-applicant.
  - `LoanAmount`: Jumlah pinjaman yang diminta.
  - `Loan_Amount_Term`: Jangka waktu pinjaman.
  - `Credit_History`: Riwayat kredit (Baik/Buruk).
  - `Property_Area`: Area properti (Perkotaan, Semi-urban, Pedesaan).

Dataset ini berisi data aplikasi pinjaman dari bank, dengan beberapa variabel kategorikal dan numerik yang relevan untuk memprediksi apakah pinjaman akan disetujui atau tidak.

---

## Tahapan Analisis Berdasarkan Siklus Hidup Data Science

Proses analisis data ini akan mengikuti tahapan dalam **Data Science Life Cycle**, yang meliputi beberapa langkah berikut:

### 1. Pemahaman Masalah (Problem Understanding)
   - **Pertanyaan Kunci**: Bagaimana kita dapat memprediksi apakah pinjaman seseorang akan disetujui berdasarkan karakteristik pemohon dan pinjaman yang diajukan?
   - **Metrik Utama**: Akurasi, Precision, Recall, dan F1-score.

### 2. Pengumpulan Data (Data Collection)
   - Dataset telah disediakan dalam file CSV yang berisi informasi tentang karakteristik pemohon pinjaman, riwayat kredit, dan status persetujuan pinjaman.

### 3. Eksplorasi Data (Data Exploration)
   - Memeriksa distribusi variabel numerik (`ApplicantIncome`, `LoanAmount`, dll.) dan kategorikal (`Gender`, `Married`, dll.).
   - Menghitung statistik deskriptif untuk memahami karakteristik data.
   - Visualisasi distribusi status pinjaman dan hubungan antara variabel prediktor dengan status pinjaman.

### 4. Persiapan Data (Data Preparation)
   - Menangani data yang hilang (`missing values`) dan melakukan pengkodean (encoding) variabel kategorikal.
   - Normalisasi atau standarisasi variabel numerik jika diperlukan.
   - Pembagian data menjadi `training set` dan `test set` untuk membangun model dan mengevaluasi performanya pada data yang tidak terlihat.

### 5. Pemodelan (Modeling)
   - Membangun model klasifikasi seperti Logistic Regression, Decision Tree, atau Random Forest.
   - Melatih model pada `training set`.
   - Memprediksi status pinjaman pada `test set`.

### 6. Evaluasi Model (Model Evaluation)
   - Mengukur performa model menggunakan akurasi, precision, recall, dan F1-score.
   - Membuat confusion matrix untuk mengevaluasi hasil prediksi.


---

## Output yang Diharapkan
- Model klasifikasi dengan evaluasi metrik akurasi, precision, recall, dan F1-score.
- Visualisasi confusion matrix dan hubungan antara variabel prediktor dengan status pinjaman.
- Interpretasi hasil dan kesimpulan dari model.


