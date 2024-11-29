**Soal Klasifikasi Menggunakan PySpark**

Anda diberikan dataset cuaca yang tersimpan dalam file **`weather_forecast_data.csv`**. Dataset ini berisi data historis cuaca dengan beberapa fitur dan label target. Tugas Anda adalah membangun model klasifikasi untuk memprediksi kondisi cuaca berdasarkan data yang diberikan. Berikut langkah-langkahnya:

### Tujuan:
Buat model klasifikasi untuk memprediksi apakah kondisi cuaca akan **"Hujan"** atau **"Tidak Hujan"** (kolom target label `Rain` dengan nilai 1 untuk hujan, 0 untuk tidak hujan).

### Instruksi:
1. **Import Dataset**:
   - Gunakan PySpark untuk membaca file CSV ini ke dalam DataFrame.
   - Tampilkan 5 baris pertama dataset untuk memahami strukturnya.

2. **Eksplorasi Data**:
   - Tampilkan tipe data dan informasi tentang kolom dataset.
   - Lakukan eksplorasi statistik dasar (mean, median, dll.) untuk memahami fitur.

3. **Data Preprocessing**:
   - Periksa apakah terdapat nilai kosong atau null, dan tangani sesuai kebutuhan.
   - Encode kolom kategorikal (jika ada) ke bentuk numerik menggunakan `StringIndexer`.
   - Normalisasi data numerik agar lebih seimbang dalam pelatihan model.

4. **Pembagian Dataset**:
   - Bagi dataset menjadi data latih (80%) dan data uji (20%).

5. **Pemodelan**:
   - Gunakan algoritma **Logistic Regression** di PySpark untuk membangun model klasifikasi.
   - Pastikan pipeline PySpark digunakan untuk preprocessing dan pelatihan model.

6. **Evaluasi Model**:
   - Gunakan data uji untuk mengevaluasi model.
   - Tampilkan metrik evaluasi seperti:
     - Accuracy
     - Precision
     - Recall
     - F1 Score

7. **Prediksi**:
   - Gunakan model yang telah dilatih untuk memprediksi data uji.
   - Tampilkan 10 prediksi pertama dari data uji, dengan kolom berikut:
     - Fitur
     - Prediksi
     - Label Sebenarnya (Ground Truth)

**Catatan Penting**:
- Sertakan komentar di setiap langkah kode untuk menjelaskan proses yang dilakukan.
- Pastikan hasil output dari setiap langkah ditampilkan.

**Deliverable**:
- File Jupyter Notebook (.ipynb) atau Python script (.py) yang menyelesaikan tugas di atas. 

Silakan mulai mengerjakan tugas dengan menggunakan PySpark! Jika Anda membutuhkan bantuan untuk memulai atau memiliki pertanyaan, beri tahu saya!