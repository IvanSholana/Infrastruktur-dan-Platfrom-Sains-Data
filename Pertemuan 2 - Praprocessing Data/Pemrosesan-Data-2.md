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

$$
Z = \frac{(X - \mu)}{\sigma}
$$

Dimana:
- $$\(X\)$$ adalah nilai data,
- $$\(\mu\)$$ adalah rata-rata populasi, dan
- $$\(\sigma\)$$ adalah deviasi standar populasi.

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

$$
IQR = Q3 - Q1
$$

Nilai di luar $$\( [Q1 - 1.5 \times IQR, Q3 + 1.5 \times IQR] \)$$ dianggap sebagai outlier.

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

$$
Z_{mod} = \frac{0.6745 \times (X - \text{Median})}{MAD}
$$

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

### **Apa itu Median Absolute Deviation (MAD)?**

**Median Absolute Deviation (MAD)** adalah ukuran statistik yang digunakan untuk mengukur penyebaran data, mirip dengan deviasi standar, tetapi lebih **robust** (tahan) terhadap outlier. MAD dihitung sebagai median dari deviasi absolut setiap titik data terhadap median data keseluruhan. Ini berarti MAD mengukur seberapa jauh setiap nilai menyimpang dari **median**, bukan dari **mean** seperti dalam kasus deviasi standar.

Rumus MAD adalah sebagai berikut:

$$
MAD = \text{median}(|X_i - \text{median}(X)|)
$$

Di mana:
- $$\(X\_i\)$$ adalah nilai data,
- $$\(text{median}(X)\)$$ adalah median dari dataset.

Jadi, pertama-tama kita menghitung median dari dataset. Kemudian, untuk setiap nilai data $$X_i$$, kita menghitung **deviasi absolut** (selisih antara nilai data dengan median). Terakhir, kita mengambil median dari deviasi absolut ini untuk mendapatkan MAD.

Baik, mari kita coba memberikan contoh yang lebih sederhana untuk memahami perbedaan **Modified Z-Score** dengan dan tanpa faktor **0.6745** menggunakan data yang lebih kecil, dan kita juga akan melihat bagaimana **deviasi standar** dan **MAD** bekerja.

### **Contoh Sederhana:**

Misalkan kita memiliki dataset yang sangat kecil:  
10, 12, 14, 16, 100 

Di sini, nilai **100** jelas merupakan outlier.

### **Langkah 1: Menghitung Z-Score (menggunakan standar deviasi)**
Rumus Z-Score:

Berikut adalah perhitungan yang disajikan dalam format yang lebih rapi:

1. **Menghitung rata-rata (\(\mu\)):**

$$
\mu = \frac{10 + 12 + 14 + 16 + 100}{5} = 30.4
$$

2. **Menghitung standar deviasi (\(\sigma\)):**

$$
\sigma = \sqrt{\frac{(10 - 30.4)^2 + (12 - 30.4)^2 + (14 - 30.4)^2 + (16 - 30.4)^2 + (100 - 30.4)^2}{5}} \approx 36.47
$$

3. **Menghitung Z-Score untuk nilai 100:**

$$
Z = \frac{100 - 30.4}{36.47} \approx 1.91
$$

Ini menunjukkan bagaimana nilai 100 berada sekitar 1.91 standar deviasi di atas rata-rata.
### **Langkah 2: Menghitung Modified Z-Score (menggunakan median dan MAD)**
Rumus Modified Z-Score:

$$
Z_{\text{mod}} = \frac{0.6745 \times (X - \text{Median})}{MAD}
$$

Berikut adalah penulisan ulang perhitungan yang lebih terstruktur:

1. **Menghitung median:**

$$
\text{Median} = 14 \quad \text{(nilai tengah dari dataset: [10, 12, 14, 16, 100])}
$$

2. **Menghitung Median Absolute Deviation (MAD):**

$$
\text{Deviasi Absolut} = |10 - 14|, |12 - 14|, |14 - 14|, |16 - 14|, |100 - 14| = 4, 2, 0, 2, 86
$$

