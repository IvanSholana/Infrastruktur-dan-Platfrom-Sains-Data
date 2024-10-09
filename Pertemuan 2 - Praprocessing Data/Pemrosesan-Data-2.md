### **Apa itu Outlier?**

Outlier adalah titik data yang menyimpang secara signifikan dari mayoritas data lain dalam suatu dataset. Nilai outlier dapat sangat tinggi atau sangat rendah dibandingkan dengan nilai-nilai lainnya. Outlier sering kali muncul akibat beberapa faktor berikut:

1. **Variasi Alami**: Dalam beberapa kasus, outlier mungkin muncul karena variasi alami dalam data. Misalnya, dalam pengukuran tinggi badan manusia, terdapat kemungkinan untuk melihat nilai yang sangat tinggi atau sangat rendah.
   
2. **Kesalahan Pengukuran**: Data outlier bisa muncul karena kesalahan dalam pengumpulan data, seperti kerusakan pada sensor atau alat pengukur.

3. **Kesalahan Input**: Salah ketik atau kesalahan manusia dalam memasukkan data juga bisa menyebabkan outlier. Contohnya, jika seseorang secara tidak sengaja menambahkan nol ekstra saat memasukkan data transaksi, maka angka tersebut akan menjadi outlier.

4. **Peristiwa Langka**: Outlier dapat mewakili peristiwa yang jarang terjadi atau fenomena unik yang tidak teramati dalam kondisi normal. Misalnya, lonjakan penjualan yang tidak biasa selama acara promosi besar atau penipuan keuangan.

---

### **Mengapa Outlier Perlu Diperhatikan?**

Mendeteksi dan menangani outlier adalah langkah penting dalam EDA karena:

1. **Pengaruh pada Statistik Deskriptif**:
   - **Rata-rata (Mean)** dan **Deviasi Standar** sangat dipengaruhi oleh outlier. Jika satu nilai outlier sangat jauh dari data lainnya, rata-rata dapat meningkat atau menurun secara tidak proporsional. Deviasi standar yang menghitung penyebaran data juga akan terdistorsi.
   - **Distribusi Data**: Kehadiran outlier dapat mengubah distribusi data, membuat distribusi yang seharusnya simetris menjadi miring (skewed).

2. **Pengaruh pada Model Pembelajaran Mesin**:
   - **Overfitting**: Model dapat menjadi terlalu fokus pada outlier, yang dapat menyebabkan overfitting—model bekerja sangat baik pada data pelatihan, tetapi buruk pada data uji.
   - **Underfitting**: Beberapa model mungkin tidak mampu menangkap pola yang baik karena terpengaruh oleh outlier.
   - **Estimasi Parameter**: Dalam beberapa model pembelajaran mesin seperti regresi linier, kehadiran outlier dapat mengganggu estimasi parameter, yang dapat menghasilkan model yang tidak akurat.

3. **Keputusan Bisnis**:
   - **Deteksi Anomali**: Dalam beberapa kasus, outlier dapat menjadi sinyal penting, seperti adanya penipuan atau masalah operasional yang perlu diselidiki lebih lanjut.
   - **Keputusan Berdasarkan Data**: Tanpa memahami outlier, keputusan yang didasarkan pada data yang terdistorsi dapat menghasilkan kebijakan yang salah.

---

### **Tahapan Pengecekan Outlier Secara Detail**

Untuk mendeteksi dan memahami outlier, ada beberapa tahapan yang bisa diikuti:

#### **1. Visualisasi Data untuk Mendeteksi Outlier**

Visualisasi data merupakan salah satu cara paling efektif untuk mendeteksi outlier secara langsung. Beberapa teknik visualisasi yang umum digunakan untuk mendeteksi outlier meliputi:

##### **a. Box Plot (Plot Kotak)**

Box plot adalah visualisasi yang menggunakan kuartil untuk membagi data menjadi beberapa bagian dan menunjukkan sebaran data. Box plot juga menampilkan nilai-nilai outlier sebagai titik yang terletak di luar **whiskers**, yang biasanya menunjukkan 1,5 kali **Interquartile Range (IQR)** dari kuartil pertama (Q1) dan kuartil ketiga (Q3).

