# **Panduan Lengkap PySpark**

## **1. Apa itu PySpark?**
PySpark adalah antarmuka Python untuk Apache Spark, yaitu sebuah framework pemrosesan data terdistribusi yang dirancang untuk menangani dan menganalisis data dalam skala besar (Big Data). Dengan PySpark, pengguna Python dapat memanfaatkan kekuatan Apache Spark untuk memproses, menganalisis, dan memodelkan data secara efisien dalam lingkungan terdistribusi, tanpa perlu memahami implementasi teknis pada tingkat rendah.

## **2. Fitur Utama PySpark**
1. **Kecepatan dan Skalabilitas**: Mendukung proses paralel yang cepat dan bisa diskalakan pada cluster besar.
2. **Kompatibilitas Multiplatform**: Bisa digunakan dengan berbagai bahasa, seperti Python, Scala, Java, dan R.
3. **Pemrosesan Data yang Beragam**:
   - Batch Processing
   - Real-Time Streaming
4. **Pustaka Tambahan**:
   - **MLlib** untuk pembelajaran mesin.
   - **GraphX** untuk analisis grafik.
   - **Spark SQL** untuk analisis data terstruktur.

## **3. Instalasi PySpark**
### **Proses Instalasi PySpark yang Sangat Lengkap**

Berikut adalah panduan instalasi lengkap untuk PySpark, mencakup persyaratan, konfigurasi, dan pengaturan untuk menjalankan PySpark di berbagai lingkungan. 

### **1. Persyaratan Sistem**
Sebelum menginstal PySpark, pastikan sistem Anda memenuhi persyaratan berikut:

#### **a. Sistem Operasi yang Didukung**
- **Windows**: Windows 10 atau lebih baru.
- **MacOS**: MacOS 10.13 atau lebih baru.
- **Linux**: Semua distribusi utama (Ubuntu, CentOS, Debian, dll.).

#### **b. Software yang Dibutuhkan**
1. **Python**: Versi 3.6 atau lebih baru.
2. **Java Development Kit (JDK)**: Versi 8 atau 11. (Spark membutuhkan JDK untuk menjalankan JVM.)
3. **Apache Spark**: Versi Spark terbaru (misalnya, 3.4.1).
4. (Opsional) **Hadoop**: Untuk integrasi dengan HDFS.

# **Panduan Lengkap Instalasi Apache Spark dan PySpark di Windows PC**

### **Persyaratan Awal**
Sebelum memulai instalasi, pastikan sistem Anda memiliki:
1. **Java Development Kit (JDK)**: Versi 8 atau lebih baru (disarankan JDK 11 atau JDK 19).
2. **Python**: Versi terbaru (contoh: Python 3.11.1).
3. **WinUtils.exe**: Diperlukan untuk menjalankan Spark di Windows.

### **Langkah-Langkah Instalasi**