Median dari deviasi absolut ini adalah 2 (nilai tengah dari [4, 2, 0, 2, 86] setelah diurutkan).

3. **Menghitung Modified Z-Score untuk nilai 100 (dengan faktor 0.6745):**

$$
Z_{\text{mod}} = \frac{0.6745 \times (100 - 14)}{2} = \frac{0.6745 \times 86}{2} \approx 28.99
$$

4. **Menghitung Modified Z-Score untuk nilai 100 (tanpa faktor 0.6745):**

$$
Z_{\text{mod}} = \frac{(100 - 14)}{2} = \frac{86}{2} = 43
$$

Perhitungan ini menunjukkan bahwa nilai 100 memiliki Modified Z-Score yang sangat tinggi, yang mengindikasikan bahwa 100 adalah outlier yang signifikan dalam dataset ini.

---

### **Perbandingan Hasil:**

- **Z-Score (menggunakan standar deviasi)**:  
  - Z-Score untuk nilai **100** = **1.91**

- **Modified Z-Score (dengan 0.6745)**:  
  - Modified Z-Score untuk nilai **100** = **28.99**

- **Modified Z-Score (tanpa 0.6745)**:  
  - Modified Z-Score untuk nilai **100** = **43**

### **Penjelasan:**
- **Z-Score** memberikan hasil yang relatif kecil (**1.91**) karena standar deviasi (\(\sigma = 36.47\)) sangat dipengaruhi oleh nilai outlier (**100**).
- **Modified Z-Score** dengan **0.6745** memberikan hasil yang lebih besar (**28.99**), tetapi lebih bisa dibandingkan dengan Z-Score karena sudah terkalibrasi untuk distribusi normal.
- **Modified Z-Score tanpa 0.6745** memberikan hasil yang jauh lebih besar (**43**), karena kita tidak menyesuaikan MAD dengan skala yang sesuai.

Nilai **0.6745** diperlukan untuk membuat **Modified Z-Score** sebanding dengan hasil dari Z-Score, sehingga lebih mudah untuk mendeteksi outlier dan melakukan analisis yang konsisten.

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

- **Clipping**: Memotong nilai outlier agar berada dalam rentang tertentu.

  Contoh kode Python:

  ```python
  df['nilai_clipped'] = np.clip(df['nilai'], lower_bound, upper_bound)
  ```
Mengubah skala data melalui **transformasi** adalah salah satu cara yang efektif untuk **menangani outlier** karena transformasi skala dapat **mengurangi pengaruh nilai-nilai ekstrem** (outlier) yang ada dalam dataset. Berikut adalah alasan utama mengapa transformasi skala bisa membantu menangani outlier:

### 1. **Mengurangi Rentang Nilai yang Terlalu Lebar**
Outlier seringkali muncul karena adanya nilai yang jauh lebih besar (atau lebih kecil) dari mayoritas data dalam dataset. Ini dapat menyebabkan distribusi data menjadi **skewed** atau tidak normal, di mana sebagian besar data berada di satu sisi, sementara outlier berada jauh di sisi lain.

Ketika kita menggunakan metode transformasi seperti **log transformation** atau **reciprocal transformation**, kita **mengompres rentang nilai** data. Transformasi ini membuat nilai-nilai yang sangat besar menjadi lebih kecil dan mendekati nilai lainnya dalam dataset. Ini berarti outlier tidak lagi menonjol atau mempengaruhi analisis secara berlebihan.

#### Contoh Sederhana:
Misalkan kita memiliki data berikut: [10, 12, 15, 20, 200].
- **Tanpa transformasi**: Nilai **200** jauh lebih besar dari nilai lainnya, dan ini akan mendominasi statistik seperti mean, standar deviasi, dan membuat distribusi skewed.
- **Setelah log transformation**: Nilai 200 akan berubah menjadi **\(\log(200) \approx 5.3\)**, mendekati nilai-nilai yang lain seperti $$\(\log(10) = 2.3\)$$ dan $$\(\log(20) = 3\)$$. Dengan demikian, pengaruh dari outlier berkurang karena skalanya menjadi lebih sebanding dengan data lainnya.


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