Contoh kode Python:

```python
import seaborn as sns
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 5))
sns.boxplot(x=df['nilai'])
plt.title('Box Plot')
plt.show()
```

Outlier dalam box plot akan terlihat sebagai titik yang jauh di luar batas whiskers.

##### **b. Scatter Plot (Plot Sebar)**

Scatter plot sangat berguna untuk mendeteksi outlier ketika melihat hubungan antara dua variabel. Titik-titik data yang jauh dari pola hubungan yang jelas antara variabel dapat dianggap sebagai outlier.

Contoh kode Python:

```python
plt.figure(figsize=(10, 5))
plt.scatter(range(len(df)), df['nilai'], color='blue')
plt.axhline(y=30, color='red', linestyle='--')  # Batas atas
plt.title('Scatter Plot')
plt.xlabel('Index')
plt.ylabel('Nilai')
plt.show()
```

Outlier akan muncul sebagai titik yang jauh dari sekumpulan titik lainnya.

##### **c. Histogram**

Histogram menunjukkan distribusi frekuensi data. Outlier terlihat sebagai batang (bar) yang berada jauh dari batang lain pada histogram, biasanya di ujung distribusi.

Contoh kode Python:

```python
plt.figure(figsize=(10, 5))
plt.hist(df['nilai'], bins=10, color='green', alpha=0.7)
plt.title('Histogram')
plt.xlabel('Nilai')
plt.ylabel('Frekuensi')
plt.show()
```

Histogram sangat berguna untuk melihat distribusi data yang luas dan memberikan petunjuk jika ada nilai yang jauh di luar rentang umum.

##### **d. Density Plot (Plot Densitas)**

Density plot adalah versi smooth dari histogram dan sangat berguna untuk melihat distribusi probabilitas. Outlier akan terlihat sebagai ekor distribusi yang panjang atau titik yang berada di daerah densitas yang sangat rendah.

Contoh kode Python:

```python
sns.kdeplot(df['nilai'], shade=True)
plt.title('Density Plot')
plt.show()
```

---

#### **2. Statistik Deskriptif untuk Mendeteksi Outlier**

Selain visualisasi, statistik deskriptif sering kali digunakan untuk mendeteksi outlier. Metode statistik yang paling umum digunakan meliputi:

##### **a. Z-Score**

**Z-Score** mengukur seberapa jauh nilai data dari rata-rata dalam satuan deviasi standar. Z-Score dihitung menggunakan rumus berikut:

\[
Z = \frac{(X - \mu)}{\sigma}
\]

Di mana:
- \( X \) adalah nilai data,
- \( \mu \) adalah rata-rata populasi, dan
- \( \sigma \) adalah deviasi standar populasi.

Data dengan Z-Score lebih dari 3 atau kurang dari -3 biasanya dianggap sebagai outlier.

Contoh kode Python:

```python
from scipy import stats

df['z_score'] = stats.zscore(df['nilai'])
outliers_zscore = df[df['z_score'].abs() > 3]
print(outliers_zscore)
```

##### **b. Interquartile Range (IQR)**

**Interquartile Range (IQR)** adalah ukuran penyebaran statistik yang dihitung dengan mengurangi kuartil pertama dari kuartil ketiga:

\[
IQR = Q3 - Q1
\]

Nilai di luar \( [Q1 - 1.5 \times IQR, Q3 + 1.5 \times IQR] \) dianggap sebagai outlier.

Contoh kode Python:

```python
Q1 = df['nilai'].quantile(0.25)
Q3 = df['nilai'].quantile(0.75)
IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR

outliers_iqr = df[(df['nilai'] < lower_bound) | (df['nilai'] > upper_bound)]
print(outliers_iqr)
```

##### **c. Modified Z-Score**

Modified Z-Score adalah variasi dari Z-Score yang lebih tahan terhadap outlier. Metode ini menggunakan **median** dan **Median Absolute Deviation (MAD)**, yang lebih robust dibandingkan rata-rata dan deviasi standar.

Rumus Modified Z-Score adalah:

\[
Z_{mod} = \frac{0.6745 \times (X - \text{Median})}{MAD}
\]

