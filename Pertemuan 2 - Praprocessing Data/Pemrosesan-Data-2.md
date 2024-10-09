### **Exploratory Data Analysis (EDA): Pengecekan Outlier secara Detail**

#### **Apa itu Outlier?**

Outlier adalah titik data yang menyimpang secara signifikan dari mayoritas data lain dalam suatu dataset. Biasanya, outlier ini terlihat sebagai nilai yang sangat tinggi atau sangat rendah dibandingkan dengan nilai-nilai lainnya. Outlier dapat disebabkan oleh beberapa faktor yang mendasarinya, di antaranya:

1. **Variasi Alami**: Dalam banyak kasus, outlier muncul karena variasi alami dalam data. Misalnya, pada populasi manusia, tinggi badan berkisar dari yang sangat pendek hingga sangat tinggi, dan nilai-nilai ekstrem ini bisa muncul sebagai outlier, meskipun mereka benar-benar mencerminkan variasi yang normal.
2. **Kesalahan Pengukuran**: Kesalahan teknis dalam proses pengumpulan data bisa menyebabkan outlier. Contohnya, sensor yang tidak berfungsi dengan baik dapat mencatat suhu yang sangat rendah di lingkungan yang seharusnya panas.
3. **Kesalahan Input**: Kesalahan manusia seperti salah ketik saat memasukkan data dapat menghasilkan nilai yang sangat besar atau kecil, sehingga nilai tersebut terlihat sebagai outlier dalam dataset.

#### **Mengapa Pengecekan Outlier Penting?**

Pentingnya mendeteksi dan menangani outlier sangat bervariasi tergantung pada tujuan analisis. Namun, berikut adalah tiga alasan utama mengapa kita harus memperhatikan outlier:

1. **Pengaruh pada Statistik Deskriptif**:
   - **Rata-rata dan deviasi standar**: Rata-rata dan deviasi standar adalah dua ukuran statistik yang sangat dipengaruhi oleh outlier. Misalnya, jika sebagian besar data berkisar antara 10 hingga 20, tetapi terdapat satu nilai 100, rata-rata keseluruhan bisa meningkat secara tidak proporsional. Deviasi standar juga akan meningkat karena adanya perbedaan besar antara outlier dengan nilai lainnya.
   - **Distribusi Data**: Outlier dapat mengubah pemahaman kita tentang distribusi data. Misalnya, distribusi yang seharusnya simetris bisa terlihat sangat miring (skewed) jika ada satu atau dua outlier.
2. **Pengaruh pada Modeling**:
   - **Overfitting**: Dalam pembelajaran mesin, outlier bisa membuat model terlalu fokus pada beberapa titik data yang menyimpang, menyebabkan **overfitting**, yaitu kondisi di mana model bekerja sangat baik pada data pelatihan, tetapi buruk pada data baru.
   - **Underfitting**: Di sisi lain, model mungkin juga mengabaikan outlier atau tidak dapat menangani data dengan outlier, yang bisa menyebabkan **underfitting**, di mana model terlalu sederhana dan tidak mampu menangkap pola penting dalam data.
   - **Estimasi Parameter**: Banyak algoritma pembelajaran mesin (seperti regresi linier) bergantung pada estimasi parameter seperti rata-rata dan varians. Jika outlier ada, parameter ini bisa salah dan menghasilkan model yang tidak akurat.
3. **Keputusan Bisnis dan Kebijakan**:
   - **Deteksi Anomali**: Dalam beberapa situasi, outlier dapat menjadi sinyal adanya anomali penting yang perlu dianalisis lebih lanjut. Misalnya, dalam data transaksi keuangan, outlier bisa menandakan aktivitas penipuan yang perlu diselidiki.
   - **Pengambilan Keputusan yang Tepat**: Jika outlier dibiarkan tanpa analisis, keputusan yang diambil berdasarkan data tersebut bisa keliru. Misalnya, lonjakan penjualan yang tidak biasa mungkin memerlukan tindakan cepat untuk menyesuaikan inventaris atau strategi pemasaran.

#### **Tahapan Pengecekan Outlier Secara Detail**

Berikut adalah langkah-langkah mendetail yang biasanya digunakan dalam mendeteksi outlier:

1. **Visualisasi Data**:

   Visualisasi adalah salah satu cara paling intuitif untuk mendeteksi outlier. Dengan bantuan grafik, kita bisa dengan cepat melihat pola yang tidak biasa. Berikut adalah beberapa teknik visualisasi yang umum digunakan:

   - **Box Plot (Plot Kotak)**: Box plot membagi data menjadi kuartil, dengan garis di tengah yang menunjukkan median. Outlier terlihat jelas sebagai titik-titik yang berada jauh di luar whiskers (ekstensi vertikal atau horizontal pada box plot). Whiskers biasanya menunjukkan 1,5 kali IQR (interquartile range), dan nilai di luar jangkauan ini dianggap sebagai outlier.
   - **Scatter Plot (Plot Sebar)**: Scatter plot menampilkan hubungan antara dua variabel. Outlier dalam scatter plot terlihat sebagai titik yang jauh dari sekumpulan titik lainnya. Dalam scatter plot, kita juga bisa melihat apakah ada hubungan antara variabel dan bagaimana outlier memengaruhi hubungan tersebut.
   - **Histogram**: Histogram menunjukkan distribusi data. Dalam histogram, outlier terlihat sebagai batang yang sangat jauh dari batang lainnya. Histogram sangat berguna untuk melihat distribusi umum dari variabel tunggal dan mengidentifikasi outlier yang berada di luar rentang distribusi normal.

   **Contoh kode Python untuk membuat visualisasi**:

   ```python
   import pandas as pd
   import matplotlib.pyplot as plt
   import seaborn as sns

   # Membuat data contoh
   data = {'nilai': [10, 12, 12, 13, 13, 14, 15, 16, 17, 20, 100]}  # 100 adalah outlier
   df = pd.DataFrame(data)

   # Box Plot
   plt.figure(figsize=(10, 5))
   sns.boxplot(x=df['nilai'])
   plt.title('Box Plot')
   plt.show()

   # Scatter Plot
   plt.figure(figsize=(10, 5))
   plt.scatter(range(len(df)), df['nilai'], color='blue')
   plt.title('Scatter Plot')
   plt.xlabel('Index')
   plt.ylabel('Nilai')
   plt.axhline(y=30, color='red', linestyle='--')  # Menandakan batas atas
   plt.show()

   # Histogram
   plt.figure(figsize=(10, 5))
   plt.hist(df['nilai'], bins=10, color='green', alpha=0.7)
   plt.title('Histogram')
   plt.xlabel('Nilai')
   plt.ylabel('Frekuensi')
   plt.show()
   ```

