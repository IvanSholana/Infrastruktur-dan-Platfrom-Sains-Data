### **Konteks Kasus: Penjualan Produk Elektronik**

#### **Deskripsi Kasus**:
Anda adalah seorang analis data yang bekerja di sebuah perusahaan retail yang menjual produk elektronik. Anda diminta untuk menganalisis data penjualan dan mendeteksi apakah ada anomali (outlier) dalam penjualan, harga produk, atau pemberian diskon yang tidak wajar. Data berisi beberapa fitur, yaitu:
- **Harga Produk**: Harga jual produk elektronik.
- **Penjualan Harian**: Jumlah produk yang terjual dalam sehari.
- **Diskon (%)**: Diskon yang diberikan untuk produk tersebut (dalam persen).
- **Stok**: Jumlah stok produk yang tersedia di gudang.

Tujuan analisis ini adalah mendeteksi apakah ada nilai yang tidak wajar atau anomali dalam harga, penjualan harian, diskon, atau stok.

### **Soal Post-Test Praktikum: Analisis Penjualan Produk Elektronik**

#### **Konteks Kasus:**
Anda diminta untuk menganalisis data penjualan produk elektronik untuk mendeteksi adanya **outlier** dalam harga, penjualan harian, diskon, dan stok produk. Outlier ini bisa menunjukkan anomali seperti harga yang tidak realistis, diskon terlalu besar, atau lonjakan penjualan.

---

### **Soal dan Pertanyaan:**

#### **1. Visualisasi Data:**
   - Buatlah **box plot** dan **scatter plot** untuk memvisualisasikan data penjualan produk dan identifikasi outlier secara visual untuk setiap fitur: **Harga Produk (USD)**, **Penjualan Harian (Unit)**, **Diskon (%)**, dan **Stok (Unit)**.
   
   **Pertanyaan:**
   1. Berdasarkan **box plot**, titik-titik data mana saja yang tampak sebagai outlier untuk setiap fitur?
   2. Pada **scatter plot**, apakah ada titik-titik yang tampak jauh dari mayoritas data? Fitur mana yang menunjukkan outlier paling signifikan?
   3. Apakah menurut Anda outlier ini memengaruhi persepsi umum tentang distribusi data?

---

#### **2. Deteksi Outlier Menggunakan Statistik:**

   **a. Menggunakan Z-Score**:
   - Hitung Z-Score untuk setiap fitur. Identifikasi nilai yang dianggap sebagai outlier (Z-Score lebih dari 3 atau kurang dari -3).
   
   **Pertanyaan:**
   1. Berapa jumlah outlier yang terdeteksi di setiap fitur berdasarkan Z-Score?
   2. Apakah outlier yang terdeteksi melalui Z-Score sesuai dengan hasil dari visualisasi?

   **b. Menggunakan IQR**:
   - Hitung **Interquartile Range (IQR)** untuk setiap fitur dan identifikasi outlier berdasarkan IQR.
   
   **Pertanyaan:**
   1. Berapa nilai **Q1**, **Q3**, dan **IQR** untuk setiap fitur?
   2. Setelah menghitung IQR, berapa jumlah outlier yang terdeteksi di setiap fitur? Apakah hasil ini berbeda dengan hasil dari Z-Score?

---

#### **3. Transformasi Data:**

   **a. Log Transformation**:
   - Terapkan **log transformation** pada fitur yang memiliki outlier, seperti **Harga Produk** atau **Penjualan Harian**, dan buat **box plot** untuk memvisualisasikan hasilnya.
   
   **Pertanyaan:**
   1. Apakah log transformation berhasil mengurangi pengaruh outlier? Apakah outlier masih terlihat pada box plot setelah transformasi?
   2. Bagaimana dampak log transformation terhadap fitur yang memiliki outlier?

#### **4. Kesimpulan:**
   - Berdasarkan hasil visualisasi dan statistik, apakah transformasi data berhasil mengurangi pengaruh outlier? Jelaskan apakah outlier masih tetap ada dan bagaimana pengaruhnya terhadap distribusi data setelah transformasi.

   **Pertanyaan:**
   1. Apakah outlier masih tetap ada setelah dilakukan transformasi data? Jika ya, apakah pengaruhnya berkurang?
   2. Apakah transformasi data membuat distribusi data lebih sesuai dengan asumsi normalitas?
   3. Menurut Anda, apakah transformasi data merupakan solusi terbaik untuk menangani outlier dalam kasus ini?

---

### **Catatan:**
- Gunakan **Python (pandas, numpy, matplotlib, seaborn)** untuk menyelesaikan soal di atas.
- Jelaskan setiap langkah yang dilakukan dan sertakan penjelasan atas hasil yang diperoleh dari setiap metode yang digunakan.