Data dengan Modified Z-Score lebih dari 3.5 biasanya dianggap sebagai outlier.

Contoh kode Python:

```python
def modified_z_score(data):
    median = np.median(data)
    mad = np.median(np.abs(data - median))
    return 0.6745 * (data - median) / mad

df['modified_z_score'] = modified_z_score(df['nilai'])
outliers_modified_z = df[df['modified_z_score'].abs() > 3.5]
print(outliers_modified_z)
```

---

### **3. Penanganan Outlier**

Setelah mendeteksi outlier, langkah selanjutnya adalah memutuskan bagaimana menanganinya. Ada beberapa strategi untuk menangani outlier, bergantung pada tujuan analisis.

#### **a. Menghapus Outlier**

Penghapusan outlier bisa menjadi pilihan jika data tersebut disebabkan oleh kesalahan input atau pengukuran, dan tidak relevan untuk analisis. Namun, penghapusan harus dilakukan dengan hati-hati agar tidak menghilangkan data yang valid dan penting.

#### **b. Imputasi Outlier**

Alih-alih menghapus outlier, kita bisa mengimputasi atau mengganti outlier dengan nilai yang lebih sesuai berdasarkan distribusi data.

- **Winsorizing**: Mengganti outlier dengan nilai batas atas atau

 bawah yang lebih masuk akal.

  Contoh kode Python:

  ```python
  from scipy.stats.mstats import winsorize
  df['nilai_winsorized'] = winsorize(df['nilai'], limits=[0.05, 0.05])
  ```

- **Imputasi Median**: Mengganti outlier dengan nilai median.

  Contoh kode Python:

  ```python
  median = df['nilai'].median()
  df.loc[df['nilai'] > upper_bound, 'nilai'] = median
  df.loc[df['nilai'] < lower_bound, 'nilai'] = median
  ```

#### **c. Transformasi Data**

Jika outlier muncul karena skala data yang besar, transformasi data bisa digunakan untuk mengurangi pengaruh outlier.

- **Log Transformation**: Digunakan untuk mengurangi rentang nilai outlier yang sangat besar.

  Contoh kode Python:

  ```python
  df['nilai_log'] = np.log1p(df['nilai'])
  ```

- **Reciprocal Transformation**: Mengambil kebalikan dari nilai outlier.

  Contoh kode Python:

  ```python
  df['nilai_reciprocal'] = 1 / df['nilai']
  ```

- **Clipping**: Memotong nilai outlier agar berada dalam rentang tertentu.

  Contoh kode Python:

  ```python
  df['nilai_clipped'] = np.clip(df['nilai'], lower_bound, upper_bound)
  ```

#### **d. Algoritma yang Lebih Tahan Terhadap Outlier**

Jika Anda membangun model pembelajaran mesin, beberapa algoritma lebih tahan terhadap outlier:

- **Decision Trees**: Algoritma ini tidak terlalu dipengaruhi oleh outlier karena mereka mempartisi data berdasarkan nilai-nilai tertentu.
  
- **Random Forest dan Gradient Boosting**: Kedua algoritma ini juga lebih robust terhadap outlier dibandingkan algoritma lain seperti regresi linier.

- **Robust Regression**: Teknik regresi yang lebih kuat seperti **Huber Regression** atau **RANSAC (Random Sample Consensus)** dapat digunakan untuk mengatasi outlier.

  Contoh kode Python untuk RANSAC:

  ```python
  from sklearn.linear_model import RANSACRegressor

  ransac = RANSACRegressor()
  ransac.fit(X, y)
  ```

---

### **Kesimpulan**

Pendeteksian dan penanganan outlier merupakan langkah penting dalam EDA dan modeling data. Outlier dapat sangat memengaruhi statistik deskriptif, distribusi data, dan kinerja model pembelajaran mesin. Dengan menggunakan metode visualisasi dan pendekatan statistik seperti Z-Score, IQR, dan Modified Z-Score, kita dapat mengidentifikasi outlier dengan lebih efektif. Penanganan outlier, seperti menghapus, mengimputasi, atau melakukan transformasi data, harus dilakukan dengan hati-hati agar hasil analisis lebih akurat dan relevan dengan tujuan bisnis.