2. **Statistik Deskriptif untuk Mendeteksi Outlier**:

   Selain visualisasi, statistik deskriptif juga dapat membantu mendeteksi outlier. Berikut adalah dua metode yang umum digunakan:

   - **Z-Score**: Z-Score mengukur seberapa jauh sebuah titik data dari rata-rata dalam satuan deviasi standar. Z-Score dihitung sebagai:
     \[
     Z = \frac{(X - \mu)}{\sigma}
     \]
     Di mana:

     - \(X\) adalah nilai data,
     - \( \mu \) adalah rata-rata, dan
     - \( \sigma \) adalah deviasi standar.

     Data yang memiliki Z-Score lebih besar dari 3 atau kurang dari -3 biasanya dianggap sebagai outlier.

   - **Interquartile Range (IQR)**: IQR mengukur rentang antara kuartil pertama (Q1) dan kuartil ketiga (Q3). Nilai-nilai yang berada di luar \( [Q1 - 1.5 \times IQR, Q3 + 1.5 \times IQR] \) dianggap sebagai outlier.

   **Contoh kode Python untuk menghitung Z-Score dan IQR**:

   ```python
   from scipy import stats

   # Menghitung Z-Score
   df['z_score'] = stats.zscore(df['nilai'])
   print("Outlier berdasarkan Z-Score:")
   print(df[df['z_score'].abs() > 3])  # Menampilkan outlier berdasarkan Z-Score

   # Menghitung IQR
   Q1 = df['nilai'].quantile(0.25)
   Q3 = df['nilai'].quantile(0.75)
   IQR = Q3 - Q1

   lower_bound = Q1 - 1.5 * IQR
   upper_bound = Q3 + 1.5 * IQR

   outliers_iqr = df[(df['nilai'] < lower_bound) | (df['nilai'] > upper_bound)]
   print("Outlier berdasarkan IQR:")
   print(outliers_iqr)  # Menampilkan outlier berdasarkan IQR
   ```

3. **Penanganan Outlier**:

   Setelah mendeteksi outlier, langkah selanjutnya adalah memutuskan bagaimana menanganinya. Ada beberapa cara untuk menangani outlier, tergantung pada konteks dan tujuan analisis:

   - **Analisis Penyebab**: Sebelum memutuskan apa yang harus dilakukan terhadap outlier, penting untuk memahami asal usulnya. Jika outlier disebabkan oleh kesalahan input atau pengukuran, mungkin bijaksana untuk menghapus atau memperbaikinya.

   - **Transformasi Data**: Dalam beberapa kasus, transformasi data dapat mengurangi dampak outlier. Transformasi umum yang digunakan adalah:

     - **Log Transformation**: Digunakan untuk mengurangi skala data dan mengurangi efek outlier yang besar.
     - **Square Root Transformation**: Transformasi ini membantu mengurangi pengaruh outlier yang tidak terlalu ekstrim dibandingkan dengan transformasi log.

   - **Penggunaan Model yang Tahan terhadap Outlier**: Beberapa algoritma pembelajaran mesin lebih tahan terhadap outlier, seperti pohon keputusan, random forest, dan robust regression. Algoritma ini tidak bergantung pada asumsi distribusi data yang ketat, sehingga dampak outlier lebih kecil.

   **Contoh kode Python untuk transformasi data**

:

```python
import numpy as np

# Transformasi menggunakan log
df['nilai_log'] = np.log1p(df['nilai'])  # log1p untuk menangani nilai nol
plt.figure(figsize=(10, 5))
sns.boxplot(x=df['nilai_log'])
plt.title('Box Plot setelah Transformasi Log')
plt.show()
```

#### **Kesimpulan**

Pengecekan dan penanganan outlier merupakan langkah penting dalam Exploratory Data Analysis (EDA). Outlier dapat memengaruhi statistik deskriptif, mengubah distribusi data, serta mempengaruhi performa model pembelajaran mesin. Oleh karena itu, dengan menggunakan teknik visualisasi dan metode statistik seperti Z-Score dan IQR, kita dapat mengidentifikasi outlier dengan lebih efektif. Setelah terdeteksi, outlier dapat dianalisis lebih lanjut untuk menentukan apakah perlu dihapus, diubah, atau ditangani melalui penggunaan model yang lebih tahan terhadap outlier.