#### **1. Instalasi Java Development Kit (JDK)**
1. **Unduh JDK**:
   - Buka browser dan cari "download JDK".
   - Kunjungi [Oracle JDK](https://www.oracle.com/java/technologies/javase-downloads.html) atau gunakan **OpenJDK**.
   - Unduh installer JDK (file `.exe`) untuk Windows (contoh: JDK 19).

2. **Instal JDK**:
   - Jalankan file `.exe` yang telah diunduh.
   - Saat proses instalasi, pilih direktori instalasi di **C:\Java\jdk**:
     - Buat folder `Java` di drive C.
     - Di dalam folder `Java`, buat folder `jdk`.

3. **Verifikasi Instalasi Java**:
   - Buka **Command Prompt**.
   - Ketik:
     ```bash
     java -version
     ```
   - Anda akan melihat versi JDK yang terinstal.

#### **2. Instalasi Python**
1. **Unduh Python**:
   - Kunjungi [python.org](https://www.python.org/downloads/).
   - Unduh versi terbaru (contoh: Python 3.11.1).

2. **Instal Python**:
   - Jalankan installer Python.
   - Centang **Add Python to PATH** untuk menambahkan Python ke variabel lingkungan secara otomatis.
   - Klik **Install Now**.

3. **Verifikasi Instalasi Python**:
   - Buka **Command Prompt**.
   - Ketik:
     ```bash
     python --version
     ```

#### **3. Unduh Apache Spark**
1. **Kunjungi Situs Apache Spark**:
   - Buka browser dan cari "download Apache Spark".
   - Kunjungi [situs resmi Spark](https://spark.apache.org/downloads.html).

2. **Pilih Versi Spark**:
   - Pilih versi Spark terbaru (contoh: 3.3.1).
   - Pilih **Pre-built for Apache Hadoop 2.7** untuk kompatibilitas dengan **WinUtils.exe**.

3. **Unduh File Spark**:
   - Unduh file tarball (contoh: `spark-3.3.1-bin-hadoop2.7.tgz`).

4. **Ekstrak File Spark**:
   - Gunakan **7-Zip** atau alat serupa untuk mengekstrak file:
     - Klik kanan pada file `.tgz` > **7-Zip** > **Extract Here**.
     - Ekstrak file `.tar` di dalamnya sehingga Anda mendapatkan folder seperti `spark-3.3.1-bin-hadoop2.7`.

5. **Pindahkan Folder Spark**:
   - Pindahkan folder hasil ekstraksi ke direktori permanen (contoh: `C:\Spark`).

#### **4. Unduh dan Konfigurasi WinUtils**
1. **Unduh WinUtils.exe**:
   - Kunjungi [GitHub WinUtils](https://github.com/steveloughran/winutils).
   - Navigasikan ke direktori untuk Hadoop 2.7 dan unduh **WinUtils.exe**.

2. **Buat Folder Hadoop**:
   - Buat folder di **C:\Hadoop\bin**.
   - Salin file `WinUtils.exe` ke folder **bin**.

#### **5. Konfigurasi Variabel Lingkungan**
1. **Buka Pengaturan Variabel Lingkungan**:
   - Cari **Environment Variables** di menu **Start** dan klik **Edit the system environment variables**.

2. **Tambahkan Variabel Baru**:
   - Tambahkan variabel berikut:
     - **JAVA_HOME**: Lokasi instalasi JDK (contoh: `C:\Java\jdk`).
     - **HADOOP_HOME**: Lokasi folder Hadoop (contoh: `C:\Hadoop`).
     - **SPARK_HOME**: Lokasi instalasi Spark (contoh: `C:\Spark`).
     - **PYSPARK_PYTHON**: Lokasi file Python (contoh: `C:\Users\YourUsername\AppData\Local\Programs\Python\Python311\python.exe`).

3. **Tambahkan Path untuk Bin Directories**:
   - Edit variabel **Path** dan tambahkan:
     ```plaintext
     %JAVA_HOME%\bin
     %HADOOP_HOME%\bin
     %SPARK_HOME%\bin
     ```

#### **6. Verifikasi Instalasi Spark**
1. **Buka Command Prompt**.
2. Jalankan Spark Shell:
   ```bash
   spark-shell
   ```
   - Jika berhasil, Anda akan melihat Spark Shell berjalan dengan versi Spark dan Scala yang terdeteksi.

3. **Jalankan PySpark**:
   ```bash
   pyspark
   ```
   - Jika berhasil, Anda akan masuk ke shell Python dengan SparkContext aktif.

4. **Cek Versi Spark**:
   Di dalam PySpark, jalankan:
   ```python
   print(spark.version)
   ```

## **Panduan Lengkap Dasar-Dasar PySpark**

PySpark adalah antarmuka Python untuk Apache Spark, yang memungkinkan pengolahan data besar secara paralel di cluster. Berikut adalah penjelasan mendalam mengenai dasar-dasar penggunaan PySpark, termasuk komponen utama, operasi dasar, dan praktik terbaik.

### **5.1. Membuat SparkSession**
`SparkSession` adalah titik awal untuk semua aplikasi PySpark. Objek ini digunakan untuk membuat DataFrame, menjalankan query SQL, dan berinteraksi dengan Spark.

#### **Kode Contoh: Membuat SparkSession**
```python
from pyspark.sql import SparkSession

# Membuat SparkSession
spark = SparkSession.builder \
    .appName("Aplikasi PySpark") \
    .getOrCreate()
```
- **`appName`**: Memberikan nama untuk aplikasi Anda.
- **`getOrCreate`**: Mengembalikan SparkSession baru atau menggunakan yang sudah ada.

### **5.2. Membaca Data**
PySpark mendukung berbagai format data, termasuk **CSV**, **JSON**, **Parquet**, dan lainnya.

#### **Kode Contoh: Membaca Berbagai Format Data**
```python
# Membaca file CSV
df_csv = spark.read.csv("path/to/file.csv", header=True, inferSchema=True)

# Membaca file JSON
df_json = spark.read.json("path/to/file.json")

# Membaca file Parquet
df_parquet = spark.read.parquet("path/to/file.parquet")
```
- **`header=True`**: Menentukan apakah file CSV memiliki header.
- **`inferSchema=True`**: Memungkinkan PySpark mendeteksi tipe data secara otomatis.

### **5.3. Struktur Data: DataFrame dan RDD**

#### **a. DataFrame**
DataFrame adalah struktur data utama di PySpark. Mirip dengan DataFrame Pandas, tetapi mampu bekerja secara terdistribusi.

#### **Operasi Dasar pada DataFrame**
```python
df.show()        # Menampilkan data (default 20 baris)
df.printSchema() # Menampilkan struktur skema DataFrame
```

#### **b. RDD (Resilient Distributed Dataset)**
RDD adalah struktur data dasar di Spark, cocok untuk data yang tidak terstruktur. Operasi pada RDD bersifat low-level dibandingkan DataFrame.

#### **Kode Contoh: Membuat dan Memanipulasi RDD**
```python
# Membuat RDD dari list
rdd = spark.sparkContext.parallelize([1, 2, 3, 4])

# Transformasi: Mengalikan setiap elemen dengan 2
rdd_transformed = rdd.map(lambda x: x * 2)

# Aksi: Mengumpulkan hasil
print(rdd_transformed.collect())  # Output: [2, 4, 6, 8]
```

## **6. Operasi Dasar pada DataFrame**

### **6.1. Transformasi**
Transformasi adalah operasi *lazy*, artinya tidak langsung dieksekusi hingga aksi dilakukan. Contoh transformasi:
- **`select`**: Memilih kolom tertentu.
- **`filter`**: Menyaring data berdasarkan kondisi.
- **`groupBy`**: Mengelompokkan data.

#### **Kode Contoh: Transformasi**
```python
# Memilih kolom
df.select("nama_kolom").show()

# Menyaring data
df.filter(df["nilai"] > 50).show()

# Mengelompokkan data
df.groupBy("kategori").count().show()
```
### **6.2. Aksi**
Aksi adalah operasi yang memicu eksekusi transformasi dan menghasilkan output. Contoh aksi:
- **`show()`**: Menampilkan data.
- **`count()`**: Menghitung jumlah baris.
- **`collect()`**: Mengembalikan semua data ke driver.

#### **Kode Contoh: Aksi**
```python
# Menampilkan data
df.show()

# Menghitung jumlah baris
print(df.count())

# Mengembalikan semua data ke driver
data = df.collect()
```

### **6.3. Menambah atau Memodifikasi Kolom**
Gunakan **`withColumn()`** untuk menambahkan atau memodifikasi kolom.

#### **Kode Contoh: Menambah atau Memodifikasi Kolom**
```python
from pyspark.sql.functions import col

# Menambahkan kolom baru
df = df.withColumn("kolom_baru", col("kolom_lama") * 2)
```

## **7. Spark SQL**
PySpark memungkinkan Anda menjalankan query SQL pada DataFrame menggunakan **Spark SQL**.

#### **Kode Contoh: Spark SQL**
```python
# Mendaftarkan DataFrame sebagai tabel SQL
df.createOrReplaceTempView("tabel_saya")

# Menjalankan query SQL
spark.sql("SELECT * FROM tabel_saya WHERE nilai > 50").show()
```

# STUDI KASUS

Berikut adalah langkah-langkah untuk melanjutkan studi kasus ini hingga proses *training* menggunakan dataset yang Anda berikan. Di akhir, kita akan membangun model *Machine Learning* sederhana menggunakan **PySpark MLlib** untuk memprediksi *rating* pelanggan berdasarkan fitur-fitur lain dalam dataset.


#### **1. Membuat SparkSession dan Membaca Dataset**
```python
from pyspark.sql import SparkSession

# Membuat SparkSession
spark = SparkSession.builder \
    .appName("Supermarket Sales Analysis with Training") \
    .getOrCreate()

# Membaca dataset
file_path = "supermarket_sales - Sheet1.csv"  # Pastikan file berada di lokasi yang sama
df = spark.read.csv(file_path, header=True, inferSchema=True)

# Menampilkan skema data
df.printSchema()
df.show(5)
```

#### **2. Pra-pemrosesan Data**

1. **Memilih Kolom Relevan**:
   Hanya kolom yang relevan akan digunakan untuk pelatihan model. Kita akan memilih:
   - *Unit price*, *Quantity*, *Total*, *Tax 5%*, dan *Rating*.

2. **Menghapus Baris dengan Nilai Null**:
   Kita akan menghapus baris yang memiliki nilai kosong di kolom yang relevan.

```python
# Memilih kolom yang relevan
df_selected = df.select("Unit price", "Quantity", "Total", "Tax 5%", "Rating")

# Menghapus baris dengan nilai null
df_cleaned = df_selected.dropna()

# Menampilkan data setelah dibersihkan
df_cleaned.show(5)
```

#### **3. Mengubah Data menjadi Format Fitur dan Label**
Untuk *training*, kita perlu menggabungkan fitur menjadi satu vektor menggunakan **VectorAssembler**.

```python
from pyspark.ml.feature import VectorAssembler

# Menggabungkan kolom fitur
feature_columns = ["Unit price", "Quantity", "Total", "Tax 5%"]
assembler = VectorAssembler(inputCols=feature_columns, outputCol="features")

# Menambahkan kolom fitur ke DataFrame
df_features = assembler.transform(df_cleaned)

# Menampilkan data dengan kolom fitur
df_features.select("features", "Rating").show(5)
```

#### **4. Membagi Data menjadi Data Latih dan Uji**
Kita akan membagi dataset menjadi data latih (*training*) dan data uji (*test*) dengan proporsi 80:20.

```python
# Membagi data menjadi training dan testing
train_data, test_data = df_features.randomSplit([0.8, 0.2], seed=42)

print(f"Jumlah data latih: {train_data.count()}")
print(f"Jumlah data uji: {test_data.count()}")
```

#### **5. Melatih Model dengan Regressor**
Gunakan regresi linier untuk memprediksi *rating* pelanggan berdasarkan fitur.

```python
from pyspark.ml.regression import LinearRegression

# Membuat model regresi linier
lr = LinearRegression(featuresCol="features", labelCol="Rating", predictionCol="prediction")

# Melatih model pada data latih
lr_model = lr.fit(train_data)

# Menampilkan koefisien dan intercept
print(f"Koefisien: {lr_model.coefficients}")
print(f"Intercept: {lr_model.intercept}")
```

#### **6. Mengevaluasi Model pada Data Uji**
Setelah model dilatih, evaluasi model pada data uji untuk mengukur performa.

```python
# Membuat prediksi pada data uji
predictions = lr_model.transform(test_data)

# Menampilkan hasil prediksi
predictions.select("features", "Rating", "prediction").show(5)

# Menghitung metrik evaluasi
from pyspark.ml.evaluation import RegressionEvaluator

evaluator = RegressionEvaluator(labelCol="Rating", predictionCol="prediction", metricName="rmse")
rmse = evaluator.evaluate(predictions)
print(f"Root Mean Squared Error (RMSE): {rmse}")
```